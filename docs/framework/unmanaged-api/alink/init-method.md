---
title: Init 메서드
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 606809533010f458272cd6fbbad6234217bddea2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741623"
---
# <a name="init-method"></a>Init 메서드
구현 하는 개체를 준비 합니다 [IALink 인터페이스](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) 사용 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a>매개 변수  
 `pDispenser`  
 [IMetaDataDispenserEx 인터페이스](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) 디스펜서 메타 데이터에 대 한 포인터입니다.  
  
 `pErrorHandler`  
 [IMetaDataError 인터페이스](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) 인터페이스를 처리 하는 선택적 오류에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드가 성공 하면 S_OK를 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  
 Alink.h 필요  
  
## <a name="see-also"></a>참고자료

- [IALink 인터페이스](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 인터페이스](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
