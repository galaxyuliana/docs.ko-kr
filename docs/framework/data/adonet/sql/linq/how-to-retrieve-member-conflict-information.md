---
title: '방법: 멤버 충돌 정보 검색'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 9d63b0b2c7d513d9f4db526b88a7c4e852637343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928627"
---
# <a name="how-to-retrieve-member-conflict-information"></a>방법: 멤버 충돌 정보 검색
<xref:System.Data.Linq.MemberChangeConflict> 클래스를 사용하여 충돌의 각 멤버에 대한 정보를 검색할 수 있습니다. 이와 동일한 컨텍스트에서 멤버의 충돌에 대한 사용자 지정 처리를 제공할 수 있습니다. 자세한 내용은 [낙관적 동시성: 개요](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>예제  
 다음 코드에서는 <xref:System.Data.Linq.ObjectChangeConflict> 개체를 반복합니다. 그런 다음 각 개체에 대해 <xref:System.Data.Linq.MemberChangeConflict> 개체를 반복합니다.  
  
> [!NOTE]
> <xref:System.Reflection> 정보를 제공하려면 <xref:System.Data.Linq.MemberChangeConflict.Member%2A>을 포함합니다.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>참고자료

- [방법: 변경 내용 충돌 관리](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
