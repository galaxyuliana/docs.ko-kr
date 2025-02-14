---
title: <remove>의에 <listeners> 대 한 요소<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: edd27dd262004aead7db4d81db8ecab0e831dac1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926989"
---
# <a name="remove-element-for-listeners-for-source"></a>\<소스 >에 대 \<한 \<수신기 > > 요소를 제거 합니다.
추적 소스의 `Listeners` 컬렉션에서 수신기를 제거합니다.  
  
 \<configuration>  
\<system.diagnostics>  
\<sources>  
\<source>  
\<listeners>  
\<remove>  
  
## <a name="syntax"></a>구문  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|`name`|필수 특성입니다.<br /><br /> `Listeners` 컬렉션에서 제거할 수신기의 이름입니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|`configuration`|공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.|  
|`system.diagnostics`|메시지를 수집하고 저장하고 라우팅하는 추적 수신기를 지정하며, 추적 스위치가 설정되는 수준을 지정합니다.|  
|`sources`|추적 메시지를 시작하는 추적 소스가 포함되어 있습니다.|  
|`source`|추적 메시지를 시작하는 추적 소스를 지정합니다.|  
|`listeners`|메시지를 수집, 저장 및 라우팅하는 수신기를 지정 합니다.|  
  
## <a name="remarks"></a>설명  
 요소 `<remove>` 는 추적 소스에 대 한 `Listeners` 컬렉션에서 지정 된 수신기를 제거 합니다.  
  
 인스턴스의 속성에서 메서드를 <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> 호출 하 `Listeners` 여 프로그래밍 방식으로 추적 소스에 대 한 컬렉션에서 요소를 제거할 수 있습니다. <xref:System.Diagnostics.TraceSource.Listeners%2A> <xref:System.Diagnostics.TraceSource>  
  
 이 요소는 컴퓨터 구성 파일 (machine.config) 및 응용 프로그램 구성 파일에서 사용할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 `<add>` 요소를 사용 하 여 `<remove>` 추적 소스 `TraceSourceApp`에 대 한 `Listeners` 컬렉션에 수신기 `console` 를 추가 하기 전에 요소를 사용 하는 방법을 보여 줍니다.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>참고자료

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [추적 및 디버그 설정 스키마](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [추적 수신기](../../../debug-trace-profile/trace-listeners.md)
