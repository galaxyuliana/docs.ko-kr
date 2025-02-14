---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 3531ff9f42289a3ad3b029f090f2dd4987e5886c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947916"
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
PresentationHost.exe가 호스트 애플리케이션과 관련된 원시 입력 디바이스(휴먼 인터페이스 디바이스)를 검색할 수 있게 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a>매개 변수  
 `ppEnum`  
  
 [out] 에 대 한 포인터를 [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) 원시 입력된 장치를 열거 합니다.  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 HRESULT:  
  
 S_OK- [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) S_OK가 반환 된 경우 PresentationHost.exe에서 사용만 됩니다.  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>설명  
 원시 입력 디바이스는 키보드, 마우스 및 리모콘과 같은 덜 일반적인 디바이스를 포함하는 입력 디바이스 집합입니다.  
  
 원시 입력 디바이스 목록이 검색된 후 PresentationHost.exe는 WM_INPUT 알림 메시지를 받을 디바이스를 등록합니다.  
  
## <a name="see-also"></a>참고자료

- [GetRawInputDeviceList](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [FilterInputMessage](filterinputmessage.md)
