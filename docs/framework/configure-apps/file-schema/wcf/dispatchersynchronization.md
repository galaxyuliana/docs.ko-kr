---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 7336c9f7d8a117f9a9bfd338e47941eeb648fa51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925849"
---
# <a name="dispatchersynchronization"></a>\<dispatcherSynchronization>
  
서비스에서 응답을 비동기적으로 보낼 수 있도록 하는 엔드포인트 동작을 지정합니다.  
  
\<system.serviceModel>  
\<behaviors>  
\<endpointBehaviors>  
\<behavior>  
  
## <a name="syntax"></a>구문  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a>형식  
  
`Type`  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
  
다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성

| 특성               | Description       |
| ----------------------- | ----------------- |
| asynchronousSendEnabled | 비동기 보내기 동작 사용 여부를 나타내는 부울입니다. |
| `maxPendingReceives`    | 채널에서 발급할 수 있는 동시 수신의 수를 지정하는 정수입니다.<br /><br /> 이 값은 서비스 스로틀 동작을 제대로 구성한 후에 구성해야 합니다. |

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

| 요소 | 설명 |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|엔드포인트 동작을 지정합니다. |

## <a name="see-also"></a>참고자료

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
