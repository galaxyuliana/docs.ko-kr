---
title: GetQualifierSet 함수 (관리 되지 않는 API 참조)
description: GetQualifierSet 함수 한정자는 클래스 또는 인스턴스를 검색 합니다.
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e392d3afcd81e6eace7a674788a2a957da28842c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746466"
---
# <a name="getqualifierset-function"></a>GetQualifierSet 함수
클래스 인스턴스 또는 클래스 정의에 대한 한정자 집합을 검색합니다.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>매개 변수

`vFunc`  
[in] 이 매개 변수 사용 되지 않습니다.

`ptr`  
[in] 에 대 한 포인터를 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 인스턴스.

`ppQualSet`  
[out] 클래스 개체의 한정자에 대 한 액세스를 허용 하는 인터페이스 포인터를 받습니다. `ppQualSet`가 `null`이 될 수 없는 경우 오류가 발생 하 고 새 개체를 반환 되지 않으면 포인터 그대로 경우 수정 합니다. 

## <a name="return-value"></a>반환 값

이 함수에 의해 반환 되는 다음 값에 정의 된 합니다 *WbemCli.h* 헤더 파일에서 정의할 수 상수로 코드:

|상수  |값  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 일반 오류가 발생이 했습니다. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 지정된 된 메서드가 존재 하지 않습니다. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 메모리가 부족 하 여 작업을 완료할 수 없습니다. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 매개 변수는 `null`합니다. |
|`WBEM_S_NO_ERROR` | 0 | 함수 호출이 성공 했습니다.  |
  
## <a name="remarks"></a>설명

이 함수에 대 한 호출을 래핑하는 [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) 메서드. 

합니다 [IWbemQualifierSet 포인터](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) 호출자가 추가, 편집 또는 이러한 한정자를 삭제할 수 있습니다. 이러한 추가, 편집 또는 삭제 된 한정자는 전체 인스턴스 또는 클래스 정의에 적용 됩니다.

## <a name="requirements"></a>요구 사항  
**플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** WMINet_Utils.idl  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>참고자료

- [WMI 및 성능 카운터 (관리 되지 않는 API 참조)](index.md)
