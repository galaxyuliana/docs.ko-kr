---
title: 웹 설정 스키마
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
ms.openlocfilehash: d53d3a105203addfacb1c982e0960bd12996f571
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941417"
---
# <a name="web-settings-schema"></a>웹 설정 스키마
웹 설정은 CPU와 ASP.NET 호스팅 계층에서 관리하는 프로세스 전반 동작에 적용되는 실행 수준 ASP.NET 설정을 지정합니다. 이러한 설정은 ASP.NET 애플리케이션의 Web.config 파일에서 지정된 애플리케이션 도메인 유형 설정과 다릅니다.  
  
 웹 설정은 .NET Framework의 버전 설치 폴더에 위치한 Aspnet.config 파일에 포함됩니다. 예를 들어 .NET Framework 2.0에 대 한 Aspnet .config 파일은 다음 폴더에 있습니다.  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 웹 설정은 machine.config 파일, 루트 Web.config 또는 애플리케이션 수준 Web.config 파일과 같은 다른 구성 파일에는 사용되지 않습니다.  
  
 [\<configuration> 요소](../configuration-element.md)  
  
 [\<system.web> 요소(웹 설정)](system-web-element-web-settings.md)  
  
 [\<applicationPool> 요소(웹 설정)](applicationpool-element-web-settings.md)  
  
|요소|설명|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|ASP.NET 호스팅 계층에서 사용하는 정보가 포함됩니다.|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|CPU와 ASP.NET 호스팅 계층에서 관리하는 프로세스 전반 동작에 적용되는 실행 수준 ASP.NET 설정을 지정합니다.|  
  
## <a name="see-also"></a>참고자료

- [구성 파일 스키마](../index.md)
