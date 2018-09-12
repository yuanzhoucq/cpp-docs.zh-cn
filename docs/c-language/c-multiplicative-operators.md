---
title: C 乘法运算符 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arithmetic operators [C++], multiplicative operators
- / operator
- / operator, multiplicative operators
- remainder operator (%)
- operators [C], multiplication
- '% operator'
- slash (/) operator
- multiplication operator [C++], multiplicative operators
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0be97e271ce8b500274d0e2ab1f271183ef7c238
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199989"
---
# <a name="c-multiplicative-operators"></a>C 乘法运算符
乘法运算符执行乘法 (<strong>\*</strong>)、除法 (/) 和余数 (%) 运算。  
  
## <a name="syntax"></a>语法

*multiplicative-expression*：  
&nbsp;&nbsp;&nbsp;&nbsp;cast-expression  
&nbsp;&nbsp;&nbsp;&nbsp;multiplicative-expression <strong>\*</strong> cast-expression  
&nbsp;&nbsp;&nbsp;&nbsp;multiplicative-expression / cast-expression  
&nbsp;&nbsp;&nbsp;&nbsp;multiplicative-expression % cast-expression

余数操作符 (%) 的操作数必须是整数。 乘法 (\*) 和除法 (/) 运算符可采用整型或浮点类型操作数；操作数的类型可以是不同的。  
  
乘法运算符对操作数执行常用算术转换。 结果的类型是转换后操作数的类型。  
  
> [!NOTE]
>  由于在溢出或下溢条件不提供由乘法运算符执行的转换，因此，如果乘法操作的结果在转换后不能用操作数类型表示，则信息可能丢失。  
  
 C 乘法运算符的描述如下：  
  
|运算符|描述|  
|--------------|-----------------|  
|<strong>\*</strong>|乘法运算符使其两个操作数相乘。|  
|**/**|除法运算符使第一个操作数除以第二个操作数。 如果两个整数操作数相除，结果不是整数，则根据下列规则截断它：<br/><br/>- 根据 ANSI C 标准，被 0 除的结果是不确定的。 Microsoft C 编译器将在编译时或运行时生成错误。<br/><br/>- 如果两个操作数都为正或无符号，则结果将截断到 0。<br/><br/>- 如果其中一个操作数为负，则不管操作结果是小于或等于代数商的最大整数还是大于或等于代数商的最小整数，结果均为定义的实现。 （请参阅下面的 Microsoft 专用部分。）|  
|**%**|第一个操作数除以第二个操作数时，余数运算符的结果是余数。 如果除法不精确，则结果将由下列规则确定：<br/><br/>- 如果右操作数为零，则结果是不确定的。<br/><br/>- 如果两个操作数均为正或无符号，则结果为正。<br/><br/>- 如果其中一个操作数为负，并且结果不精确，则结果将是定义的实现。 （请参阅下面的 Microsoft 专用部分。）|  
  
 **Microsoft 专用**  
  
 在其中一个操作数为负的除法中，截断的方向将是朝向 0。  
  
 如果使用余数运算符的除法中任一操作数为负，则结果与被除数（表达式中的第一个操作数）有相同的符号。  
  
 **结束 Microsoft 专用**  
  
## <a name="examples"></a>示例  
 如下所示的声明将用于下列示例：  
  
```  
int i = 10, j = 3, n;  
double x = 2.0, y;  
```  
  
 此语句使用乘法运算符：  
  
```  
y = x * i;  
```  
  
 在此示例中，`x` 乘以 `i` 将得到值 20.0。 结果为 double 类型。  
  
```  
n = i / j;  
```  
  
 在此示例中，10 除以 3。 结果将被截断到 0，同时产生整数值 3。  
  
```  
n = i % j;  
```  
  
 当 10 除以 3 时，此语句为 `n` 分配整数余数 1。  
  
 **Microsoft 专用**  
  
 余数的符号与被除数的符号相同。 例如:  
  
```  
50 % -6 = 2  
-50 % 6 = -2  
```  
  
 在所有情况下，`50` 和 `2` 具有相同的符号。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [乘法运算符和取模运算符](../cpp/multiplicative-operators-and-the-modulus-operator.md)