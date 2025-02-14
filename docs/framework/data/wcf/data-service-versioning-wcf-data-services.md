---
title: 데이터 서비스 버전 관리(WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: 9a58f375821109c0ec5f2230ae330dc6a2caa102
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959498"
---
# <a name="data-service-versioning-wcf-data-services"></a>데이터 서비스 버전 관리(WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 클라이언트 리소스 Uri를 사용 하 여 데이터 모델을 기반으로 하는 데이터를 액세스할 수 있도록 데이터 서비스를 만들 수 있습니다. 또한 OData 서비스 작업의 정의 지원합니다. 이러한 데이터 서비스는 비즈니스 요구 사항의 변경, 정보 기술의 요구 사항 또는 다른 문제 해결 등의 다양한 이유 때문에 최초로 배포된 후, 수명 동안 여러 차례에 걸쳐 변경되어야 할 수 있습니다. 기존 데이터 서비스를 변경한 경우 새 버전의 데이터 서비스를 정의할 것인지 그리고 기존 클라이언트 애플리케이션에 미치는 영향을 최소화할 최선의 방법을 고려해야 합니다. 이 항목에서는 새 버전의 데이터 서비스를 만드는 방법 및 시기에 대한 지침을 제공합니다. WCF Data Services 클라이언트 및 OData 프로토콜의 다른 버전을 지 원하는 데이터 서비스 간의 교환을 처리 하는 방법을 설명 합니다.

## <a name="versioning-a-wcf-data-service"></a>WCF Data Service 버전 관리
 데이터 서비스를 배포한 후 데이터가 사용되고 있을 때 데이터 서비스를 변경하면 기존 클라이언트 애플리케이션에 호환성 문제가 나타날 수 있습니다. 하지만 서비스의 전반적 비즈니스 요구 사항으로 인해 변경이 필요한 경우가 많기 때문에 클라이언트 애플리케이션에 가장 적은 영향을 미치면서 데이터 서비스의 새 버전을 만들 시기와 방법을 고려해야 합니다.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>새 데이터 서비스 버전을 권장하는 데이터 모델 변경
 데이터 서비스의 새로운 버전을 게시할 것인지를 고려할 때에는 다른 종류의 변경이 클라이언트 애플리케이션에 어떻게 영향을 미칠 것인가를 이해하는 것이 중요합니다. 데이터 서비스의 새로운 버전을 만들어야 할 수 있는 데이터 서비스 변경은 다음 두 가지 범주로 나눌 수 있습니다.

- 서비스 계약 변경 - 서비스 작업 업데이트, 엔터티 집합(피드)의 액세스 가능성 변경, 버전 변경, 기타 서비스 동작 변경이 포함됩니다.

- 데이터 계약 변경 - 데이터 모델 또는 피드 형식 변경이나 피드 사용자 지정이 포함됩니다.

 다음 표에는 새 버전의 데이터 서비스를 게시할 때 고려해야 하는 변경의 종류가 자세히 나와 있습니다.

|변경 형식|새 버전 필요|새 버전이 필요하지 않음|
|--------------------|----------------------------|----------------------------|
|서비스 작업|-새 매개 변수를 추가 합니다.<br />반환 형식 변경<br />-서비스 작업을 제거 합니다.|--기존 매개 변수를 삭제 하는 중<br />-새 서비스 작업을 추가 합니다.|
|서비스 동작|-계산 요청 사용 하지 않도록 설정<br />-프로젝션 지원 사용 안 함<br />-필요한 데이터 서비스 버전 증가|--개수 요청을 사용 하는 중<br />-프로젝션 지원 사용<br />-필요한 데이터 서비스 버전 감소|
|엔터티 집합 권한|-엔터티 집합 권한 제한<br />--응답 코드를 변경 하는 중 (새로운 첫 번째 숫자 값) <sup>1</sup>|-엔터티 집합 권한 완화<br />--응답 코드를 변경 하는 중 (동일한 첫 번째 숫자 값)|
|엔터티 속성|-기존 속성 또는 관계 제거<br />--Nullable이 아닌 속성을 추가 하는 중<br />--기존 속성을 변경 하는 중|--Null 허용 속성을 추가 하는 중<sup>2</sup>|
|엔터티 집합|-엔터티 집합을 제거 합니다.|-파생된 형식 추가<br />기본 형식 변경<br />--엔터티 집합을 추가 하는 중|
|피드 사용자 지정|-엔터티 속성 매핑을 변경 합니다.||

 <sup>1</sup> 이 특정 오류 코드를 받으면 클라이언트 응용 프로그램을 사용 하는 얼마나 엄격 하 게 종속 될 수 있습니다.

 <sup>2</sup> 설정할 수 있습니다 합니다 <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> 속성을 `true` 클라이언트가 클라이언트에 정의 되어 있지 않은 데이터 서비스에서 보낸 새 속성을 무시 하도록 합니다. 그러나 삽입이 수행되면 클라이언트에 의해 POST 요청에 포함되지 않은 속성이 기본값으로 설정됩니다. 업데이트의 경우 클라이언트에 알려지지 않은 속성의 모든 기존 데이터는 기본값으로 덮어쓰여질 수 있습니다. 이 경우 업데이트를 기본값인 MERGE 요청으로 보내야 합니다. 자세한 내용은 [데이터 서비스 컨텍스트 관리](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)합니다.

### <a name="how-to-version-a-data-service"></a>데이터 서비스 버전을 관리하는 방법
 필요한 경우 업데이트된 서비스 계약 또는 데이터 모델로 서비스의 새 인스턴스를 만들어 새 데이터 서비스 버전을 정의할 수 있습니다. 그런 다음 이 새로운 서비스는 이전 버전과 차별화하는 새 URI 엔드포인트를 사용하여 노출됩니다. 예를 들어:

- 이전 버전: `http://services.odata.org/Northwind/v1/Northwind.svc/`

- 새 버전: `http://services.odata.org/Northwind/v2/Northwind.svc/`

 또한 데이터 서비스를 업그레이드 하는 경우 새 데이터 서비스 메타데이터를 기반으로 클라이언트를 업데이트해야 하고 클라이언트에서 새 루트 URI를 사용해야 합니다. 가능한 경우, 아직 업그레이드되지 않아 새 버전을 사용하지 않는 클라이언트를 지원할 수 있도록 이전 버전의 데이터 서비스를 유지해야 합니다. 이전 버전의 데이터 서비스가 더 이상 필요하지 않으면 제거할 수 있습니다. 외부 구성 파일에 데이터 서비스 엔드포인트의 URI를 유지하는 것을 고려해야 합니다.

## <a name="odata-protocol-versions"></a>OData 프로토콜 버전
 OData의 새 버전이 출시 되 면 클라이언트 응용 프로그램 사용 하지 않을 데이터 서비스에서 지원 되는 OData 프로토콜의 동일한 버전입니다. 이전 클라이언트 응용 프로그램이 최신 버전의 OData 지 원하는 데이터 서비스에 액세스할 수 있습니다. 또한 클라이언트 응용 프로그램을 액세스 하는 데이터 서비스를 보다 최신 버전의 OData 지 원하는 WCF Data Services 클라이언트 라이브러리의 최신 버전을 사용할 수 있습니다.

 WCF Data Services는 이러한 버전 관리 시나리오를 처리 하는 OData에서 제공 하는 지원을 활용 합니다. 지원도 생성 하 고 데이터 모델 메타 데이터를 사용 하 여 클라이언트를 다른 버전의 OData 데이터를 사용 하는 경우 클라이언트 데이터 서비스 클래스를 만드는 데 사용 하 여 서비스입니다. 자세한 내용은 참조 하세요. [OData: 버전 관리 프로토콜](https://go.microsoft.com/fwlink/?LinkId=186071)합니다.

### <a name="version-negotiation"></a>버전 협상
 클라이언트에서 요청한 버전에 관계 없이 서비스에 사용할 OData 프로토콜의 가장 높은 버전을 정의 하려면 데이터 서비스를 구성할 수 있습니다. 지정 하 여이 수행할 수 있습니다는 <xref:System.Data.Services.Common.DataServiceProtocolVersion> 값을 <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> 의 속성은 <xref:System.Data.Services.DataServiceBehavior> 데이터 서비스에서 사용 하는. 자세한 내용은 [데이터 서비스 구성](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)합니다.

 WCF Data Services 클라이언트 라이브러리를 사용 하 여 데이터 서비스에 액세스 하는 응용 프로그램, 라이브러리 버전 OData 및 응용 프로그램에서 사용 되는 기능에 따라 올바른 값으로 이러한 헤더를 자동으로 설정 합니다. 기본적으로 WCF Data Services는 요청한 작업을 지 원하는 가장 낮은 프로토콜 버전을 사용 합니다.

 다음 테이블 세부 정보를 WCF Data Services를 포함 하는 버전의.NET Framework 및 Silverlight OData 프로토콜의 특정 버전에 대 한 지원.

|OData 프로토콜 버전|도입된 지원|
|-----------------------------------------------------------------------------------|----------------------------|
|버전 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 서비스 팩 1 (SP1)<br />Silverlight 버전 3|
|버전 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-업데이트 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] SP1. 다운로드 하 여에서 업데이트를 설치 합니다 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/?LinkId=158125)합니다.<br />Silverlight 버전 4|
|버전 3|-다운로드 하 고 수에서 OData 버전 3을 지 원하는 시험판 버전을 설치 합니다 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/?LinkId=203885)합니다.|

### <a name="metadata-versions"></a>메타데이터 버전
 기본적으로 WCF Data Services CSDL 버전 1.1을 사용 하 여 데이터 모델을 나타냅니다. 이는 리플렉션 공급자 또는 사용자 지정 데이터 서비스 공급자를 기반으로 하는 데이터 모델의 경우 항상 해당됩니다. 그러나 데이터 모델이 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]를 사용하여 정의된 경우 반환된 CSDL 버전은 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]에서 사용되는 버전과 동일합니다. CSDL의 버전의 네임 스페이스에 의해 결정 됩니다 합니다 [스키마 요소 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl)합니다.

 반환된 메타데이터의 `DataServices` 요소에는 응답 메시지의 `DataServiceVersion` 헤더와 값이 동일한 `DataServiceVersion` 특성도 포함되어 있습니다. 클라이언트 응용 프로그램 같은 합니다 **서비스 참조 추가** 대화 상자 데이터 서비스를 호스팅하는 WCF Data Services의 버전과 올바르게 작동 하는 클라이언트 데이터 서비스 클래스를 생성 하려면 Visual Studio에서이 정보를 사용 합니다. 자세한 내용은 참조 하세요. [OData: 버전 관리 프로토콜](https://go.microsoft.com/fwlink/?LinkId=186071)합니다.

## <a name="see-also"></a>참고자료

- [Data Services 공급자](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [WCF Data Services 정의](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
