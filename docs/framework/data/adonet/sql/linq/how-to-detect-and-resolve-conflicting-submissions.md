---
title: '방법: 충돌하는 전송 검색 및 문제 해결'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: ff33196f83e2c0d8d759e4ffc3fb7442e8ba0e3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940100"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>방법: 충돌하는 전송 검색 및 문제 해결
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서는 여러 사용자에 의한 데이터베이스 변경으로 발생하는 충돌을 검색하고 해결하는 많은 리소스를 제공합니다. 자세한 내용은 [방법: 변경 충돌](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)을 관리 합니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 예외를 `try` / `catch` catch<xref:System.Data.Linq.ChangeConflictException> 하는 블록을 보여 줍니다. 각 충돌의 엔터티 및 멤버 정보는 콘솔 창에 표시됩니다.  
  
> [!NOTE]
> 정보 검색을 지원하려면 `using System.Reflection` 지시문(Visual Basic의 `Imports System.Reflection`)을 포함해야 합니다. 자세한 내용은 <xref:System.Reflection>을 참조하세요.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>참고자료

- [데이터 변경 및 변경 내용 전송](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [방법: 변경 내용 충돌 관리](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
