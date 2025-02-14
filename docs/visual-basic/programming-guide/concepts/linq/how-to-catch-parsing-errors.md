---
title: '방법: 구문 분석 (Visual Basic) 오류 catch'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: 1a5d01d4853a9fd0cc7f0a0e5071b394ab3f218b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855638"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>방법: 구문 분석 (Visual Basic) 오류 catch
이 항목에서는 잘못 구성되었거나 유효하지 않은 XML을 검색하는 방법을 보여 줍니다.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]은(는) <xref:System.Xml.XmlReader>를 사용하여 구현됩니다. 잘못 구성되었거나 유효하지 않은 XML이 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]에 전달되면 기본 <xref:System.Xml.XmlReader> 클래스에서 예외를 throw합니다. XML의 구문을 분석하는 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>와 같은 다양한 메서드는 예외를 catch하지 않습니다. 예외는 애플리케이션에 의해 catch될 수 있습니다.  
  
 XML 리터럴을 사용하는 경우에는 구문 분석 오류를 가져올 수 없습니다. Visual Basic 컴파일러는 잘못 구성되었거나 유효하지 않은 XML의 오류를 catch합니다.  
  
## <a name="example"></a>예제  
 다음 코드에서는 유효하지 않은 XML의 구문 분석을 시도합니다.  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 이 코드를 실행하면 다음 예외가 throw됩니다.  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 및 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 메서드가 throw할 수 있는 예외에 대한 자세한 내용은 <xref:System.Xml.XmlReader> 문서를 참조하세요.  
  
## <a name="see-also"></a>참고자료

- [(Visual Basic) XML 구문 분석](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
