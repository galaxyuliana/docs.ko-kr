---
title: 세션의 대기 중인 메시지 그룹화
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 37f0874ea99ee928e49a54a3e6a05ea4ef06f84e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855922"
---
# <a name="grouping-queued-messages-in-a-session"></a>세션의 대기 중인 메시지 그룹화
Windows Communication Foundation (WCF) 단일 수신 응용 프로그램 처리 관련된 메시지 집합을 그룹화 할 수 있는 세션을 제공 합니다. 세션의 일부인 메시지는 동일한 트랜잭션의 일부여야 합니다. 모든 메시지가 동일한 트랜잭션의 일부이므로, 하나의 메시지가 처리되지 않으면 전체 세션이 롤백됩니다. 세션은 배달 못 한 편지 큐 및 포이즌 큐와 관련하여 유사하게 동작합니다. 세션에 대해 구성된 대기 중인 바인딩에 대해 설정된 TTL(Time to Live) 속성은 세션에 전체적으로 적용됩니다. TTL이 만료되기 전에 세션에 있는 메시지 중 일부만 전송된 경우 전체 세션이 배달 못 한 편지 큐에 배치됩니다. 마찬가지로 세션에 있는 메시지가 애플리케이션 큐에서 애플리케이션으로 전송되지 못하면 전체 세션이 포이즌 큐(사용 가능한 경우)에 배치됩니다.  
  
## <a name="message-grouping-example"></a>메시지 그룹화 예제  
 메시지 그룹화가 유용한 한 가지 예는 주문 처리 응용 프로그램을 WCF 서비스로 구현 하는 경우에 합니다. 예를 들어 클라이언트가 많은 항목을 포함하는 주문을 이 애플리케이션에 제출합니다. 각 항목에 대해 클라이언트가 서비스를 호출하고, 그 결과 메시지가 개별적으로 전송됩니다. 서버 A가 첫 번째 항목을 수신하고 서버 B가 두 번째 항목을 수신할 수 있습니다. 항목이 추가될 때마다 해당 항목을 처리하는 서버는 해당 주문을 찾아서 항목을 추가해야 하므로 매우 비효율적입니다. 서버에서 현재 처리 중인 모든 주문을 추적하여 새 항목이 속하는 주문을 확인해야 하기 때문에 단일 서버에서 모든 요청을 처리하는 이런 비효율성이 여전히 발생합니다. 단일 주문에 대한 모든 요청을 그룹화하면 이러한 애플리케이션의 구현이 크게 간소화됩니다. 클라이언트 애플리케이션이 세션에 있는 단일 주문에 대한 모든 항목을 보내기 때문에 서비스에서 주문을 처리할 때 전체 세션을 한 번에 처리합니다. \  
  
## <a name="procedures"></a>절차  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>세션을 사용하도록 서비스 계약을 설정하려면  
  
1. 세션이 필요한 서비스 계약을 정의합니다. 이 작업은 <xref:System.ServiceModel.OperationContractAttribute> 특성을 사용하고 다음을 지정하여 이 작업을 수행합니다.  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2. 이러한 메서드는 아무것도 반환하지 않기 때문에 계약의 작업을 단방향으로 표시합니다. 이 작업은 <xref:System.ServiceModel.OperationContractAttribute> 특성을 사용하고 다음을 지정하여 수행합니다.  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. 서비스 계약을 구현하고 `InstanceContextMode`의 `PerSession`를 지정합니다. 그러면 각 세션에 대해 서비스가 한 번씩만 인스턴스화됩니다.  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. 서비스 작업마다 하나의 트랜잭션이 필요합니다. <xref:System.ServiceModel.OperationBehaviorAttribute> 특성을 사용하여 이를 지정합니다. 트랜잭션을 완료하는 작업에서는 `TransactionAutoComplete`를 `true`로 설정해야 합니다.  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. 시스템 제공 `NetMsmqBinding` 바인딩을 사용하는 엔드포인트를 구성합니다.  
  
6. <xref:System.Messaging>을 사용하여 트랜잭션 큐를 만듭니다. 메시지 큐(MSMQ) 또는 MMC를 사용하여 큐를 만들 수도 있습니다. 그러면 트랜잭션 큐가 만들어집니다.  
  
7. <xref:System.ServiceModel.ServiceHost>를 사용하여 서비스에 대한 서비스 호스트를 만듭니다.  
  
8. 서비스를 사용할 수 있도록 서비스 호스트를 엽니다.  
  
9. 서비스 호스트를 닫습니다.  
  
#### <a name="to-set-up-a-client"></a>클라이언트를 설정하려면  
  
1. 트랜잭션 큐에 쓸 트랜잭션 범위를 만듭니다.  
  
2. 사용 하 여 WCF 클라이언트 만들기는 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 도구입니다.  
  
3. 주문을 합니다.  
  
4. WCF 클라이언트를 닫습니다.  
  
## <a name="example"></a>예제  
  
### <a name="description"></a>설명  
 다음 예제에서는 `IProcessOrder` 서비스와 이 서비스를 사용하는 클라이언트에 대한 코드를 제공합니다. WCF 그룹화 동작을 제공 하도록 큐에 대기 중인된 세션을 사용 하는 방법을 보여 줍니다.  
  
### <a name="code-for-the-service"></a>서비스 코드  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>클라이언트 코드  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>참고자료

- [세션 및 큐](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [큐 개요](../../../../docs/framework/wcf/feature-details/queues-overview.md)
