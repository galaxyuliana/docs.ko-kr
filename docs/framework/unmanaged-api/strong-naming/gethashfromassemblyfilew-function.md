---
title: GetHashFromAssemblyFileW 함수
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d034f15db8f3d452a055c127bb7095667c089ffe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772056"
---
# <a name="gethashfromassemblyfilew-function"></a>GetHashFromAssemblyFileW 함수
지정된 해시 알고리즘을 사용하여 지정된 어셈블리 파일의 해시를 가져옵니다. 어셈블리 파일의 경로를 유니코드 문자열로 지정 해야 합니다.  
  
 이 함수는 더 이상 사용 되지 않습니다. 사용 된 [iclrstrongname:: Gethashfromassemblyfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) 메서드 대신 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 `wszFilePath`  
 [in] 해시할 파일 경로입니다. 이 매개 변수는 유니코드 문자열 이어야 합니다.  
  
 `piHashAlg`  
 [out에서] 해시 알고리즘을 지정 하는 상수입니다. 기본 해시 알고리즘에 0을 사용 합니다.  
  
 `pbHash`  
 [out] 반환 된 해시 버퍼입니다.  
  
 `cchHash`  
 [in] 요청 된 최대 크기인 `pbHash`합니다.  
  
 `pchHash`  
 [out] 크기 (바이트)를 반환 `pbHash`합니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** StrongName.h  
  
 **라이브러리:** MsCorEE.dll에 리소스로 포함  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고자료

- [GetHashFromAssemblyFileW 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [GetHashFromAssemblyFile 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [ICLRStrongName 인터페이스](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
