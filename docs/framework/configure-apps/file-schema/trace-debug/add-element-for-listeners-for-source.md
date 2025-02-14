---
title: <add>의에 <listeners> 대 한 요소<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 96bfde3ec425f6f77d1d655808d155eb0e6fcd0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927208"
---
# <a name="add-element-for-listeners-for-source"></a>\<\<소스 > 수신기 > \<에 대 한 > 요소 추가
추적 소스의 `Listeners` 컬렉션에 수신기를 추가합니다.  
  
 \<configuration>  
\<system.diagnostics>  
\<sources>  
\<source>  
\<listeners>  
\<add>  
  
## <a name="syntax"></a>구문  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|`type`|`sharedListeners` 컬렉션에서 수신기를 참조 하는 경우를 제외 하 고 이름으로 참조 하기만 하면 되는 경우 필수 특성입니다 ( [예제](#example)참조).<br /><br /> 수신기의 유형을 지정 합니다. 정규화 된 [형식 이름 지정](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)에 지정 된 요구 사항을 충족 하는 문자열을 사용 해야 합니다.|  
|`initializeData`|선택적 특성입니다.<br /><br /> 지정 된 클래스의 생성자에 전달 된 문자열입니다. 클래스에 문자열을 사용 하는 생성자가 없으면 이throw됩니다.<xref:System.Configuration.ConfigurationException>|  
|`name`|선택적 특성입니다.<br /><br /> 수신기의 이름을 지정 합니다.|  
|`traceOutputOptions`|선택적 특성입니다.<br /><br /> 추적 수신기 <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> 의 속성 값을 지정 합니다.|  
|[사용자 지정 특성]|선택적 특성입니다.<br /><br /> 해당 수신기에 대해 <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> 메서드로 식별 되는 수신기 별 특성의 값을 지정 합니다. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>는 <xref:System.Diagnostics.DelimitedListTraceListener> 클래스에 고유한 추가 특성의 한 예입니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|추적 소스의 `Listeners` 컬렉션에 있는 수신기에 필터를 추가합니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|`configuration`|공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.|  
|`system.diagnostics`|메시지를 수집하고 저장하고 라우팅하는 추적 수신기를 지정하며, 추적 스위치가 설정되는 수준을 지정합니다.|  
|`sources`|추적 메시지를 시작하는 추적 소스가 포함되어 있습니다.|  
|`source`|추적 메시지를 시작하는 추적 소스를 지정합니다.|  
|`listeners`|메시지를 수집, 저장 및 라우팅하는 수신기를 지정 합니다.|  
  
## <a name="remarks"></a>설명  
 .NET Framework와 함께 제공 되는 수신기 클래스는 <xref:System.Diagnostics.TraceListener> 클래스에서 파생 됩니다.  
  
 추적 수신기의 `name` 특성을 지정 하지 않는 경우 추적 수신기의 속성 <xref:System.Diagnostics.TraceListener.Name%2A> 은 기본적으로 빈 문자열 ("")로 설정 됩니다. 응용 프로그램에 수신기가 하나만 있는 경우 이름을 지정 하지 않고 수신기를 추가 하 고 이름에 대해 빈 문자열을 지정 하 여 제거할 수 있습니다. 그러나 응용 프로그램에 둘 이상의 수신기가 있는 경우 각 추적 수신기에 고유한 이름을 지정 하 여 <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> 컬렉션에서 개별 추적 수신기를 식별 하 고 관리할 수 있도록 해야 합니다.  
  
> [!NOTE]
> 동일한 형식의 추적 수신기를 두 개 이상 추가 하면 해당 형식 및 이름이 `Listeners` 컬렉션에 추가 되는 하나의 추적 수신기만 생성 됩니다. 그러나 `Listeners` 컬렉션에 여러 개의 동일한 수신기를 프로그래밍 방식으로 추가할 수 있습니다.  
  
 `initializeData` 특성의 값은 만드는 수신기의 형식에 따라 달라 집니다. 모든 추적 수신기에서을 지정 `initializeData`해야 하는 것은 아닙니다.  
  
> [!NOTE]
> `initializeData` 특성을 사용 하는 경우 컴파일러 경고 "' initializedata ' 특성이 선언 되지 않았습니다." 라는 메시지가 표시 될 수 있습니다. 이 경고는 <xref:System.Diagnostics.TraceListener> `initializeData` 특성을 인식 하지 않는 추상 기본 클래스에 대해 구성 설정의 유효성을 검사 하기 때문에 발생 합니다. 일반적으로 매개 변수를 사용 하는 생성자가 있는 추적 수신기 구현에 대해서는이 경고를 무시할 수 있습니다.  
  
 다음 표에서는 .NET Framework에 포함 된 추적 수신기를 보여 주고 해당 `initializeData` 특성의 값을 설명 합니다.  
  
|추적 수신기 클래스|initializeData 특성 값|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|생성자에 대 한 `useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 값입니다.  표준 오류 스트림에 추적 및`true`디버그 출력을 쓰려면`false`특성을 ""로 설정 하 고, 표준 출력 스트림에 쓰려면 ""로 설정 합니다. `initializeData`|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener>가 쓸 파일 이름입니다.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|기존 이벤트 로그 소스의 이름입니다.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|에서 <xref:System.Diagnostics.EventSchemaTraceListener> 쓰는 파일의 이름입니다.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|에서 <xref:System.Diagnostics.TextWriterTraceListener> 쓰는 파일의 이름입니다.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|에서 <xref:System.Diagnostics.XmlWriterTraceListener> 쓰는 파일의 이름입니다.|  
  
## <a name="configuration-file"></a>구성 파일  
 이 요소는 컴퓨터 구성 파일 (machine.config) 및 응용 프로그램 구성 파일에서 사용할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 요소 `<add>` 를 사용 하 여 `textListener` 수신기 `console` 를 추적 소스 `TraceSourceApp`에 대 한 `Listeners` 컬렉션에 추가 하는 방법을 보여 줍니다. 수신기 `textListener` 는 추적 출력을 mylistener .log 파일에 기록 합니다.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>참고자료

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [추적 및 디버그 설정 스키마](index.md)
- [추적 수신기](../../../debug-trace-profile/trace-listeners.md)
