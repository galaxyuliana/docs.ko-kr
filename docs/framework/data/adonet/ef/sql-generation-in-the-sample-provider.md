---
title: 샘플 공급자의 SQL 생성
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: d0e058cdc4dd3f7a1a04ab6eea5acf4d3deabb89
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248504"
---
# <a name="sql-generation-in-the-sample-provider"></a>샘플 공급자의 SQL 생성
[Entity Framework 샘플 공급자](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) 는를 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]지 원하는 ADO.NET 데이터 공급자의 새로운 구성 요소를 보여 줍니다.  샘플 공급자는 SQL Server 2005 데이터베이스와 작동하며 System.Data.SqlClient ADO.NET 2.0 데이터 공급자에 대한 래퍼로 구현됩니다.  
  
 샘플 공급자의 SQL 생성 모듈(DmlSqlGenerator.cs 파일을 제외하고 SQL Generation 폴더에 있음)은 DbQueryCommandTree 입력을 사용하고 단일 SQL SELECT 문을 생성합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 이 섹션에서는 다음 항목을 다룹니다.  
  
 [아키텍처 및 디자인](architecture-and-design.md)  
  
 [연습: SQL 생성](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>참고자료

- [SQL 생성](sql-generation.md)
