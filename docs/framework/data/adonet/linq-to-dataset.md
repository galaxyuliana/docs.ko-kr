---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: c4069ef760877935c4ce194144d131d0dc58b4d3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504360"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
LINQ to DataSet 쉽게 및 데이터에 대 한 쿼리도 빨리 수행 캐시는 <xref:System.Data.DataSet> 개체입니다. 특히 LINQ to DataSet 쿼리를 작성할 프로그래밍 언어 자체에서 대신 별도 쿼리 언어를 사용 하 여 사용 하 여 쿼리를 단순화 합니다. 지금 활용할 수 컴파일 타임 구문 검사, 정적 입력 및 IntelliSense 지원을 해당 쿼리에 Visual Studio에서 제공 하는 Visual Studio 개발자에 게 특히 유용 합니다.  
  
 LINQ to DataSet도 사용할 수 있습니다 하나 이상의 데이터 원본에서 통합 된 데이터에 대해 쿼리 합니다. 이 기능은 논리적으로 집계된 데이터 쿼리, 웹 애플리케이션의 중간 계층 캐시 등과 같이 유연하게 데이터를 표현하고 처리해야 하는 여러 시나리오에 사용될 수 있습니다. 이러한 조작 방법은 일반적인 보고, 분석 및 비즈니스 인텔리전스 애플리케이션에 특히 필요합니다.  
  
 LINQ to DataSet 기능 주로의 확장 메서드를 통해 노출 되는 <xref:System.Data.DataRowExtensions> 고 <xref:System.Data.DataTableExtensions> 클래스입니다. LINQ to DataSet 기반으로 하 고 기존 ADO.NET 아키텍처를 사용 하 여 및 응용 프로그램 코드에서 ADO.NET을 대체 하기 위한 것입니다. 기존 ADO.NET 코드는 LINQ to DataSet 응용 프로그램에서 계속 합니다. LINQ to DataSet ADO.NET을 데이터 저장소의 관계는 다음 다이어그램에 나와 있습니다.  
  
 ![LINQ to DataSet은 ADO.NET 공급자를 기반으로 한다는 보여 주는 다이어그램입니다.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>섹션 내용  
 [시작](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [프로그래밍 가이드](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>참조  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>참고자료

- [LINQ(Language-Integrated Query) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ(Language-Integrated Query) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ 및 ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
