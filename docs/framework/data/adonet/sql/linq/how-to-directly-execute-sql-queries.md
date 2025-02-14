---
title: '방법: SQL 쿼리 직접 실행'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 04353361f8356b1d2b2aa3b930bb9b5ab88b9c0b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583675"
---
# <a name="how-to-directly-execute-sql-queries"></a>방법: SQL 쿼리 직접 실행
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]을 작성한 쿼리를 텍스트 형식의 매개 변수가 있는 SQL 쿼리로 변환하고 SQL 서버에 전달하여 처리합니다.  
  
 SQL에서는 애플리케이션에서 로컬로 사용할 수 있는 다양한 메서드를 실행할 수 없습니다. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 이러한 로컬 메서드를 해당 작업과 SQL 환경 내부에서 사용 가능한 함수로 변환하려 합니다. 대부분의 메서드 및.NET Framework 기본 제공 형식에서 연산자가 SQL 명령으로 직접 변환 합니다. 일부는 사용할 수 있는 함수에서 생성될 수 있습니다. 생성될 수 없는 일부는 런타임 예외를 발생시킵니다. 자세한 내용은 [SQL-CLR 형식 매핑](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)합니다.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 쿼리가 부족하여 특수한 작업을 수행할 수 없는 경우 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 메서드를 사용하여 SQL 쿼리를 실행하고 쿼리의 결과를 직접 개체로 변환합니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 `Customer` 클래스의 데이터가 두 개의 테이블(customer1 및 customer2)에 나누어져 있다고 가정합니다. 쿼리는 `Customer` 개체의 시퀀스를 반환합니다.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 표 형식 결과의 열 이름이 엔터티 클래스의 열 속성과 일치할 경우 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]은 모든 SQL 쿼리에서 개체를 만듭니다.  
  
## <a name="example"></a>예제  
 또한 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 메서드는 매개 변수를 허용합니다. 다음의 코드를 사용하여 매개 변수가 있는 쿼리를 실행합니다.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 매개 변수는 `Console.WriteLine()` 및 `String.Format()`에서 사용되는 동일한 중괄호 표기법을 사용하여 쿼리 텍스트에서 표현됩니다. 사실 `String.Format()` 중괄호 중괄호로 묶인된 매개 변수를 대체와 같은 매개 변수 이름 생성을 제공 하는 쿼리 문자열에서 실제로 라고 @p0를 @p1 ..., @p(n).  
  
## <a name="see-also"></a>참고자료

- [배경 정보](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [데이터베이스 쿼리](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
