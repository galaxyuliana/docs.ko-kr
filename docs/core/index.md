---
title: .NET Core 가이드
description: .NET Core는 Windows, Linux 및 Mac 앱을 만들기 위한 모듈식 고성능 .NET 구현입니다. 시작하려면 .NET Core에 관해 알아봅니다.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: db4daa8c78a181f0599c4c75ccd31f46ee278e63
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202831"
---
# <a name="net-core-guide"></a>.NET Core 가이드

[.NET Core](about.md)는 Microsoft 및 [GitHub](https://github.com/dotnet/core)의 .NET 커뮤니티에서 유지 관리하는 [오픈 소스](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) 범용 개발 플랫폼입니다. 플랫폼 간으로 Windows, macOS 및 Linux를 지원하며 디바이스, 클라우드 및 IoT 애플리케이션을 빌드하는 데 사용할 수 있습니다.

특성, 지원되는 언어 및 프레임워크, 키 API를 비롯한 .NET Core에 대한 자세한 내용은 [.NET Core 정보](about.md)를 참조하세요.

.NET Core 애플리케이션을 만드는 방법은 [.NET Core 자습서](tutorials/index.md)를 참조하세요. 첫 번째 앱을 만들고 실행하는 데 몇 분밖에 걸리지 않습니다. 브라우저에서 .NET Core를 사용하려면 [C#의 숫자](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) 온라인 자습서를 확인하세요.

## <a name="download-net-core-22"></a>.NET Core 2.2 다운로드

[.NET Core 2.2 SDK](https://www.microsoft.com/net/download)를 다운로드하여 Windows, macOS 또는 Linux 머신에서 .NET Core를 사용해 보세요. Docker 컨테이너를 사용하려면 [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/)를 방문하세요.

다른 .NET Core 버전을 찾는 경우 [.NET Core 다운로드](https://www.microsoft.com/net/download/archives)에서 모든 .NET Core 버전을 사용할 수 있습니다.

## <a name="net-core-22"></a>.NET Core 2.2

최신 버전은 [.NET Core 2.2](whats-new/dotnet-core-2-2.md)입니다. 새 기능으로는 프레임워크 종속 배포, 시작 후크, Azure SQL에서 AAD 인증, Windows ARM32에 대한 지원 등이 있습니다.

## <a name="create-your-first-application"></a>첫 애플리케이션 만들기

.NET Core SDK를 설치한 후 명령 프롬프트를 엽니다. 다음 `dotnet` 명령을 입력하여 C# 애플리케이션을 만들고 실행합니다.

```console
dotnet new console
dotnet run
```

다음과 같은 내용이 출력됩니다.

```output
Hello World!
```

## <a name="support"></a>고객 지원팀

.NET Core는 [Microsoft에 의해](https://www.microsoft.com/net/support/policy) Windows, macOS 및 Linux에서 지원됩니다. 보안 및 품질을 위해 1년에 여러 번, 일반적으로 매월 업데이트됩니다.

.NET Core 이진 배포는 Azure의 Microsoft가 유지 관리하는 서버에서 빌드 및 테스트되고 Microsoft 제품처럼 지원됩니다.

RHEL(Red Hat Enterprise Linux)에서 [Red Hat이 .NET Core를 지원](http://redhatloves.net/)합니다. Red Hat은 소스에서 .NET Core를 빌드하여 [Red Hat 소프트웨어 컬렉션](https://developers.redhat.com/products/softwarecollections/overview/)에서 사용할 수 있게 합니다. Red Hat 및 Microsoft는 협력하여 RHEL에서 .NET Core가 잘 작동하도록 합니다.
