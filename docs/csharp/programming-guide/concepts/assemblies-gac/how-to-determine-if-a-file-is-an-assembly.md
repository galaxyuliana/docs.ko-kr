---
title: '방법: 파일이 어셈블리인지 확인(C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: 803159eed25a7785b1a2b4433e6950fa65e0a734
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595869"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>방법: 파일이 어셈블리인지 확인(C#)
파일은 관리되고 해당 메타데이터에 어셈블리 항목을 포함하는 경우에만 어셈블리입니다. 어셈블리 및 메타데이터에 대한 자세한 내용은 [어셈블리 매니페스트](../../../../framework/app-domains/assembly-manifest.md) 항목을 참조하세요.  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>파일이 어셈블리인지 수동으로 확인하는 방법  
  
1. [Ildasm.exe(IL 디스어셈블러)](../../../../framework/tools/ildasm-exe-il-disassembler.md)를 시작합니다.  
  
2. 테스트하려는 파일을 로드합니다.  
  
3. **ILDASM**에서 파일이 PE(이식 가능) 파일이 아니라고 보고하는 경우에는 어셈블리가 아닙니다. 자세한 내용은 항목 [방법: 어셈블리 콘텐츠 보기](../../../../framework/app-domains/how-to-view-assembly-contents.md)를 참조하세요.  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>파일이 어셈블리인지 프로그래밍 방식으로 확인하는 방법  
  
1. 테스트하는 파일의 전체 파일 경로와 이름을 전달하여 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 메서드를 호출합니다.  
  
2. <xref:System.BadImageFormatException> 예외가 throw되는 경우 파일이 어셈블리가 아닙니다.  
  
## <a name="example"></a>예  
 이 예제에서는 DLL을 테스트하여 어셈블리인지 확인합니다.  
  
```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 메서드는 테스트 파일을 로드한 다음 정보를 읽고 나면 해제합니다.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Reflection.AssemblyName>
- [C# 프로그래밍 가이드](../../index.md)
- [.NET 어셈블리](../../../../standard/assembly/index.md)
