---
title: <socket> 요소(네트워크 설정)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: aa455945b839ada4100138d5bdf9fc239376e5cb
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663981"
---
# <a name="socket-element-network-settings"></a>\<socket > 요소 (네트워크 설정)
소켓 작업에서 완료 포트를 사용 하는지 여부를 지정 합니다.  
  
 \<configuration>  
\<system.net>  
\<settings>  
\<socket>  
  
## <a name="syntax"></a>구문  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|**특성**|**설명**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|소켓이 항상 허용 메서드 호출에 대해 완료 포트를 사용 해야 하는지 여부를 나타냅니다. 기본값은 `false`입니다.|  
|`alwaysUseCompletionPortsForConnect`|소켓이 연결 메서드 호출에 대해 항상 완료 포트를 사용 해야 하는지 여부를 나타냅니다. 기본값은 `false`입니다.|  
|`ipProtectionLevel`|소켓에 사용할 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 기본값을 지정 합니다. 기본값은 Windows 버전에 따라 다릅니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|**요소**|**설명**|  
|-----------------|---------------------|  
|[settings](settings-element-network-settings.md)|<xref:System.Net> 네임스페이스에 대한 기본 네트워크 옵션을 구성합니다.|  
  
## <a name="remarks"></a>설명  
 `alwaysUseCompletionPortsForAccept` 및 `alwaysUseCompletionPortsForConnect` 특성이 <xref:System.Net.Sockets?displayProperty=nameWithType> 네임스페이스에 있는 클래스에 의해 완료 포트의 사용과 관련된 기본 동작을 지정하는 데 사용됩니다. 고성능 서버 응용 프로그램에는 완료 포트를 권장 합니다.  
  
 `alwaysUseCompletionPortsForAccept` 및`alwaysUseCompletionPortsForConnect` 특성의 기본값은 **false**입니다.  
  
 는 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> 적용 가능한 구성 파일에서 `alwaysUseCompletionPortsForAccept` 특성의 현재 값을 가져오는 데 사용할 수 있습니다. 는 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> 적용 가능한 구성 파일에서 `alwaysUseCompletionPortsForConnect` 특성의 현재 값을 가져오는 데 사용할 수 있습니다.  
  
 특성 `ipProtectionLevel` 은 소켓에 사용할 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 기본값을 지정 합니다. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> 속성 주소 같은 링크 로컬 또는 사이트 로컬 접두사가 같은 지정된 된 범위에 IPv6 소켓에 대 한 제한 구성할 수 있도록 합니다. 이 옵션에는 애플리케이션을으로 IPv6 소켓에 대 한 액세스 제한을 적용할 수 있습니다. 이러한 제한을 사용하면 사설 LAN에서 실행되는 애플리케이션을 간단하고 강력하게 외부 공격으로부터 보호할 수 있습니다. 이 옵션의 공용 및 개인 사용자가 해당 하는 경우 필요에 따라 같은 사이트로 액세스를 제한 또는 무제한 액세스를 수신 대기 소켓의 범위를 넓히거나 설정.  
  
 이 `ipProtectionLevel` 특성 설정은 초기 들어오는 트래픽에만 영향을 줍니다.  
  
- 소켓에서 들어오는 연결을 수신 대기 하는 TCP 서버입니다.  
  
- 소켓에서 패킷을 수신 하는 UDP 응용 프로그램입니다.  
  
 이 구성 설정은 이미 설정 된 TCP 연결에는 영향을 주지 않습니다. (트래픽은 양방향으로 제한 되지 않음), UDP 패킷을 보내는 응용 프로그램에는 영향을 주지 않습니다.  
  
 `ipProtectionLevel` 특성 설정에 사용할 수 있는 값은 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 열거형에 지정 된 다음과 같이 정의 된 보호 수준에 해당 합니다.  
  
|**특성 값**|**설명**|  
|-|-|  
|EdgeRestricted|IP 보호 수준이 경계 제한 됨입니다. 이 값은 인터넷을 통해 작동하도록 디자인된 애플리케이션에서 사용됩니다. 이 설정은 Windows Teredo 구현을 사용 하 여 네트워크 주소 변환 (NAT) 통과 허용 하지 않습니다. 이러한 애플리케이션에서는 IPv4 방화벽이 무시될 수 있으므로 열린 포트로 향하는 인터넷 공격을 막기 위해 애플리케이션의 보안 기능을 강화해야 합니다. Windows Server 2003 및 Windows XP에서는 소켓에 IP 보호 수준에 대 한 기본값인 경계 제한 합니다.|  
|액세스가|IP 보호 수준이 제한 됩니다. 이 값은 인터넷 시나리오를 구현하지 않는 인트라넷 애플리케이션에서 사용됩니다. 일반적으로 이러한 애플리케이션은 인터넷형 공격에 대해 테스트되거나 보안이 강화되어 있지 않습니다. 이 설정은 링크 로컬 에서만 트래픽이 받도록된 제한 합니다.|  
|제한 없음|IP 보호 수준이 제한 되지 않습니다. 이 값은 Windows에 구축된 IPv6 NAT 통과 기능(예: Teredo)을 이용하는 애플리케이션을 비롯하여 인터넷을 통해 작동하도록 디자인된 애플리케이션에서 사용됩니다. 이러한 애플리케이션에서는 IPv4 방화벽이 무시될 수 있으므로 열린 포트로 향하는 인터넷 공격을 막기 위해 애플리케이션의 보안 기능을 강화해야 합니다. Windows Server 2008 R2 및 Windows Vista에서는 소켓에 IP 보호 수준에 대 한 기본 값 제한 되지 않습니다.|  
|지정되지 않음|IP 보호 수준이 지정 되지 않습니다. Windows 7 및 Windows Server 2008 R2에서는 소켓에 IP 보호 수준이 기본값이 지정 되지 않습니다.|  
  
 `ipProtectionLevel` 특성의 기본값은 **지정**되지 않습니다.  
  
 속성을 사용 하 여 적용 가능한 구성 파일에서 `ipProtectionLevel` 특성의 현재 값을 가져올 수 있습니다. <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>  
  
## <a name="configuration-files"></a>구성 파일  
 이 요소는 애플리케이션 구성 파일 또는 컴퓨터 구성 파일(Machine.config)에서 사용할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 완료 포트를 사용 하도록 지정 하는 방법과 기본값 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 을 제한 하지 않아야 함을 지정 하는 방법을 보여 줍니다.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>참고자료

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [네트워크 설정 스키마](index.md)
