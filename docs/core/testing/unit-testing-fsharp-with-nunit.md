---
title: dotnet 테스트 및 NUnit을 사용하여 .NET Core에서 F# 단위 테스트
description: dotnet test 및 NUnit을 사용하여 샘플 솔루션을 단계별로 빌드하는 대화형 환경을 통해 .NET Core의 F#에 대한 단위 테스트 개념을 알아봅니다.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 7b559d94c03081a8ef67cf91ccfb7d08ff5b6c60
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626453"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>dotnet test 및 NUnit을 사용하여 .NET Core에서 F# 라이브러리 유닛 테스트

이 자습서에서는 샘플 솔루션을 단계별로 빌드하는 대화형 환경을 통해 단위 테스트 개념을 알아볼 수 있습니다. 미리 빌드된 솔루션을 사용하여 이 자습서를 진행하려는 경우 시작하기 전에 [샘플 코드를 보거나 다운로드](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/). 다운로드 지침은 [샘플 및 자습서](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)를 참조하세요.

## <a name="prerequisites"></a>전제 조건

- [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) 이상 버전.
- 선택하는 텍스트 편집기 또는 코드 편집기입니다.

## <a name="creating-the-source-project"></a>소스 프로젝트 만들기

셸 창을 엽니다. 솔루션을 저장할 *unit-testing-with-fsharp*라는 디렉터리를 만듭니다.
이 새 디렉터리 내에서 다음 명령을 실행하여 클래스 라이브러리 및 테스트 프로젝트에 대한 새 솔루션 파일을 만듭니다.

```console
dotnet new sln
```

다음으로, *MathService* 디렉터리를 만듭니다. 다음 개요는 지금까지의 디렉터리와 파일 구조를 보여 줍니다.

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

*MathService*를 현재 디렉터리로 만들고 다음 명령을 실행하여 소스 프로젝트를 만듭니다.

```console
dotnet new classlib -lang F#
```

다음과 같이 수학 서비스의 실패 구현을 만듭니다.

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

디렉터리를 다시 *unit-testing-with-fsharp* 디렉터리로 변경합니다. 다음 명령을 실행하여 클래스 라이브러리 프로젝트를 솔루션에 추가합니다.

```console
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a>테스트 프로젝트 만들기

다음으로 *MathService.Tests* 디렉터리를 만듭니다. 다음 개요에는 디렉터리 구조가 나와 있습니다.

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

*MathService.Tests* 디렉터리를 현재 디렉터리로 만들고 다음 명령을 사용하여 새 프로젝트를 만듭니다.

```console
dotnet new nunit -lang F#
```

그러면 NUnit를 테스트 프레임워크로 사용하는 테스트 프로젝트가 만들어집니다. 생성된 템플릿은 *MathServiceTests.fsproj*에 Test Runner를 구성합니다.

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

테스트 프로제트는 다른 패키지에 단위 테스트를 만들고 실행하도록 요구합니다. 이전 단계의 `dotnet new`는 NUnit 및 NUnit 테스트 어댑터를 추가했습니다. 이제 `MathService` 클래스 라이브러리를 프로젝트에 다른 종속성으로 추가합니다. [`dotnet add reference`](../tools/dotnet-add-reference.md) 명령을 사용합니다.

```console
dotnet add reference ../MathService/MathService.fsproj
```

GitHub의 [샘플 리포지토리](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj)에서 전체 파일을 볼 수 있습니다.

최종 솔루션 레이아웃은 다음과 같습니다.

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathService.Tests.fsproj
```

*unit-testing-with-fsharp* 디렉터리에서 다음 명령을 실행합니다.

```console
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a>첫 번째 테스트 만들기

하나의 실패 테스트를 작성하고, 테스트가 성공하도록 만듭니다. 이 작업을 반복합니다. *UnitTest1.fs*를 열고 다음 코드를 추가합니다.

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

`[<TestFixture>]` 특성은 테스트가 포함된 클래스를 나타냅니다. `[<Test>]` 특성은 Test Runner에서 실행하는 테스트 메서드를 나타냅니다. *unit-testing-with-fsharp* 디렉터리에서 [`dotnet test`](../tools/dotnet-test.md)를 실행하여 테스트 및 클래스 라이브러리를 빌드한 다음 테스트를 실행합니다. NUnit Test Runner에는 테스트를 실행할 프로그램 진입점이 포함되어 있습니다. `dotnet test`는 만든 단위 테스트 프로젝트를 사용하여 Test Runner를 시작합니다.

이러한 두 테스트는 가장 기본적인 통과 및 실패 테스트를 보여 줍니다. `My test`는 통과하고 `Fail every time`은 실패합니다. 이제 `squaresOfOdds` 메서드에 대한 테스트를 만듭니다. `squaresOfOdds` 메서드는 입력 시퀀스에 포함된 모든 홀수 정수 값 제곱의 시퀀스를 반환합니다. 이러한 모든 함수를 한 번에 작성하지 않고 기능의 유효성을 검사하는 테스트를 반복적으로 만들 수 있습니다. 각 테스트 패스를 만들면 메서드에 필요한 기능이 만들어집니다.

작성할 수 있는 가장 간단한 테스트는 모든 짝수를 사용하여 `squaresOfOdds`를 호출하는 것입니다. 이 경우 결과는 빈 정수 시퀀스여야 합니다.  해당 테스트는 다음과 같습니다.

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

`expected` 시퀀스가 목록으로 변환되었습니다. NUnit 프레임워크는 많은 표준 .NET 형식을 사용합니다. 해당 종속성으로 인해 공용 인터페이스 및 예상 결과에서 <xref:System.Collections.IEnumerable> 대신 <xref:System.Collections.ICollection>을 지원합니다.

테스트를 실행하면 테스트가 실패합니다. 구현은 아직 만들지 않았습니다. MathService 프로젝트의 *Library.fs* 클래스에서 작동하는 가장 간단한 코드를 작성하여 이 테스트를 통과시킵니다.

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

*unit-testing-with-fsharp* 디렉터리에서 `dotnet test`를 다시 실행합니다. `dotnet test` 명령은 `MathService` 프로젝트에 대한 빌드를 실행한 다음 `MathService.Tests` 프로젝트에 대한 빌드를 실행합니다. 두 프로젝트를 모두 빌드한 후 테스트를 실행합니다. 이제 두 개의 테스트를 통과합니다.

## <a name="completing-the-requirements"></a>요구 사항 완료

이제 하나의 테스트를 통과했으므로 더 작성할 수 있습니다. 다음의 단순한 사례에서는 유일한 홀수가 `1`인 시퀀스를 사용합니다. 숫자 1은 제곱이 1이므로 더 간단합니다. 이 테스트는 다음과 같습니다.

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

`dotnet test`를 실행하면 새 테스트가 실패합니다. 이제 `squaresOfOdds` 메서드를 업데이트하여 이 새 테스트를 처리해야 합니다. 시퀀스에서 모든 짝수를 필터링하여 이 테스트가 통과하게 만들어야 합니다. 이렇게 하려면 작은 필터 함수를 작성하고 `Seq.filter`를 사용합니다.

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

`Seq.toList`를 호출합니다. 그러면 <xref:System.Collections.ICollection> 인터페이스를 구현하는 목록이 생성됩니다.

한 가지 단계가 남았습니다. 즉, 각 홀수를 제곱합니다. 먼저 새 테스트를 작성합니다.

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

맵 작업을 통해 필터링된 시퀀스를 파이프하여 각 홀수의 제곱을 계산하는 방법으로 테스트를 수정합니다.

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

작은 라이브러리 및 이 라이브러리에 대한 단위 테스트 집합을 작성했습니다. 새 패키지 및 테스트 추가가 정상 워크플로에 포함되도록 솔루션을 구조화했습니다. 애플리케이션의 목표를 해결하는 데 대부분의 시간과 노력을 들였습니다.
