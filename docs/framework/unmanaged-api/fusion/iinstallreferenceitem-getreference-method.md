---
title: IInstallReferenceItem::GetReference 메서드
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b01c7cea477182c7590664ae9e850e99a89c4bc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773952"
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference 메서드
포인터를 가져 합니다 [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) 이 표시 되는 구조 [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 `ppRefData`  
 [out] 반환 된 `FUSION_INSTALL_REFERENCE` 포인터입니다.  
  
 `dwFlags`  
 [in] 향후 확장성을 위해 예약 되어 있습니다. `dwFlags` 0 (영) 이어야 합니다.  
  
 `pvReserved`  
 [in] 향후 확장성을 위해 예약 되어 있습니다. `pvReserved` null 참조 여야 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** Fusion.h  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고자료

- [IInstallReferenceItem 인터페이스](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [FUSION_INSTALL_REFERENCE 구조체](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
