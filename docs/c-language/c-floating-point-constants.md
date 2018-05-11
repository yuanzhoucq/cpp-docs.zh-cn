---
title: C 浮点常量 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3608e40db2aa3eb0c49942de278c1d428e26689f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="c-floating-point-constants"></a>C 浮点常量
“浮点常量”是表示带符号实数的十进制数字。 带符号实数的表现形式包括整数部分、小数部分和指数。 浮点常量用于表示不可更改的浮点值。  
  
## <a name="syntax"></a>语法  
 *floating-point-constant*：  
 &nbsp;&nbsp; *fractional-constant exponent-part*<sub>opt</sub> *floating-suffix*<sub>opt</sub>  
 &nbsp;&nbsp; *digit-sequence exponent-part floating-suffix*<sub>opt</sub>  
  
 *fractional-constant*：  
 &nbsp;&nbsp; *digit-sequence*<sub>opt</sub> **.** *digit-sequence*  
 &nbsp;&nbsp; *digit-sequence*  **.**  
  
 *exponent-part*：  
 &nbsp;&nbsp; **e**  *sign*<sub>opt</sub> *digit-sequence*  
 &nbsp;&nbsp; **E**  *sign*<sub>opt</sub> *digit-sequence*  
  
 *sign*：一个   
 &nbsp;&nbsp; **+ -**  
  
 *digit-sequence*：  
 &nbsp;&nbsp; *digit*  
 &nbsp;&nbsp; *digit-sequence digit*  
  
 *floating-suffix*一个   
 &nbsp;&nbsp; **f l F L**  
  
 你可以省略小数点前面的数字（整数部分）或小数点后面的数字（小数部分），但不能同时省略。 仅当包括一个指数时可省略小数点。 空白字符不能分隔常量的数字或字符。  
  
 以下示例阐释了某些形式的浮点常量和表达式：  
  
```  
15.75  
1.575E1   /* = 15.75   */  
1575e-2   /* = 15.75   */  
-2.5e-3   /* = -0.0025 */  
25E-4     /* =  0.0025 */  
```  
  
 浮点常量为正数，除非它们的前面有减号 (**-**)。 在这种情况下，减号将视为一元算术求反运算符。 浮点常量包括类型 `float`、`double` 或 `long double`。  
  
 浮点常量没有 **f**、**F** 或 **l**，或者 **L** 后缀类型为 `double`。 如果后缀是字母 **f** 或 **F**，则该常量类型为 `float`。 如果后缀是字母 **l** 或 **L**，则该常量类型为 `long double`。 例如:  
  
```  
100L  /* Has type long double  */  
100F  /* Has type float        */  
```  
  
 请注意，与 `double` 类型相同，Microsoft C 编译器在内部表示 `long double`。 请参阅[基本类型的存储](../c-language/storage-of-basic-types.md)，了解有关类型 `double`、`float` 和 `long double` 的信息。  
  
 如下例所示，可以省略浮点常量的整数部分。 可以通过包括下列方式在内的多种方式表达 .75：  
  
```  
.0075e2  
0.075e1  
.075e1  
75e-2  
```  
  
## <a name="see-also"></a>请参阅  
 [C 常量](../c-language/c-constants.md)