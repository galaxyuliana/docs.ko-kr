---
title: '방법: 어셈블리 로드 및 언로드(C#)'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 3f3c244a74e029eeaead77f561cd4c1adfca519a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595833"
---
# <a name="how-to-load-and-unload-assemblies-c"></a>방법: 어셈블리 로드 및 언로드(C#)
프로그램에서 참조하는 어셈블리는 빌드 시 자동으로 로드되지만, 런타임에 현재 애플리케이션 도메인에 특정 어셈블리를 로드할 수도 있습니다. 자세한 내용은 [방법: 애플리케이션 도메인에 어셈블리 로드](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)를 참조하세요.  
  
 해당 어셈블리가 포함된 애플리케이션 도메인을 모두 언로드하지 않으면 개별 어셈블리를 언로드할 수 없습니다. 어셈블리가 범위를 벗어난 경우에도 실제 어셈블리 파일은 해당 파일을 포함하는 애플리케이션 도메인이 모두 언로드될 때까지 로드된 상태로 유지됩니다.  
  
 일부 어셈블리만 언로드하고 다른 어셈블리는 언로드하지 않으려는 경우 새 애플리케이션 도메인을 만들고, 이 도메인 내에서 코드를 실행한 다음 해당 애플리케이션 도메인을 언로드하는 것이 좋습니다. 자세한 내용은 [방법: 애플리케이션 도메인 언로드](../../../../framework/app-domains/how-to-unload-an-application-domain.md)를 참조하세요.  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>애플리케이션 도메인에 어셈블리를 로드하려면  
  
1. <xref:System.AppDomain> 및 <xref:System.Reflection> 클래스에 포함된 여러 로드 메서드 중 하나를 사용합니다. 자세한 내용은 [방법: 애플리케이션 도메인에 어셈블리 로드](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)를 참조하세요.  
  
### <a name="to-unload-an-application-domain"></a>애플리케이션 도메인을 언로드하려면  
  
1. 해당 어셈블리가 포함된 애플리케이션 도메인을 모두 언로드하지 않으면 개별 어셈블리를 언로드할 수 없습니다. <xref:System.AppDomain>의 `Unload` 메서드를 사용하여 애플리케이션 도메인을 언로드합니다. 자세한 내용은 [방법: 애플리케이션 도메인 언로드](../../../../framework/app-domains/how-to-unload-an-application-domain.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목

- [C# 프로그래밍 가이드](../../index.md)
- [.NET 어셈블리](../../../../standard/assembly/index.md)
- [방법: 애플리케이션 도메인에 어셈블리 로드](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
