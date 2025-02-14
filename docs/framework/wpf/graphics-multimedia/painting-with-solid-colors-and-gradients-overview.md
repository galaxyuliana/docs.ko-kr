---
title: 단색 및 그라데이션을 사용한 그리기 개요
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- painting with gradients [WPF]
- gradients [WPF], painting with
- brushes [WPF], painting with solid colors
- brushes [WPF], painting with gradients
- painting with solid colors [WPF]
ms.assetid: f5b182f3-c5c7-4cbe-9f2f-65e690d08255
ms.openlocfilehash: 5ba8127d5be24a9fdcccf0bebcc08e5699d98033
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238397"
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>단색 및 그라데이션을 사용한 그리기 개요
이 항목에서는 사용 하는 방법을 설명 <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.LinearGradientBrush>, 및 <xref:System.Windows.Media.RadialGradientBrush> 단색, 선형 그라데이션 및 방사형 그라데이션을 그릴 개체입니다.  

<a name="solidcolor"></a>   
## <a name="painting-an-area-with-a-solid-color"></a>단색으로 영역 그리기  
 단색으로 영역 그리기를 모든 플랫폼에서 가장 일반적인 작업 중 <xref:System.Windows.Media.Color>합니다. 이 작업을 수행할 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 제공 된 <xref:System.Windows.Media.SolidColorBrush> 클래스입니다. 다음 섹션에서는 다양 한 방법을 사용 하 여 그리기를 <xref:System.Windows.Media.SolidColorBrush>입니다.  
  
<a name="solidcolorinxaml"></a>   
### <a name="using-a-solidcolorbrush-in-xaml"></a>"XAML"에서 SolidColorBrush 사용  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]에서 단색으로 영역을 그리려면 다음 옵션 중 하나를 사용합니다.  
  
- 미리 정의된 단색 브러시를 이름으로 선택합니다.  예를 들어, 단추를 설정할 수 있습니다 <xref:System.Windows.Controls.Control.Background%2A> "Red" 또는 "mediumblue 로" 합니다.  단색 브러시 목록을 다른 미리 정의의 정적 속성 참조는 <xref:System.Windows.Media.Brushes> 클래스입니다. 다음은 예제입니다.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]  
  
- 단색으로 조합할 빨강, 녹색 및 파랑의 양을 지정하여 32비트 색상표에서 색을 선택합니다.  32비트 색상표에서 색을 지정하기 위한 형식은 " *#rrggbb*"입니다. 여기서 *rr*은 빨강의 상대적 양을 지정하는 2자리 16진수 숫자이고 *gg*는 녹색의 양을 지정하고, *bb*는 파랑의 양을 지정합니다.  또한 "#*aarrggbb*"로 색을 지정할 수도 있습니다. 여기서 *aa*는 색의 *알파* 값 또는 투명도를 지정합니다. 이 방법은 사용하면 부분적으로 투명한 색을 만들 수 있습니다.  다음 예제에서는 <xref:System.Windows.Controls.Control.Background%2A> 의 <xref:System.Windows.Controls.Button> 16 진수 표기법을 사용 하는 완전히 불투명 한 빨강으로 설정 됩니다.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]  
  
- 속성 태그 구문을 설명 하는 데는 <xref:System.Windows.Media.SolidColorBrush>합니다. 이 구문은 좀 더 복잡하지만 브러시의 불투명도 등의 추가 설정을 지정할 수 있습니다. 다음 예제에서는 <xref:System.Windows.Controls.Control.Background%2A> 의 두 속성 <xref:System.Windows.Controls.Button> 요소는 완전히 불투명 한 빨강으로 설정 됩니다. 첫 번째 브러시 색은 미리 정의된 색 이름을 사용하여 설명됩니다. 두 번째 브러시 색은 16진수 표기법을 사용하여 설명됩니다.  
  
     [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]  
  
<a name="solidcolorsincode"></a>   
### <a name="painting-with-a-solidcolorbrush-in-code"></a>코드에서 SolidColorBrush를 사용하여 그리기  
 단색으로 영역을 그리려면 다음 옵션 중 하나를 사용합니다.  
  
- 제공한 미리 정의 된 브러시 중 하나를 사용 하 여 <xref:System.Windows.Media.Brushes> 클래스입니다. 다음 예제에서는 <xref:System.Windows.Controls.Control.Background%2A> 의 <xref:System.Windows.Controls.Button> 로 설정 된 <xref:System.Windows.Media.Brushes.Red%2A>합니다.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]  
  
- 만들기는 <xref:System.Windows.Media.SolidColorBrush> 설정 및 해당 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 사용 하 여 속성을 <xref:System.Windows.Media.Color> 구조입니다. 미리 정의 된 색을 사용할 수는 <xref:System.Windows.Media.Colors> 클래스 만들 수 있습니다를 <xref:System.Windows.Media.Color> 정적을 사용 하 여 <xref:System.Windows.Media.Color.FromArgb%2A> 메서드.  
  
     다음 예제에서는 설정 하는 방법을 보여 줍니다 합니다 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 의 속성을 <xref:System.Windows.Media.SolidColorBrush> 미리 정의 된 색을 사용 하 여 합니다.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]  
  
 정적 <xref:System.Windows.Media.Color.FromArgb%2A> 색의 알파, 빨강, 녹색 및 파랑 값을 지정할 수 있습니다. 이러한 각 값의 일반적인 범위는 0-255입니다. 예를 들어 알파 값이 0이면 색이 완전히 투명하고, 값이 255이면 색이 완전히 불투명합니다. 마찬가지로 빨강 값이 0이면 색에 빨강이 전혀 없는 것이지만 255이면 최대의 빨강이 포함되어 있는 것입니다.  다음 예제에서 브러시의 색은 알파, 빨강, 녹색 및 파랑 값을 지정하여 설명됩니다.  
  
 [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]  
  
 색을 지정 하는 다른 방법에 대해서는 <xref:System.Windows.Media.Color> 참조 항목입니다.  
  
<a name="gradient"></a>   
## <a name="painting-an-area-with-a-gradient"></a>그라데이션으로 영역 그리기  
 그라데이션 브러시는 축을 따라 서로 혼합되는 여러 색으로 영역을 그립니다. 이를 사용하여 빛과 그림자를 나타내고 컨트롤에 3차원 느낌을 줄 수 있습니다. 또한 유리, 크롬, 물, 기타 매끄러운 표면을 시뮬레이트하는 데도 사용할 수 있습니다.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 두 가지 유형의 그라데이션 브러시를 제공 합니다. <xref:System.Windows.Media.LinearGradientBrush> 고 <xref:System.Windows.Media.RadialGradientBrush>입니다.  
  
<a name="lineargradientbrush"></a>   
## <a name="linear-gradients"></a>선형 그라데이션  
 A <xref:System.Windows.Media.LinearGradientBrush> 는 선을 따라 정의 된 그라데이션으로 영역을 그리는 합니다 *그라데이션 축*합니다.  그라데이션 중지점의 색 및 사용 하 여 그라데이션 축을 따라 위치를 지정할 <xref:System.Windows.Media.GradientStop> 개체입니다.  그라데이션 축을 수정하여 가로 및 세로 그라데이션을 만들고 그라데이션 방향을 반대로 바꿀 수도 있습니다. 그라데이션 축은 다음 섹션에서 설명합니다. 기본적으로는 대각선 그라데이션이 생성됩니다.  
  
 다음 예제에서는 네 가지 색으로 선형 그라데이션을 만드는 코드를 보여 줍니다.  
  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 이 코드는 다음 그라데이션을 생성합니다.  
  
 ![대각선 선형 그라데이션](./media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")  
  
 **참고:** 이 항목의 그라데이션 예제는 시작점 및 끝점 설정에 대 한 기본 좌표계를 사용 합니다. 기본 좌표계는 경계 상자를 기준으로 합니다. 0의 경계 상자 및 1 0% 나타냅니다 경계 상자의 100%를 나타냅니다. 설정 하 여이 좌표계를 변경할 수 있습니다 합니다 <xref:System.Windows.Media.GradientBrush.MappingMode%2A> 속성 값을 <xref:System.Windows.Media.BrushMappingMode.Absolute>입니다. 절대 좌표계는 경계 상자를 기준으로 하지 않습니다. 값은 로컬 공간에서 직접 해석됩니다.  
  
 <xref:System.Windows.Media.GradientStop> 그라데이션 브러시의 기본 빌딩 블록입니다.  그라데이션 중지점 지정 된 <xref:System.Windows.Media.GradientStop.Color%2A> 에 <xref:System.Windows.Media.GradientStop.Offset%2A> 그라데이션 축을 따라 합니다.  
  
- 그라데이션 중지점의 <xref:System.Windows.Media.GradientStop.Color%2A> 속성은 그라데이션 중지점의 색을 지정 합니다. 미리 정의 된 색을 사용 하 여 색을 설정할 수 있습니다 (제공한는 <xref:System.Windows.Media.Colors> 클래스) 또는 ScRGB 또는 ARGB 값을 지정 합니다. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]에서는 16진수 표기법을 사용하여 색을 설명할 수도 있습니다. 자세한 내용은 참조는 <xref:System.Windows.Media.Color> 구조입니다.  
  
- 그라데이션 중지점의 <xref:System.Windows.Media.GradientStop.Offset%2A> 속성은 그라데이션 축에서 그라데이션 중지점의 색의 위치를 지정 합니다. 오프셋은을 <xref:System.Double> 0에서 1로 범위입니다. 그라데이션 중지점의 오프셋 값이 0에 가까울수록 색이 그라데이션의 시작에 더 가깝습니다. 그라데이션 중지점의 오프셋 값이 1에 가까울수록 색이 그라데이션의 끝에 더 가깝습니다.  
  
 그라데이션 중지점 사이에 있는 각 점의 색은 두 경계 그라데이션 중지점으로 지정되는 색 조합으로 선형 보간됩니다. 다음 그림에서는 이전 예제의 그라데이션 중지점을 강조해서 보여 줍니다. 그라데이션 중지점에는 동그라미가 그려져 있고 그라데이션 축은 점선으로 표시됩니다.  
  
 ![선형 그라데이션의 그라데이션 중지점](./media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")  
  
 첫 번째 그라데이션 중지점은 오프셋 `0.0`에서 노란색을 지정합니다.  두 번째 그라데이션 중지점은 오프셋 `0.25`에서 빨간색을 지정합니다.  이러한 두 중지점 사이에 있는 점들은 그라데이션 축을 따라 왼쪽에서 오른쪽으로 이동할 때 노란색에서 빨간색으로 서서히 변경됩니다.  세 번째 그라데이션 중지점은 오프셋 `0.75`에서 파란색을 지정합니다.  두 번째 및 세 번째 그라데이션 중지점 사이에 있는 점들은 빨간색에서 파란색으로 서서히 변경됩니다. 네 번째 그라데이션 중지점은 오프셋 `1.0`에서 라임 녹색을 지정합니다. 세 번째 및 네 번째 그라데이션 중지점 사이에 있는 점들은 파란색에서 라임 녹색으로 서서히 변경됩니다.  
  
<a name="gradientaxis"></a>   
### <a name="the-gradient-axis"></a>그라데이션 축  
 앞서 설명한 것처럼 선형 그라데이션 브러시의 그라데이션 중지점은 그라데이션 축에 해당하는 선을 따라 배치됩니다. 방향 및 브러시를 사용 하 여 선의 크기를 변경할 수 있습니다 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 고 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 속성입니다. 브러시의 조작 하 여 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 고 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, 가로 만들 수 있습니다 및 세로 그라데이션을 그라데이션 방향을 반대로, 그라데이션 확산을 축소 합니다.  
  
 기본적으로 선형 그라데이션 브러시의 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 고 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 그려지는 영역을 기준으로 합니다. 점 (0,0)은 그리는 영역의 왼쪽 위 구석을 나타내고 (1,1)은 그리는 영역의 오른쪽 아래 구석을 나타냅니다. 기본값 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 의 <xref:System.Windows.Media.LinearGradientBrush> 은 (0, 0) 및 해당 기본 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> (1, 1) 왼쪽 위 모퉁이에서 시작 하 고 그리는 영역의 오른쪽 아래 모서리에 확장 대각선 그라데이션을 만듭니다. 다음 그림에서는 기본값을 사용 하 여 선형 그라데이션 브러시의 그라데이션 축은 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 고 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>입니다.  
  
 ![대각선 선형 그라데이션의 그라데이션 축](./media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")  
  
 다음 예제에서는 만드는 방법을 보여 줍니다 가로 그라데이션 브러시를 지정 하 여 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 고 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>입니다. 그라데이션 중지점의 이전 예와 동일한 지 확인할 수 있습니다. 단순히 변경 하 여는 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 고 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, 그라데이션 대각선에서 가로로 변경 되었습니다.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 다음 그림은 만들어진 그라데이션을 보여 줍니다. 그라데이션 축은 점선으로 표시되고 그라데이션 중지점은 동그라미로 표시됩니다.  
  
 ![가로 선형 그라데이션의 그라데이션 축](./media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")  
  
 다음 예제에서는 세로 그라데이션을 만드는 방법을 보여 줍니다.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 다음 그림은 만들어진 그라데이션을 보여 줍니다. 그라데이션 축은 점선으로 표시되고 그라데이션 중지점은 동그라미로 표시됩니다.  
  
 ![세로 그라데이션의 그라데이션 축](./media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")  
  
<a name="radialgradients"></a>   
## <a name="radial-gradients"></a>방사형 그라데이션  
 같은 <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush> 축을 따라 함께 혼합 되는 색으로 영역을 그립니다. 이전 예제에서는 어떻게 선형 그라데이션 브러시의 축이 직선이 되는지를 보여 주었습니다. 방사형 그라데이션 브러시의 축은 원으로 정의되고 해당 색은 원점에서 바깥으로 "방사"됩니다.  
  
 다음 예제에서는 방사형 그라데이션 브러시를 사용하여 사각형의 내부를 그립니다.  
  
 [!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]  
  
 다음 그림은 이전 예제에서 만든 그라데이션을 보여 줍니다. 브러시의 그라데이션 중지점은 강조 표시되어 있습니다. 결과는 다르지만 이 예제의 그라데이션 중지점은 이전 선형 그라데이션 브러시 예제의 그라데이션 중지점과 동일합니다.  
  
 ![방사형 그라데이션의 그라데이션 중지점](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops")  
  
 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> 방사형 그라데이션 브러시의 그라데이션 축의 시작점을 지정 합니다. 그라데이션 축은 그라데이션 원점에서 그라데이션 원으로 방사됩니다. 브러시의 그라데이션 원은 정의한 해당 <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, 및 <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> 속성입니다.  
  
 다음 그림에서는 다른 몇 개의 방사형 그라데이션을 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>, <xref:System.Windows.Media.RadialGradientBrush.Center%2A>를 <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A>, 및 <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> 설정 합니다.  
  
 ![RadialGradientBrush 설정](./media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii")  
다른 GradientOrigin, Center, RadiusX 및 RadiusY 설정을 갖는 RadialGradientBrushes입니다.  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>투명 또는 부분적으로 투명한 그라데이션 중지점 지정  
 그라데이션 중지점은 불투명도 속성을 제공 하지 않으므로, 태그 또는 사용에 ARGB 16 진수 표기법을 사용 하 여 색의 알파 채널 지정 해야 합니다는 <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> 투명 하거나 부분적으로 투명 한 그라데이션 중 지점을 만들어야 하는 방법입니다. 다음 섹션에서는 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 및 코드에서 부분적으로 투명한 그라데이션 중지점을 만드는 방법을 설명합니다.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>"XAML"에서 색 불투명도 지정  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ARGB 16 진수 표기법을 사용 하 여 개별 색의 불투명도 지정 합니다. ARGB 16 진수 표기법으로 다음 구문을 사용합니다.  
  
 `#` **aa** *rrggbb*  
  
 이전 줄의 *aa*는 색의 불투명도 지정하는 데 사용되는 2자리 16진수 값을 나타냅니다. *rr*, *gg* 및 *bb* 각각은 색에서 빨강, 녹색 및 파랑의 양을 지정하는 데 사용되는 2자리 16진수 값을 나타냅니다. 각 16진수 숫자는 0-9 또는 A-F의 값을 가질 수 있습니다. 0이 가장 작은 값이고 F가 가장 큰 값입니다. 알파 값 00은 완전히 투명한 색을 지정하지만 알파 값 FF는 완전히 불투명한 색을 만듭니다.  다음 예제에서는 16 진수 ARGB 표기법은 두 색을 지정 하려면 사용 됩니다. 첫 번째는 부분적으로 투명하지만(알파 값 x20), 두 번째는 완전히 불투명합니다.  
  
 [!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]  
  
<a name="fromscrgbsyntax"></a>   
### <a name="specifying-color-opacity-in-code"></a>코드에서 색 불투명도 지정  
 정적 코드를 사용 하는 경우 <xref:System.Windows.Media.Color.FromArgb%2A> 메서드를 사용 하면 색을 만들 때 알파 값을 지정할 수 있습니다. 메서드는 4 개의 매개 변수 형식의 <xref:System.Byte>합니다. 첫 번째 매개 변수는 색의 알파 채널을 지정하고, 나머지 매개 변수 3개는 색의 빨강, 녹색 및 파랑 값을 지정합니다. 각 값은 0에서 255 이하여야 합니다. 알파 값이 0이면 색이 완전히 투명하고, 알파 값이 255이면 색이 완전히 불투명한 것입니다. 다음 예에서 <xref:System.Windows.Media.Color.FromArgb%2A> 메서드는 두 가지 색을 만드는 데 사용 됩니다. 첫 번째 색은 부분적으로 투명하지만(알파 값 32), 두 번째 색은 완전히 불투명합니다.  
  
 [!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]  
  
 사용할 수 있습니다는 <xref:System.Windows.Media.Color.FromScRgb%2A> 메서드 ScRGB 값을 사용 하 여 색을 만들 수 있습니다.  
  
<a name="otherbrushes"></a>   
## <a name="painting-with-images-drawings-visuals-and-patterns"></a>이미지, 그림, 시각적 표시 및 패턴으로 그리기  
 <xref:System.Windows.Media.ImageBrush>를 <xref:System.Windows.Media.DrawingBrush>, 및 <xref:System.Windows.Media.VisualBrush> 클래스를 사용 하면 이미지, 그림 및 시각적 개체를 사용 하 여 영역을 그릴 수 있습니다. 이미지, 그림 및 패턴으로 그리기에 대한 자세한 내용은 [이미지, 그림 및 시각적 표시로 그리기](painting-with-images-drawings-and-visuals.md)를 참조하세요.  
  
## <a name="see-also"></a>참고자료

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- [이미지, 그림 및 시각적 표시로 그리기](painting-with-images-drawings-and-visuals.md)
- [브러시 변환 개요](brush-transformation-overview.md)
- [그래픽 렌더링 계층](../advanced/graphics-rendering-tiers.md)
