---
title: StrongNameTokenFromAssembly 함수
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 484dacd4d9803139edf3fd5bad22c164d50de3dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757247"
---
# <a name="strongnametokenfromassembly-function"></a>StrongNameTokenFromAssembly 함수
지정된 어셈블리 파일에서 강력한 이름 토큰을 만듭니다.  
  
 이 함수는 더 이상 사용 되지 않습니다. 사용 된 [iclrstrongname:: Strongnametokenfromassembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) 메서드 대신 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 `wszFilePath`  
 [in] 어셈블리의 pe (이식 가능) 파일 경로입니다.  
  
 `ppbStrongNameToken`  
 [out] 반환 된 강력한 이름 토큰입니다.  
  
 `pcbStrongNameToken`  
 [out] 강력한 이름 토큰의 바이트 크기입니다.  
  
## <a name="return-value"></a>반환 값  
 `true` 성공적으로 완료 됩니다. 그렇지 않으면 `false`합니다.  
  
## <a name="remarks"></a>설명  
 강력한 이름 토큰은 공개 키의 축약 형태입니다. 토큰은 어셈블리 서명에 사용 된 공개 키에서 생성 되는 64 비트 해시입니다. 토큰에는 어셈블리에 대 한 강력한 이름의 일부인 되며 어셈블리 메타 데이터에서 읽을 수 있습니다.  
  
 토큰을 만든 후 호출 해야 합니다 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) 할당 된 메모리를 해제 하는 함수입니다.  
  
 경우는 `StrongNameTokenFromAssembly` 함수가 성공적으로 완료으로 호출 되지 않으면 합니다 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) 마지막 생성 된 오류를 검색 하는 함수입니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** StrongName.h  
  
 **라이브러리:** Mscoree.dll에 리소스로 포함  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고자료

- [StrongNameTokenFromAssembly 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [StrongNameTokenFromAssemblyEx 메서드](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [ICLRStrongName 인터페이스](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
