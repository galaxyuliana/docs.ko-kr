---
title: '방법: 특정 요소 이름으로 하위 항목 찾기 (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 78915518-0d25-4051-ab55-929779989510
ms.openlocfilehash: 0084f04db5af7b012748b66187e029c77d0cfce5
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710269"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-visual-basic"></a>방법: 특정 요소 이름으로 하위 항목 찾기 (Visual Basic)
특정 이름을 가진 모든 하위 요소를 찾으려는 경우가 있습니다. 모든 하위 요소를 반복하는 코드를 작성할 수 있지만 <xref:System.Xml.Linq.XContainer.Descendants%2A> 축을 사용하는 것이 더 쉽습니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 요소 이름에 따라 하위 요소를 찾는 방법을 보여 줍니다.  
  
```vb  
Dim root As XElement = _  
    <root>  
        <para>  
            <r>  
                <t>Some text </t>  
            </r>  
            <n>  
                <r>  
                    <t>that is broken up into </t>  
                </r>  
            </n>  
            <n>  
                <r>  
                    <t>multiple segments.</t>  
                </r>  
            </n>  
        </para>  
    </root>  
  
Dim textSegs As IEnumerable(Of String) = _  
    From seg In root...<t> _  
    Select seg.Value  
  
Dim str As String = textSegs.Aggregate( _  
    New StringBuilder, _  
    Function(sb, i) sb.Append(i), _  
    Function(sb) sb.ToString)  
  
Console.WriteLine(str)  
```  
  
 이 코드의 결과는 다음과 같습니다.  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a>예제  
 다음 예제에서는 네임스페이스에 있는 XML에 대한 동일한 쿼리를 보여 줍니다. 자세한 내용은 [네임 스페이스 개요 (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)를 참조 하세요.  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <root>  
                <para>  
                    <r>  
                        <t>Some text </t>  
                    </r>  
                    <n>  
                        <r>  
                            <t>that is broken up into </t>  
                        </r>  
                    </n>  
                    <n>  
                        <r>  
                            <t>multiple segments.</t>  
                        </r>  
                    </n>  
                </para>  
            </root>  
  
        Dim textSegs As IEnumerable(Of String) = _  
            From seg In root...<t> _  
            Select seg.Value  
  
        Dim str As String = textSegs.Aggregate( _  
            New StringBuilder, _  
            Function(sb, i) sb.Append(i), _  
            Function(sb) sb.ToString)  
  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 이 코드의 결과는 다음과 같습니다.  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a>참고자료

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- [기본 쿼리 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
