---
title: <oidEntry> 요소
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: cbdf6150010ca2dace3f0610d9caa90c2bf52746
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921053"
---
# <a name="oidentry-element"></a>\<y > 요소
ASN.1 OID(개체 식별자)를 이름에 매핑합니다.  
  
 \<configuration>  
\<mscorlib>  
\<cryptographySettings>  
\<oidMap>  
\<oidEntry>  
  
## <a name="syntax"></a>구문  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|**OID**|필수 특성입니다.<br /><br /> 클래스에서 구현 하는 알고리즘에 해당 하는 ASN OID를 지정 합니다.|  
|**name**|필수 특성입니다.<br /><br /> Nameentry > 태그에 **name 특성** 의 값을 지정 합니다. [ \<](nameentry-element.md)|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|`configuration`|공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.|  
|`cryptographySettings`|암호화 설정이 포함되어 있습니다.|  
|`mscorlib`|요소를 `cryptographySettings` 포함 합니다.|  
|`oidMap`|클래스에 대 한 OID (개체 식별자) 매핑을 포함 합니다.|  
  
## <a name="remarks"></a>설명  
 ASN 개체 식별자는 일부 암호화 형식의 알고리즘을 식별 합니다. 식별 하려는 알고리즘의 이름에 개체 식별자를 매핑합니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는  **\<y >** 요소를 사용 하 여 RIPEMD-160 해시 알고리즘에 대 한 개체 식별자를 해당 해시 알고리즘의 구현에 매핑하는 방법을 보여 줍니다.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>참고자료

- [구성 파일 스키마](../index.md)
- [암호화 설정 스키마](index.md)
- [Cryptographic Services](../../../../standard/security/cryptographic-services.md)
- [암호화 클래스 구성](../../configure-cryptography-classes.md)
- [개체 식별자를 암호화 알고리즘에 매핑](../../map-object-identifiers-to-cryptography-algorithms.md)
