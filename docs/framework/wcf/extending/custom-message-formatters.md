---
title: 사용자 지정 메시지 포맷터
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: af1596c65fc87a68bc3dc2ab5ab2d82133e0fed4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857976"
---
# <a name="custom-message-formatters"></a>사용자 지정 메시지 포맷터
메시지 내용은 애플리케이션에 편리한 형식이 아닌 XML 형식인 경우가 많습니다. 애플리케이션은 속성을 가져오고 설정하여 개체를 조작합니다. Windows Communication Foundation (WCF)를 사용 합니다 *데이터 계약* 변환할는 <xref:System.ServiceModel.Channels.Message> 개체로 응용 프로그램에서 쉽게 처리 하는 개체입니다. 이러한 프로세스를 serialization 및 deserialization이라고 합니다. 전송 계층에서 메시지 통신 형식에 대해 수행하는 관련 없는 프로세스인 serialization 및 deserialization을 설명하는 데에도 동일한 용어가 사용됩니다.  
  
 데이터 계약을 통해 수행할 수 없는 메시지 및 개체 간의 특별한 변환을 구현해야 하는 경우 사용자 지정 메시지 포맷터를 사용할 수 있습니다. 이렇게 하려면 클라이언트 또는 서비스에서 특정 계약 작업의 실행 동작을 수정하거나 확장합니다.  
  
## <a name="custom-message-formatters-on-the-client"></a>클라이언트의 사용자 지정 메시지 포맷터  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> 인터페이스는 클라이언트 애플리케이션에 대해 메시지를 개체로 변환하고, 개체를 메시지로 변환하는 과정을 제어하는 데 사용되는 메서드를 정의합니다.  
  
 이 인터페이스를 구현해야 합니다. 먼저 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> 메서드를 재정의하여 메시지를 deserialize합니다. 이 메서드는 들어오는 메시지가 수신된 후, 메시지가 클라이언트 작업에 디스패치되기 전에 호출됩니다.  
  
 다음에는 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> 메서드를 재정의하여 개체를 serialize합니다. 이 메서드는 보내는 메시지를 보내기 전에 호출됩니다.  
  
 사용자 지정 포맷터를 서비스 애플리케이션에 삽입하려면 작업 동작을 사용하여 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> 개체를 <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> 속성에 할당합니다. 동작에 대 한 정보를 참조 하세요 [구성 및 동작을 사용 하 여 런타임 확장](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)합니다.  
  
## <a name="custom-message-formatters-on-the-service"></a>서비스의 사용자 지정 메시지 포맷터  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> 인터페이스는 <xref:System.ServiceModel.Channels.Message> 개체를 작업 매개 변수로 변환하고 매개 변수에서 서비스 애플리케이션의 <xref:System.ServiceModel.Channels.Message> 개체로 변환하는 메서드를 정의합니다.  
  
 이 인터페이스를 구현해야 합니다. 먼저 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> 메서드를 재정의하여 메시지를 deserialize합니다. 이 메서드는 들어오는 메시지가 수신된 후, 메시지가 클라이언트 작업에 디스패치되기 전에 호출됩니다.  
  
 다음에는 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> 메서드를 재정의하여 개체를 serialize합니다. 이 메서드는 보내는 메시지를 보내기 전에 호출됩니다.  
  
 사용자 지정 포맷터를 서비스 애플리케이션에 삽입하려면 작업 동작을 사용하여 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> 개체를 <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> 속성에 할당합니다. 동작에 대 한 정보를 참조 하세요 [구성 및 동작을 사용 하 여 런타임 확장](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)합니다.  
  
## <a name="see-also"></a>참고자료

- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>
- [동작을 사용하여 런타임 구성 및 확장](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
