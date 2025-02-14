---
title: SQL Server에서 권한 부여 및 권한
ms.date: 03/30/2017
ms.assetid: d340405c-91f4-4837-a3cc-a238ee89888a
ms.openlocfilehash: 66bf347543641808cc463d8035223fcf59b08231
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918106"
---
# <a name="authorization-and-permissions-in-sql-server"></a>SQL Server에서 권한 부여 및 권한
데이터베이스 개체를 만들 때는 사용자가 해당 개체에 액세스할 수 있도록 권한을 명시적으로 부여해야 합니다. 모든 보안 개체에는 권한 문을 통해 보안 주체에게 부여할 수 있는 권한이 있습니다.  
  
## <a name="the-principle-of-least-privilege"></a>최소 권한의 원칙  
 LUA(최소 권한 사용자 계정) 방식을 사용하여 애플리케이션을 개발하는 것은 보안 위협에 대처하는 심층적인 방어 전략을 구현하는 데 있어 매우 중요합니다. LUA 방식을 사용할 경우 사용자는 최소 권한의 원칙에 따라야 하며, 항상 제한된 사용자 계정으로 로그온해야 합니다. 관리 작업은 고정 서버 역할을 통해 분산되며 `sysadmin` 고정 서버 역할의 사용은 엄격하게 제한됩니다.  
  
 데이터베이스 사용자에게 권한을 부여할 때는 항상 최소 권한의 원칙에 따라 지정된 작업을 수행하는 데 필요한 최소한의 권한을 사용자 또는 역할에 부여해야 합니다.  
  
> [!IMPORTANT]
> LUA 방식을 사용하여 애플리케이션을 개발하고 테스트하면 개발 프로세스가 더 복잡해집니다. 시스템 관리자나 데이터베이스 소유자로 로그온하면 LUA 계정을 사용할 때보다 개체를 만들고 코드를 작성하는 것이 훨씬 쉽습니다. 그러나 높은 수준의 권한을 가진 계정을 사용하여 애플리케이션을 개발하면 최소 권한을 가진 사용자가 높은 수준의 권한이 필요한 애플리케이션을 실행하려고 할 때 기능이 제한되기 때문에 이로 인해 문제가 발생할 수 있습니다. 사용할 수 없는 기능을 사용할 수 있도록 사용자에게 권한을 과도하게 부여하면 애플리케이션이 공격에 쉽게 노출될 수 있습니다. LUA 계정으로 로그온하여 애플리케이션을 디자인, 개발 및 테스트하면 보안을 보다 체계적으로 계획하여 예기치 않은 문제를 방지할 수 있을 뿐만 아니라 임시 방편으로 높은 권한을 부여하는 위험을 제거할 수 있습니다. Windows 인증을 사용하여 배포하도록 애플리케이션을 개발하는 경우에도 SQL Server 로그인을 사용하여 테스트할 수 있습니다.  
  
## <a name="role-based-permissions"></a>역할 기반 권한  
 사용자가 아닌 역할에 권한을 부여하면 더 간편하게 보안을 관리할 수 있습니다. 역할에 할당한 권한 집합은 해당 역할의 모든 멤버에게 상속됩니다. 개별 사용자에 대해 별도의 권한 집합을 다시 만드는 것보다는 역할에 사용자를 추가하거나 역할에서 사용자를 제거하는 것이 쉽습니다. 역할은 중첩될 수 있지만 너무 많이 중첩하면 성능이 저하될 수 있습니다. 고정 데이터베이스 역할에 사용자를 추가하여 권한 할당 작업을 간소화할 수도 있습니다.  
  
 스키마 수준에서 권한을 부여할 수 있습니다. 이렇게 하면 스키마에 새로 만드는 모든 개체에 대한 권한이 자동으로 사용자에게 상속되기 때문에 새 개체를 만들 때마다 권한을 부여하지 않아도 됩니다.  
  
## <a name="permissions-through-procedural-code"></a>프로시저 코드를 통한 권한 부여  
 저장 프로시저 및 사용자 정의 함수와 같은 모듈을 통해 데이터 액세스를 캡슐화하면 애플리케이션의 보안을 강화할 수 있습니다. 예를 들어 저장 프로시저나 함수에 대한 권한만 부여하고 테이블과 같은 기본 개체에 대한 권한은 거부하여 사용자가 데이터베이스 개체와 직접 상호 작용하지 못하게 할 수 있습니다. SQL Server에서는 소유권 체인을 통해 이러한 설정을 구현할 수 있습니다.  
  
## <a name="permission-statements"></a>권한 문  
 다음 표에서는 세 가지 Transact-SQL 권한 문에 대해 설명합니다.  
  
|권한 문|Description|  
|--------------------------|-----------------|  
|GRANT|권한을 부여합니다.|  
|REVOKE|권한을 취소합니다. 이것은 새 개체의 기본 상태입니다. 사용자나 역할에 대해 취소한 권한은 해당 보안 주체가 할당된 다른 그룹이나 역할로부터 여전히 상속될 수 있습니다.|  
|DENY|DENY는 권한을 상속할 수 없도록 취소합니다. DENY는 다른 모든 권한보다 우선적으로 적용됩니다. 단, 개체 소유자 또는 `sysadmin`의 멤버에는 DENY가 적용되지 않습니다. `public` 역할에서 개체에 대한 권한을 DENY로 설정하면 해당 권한은 개체 소유자와 `sysadmin` 멤버를 제외한 모든 사용자와 역할에 대해 거부됩니다.|  
  
- GRANT 문을 사용하면 그룹 또는 역할에 권한을 할당할 수 있으며 데이터베이스 사용자는 이 그룹 또는 역할에서 권한을 상속할 수 있습니다. 그러나 DENY 문은 다른 모든 권한 문보다 우선적으로 적용되므로 권한이 거부된 사용자는 다른 역할에서 해당 권한을 상속할 수 없습니다.  
  
> [!NOTE]
> `sysadmin` 고정 서버 역할의 멤버 및 개체 소유자의 권한은 거부할 수 없습니다.  
  
## <a name="ownership-chains"></a>소유권 체인  
 SQL Server에서는 권한이 부여된 보안 주체만 개체에 액세스할 수 있습니다. 여러 데이터베이스 개체가 서로 액세스하는 시퀀스를 체인이라고 합니다. 개체 체인의 링크에서 이동할 때 SQL Server는 각 개체를 개별적으로 액세스할 때와는 다른 방법으로 권한을 확인합니다. 체인을 통해 개체에 액세스할 경우 SQL Server는 먼저 개체의 소유자와 해당 개체를 호출한 소유자(체인의 이전 링크)를 비교합니다. 두 개체의 소유자가 같으면 참조되는 개체의 권한을 확인하지 않습니다. 그러나 개체가 소유자가 서로 다른 또 하나의 개체에 액세스할 때마다 소유권 체인은 끊어지고 SQL Server는 호출자의 보안 컨텍스트를 확인합니다.  
  
## <a name="procedural-code-and-ownership-chaining"></a>프로시저 코드 및 소유권 체인  
 사용자가 테이블에서 데이터를 선택하는 저장 프로시저에 대한 실행 권한을 가지고 있다고 가정합니다. 이 저장 프로시저와 테이블의 소유자가 동일하면 사용자에게 테이블에 대한 별도의 권한을 부여할 필요가 없으며 해당 사용자의 권한을 거부할 수도 있습니다. 그러나 저장 프로시저와 테이블의 소유자가 서로 다르면 SQL Server는 데이터에 대한 액세스를 허용하기 전에 테이블에 대한 사용자의 권한을 확인해야 합니다.  
  
> [!NOTE]
> 소유권 체인은 동적 SQL 문에는 적용되지 않습니다. SQL 문을 실행하는 프로시저를 호출하려면 호출자에게 기본 테이블에 대한 권한을 부여해야 하기 때문에 결과적으로 애플리케이션이 SQL 삽입 공격에 노출될 위험이 있습니다. SQL Server에서는 가장 및 인증서를 사용한 모듈 서명과 같은 새로운 메커니즘을 제공하므로 기본 테이블에 대한 권한을 부여하지 않아도 됩니다. 이러한 기능은 CLR 저장 프로시저에 대해서도 사용할 수 있습니다.  
  
## <a name="external-resources"></a>외부 리소스  
 자세한 내용은 다음 리소스를 참조하세요.  
  
|리소스|설명|  
|--------------|-----------------|  
|[사용 권한](/sql/relational-databases/security/permissions-database-engine)|권한 계층 구조, 카탈로그 뷰, 고정 서버 역할 및 데이터베이스 역할의 권한에 대해 설명하는 항목을 제공합니다.|
  
## <a name="see-also"></a>참고자료

- [ADO.NET 응용 프로그램 보안](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server의 응용 프로그램 보안 시나리오](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [SQL Server에서 인증](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [SQL Server의 서버 및 데이터베이스 역할](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)
- [SQL Server에서 소유권 및 사용자 스키마 분리](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)
- [ADO.NET 관리되는 공급자 및 데이터 집합 개발자 센터](https://go.microsoft.com/fwlink/?LinkId=217917)
