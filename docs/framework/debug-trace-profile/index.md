---
title: 디버깅, 추적 및 프로파일링
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 855a1329c9804e4b40d796c639bbe8768156dcc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754468"
---
# <a name="debugging-tracing-and-profiling"></a>디버깅, 추적 및 프로파일링
.NET Framework 애플리케이션을 디버그하려면 디버거가 애플리케이션에 연결하고 가능한 경우 애플리케이션 및 해당 MSIL(Microsoft intermediate language)에 대한 기호 및 라인 맵을 둘 다 생성할 수 있도록 컴파일러 및 런타임 환경을 구성해야 합니다. 관리되는 애플리케이션이 디버그된 후 성능을 향상시키기 위해 프로파일링할 수 있습니다. 프로파일링은 가장 자주 실행된 코드를 생성하는 소스 코드 줄과 실행하는 데 소요된 시간을 평가 및 설명합니다.  
  
 .NET framework 애플리케이션은 다양한 구성 세부 정보를 처리하는 Visual Studio를 사용하여 쉽게 디버그됩니다. Visual Studio가 설치되어 있지 않으면 .NET Framework <xref:System.Diagnostics> 네임스페이스의 디버깅 클래스를 사용하여 .NET Framework 애플리케이션의 성능을 검사 및 향상시킬 수 있습니다. 이 네임스페이스에는 실행 흐름 추적을 위한 <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug> 및 <xref:System.Diagnostics.TraceSource> 클래스 및 코드 프로파일링을 위한 <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog> 및 <xref:System.Diagnostics.PerformanceCounter> 클래스가 포함됩니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [JIT 연결 디버깅 설정](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 .NET Framework 애플리케이션에 디버그 엔진을 JIT 연결하도록 레지스트리를 구성하는 방법을 보여 줍니다.  
  
 [쉽게 디버깅할 수 있도록 이미지 만들기](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 어셈블리를 디버그하기 쉽도록 JIT 추적을 설정하고 최적화를 해제하는 방법을 보여 줍니다.  
  
 [응용 프로그램 추적 및 조율](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 실행되는 동안 애플리케이션 실행을 모니터링하는 방법 및 성능이나 오류가 발생했는지 여부를 표시하도록 계측하는 방법을 설명합니다.  
  
 [관리 디버깅 도우미를 사용하여 오류 진단](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 런타임 상태에 대한 정보를 제공하기 위해 CLR(공용 언어 런타임)과 함께 작동하는 디버깅 도우미인 MDA(관리 디버깅 도우미)를 설명합니다.  
  
 [디버거 표시 특성을 사용하여 디버깅 향상](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 형식 개발자가 디버거에 표시될 때 형식의 모양을 지정할 수 있는 방법을 설명합니다.  
  
 [성능 카운터](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 애플리케이션의 성능을 추적하는 데 사용할 수 있는 카운터를 설명합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [Visual Studio에서 ASP.NET 또는 ASP.NET Core 앱 디버그](/visualstudio/debugger/debugging-aspnet-and-ajax-applications)  
 개발 중이나 개발 후에 ASP.NET 애플리케이션을 디버그하는 방법에 대한 지침과 필수 전제 조건을 제공합니다.  
  
 [개발 가이드](../../../docs/framework/development-guide.md)  
 만들기, 구성, 디버깅, 보안, 애플리케이션 배포, 동적 프로그래밍에 대한 정보, 상호 운용성, 확장성, 메모리 관리 및 스레딩을 포함하여 애플리케이션 개발에 대한 모든 주요 기술 분야 및 작업에 대한 지침을 제공합니다.
