---
title: XAML 리소스
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: 738a4f397b1677b867126c7bb439b027f951baa0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958816"
---
# <a name="xaml-resources"></a>XAML 리소스
리소스는 애플리케이션의 여러 위치에서 다시 사용할 수 있는 개체입니다. 리소스의 예로는 브러시와 스타일이 있습니다. 이 개요에서는에서 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]리소스를 사용 하는 방법을 설명 합니다. 코드를 사용 하 여 리소스를 만들고 액세스할 수도 있으며 코드와 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]를 서로 바꿔 볼 수도 있습니다. 자세한 내용은 [리소스 및 코드](resources-and-code.md)를 참조 하세요.  
  
> [!NOTE]
> 이 항목에서 설명 하는 리소스 파일은 [WPF 응용 프로그램 리소스, 콘텐츠 및 데이터 파일](../app-development/wpf-application-resource-content-and-data-files.md) 에 설명 된 리소스 파일과 다르며 [응용 프로그램 리소스 관리 (.net)에 설명 된 포함 또는 링크 된 리소스와 다릅니다. ](/visualstudio/ide/managing-application-resources-dotnet).  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>XAML의 리소스 사용  
 다음 예제에서는 페이지의 <xref:System.Windows.Media.SolidColorBrush> 루트 요소에서를 리소스로 정의 합니다. 그런 다음이 예제에서는 리소스를 참조 하 고이를 사용 하 여 <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Controls.TextBlock>, 및 <xref:System.Windows.Controls.Button>를 비롯 한 여러 자식 요소의 속성을 설정 합니다.  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 모든 프레임 워크 수준 요소 (<xref:System.Windows.FrameworkElement> 또는 <xref:System.Windows.FrameworkContentElement>)에 <xref:System.Windows.FrameworkElement.Resources%2A> 는 리소스를 정의 하는 리소스로 <xref:System.Windows.ResourceDictionary>를 포함 하는 속성인 속성이 있습니다. 모든 요소에서 리소스를 정의할 수 있습니다. 그러나 리소스는 루트 요소에 정의 되는 경우가 가장 많습니다 .이 <xref:System.Windows.Controls.Page> 는 예제에 있습니다.  
  
 리소스 디렉터리의 각 리소스에는 고유 키가 있어야 합니다. 태그에 리소스를 정의 하는 경우 [X:Key 지시문](../../xaml-services/x-key-directive.md)을 통해 고유 키를 할당 합니다. 일반적으로 키는 문자열이지만, 적절한 태그 확장을 사용하여 다른 개체 형식으로도 설정할 수 있습니다. 리소스에 대 한 문자열이 아닌 키는의 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]특정 기능 영역, 특히 스타일, 구성 요소 리소스 및 데이터 스타일에 사용 됩니다.  
  
 리소스를 정의한 다음 키 이름을 지정하는 리소스 태그 확장 구문을 사용하여 속성에 사용되도록 해당 리소스를 참조할 수 있습니다. 예를 들어 다음과 같습니다.  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 앞의 예제에서 로더가 <xref:System.Windows.Controls.Control.Background%2A> 속성 <xref:System.Windows.Controls.Button>의 값 `{StaticResource MyBrush}` 을 처리할 때 리소스 조회 논리 <xref:System.Windows.Controls.Button> 는 먼저 해당 요소에 대 한 리소스 사전을 확인 합니다. 에 <xref:System.Windows.Controls.Button> 리소스 키 `MyBrush` 에 대 한 정의가 없는 경우 (해당 리소스 컬렉션이 비어 있음) 조회는 다음의 <xref:System.Windows.Controls.Button>부모 <xref:System.Windows.Controls.Page>요소 ()를 확인 합니다. 따라서 <xref:System.Windows.Controls.Page> 루트 요소에 리소스를 정의 하는 경우 <xref:System.Windows.Controls.Page> 의 논리적 트리에서 모든 요소가 액세스할 수 있으며, 리소스를 사용 하는를 <xref:System.Type> 허용 하는 모든 속성의 값을 설정 하는 데 동일한 리소스를 다시 사용할 수 있습니다. 나타내는지. 이전 예제에서 동일한 리소스는의 `MyBrush` 및 <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>의와 같은 두 가지 속성을 설정 합니다. <xref:System.Windows.Shapes.Rectangle>  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>정적 및 동적 리소스  
 리소스는 정적 리소스 또는 동적 리소스로 참조될 수 있습니다. [StaticResource 태그 확장](staticresource-markup-extension.md) 또는 [DynamicResource 태그 확장](dynamicresource-markup-extension.md)을 사용 하 여이 작업을 수행 합니다. 태그 확장은 태그 확장이 특성 문자열 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 을 처리 하 고 개체 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 를 로더에 반환 하도록 하 여 개체 참조를 지정할 수 있는의 기능입니다. 태그 확장 동작에 대 한 자세한 내용은 [태그 확장 및 WPF XAML](markup-extensions-and-wpf-xaml.md)을 참조 하세요.  
  
 태그 확장을 사용하면 일반적으로 설정 중인 속성의 컨텍스트에서 평가되는 것이 아니라 특정 태그 확장을 통해 처리되는 문자열 형식으로 하나 이상의 매개 변수를 제공합니다. [StaticResource 태그 확장](staticresource-markup-extension.md) 은 사용 가능한 모든 리소스 사전에서 해당 키에 대 한 값을 조회 하 여 키를 처리 합니다. 이 작업은 로드 프로세스에서 정적 리소스 참조를 사용하는 속성 값을 할당해야 하는 시점인 로드 시에 수행됩니다. [DynamicResource 태그 확장](dynamicresource-markup-extension.md) 은 대신 식을 만들어 키를 처리 하 고, 해당 식은 응용 프로그램이 실제로 실행 될 때까지 확인 되지 않은 상태로 유지 되며,이 경우 식이 계산 되 고 값이 제공 됩니다.  
  
 리소스를 참조할 때 정적 리소스 참조를 사용하는지 아니면 동적 리소스 참조를 사용하는지에 상관없이 영향을 미칠 수 있는 고려 사항은 다음과 같습니다.  
  
- 응용 프로그램에 대 한 리소스를 만드는 방법에 대 한 전반적인 디자인으로, 응용 프로그램에서 응용 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]프로그램에 대 한 리소스를 만드는 방법에 대 한 전반적인 디자인은 리소스 전용 어셈블리에 있습니다.  
  
- 애플리케이션 기능: 애플리케이션 요구 사항의 일부로서 실시간으로 리소스 업데이트.  
  
- 해당 리소스 참조 형식의 각 조회 동작.  
  
- 특정 속성 또는 리소스 형식 및 해당 형식의 기본 동작.  
  
### <a name="static-resources"></a>정적 리소스  
 정적 리소스 참조는 다음 환경에 가장 적합합니다.  
  
- 애플리케이션 디자인에서는 대부분의 리소스를 페이지나 애플리케이션 수준 리소스 사전에 집중합니다. 정적 리소스 참조는 페이지 다시 로드와 같은 런타임 동작을 기반으로 다시 평가하지 않으므로, 리소스와 애플리케이션 디자인별로 필요하지 않을 때 다수의 동적 리소스 참조를 사용하지 않을 수 있다는 성능상의 이점이 있습니다.  
  
- <xref:System.Windows.DependencyObject>또는에 없는 속성의 값을 설정 합니다. <xref:System.Windows.Freezable>  
  
- DLL로 컴파일되고 애플리케이션의 일부로 컴파일되거나 애플리케이션에 공유될 리소스 사전을 만듭니다.  
  
- 사용자 지정 컨트롤의 테마를 만들고 테마에서 사용되는 리소스를 정의합니다. 이 경우 일반적으로 동적 리소스 참조 조회 동작을 사용하지 않습니다. 대신, 조회가 예측 가능하고 테마에 자체 포함되도록 정적 리소스 참조 동작을 사용합니다. 동적 리소스 참조를 사용하면, 테마에 있는 참조까지도 런타임 시까지 평가되지 않은 상태로 남아 있게 되며, 테마를 적용할 때 일부 요소에서 테마가 참조하려는 키를 재정의하고 조회에서 로컬 요소가 테마 자체보다 앞에 옵니다. 이 경우 테마가 예상대로 작동하지 않습니다.  
  
- 리소스를 사용하여 다수의 종속성 속성을 설정합니다. 종속성 속성에는 속성 시스템에서 사용하게 설정한 유효 값이 캐싱이 있습니다. 따라서 로드 시 평가될 수 있는 종속성 속성의 값을 제공하는 경우, 종속성 속성에서 재평가된 식을 확인하지 않아도 되며 마지막 유효 값을 반환할 수 있습니다. 이 기술을 사용하면 성능상의 이점이 있습니다.  
  
- 모든 소비자에 대 한 기본 리소스를 변경 하거나 [X:Shared 특성](../../xaml-services/x-shared-attribute.md)을 사용 하 여 각 소비자에 대해 별도의 쓰기 가능한 인스턴스를 유지 하려고 합니다.  
  
#### <a name="static-resource-lookup-behavior"></a>정적 리소스 조회 동작  
  
1. 조회 프로세스가 속성을 설정하는 요소를 통해 정의된 리소스 사전에서 요청된 키를 확인합니다.  
  
2. 그런 다음 조회 프로세스가 논리 트리를 상향식으로 통과하여 부모 요소와 해당 리소스 사전으로 이동합니다. 이 작업은 루트 요소에 도달할 때까지 계속됩니다.  
  
3. 다음으로 애플리케이션 리소스를 확인합니다. 응용 프로그램 리소스는 <xref:System.Windows.Application> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 응용 프로그램에 대해 개체에 의해 정의 되는 리소스 사전 내의 리소스입니다.  
  
 리소스 사전 내의 정적 리소스 참조는 리소스 참조 전에 사전순으로 이미 정의된 리소스를 참조해야 합니다. 전방 참조는 정적 리소스 참조로 확인할 수 없습니다. 따라서 정적 리소스 참조를 사용하는 경우, 리소스별 용도에 맞게 리소스를 각 리소스 사전의 시작 부분에 정의하도록 리소스 사전 구조를 디자인해야 합니다.  
  
 정적 리소스 조회는 테마 또는 시스템 리소스로 확장 될 수 있지만 로더가 요청을 지연 하는 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 경우에만 지원 됩니다. 페이지가 로드될 때 런타임 테마가 애플리케이션에 적절하게 적용되기 위해 지연이 필요합니다. 그러나 테마에만 존재하거나 시스템 리소스로 존재하는 것으로 알려진 키의 정적 리소스 참조는 사용하지 않는 것이 좋습니다. 사용자가 실시간으로 테마를 변경하는 경우 해당 참조가 다시 평가되지 않기 때문입니다. 동적 리소스 참조는 테마나 시스템 리소스를 요청할 때 더욱 안정적입니다. 테마 요소 자체가 다른 리소스를 요청할 때는 예외입니다. 이러한 참조는 앞서 설명한 이유때문에 정적 리소스 참조여야 합니다.  
  
 정적 리소스 참조가 없으면 다양한 예외 동작이 발생합니다. 리소스가 지연되면 런타임 시 예외가 발생합니다. 리소스가 지연되지 않으면 로드 시 예외가 발생합니다.  
  
### <a name="dynamic-resources"></a>동적 리소스  
 동적 리소스는 다음과 같은 환경에 가장 적합합니다.  
  
- 리소스 값은 런타임 시까지 알려지지 않은 조건에 따라 달라집니다. 여기에는 시스템 리소스 또는 사용자가 설정 가능한 리소스가 포함됩니다. 예를 들어, <xref:System.Windows.SystemColors> <xref:System.Windows.SystemFonts>또는 <xref:System.Windows.SystemParameters>에 의해 노출 되는 시스템 속성을 참조 하는 setter 값을 만들 수 있습니다. 이러한 값은 궁극적으로 운영 체제와 사용자의 런타임 환경에서 오므로 정말로 동적입니다. 변경할 수 있는 애플리케이션 수준 테마도 있습니다. 이 경우 페이지 수준 리소스 액세스를 통해서도 변경 사항을 캡처해야 합니다.  
  
- 사용자 지정 컨트롤의 테마 스타일을 만들거나 참조합니다.  
  
- 응용 프로그램 수명 <xref:System.Windows.ResourceDictionary> 동안의 내용을 조정 하려고 합니다.  
  
- 상호 종속된 복잡한 리소스 구조체 가 있으며, 이 경우에는 전방 참조가 필요할 수 있습니다. 정적 리소스 참조는 전방 참조를 지원 하지 않지만, 동적 리소스 참조는 런타임에 대 한 리소스를 평가할 필요가 없으며 전방 참조가 관련 개념이 아닐 수 있으므로 이러한 참조를 지원 합니다.  
  
- 컴파일 또는 작업 집합 면에서 특히 큰 리소스를 참조하며, 페이지를 로드할 때 즉시 리소스를 사용하지 않을 수도 있습니다. 정적 리소스 참조는 페이지가 로드 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 될 때 항상에서 로드 되지만 동적 리소스 참조는 실제로 사용할 때까지 로드 되지 않습니다.  
  
- setter 값이 테마나 다른 사용자 설정의 영향을 받는 다른 값에서 오는 스타일을 만듭니다.  
  
- 애플리케이션 수명 중에 논리 트리에서 다시 부모가 지정될 수 있는 요소에 리소스를 적용합니다. 부모를 변경하면 리소스 조회 범위도 변경될 수 있으므로, 부모가 재지정된 요소의 리소스를 새 범위에 따라 재평가하려면 항상 동적 리소스 참조를 사용하세요.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>동적 리소스 조회 동작  
 <xref:System.Windows.FrameworkElement.FindResource%2A> 또는<xref:System.Windows.FrameworkElement.SetResourceReference%2A>를 호출 하는 경우 동적 리소스 참조의 리소스 조회 동작은 코드의 조회 동작과 유사 합니다.  
  
1. 조회 프로세스가 속성을 설정하는 요소를 통해 정의된 리소스 사전에서 요청된 키를 확인합니다.  
  
    - 요소가 속성을 <xref:System.Windows.FrameworkElement.Style%2A> 정의 <xref:System.Windows.Style.Resources%2A> 하는 경우 내에서 <xref:System.Windows.Style> 사전을 검사 합니다.  
  
    - 요소가 속성을 <xref:System.Windows.Controls.Control.Template%2A> 정의 <xref:System.Windows.FrameworkTemplate.Resources%2A> 하는 경우 내에서 <xref:System.Windows.FrameworkTemplate> 사전을 검사 합니다.  
  
2. 그런 다음 조회 프로세스가 논리 트리를 상향식으로 통과하여 부모 요소와 해당 리소스 사전으로 이동합니다. 이 작업은 루트 요소에 도달할 때까지 계속됩니다.  
  
3. 다음으로 애플리케이션 리소스를 확인합니다. 응용 프로그램 리소스는 <xref:System.Windows.Application> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 응용 프로그램에 대해 개체에 의해 정의 되는 리소스 사전 내의 리소스입니다.  
  
4. 현재 활성 테마의 테마 리소스 사전을 확인합니다. 런타임 시 테마가 변경되면 값을 재평가합니다.  
  
5. 시스템 리소스를 확인합니다.  
  
 예외 동작이 있는 경우 다음과 같이 다양합니다.  
  
- <xref:System.Windows.FrameworkElement.FindResource%2A> 호출에서 리소스를 요청 했지만를 찾을 수 없는 경우 예외가 발생 합니다.  
  
- <xref:System.Windows.FrameworkElement.TryFindResource%2A> 호출에서 리소스를 요청 했지만 찾을 수 없는 경우 예외가 발생 하지 않지만 반환 되는 `null`값은입니다. 설정 되는 속성이 허용 `null`되지 않는 경우에도 더 깊은 예외가 발생할 수 있습니다 .이는 설정 된 개별 속성에 따라 달라 집니다.  
  
- 에서 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]동적 리소스 참조를 통해 리소스를 요청 하 고를 찾을 수 없는 경우 동작은 일반 속성 시스템에 따라 다르지만 일반적인 동작은 리소스가 있는 수준에서 속성 설정 작업이 발생 하지 않은 것과 같습니다. 예를 들어, 평가할 수 없는 리소스를 사용하여 개별 단추 요소에서 배경을 설정하려고 하면 값 집합이 생기지 않지만, 속성 시스템 및 값 우선 순위의 다른 참가자로부터 유효 값을 여전히 가져올 수 있습니다. 예를 들어, 배경색은 로컬에 정의한 단추 스타일 또는 테마 스타일에서 여전히 가져올 수 있습니다. 테마 스타일이 정의하지 않은 속성의 경우, 실패한 리소스 평가 후 유효 값은 속성 메타데이터의 기본값에서 가져올 수 있습니다.  
  
#### <a name="restrictions"></a>제한  
 동적 리소스 참조에는 몇 가지 주목할 만한 제한 사항이 있습니다. 다음 중 하나 이상이 참이어야 합니다.  
  
- 설정 되는 속성은 <xref:System.Windows.FrameworkElement> 또는 <xref:System.Windows.FrameworkContentElement>의 속성 이어야 합니다. 이 속성은에서 <xref:System.Windows.DependencyProperty>지원 되어야 합니다.  
  
- <xref:System.Windows.Style> 내의<xref:System.Windows.Setter>값에 대 한 참조입니다.  
  
- 설정 <xref:System.Windows.Freezable> 되는 속성은 <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>또는속성 값 또는 값으로제공되는의속성이어야합니다.<xref:System.Windows.Setter>  
  
 설정 <xref:System.Windows.DependencyProperty> 되는 속성은 또는 <xref:System.Windows.Freezable> 속성 이어야 하므로 속성 시스템에서 속성 변경 (변경 된 동적 리소스 값)이 승인 되기 때문에 대부분의 속성 변경 내용이 UI에 전파 될 수 있습니다. 대부분의 컨트롤에는 <xref:System.Windows.DependencyProperty> 변경 및 해당 속성이 레이아웃에 영향을 줄 수 있는 경우 컨트롤의 다른 레이아웃을 강제로 적용 하는 논리가 포함 됩니다. 그러나 [DynamicResource 태그 확장이](dynamicresource-markup-extension.md) 값으로 포함 된 일부 속성은 UI에서 실시간으로 업데이트 하는 방식으로 값을 제공 하도록 보장 됩니다. 이 기능은 속성 외에도 속성을 소유하는 형식, 심지어는 애플리케이션의 논리 구조체에 따라서도 여전히 달라질 수 있습니다.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>스타일, DataTemplates 및 암시적 키  
 이전에는 <xref:System.Windows.ResourceDictionary> 의 모든 항목에 키가 있어야 한다고 설명 했습니다. 그러나 모든 리소스에 명시적 `x:Key`가 있어야 한다는 의미는 아닙니다. 리소스로 정의된 경우 여러 개체 형식에서 암시적 키를 지원하며, 이 경우 키 값이 다른 속성의 값과 연결됩니다. 이를 암시적 키 `x:Key` 라고 하지만 특성은 명시적 키입니다. 명시적 키를 지정하여 암시적 키를 덮어쓸 수 있습니다.  
  
 리소스에 대해 매우 중요 한 시나리오 중 하나는를 <xref:System.Windows.Style>정의 하는 경우입니다. 실제로 스타일은 기본적 <xref:System.Windows.Style> 으로 다시 사용 하기 위한 것 이므로는 리소스 사전의 항목으로 거의 항상 정의 됩니다. 스타일에 대 한 자세한 내용은 스타일 지정 [및 템플릿](../controls/styling-and-templating.md)을 참조 하세요.  
  
 컨트롤의 스타일은 암시적 키로 만들어 참조될 수 있습니다. 컨트롤의 기본 모양을 정의하는 테마 스타일은 이 암시적 키에 따라 달라집니다. 를 요청 하 <xref:System.Type> 는 관점에서 암시적 키는 컨트롤 자체의입니다. 리소스를 정의 하는 관점에서 암시적 키는 스타일 <xref:System.Windows.Style.TargetType%2A> 의입니다. 따라서 사용자 지정 컨트롤에 대 한 테마를 만들고 기존 테마 스타일과 상호 작용 하는 스타일을 만드는 경우 해당 <xref:System.Windows.Style>에 대 한 [x:Key 지시문](../../xaml-services/x-key-directive.md) 을 지정할 필요가 없습니다. 테마로 지정된 스타일을 사용하려면 스타일을 전혀 지정하지 않아도 됩니다. 예를 들어 다음 스타일 정의는 <xref:System.Windows.Style> 리소스가 키가 없는 것 처럼 보이는 경우에도 작동 합니다.  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 해당 스타일에는 암시적 키인 `typeof(` <xref:System.Windows.Controls.Button> `)`키가 있습니다. 태그에서을 <xref:System.Windows.Style.TargetType%2A> 형식 이름으로 직접 지정할 수 있습니다. 또는 선택적으로 [{x:Type...}](../../xaml-services/x-type-markup-extension.md) 을 사용할 수 있습니다. 을 <xref:System.Type>반환 하려면입니다.  
  
 에서 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]사용 하는 기본 테마 스타일 메커니즘을 통해 해당 스타일은 해당 <xref:System.Windows.FrameworkElement.Style%2A> 속성이 나 특정 리소스를 <xref:System.Windows.Controls.Button> 지정 하지 않는 경우 <xref:System.Windows.Controls.Button> 에도 페이지에 대 한 런타임 스타일로 적용 됩니다. 스타일에 대 한 참조입니다. 페이지에 정의 된 스타일은 테마 사전 스타일과 동일한 키를 사용 하 여 조회 시퀀스에서 테마 사전 스타일 보다 먼저 발견 됩니다. 페이지에서 아무 곳 `<Button>Hello</Button>` 이나 지정할 수 있으며,를 `Button` 사용 <xref:System.Windows.Style.TargetType%2A> 하 여 정의한 스타일이 해당 단추에 적용 됩니다. 원하는 경우 태그를 명확 하 게 하기 위해와 동일한 유형 값을 사용 하 여 <xref:System.Windows.Style.TargetType%2A>스타일을 명시적으로 키로 지정할 수 있지만이는 선택 사항입니다.  
  
 스타일에 대 한 암시적 키는가 인 경우 <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> 컨트롤에 적용 되지 않습니다. 또한 <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> 컨트롤의 인스턴스에서 명시적이 `true` 아닌 컨트롤 클래스에 대 한 기본 동작의 일부로 설정할 수 있습니다. 또한 파생 된 클래스 시나리오에 대해 암시적 키를 지원 하려면 컨트롤이를 재정의 해야 합니다 <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> .의 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 일부로 제공 되는 모든 기존 컨트롤을 재정의 해야 합니다. 스타일, 테마 및 컨트롤 디자인에 대 한 자세한 내용은 [스타일 컨트롤을 디자인 하기 위한 지침](../controls/guidelines-for-designing-stylable-controls.md)을 참조 하세요.  
  
 <xref:System.Windows.DataTemplate>에는 암시적 키도 있습니다. <xref:System.Windows.DataTemplate> 의<xref:System.Windows.DataTemplate.DataType%2A> 암시적 키는 속성 값입니다. <xref:System.Windows.DataTemplate.DataType%2A>는 명시적으로 [{x:Type...}](../../xaml-services/x-type-markup-extension.md)를 사용 하는 대신 형식의 이름으로 지정할 수도 있습니다. 자세한 내용은 [데이터 템플릿 개요](../data/data-templating-overview.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고자료

- <xref:System.Windows.ResourceDictionary>
- [응용 프로그램 리소스](optimizing-performance-application-resources.md)
- [리소스 및 코드](resources-and-code.md)
- [리소스 정의 및 참조](how-to-define-and-reference-a-resource.md)
- [응용 프로그램 관리 개요](../app-development/application-management-overview.md)
- [x:Type 태그 확장](../../xaml-services/x-type-markup-extension.md)
- [StaticResource 태그 확장](staticresource-markup-extension.md)
- [DynamicResource 태그 확장](dynamicresource-markup-extension.md)
