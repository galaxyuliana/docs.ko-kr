---
title: LINQ to DataSet 개요
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: f60308b122841421613d8e1f84aa5b9a23cc3315
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504444"
---
# <a name="linq-to-dataset-overview"></a>LINQ to DataSet 개요
<xref:System.Data.DataSet> ADO.NET의 많이 사용 되는 구성 요소 중 하나입니다. ADO.NET의 기반이 되는 연결 되지 않은 프로그래밍 모델의 핵심 요소 이며 하면 명시적으로 캐시 데이터를 다른 데이터 원본에서. 프레젠테이션 계층의 경우 <xref:System.Data.DataSet>은 데이터 바인딩을 위해 GUI 컨트롤과 밀접하게 통합됩니다. 중간 계층의 경우 데이터의 관계 모양을 유지하는 캐시를 제공하고 빠르고 간단한 쿼리 및 계층 탐색 서비스를 포함합니다. 데이터베이스에 대한 요청 수를 줄이는 가장 일반적인 방법은 중간 계층에서 <xref:System.Data.DataSet>을 캐시 작업에 사용하는 것입니다. 예를 들어, 데이터 기반 ASP.NET 웹 응용 프로그램을 고려 합니다. 애플리케이션 데이터의 많은 부분은 자주 바뀌지 않으면서 세션이나 사용자를 통해 일반적으로 사용됩니다. 이 데이터를 웹 서버의 메모리에 유지하면 데이터베이스에 대한 요청의 수가 줄어서 사용자의 상호 작용 속도가 높아질 수 있습니다. 또 다른 유용한 측면은 <xref:System.Data.DataSet> 응용 프로그램 공간에 하나 이상의 데이터 원본에서 데이터의 하위 집합을 응용 프로그램 수 있다는 점입니다. 이 경우 애플리케이션에서는 메모리 내 데이터를 조작하는 동시에 관계 모양을 유지할 수 있습니다.  
  
 이러한 탁월함에도 불구하고 <xref:System.Data.DataSet>의 쿼리 기능에는 한계가 있습니다. <xref:System.Data.DataTable.Select%2A> 메서드는 필터링과 정렬에 사용할 수 있고 <xref:System.Data.DataRow.GetChildRows%2A> 및 <xref:System.Data.DataRow.GetParentRow%2A> 메서드는 계층 탐색에 사용할 수 있습니다. 그러나 더 복잡한 작업을 수행하려면 개발자가 사용자 지정 쿼리를 작성해야 합니다. 이 경우 애플리케이션의 성능이 저하되고 유지 관리가 어려워질 수 있습니다.  
  
 LINQ to DataSet 쉽게 및 데이터에 대 한 쿼리도 빨리 수행 캐시는 <xref:System.Data.DataSet> 개체입니다. 이러한 쿼리는 애플리케이션 코드에 포함된 문자열 리터럴이 아니라 프로그래밍 언어 자체로 표현됩니다. 즉, 개발자가 별도의 쿼리 언어를 배우지 않아도 됩니다. 컴파일 타임 구문 검사, 정적 입력 및 IntelliSense 지원에 대 한 Visual Studio IDE를 제공 하기 때문에 LINQ to DataSet 수 Visual Studio 개발자가 생산성을 높일 수 있도록 하는 또한 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]합니다. LINQ to DataSet도 사용할 수 있습니다 하나 이상의 데이터 원본에서 통합 된 데이터에 대해 쿼리 합니다. 이 기능은 데이터를 유연하게 표현하고 처리해야 하는 많은 시나리오에서 유용하게 사용할 수 있습니다. 이러한 조작 방법은 일반적인 보고, 분석 및 비즈니스 인텔리전스 애플리케이션에 특히 필요합니다.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>LINQ to DataSet을 사용한 데이터 집합 쿼리  
 쿼리를 시작 하기 전에 <xref:System.Data.DataSet> LINQ to DataSet 사용 하 여 개체를 채워야 합니다 <xref:System.Data.DataSet>. 데이터를 로드 하는 방법은 여러 가지가 있습니다를 <xref:System.Data.DataSet>를 사용 하는 등의 <xref:System.Data.Common.DataAdapter> 클래스 또는 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)합니다. 데이터가 <xref:System.Data.DataSet> 개체에 로드되면 해당 개체를 쿼리할 수 있습니다. LINQ to DataSet 사용 하 여 쿼리를 작성 하는 작업 하는 것은 사용 하 여 비슷합니다 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 에 대해 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-데이터 소스를 사용 하도록 설정 합니다. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 단일 테이블에 대해 쿼리를 수행할 수 있습니다는 <xref:System.Data.DataSet> 또는 사용 하 여 둘 이상의 테이블에 대해 합니다 <xref:System.Linq.Enumerable.Join%2A> 및 <xref:System.Linq.Enumerable.GroupJoin%2A> 표준 쿼리 연산자입니다.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 쿼리는 형식화 및 형식화되지 않은 <xref:System.Data.DataSet> 개체에 대해 지원됩니다. 애플리케이션 디자인 타임에 <xref:System.Data.DataSet> 스키마가 인식되는 경우 형식화된 <xref:System.Data.DataSet>을 사용하는 것이 좋습니다. 형식화된 <xref:System.Data.DataSet>에서 테이블과 행에는 각 열에 대한 형식화된 멤버가 있으며, 이를 통해 간단하고 이해하기 쉬운 쿼리를 만들 수 있습니다.  
  
 System.Core.dll에 구현 된 표준 쿼리 연산자 뿐만 아니라 LINQ to DataSet 몇 개 추가 <xref:System.Data.DataSet>-특정 확장 집합에 대해 쿼리를 쉽게 확인 하는 <xref:System.Data.DataRow> 개체입니다. 이러한 <xref:System.Data.DataSet>별 확장에는 행의 시퀀스를 비교하는 연산자와 <xref:System.Data.DataRow>의 열 값에 액세스할 수 있도록 하는 메서드가 포함됩니다.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N 계층 애플리케이션과 LINQ to DataSet  
 N 계층 데이터 애플리케이션은 여러 논리 계층으로 분리된 데이터 중심 애플리케이션입니다. 일반적인 N 계층 애플리케이션에는 프레젠테이션 계층, 중간 계층 및 데이터 계층이 포함됩니다. 애플리케이션 구성 요소를 별도의 계층으로 분리하면 애플리케이션의 유지 관리성과 확장성이 높아집니다. N 계층 데이터 응용 프로그램에 대 한 자세한 내용은 참조 하세요. [n 계층 응용 프로그램에서 데이터 집합 작업](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)합니다.  
  
 N 계층 애플리케이션에서 <xref:System.Data.DataSet>은 주로 중간 계층에 사용되어 웹 애플리케이션의 정보를 캐시합니다. LINQ to DataSet 쿼리 기능은 확장명 메서드를 통해 구현 되 고 기존 ADO.NET 2.0 확장 <xref:System.Data.DataSet>합니다.  
  
## <a name="see-also"></a>참고자료

- [데이터 집합 쿼리](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [LINQ(Language-Integrated Query) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ(Language-Integrated Query) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
