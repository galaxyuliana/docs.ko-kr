---
title: .NET의 Serialization
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 1f90a128ef6b29acbd315beae7aaaf1d1b78a62b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638854"
---
# <a name="serialization-in-net"></a>.NET의 Serialization
serialization은 지속시키거나 전송할 수 있는 형태로 개체 상태를 변환하는 프로세스입니다. serialization과 짝을 이루는 것은 스트림을 개체로 변환하는 deserialization입니다. 이 두 프로세스를 통해 데이터를 쉽게 저장하고 전송할 수 있습니다.  
  
.NET에서는 다음 두 가지의 serialization 기술을 제공합니다.  
  
- 이진 serialization은 형식 정확도를 유지하므로 애플리케이션의 여러 호출 간에 개체 상태를 유지하는 데 유용합니다. 예를 들어, 개체를 클립보드로 serialize하면 여러 애플리케이션 간에 개체를 공유할 수 있습니다. 개체를 스트림, 디스크, 메모리, 네트워크 등으로 serialize할 수 있습니다. Remoting에서는 serialization을 사용하여 한 컴퓨터 또는 응용 프로그램 도메인의 개체를 다른 컴퓨터 또는 응용 프로그램 도메인으로 "값으로" 전달합니다.  
  
- XML serialization은 public 속성과 필드만 serialize하며 형식 정확도를 유지하지 않습니다. 데이터를 사용하는 애플리케이션을 제한하지 않고 데이터를 제공하거나 사용하려고 할 때 유용합니다. XML은 공개 표준이기 때문에 웹을 통해 정보를 공유할 때 적합합니다. SOAP도 마찬가지로 공개 표준이어서 적합한 선택입니다.  
  
## <a name="in-this-section"></a>섹션 내용  
[serialization 방법 항목](../../../docs/standard/serialization/serialization-how-to-topics.md)  
이 단원에 포함된 방법 항목에 대한 링크를 나열합니다.
  
[이진 serialization](../../../docs/standard/serialization/binary-serialization.md)  
공용 언어 런타임에 포함된 이진 serialization 메커니즘을 설명합니다.

[XML 및 SOAP serialization](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
공용 언어 런타임에 포함된 XML 및 SOAP serialization 메커니즘을 설명합니다.

[serialization 도구](../../../docs/standard/serialization/serialization-tools.md)  
이러한 도구는 serialization 코드를 개발하는 데 도움이 됩니다.

[serialization 샘플](../../../docs/standard/serialization/serialization-samples.md)  
이러한 샘플에서는 serialization을 수행하는 방법을 보여 줍니다.

## <a name="reference"></a>참조
<xref:System.Runtime.Serialization> 개체를 직렬화하거나 deserialize하는 데 사용할 수 있는 클래스를 포함합니다.
  
<xref:System.Xml.Serialization>  
개체를 XML 형식 문서 또는 스트림으로 serialize하는 데 사용할 수 있는 클래스를 포함합니다.
