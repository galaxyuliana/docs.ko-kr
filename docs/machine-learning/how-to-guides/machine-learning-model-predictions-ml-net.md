---
title: 학습된 모델로 예측
description: 학습된 모델을 사용한 예측 알아보기
ms.date: 06/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: ef2b22ff220d1fce1ec43f26c7d51f7e551e038d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307392"
---
# <a name="make-predictions-with-a-trained-model"></a>학습된 모델로 예측

학습된 모델을 사용하여 예측을 수행하는 방법 알아보기

## <a name="create-data-models"></a>데이터 모델 만들기

### <a name="input-data"></a>입력 데이터

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="output-data"></a>출력 데이터

`Features` 및 `Label` 열 이름처럼 ML.NET에는 모델에서 생성한 예측된 값 열에 대한 기본 이름이 있습니다. 작업에 따라 이 이름을 달라질 수 있습니다.

이 샘플에서 사용하는 알고리즘은 선형 회귀 알고리즘이므로 출력 열의 기본 이름은 `Score`이며 `PredictedPrice` 속성에 대한 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 특성으로 정의됩니다.

```csharp
class HousingPrediction : HousingData
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

`HousingPrediction` 데이터 모델은 `HousingData`에서 상속되므로 모델에서 생성된 출력과 함께 원래의 입력 데이터를 간편하게 시각화할 수 있습니다.  

## <a name="set-up-a-prediction-pipeline"></a>예측 파이프라인 설정

단일 또는 일괄 처리 예측 모두에서 예측 파이프라인을 애플리케이션에 로드해야 합니다. 이 파이프라인은 미리 처리된 변환과 학습된 모델을 모두 포함합니다. 아래 코드 조각은 이름이 `model.zip`인 파일에서 예측 파이프라인을 로드합니다.

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>단일 예측

단일 예측을 만들려면 로드된 예측 파이프라인을 사용하여 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)을 만듭니다.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

그런 다음, [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) 메서드를 사용하여 입력 데이터를 매개 변수로 전달합니다. [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) 메서드를 사용할 때는 입력이 [`IDataView`](xref:Microsoft.ML.IDataView)가 되지 않아도 됩니다. 이것은 입력 데이터 형식의 개체를 전달할 수 있도록 입력 데이터 형식 조작을 간편하게 내부화하기 때문입니다. 또한 `CurrentPrice`는 새 데이터를 통해 예측하려는 대상 또는 레이블이므로 해당 시점에는 값이 없다고 가정합니다.

```csharp
// Input Data
HousingData inputData = new HousingData
{
    Size = 900f,
    HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
};

// Get Prediction
HousingPrediction prediction = predictionEngine.Predict(inputData);
```

`prediction` 개체의 `Score` 속성에 액세스할 경우 `150079`와 유사한 값을 가져와야 합니다.

## <a name="batch-prediction"></a>일괄 처리 예측

다음 데이터의 경우 [`IDataView`](xref:Microsoft.ML.IDataView)에 로드합니다. 이 경우 [`IDataView`](xref:Microsoft.ML.IDataView)의 이름은 `inputData`입니다. `CurrentPrice`는 새 데이터를 통해 예측하려는 대상 또는 레이블이므로 해당 시점에는 값이 없다고 가정합니다.

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f }
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f }
    }
};
```

이제 [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) 메서드를 사용하여 데이터 변환을 적용하고 예측을 생성합니다.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) 메서드를 사용하여 예측된 값을 검사합니다.

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

점수 열의 예측된 값은 다음과 유사합니다.

| 관측 | 예측 |
|---|---|
| 1 | 144638.2 |
| 2 | 150079.4 |
| 3 | 107789.8 |
