---
title: Not 연산자(Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 29e2b159e4c6261a62e788b537102b9b457fe0c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955826"
---
# <a name="not-operator-visual-basic"></a>Not 연산자(Visual Basic)
`Boolean` 식에 논리 부정을 수행 하거나 숫자 식에 비트 부정을 수행 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>요소  
 `result`  
 필수 요소. 모든 `Boolean` 또는 숫자 식입니다.  
  
 `expression`  
 필수. 모든 `Boolean` 또는 숫자 식입니다.  
  
## <a name="remarks"></a>설명  
 다음 `Boolean` 표에서는 식의 경우를 결정 `result` 하는 방법을 보여 줍니다.  
  
|경우 `expression` 됩니다|의 `result` 값이 인 경우|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 숫자 식의 경우 연산자 `Not` 는 숫자 식의 비트 값을 반전 하 고 다음 표에 따라의 `result` 해당 비트를 설정 합니다.  
  
|비트가 `expression` 인 경우|의 `result` 비트는|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> 논리 및 비트 연산자는 다른 산술 및 관계형 연산자 보다 낮은 우선 순위를 가지 므로 정확한 실행을 위해 모든 비트 연산을 괄호로 묶어야 합니다.  
  
## <a name="data-types"></a>데이터 형식  
 부울 부정의 경우 결과 `Boolean`의 데이터 형식은입니다. 비트 부정의 경우 결과 데이터 형식은의 `expression`경우와 동일 합니다. 그러나 expression이 `Decimal`이면 `Long`결과는입니다.  
  
## <a name="overloading"></a>오버로딩  
 연산자를 오버 로드할 수 있습니다. 즉, 해당 피연산자의 형식이 해당 클래스 또는 구조체의 형식인 경우 클래스 또는 구조체에서 해당 동작을 다시 정의할 수 있습니다. `Not` 코드가 이러한 클래스 또는 구조체에서이 연산자를 사용 하는 경우 다시 정의 된 동작을 이해 해야 합니다. 자세한 내용은 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)을 참조하세요.  
  
## <a name="example"></a>예제  
 다음 예에서는 `Not` 연산자를 사용 하 여 `Boolean` 식에 논리 부정을 수행 합니다. 결과는 식의 `Boolean` 값을 반대로 나타내는 값입니다.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 앞의 예제에서는 각각 및 `False` `True`의 결과를 생성 합니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 `Not` 연산자를 사용 하 여 숫자 식의 개별 비트에 대 한 논리 부정을 수행 합니다. 결과 패턴의 비트는 부호 비트를 포함 하 여 피연산자 패턴에서 해당 비트의 역방향으로 설정 됩니다.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 앞의 예제에서는 – 11, – 9 및 – 7의 결과를 각각 생성 합니다.  
  
## <a name="see-also"></a>참고자료

- [논리/비트 연산자 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic에서의 연산자 우선 순위](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [기능별 연산자 목록](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 논리 및 비트 연산자](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
