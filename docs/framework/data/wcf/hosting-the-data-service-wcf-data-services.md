---
title: 데이터 서비스 호스팅(WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: c240a76ea54d57456ff13fee7a48981354f669de
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881280"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>데이터 서비스 호스팅(WCF Data Services)
WCF Data Services를 사용 하 여 데이터를 노출 하는 서비스를 만들 수 있습니다는 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 피드 합니다. 이 데이터 서비스는 <xref:System.Data.Services.DataService%601>에서 상속되는 클래스로 정의됩니다. 이 클래스에서 요청 메시지를 처리 하 고, 데이터 원본에 대해 업데이트를 수행 하 고, OData에서 필요에 따라 응답 메시지를 생성 하는 데 필요한 기능을 제공 합니다. 그러나 데이터 서비스에 바인딩할 수 없으며 들어오는 HTTP 요청에 대 한 네트워크 소켓에서 수신 대기 합니다. 이 필요한 기능을 위해 데이터 서비스는 호스팅 구성 요소를 사용합니다.

 데이터 서비스 호스트는 데이터 서비스를 대신하여 다음 작업을 수행합니다.

- 요청을 수신 대기하고 이러한 요청을 데이터 서비스로 라우트합니다.

- 각 요청에 대한 데이터 서비스의 인스턴스를 만듭니다.

- 데이터 서비스가 들어오는 요청을 처리하도록 요청합니다.

- 데이터 서비스를 대신하여 응답을 보냅니다.

 호스팅을 단순화 하기 위해 데이터 서비스, WCF Data Services는 Windows Communication Foundation (WCF)를 사용 하 여 통합 되도록 설계 되었습니다. 데이터 서비스는 ASP.NET 응용 프로그램에서 데이터 서비스 호스트 역할을 하는 기본 WCF 구현을 제공 합니다. 따라서 다음 방법 중 하나로 데이터 서비스를 호스트할 수 있습니다.

- ASP.NET 응용 프로그램입니다.

- 자체 호스팅 WCF 서비스를 지원하는 관리되는 애플리케이션에서

- 다른 사용자 지정 데이터 서비스 호스트에서

## <a name="hosting-a-data-service-in-an-aspnet-application"></a>ASP.NET 애플리케이션에서 데이터 서비스 호스팅

사용 하는 경우는 **새 항목 추가** 도구 ASP.NET 응용 프로그램에서 데이터 서비스를 정의 하려면 Visual Studio 2015의 대화 상자는 프로젝트에서 두 개의 새 파일을 생성 합니다. 첫 번째 파일은 확장명이 `.svc`이고 데이터 서비스를 인스턴스화하는 방법을 WCF 런타임에 지시합니다. 다음은 완료할 때 만들었던 Northwind 샘플 데이터 서비스에 대 한이 파일의 예는 [퀵 스타트](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 이 지시문은 <xref:System.Data.Services.DataServiceHostFactory> 클래스를 사용하여 명명된 데이터 서비스 클래스에 대한 서비스 호스트를 만들도록 애플리케이션에 지시합니다.

 `.svc` 파일의 코드 숨김 페이지에는 Northwind 샘플 데이터 서비스에 대해 다음과 같이 정의된 데이터 서비스 자체의 구현인 클래스가 포함되어 있습니다.

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 데이터 서비스가 WCF 서비스 처럼 때문에 데이터 서비스는 ASP.NET과 통합 하 고 WCF 웹 프로그래밍 모델을 따릅니다. 자세한 내용은 [WCF 서비스 및 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) 하 고 [WCF 웹 HTTP 프로그래밍 모델](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)합니다.

## <a name="self-hosted-wcf-services"></a>자체 호스팅 WCF 서비스
 WCF 구현을 통합, 때문에 WCF Data Services는 데이터 서비스를 WCF 서비스로 자체 호스팅 지원. 서비스 콘솔 응용 프로그램과 같은 모든.NET Framework 응용 프로그램에서 자체 호스트할 수 있습니다. <xref:System.Data.Services.DataServiceHost>에서 상속되는 <xref:System.ServiceModel.Web.WebServiceHost> 클래스는 특정 주소에서 데이터 서비스를 인스턴스화하는 데 사용됩니다.

 셀프 호스팅을 개발과 테스트에 사용하면 서비스의 배포와 문제 해결이 보다 쉬워질 수 있습니다. 그러나 이러한 종류의 호스팅은 고급 호스팅 및 ASP.NET에서 또는 인터넷 정보 서비스 (IIS)에서 제공 하는 관리 기능을 제공 하지 않습니다. 자세한 내용은 [관리 되는 응용 프로그램에서 호스팅](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)합니다.

## <a name="defining-a-custom-data-service-host"></a>사용자 지정 데이터 서비스 호스트 정의
 WCF 호스트 구현이 너무 제한적인 경우 데이터 서비스에 대한 사용자 지정 호스트도 정의할 수 있습니다. <xref:System.Data.Services.IDataServiceHost> 인터페이스를 구현하는 모든 클래스를 데이터 서비스에 대한 네트워크 호스트로 사용할 수 있습니다. 사용자 지정 호스트는 <xref:System.Data.Services.IDataServiceHost> 인터페이스를 구현해야 하며 다음과 같은 데이터 서비스 호스트의 기본 임무를 처리할 수 있어야 합니다.

- 데이터 서비스에 서비스 루트 경로를 제공합니다.

- 적절한 <xref:System.Data.Services.IDataServiceHost> 멤버 구현에 대한 요청 및 응답 헤더 정보를 처리합니다.

- 데이터 서비스에서 발생한 예외를 처리합니다.

- 쿼리 문자열의 매개 변수 유효성을 검사합니다.

## <a name="see-also"></a>참고자료

- [WCF Data Services 정의](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [서비스로 데이터 노출](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
- [데이터 서비스 구성](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
