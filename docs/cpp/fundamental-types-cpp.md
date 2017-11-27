---
title: "基本类型 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- double_cpp
- float_cpp
- int_cpp
- long_cpp
- long_double_cpp
- short_cpp
- signed_cpp
- unsigned_cpp
- unsigned_int_cpp
- wchar_t_cpp
dev_langs: C++
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type [C++], C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type [C++]
- double data type [C++], summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers [C++], C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++], C++ data types
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f30f680449ee0eee1d25f1705d2c98adfe88c312
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="fundamental-types--c"></a>基本类型 (C++)
C++ 中的基础类型分为三个类别：整数、浮点和 void。 整数类型能够处理整数。 浮点类型能够指定可具有小数部分的值。  
  
 [void](../cpp/void-cpp.md) 类型描述了值的空集。 `void` 类型的变量无法指定 - 它主要用于声明不返回值的函数或用于声明指向非类型化或任意类型化数据的一般指针。 任何表达式都可以显示或强制转换为类型 `void`。 但是，此类表达式仅限于下列用途：  
  
-   表达式语句。 （有关详细信息，请参阅 [表达式](../cpp/expressions-cpp.md)。）  
  
-   逗号运算符的左操作数。 （有关详细信息，请参阅 [逗号运算符](../cpp/comma-operator.md) 。）  
  
-   条件运算符的第二个或第三个操作数 (`? :`)。 （有关详细信息，请参阅 [带条件运算符的表达式](../cpp/conditional-operator-q.md) 。）  
  
 下表说明了类型大小的限制。 这些限制与 Microsoft 实现无关。  
  
### <a name="fundamental-types-of-the-c-language"></a>C++ 语言的基础类型  
  
|类别|类型|内容|  
|--------------|----------|--------------|  
|整数|`char`|类型 `char` 是通常包含基本执行字符集成员的整数类型 - 默认情况下，这是 Microsoft C++ 中的 ASCII。<br /><br /> C++ 编译器将 `char`, `signed` `char`和 `unsigned` `char` 类型的变量视为不同类型。 `char` 类型的变量将提升到 `int` ，就像它们在默认情况下是 `signed` `char` 类型一样，除非使用 /J 编译选项。 在这种情况下，它们被视为 `unsigned` `char` 类型并提升为 `int` （没有符号扩展）。|  
||`bool`|`bool` 类型是可以具有 `true` 或 `false`这两个值之一的整数类型。 其大小未指定。|  
||`short`|`short` `int` 类型（或 `short`）是大于或等于 `char`类型的大小但小于或等于 `int`类型的大小的整型类型。<br /><br /> `short`类型的对象可声明为 `signed` `short` 或 `unsigned short`。 `Signed short` 是 `short`的同义词。|  
||`int`|`int` 类型是大于或等于 `short` `int`类型的大小但小于或等于 `long`类型的大小的整数类型。<br /><br /> `int` 类型的对象可声明为 `signed` `int` 或 `unsigned` `int`。 `Signed` `int` 是 `int`的同义词。|  
||`__int8`, `__int16`, `__int32`, `__int64`|固定大小的整数 `__int n`，其中 `n` 是整数变量的大小（以比特为单位）。 `__int8`、 `__int16`、 `__int32` 和 `__int64` 是 Microsoft 专用的关键字。 并非所有类型在所有体系结构上都都可用。 `(__int128`不支持。）|  
||`long`|`long` 类型（或 `long` `int`）是大于或等于 `int`类型的大小的整数类型。<br /><br /> `long` 类型的对象可声明为 `signed` `long` 或 `unsigned` `long`。 `Signed` `long` 是 `long`的同义词。|  
||`long` `long`|大于无符号 `long`。<br /><br /> `long long` 类型的对象可声明为 `signed` `long long` 或 `unsigned` `long long`。 `signed``long long`是同义词`long long`。|  
||`wchar_t`, `__wchar_t`|`wchar_t` 类型的变量指定宽字符或多字节字符类型。 默认情况下， `wchar_t` 是本机类型，但可以使用 [/Zc: wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 使 `wchar_t` 成为 `unsigned short`的 typedef。 `__wchar_t` 类型是本机 `wchar_t` 类型的 Microsoft 专用同义词。<br /><br /> 在字符或字符串文本前使用 L 前缀可指定宽字符类型。|  
|浮点|`float`|`float` 类型是最小的浮点类型。|  
||`double`|`double` 类型是大于或等于 `float`类型的大小但小于或等于 `long` `double`类型的大小的浮点类型。<br /><br /> Microsoft 专用： `long double` 和 `double` 的表示形式完全相同。 但是， `long double` 和 `double` 是不同的类型。|  
||`long double`|`long` `double` 类型是大于或等于 `double`类型的浮点类型。|  
  
 **Microsoft 专用**  
  
 下表列出了 Microsoft C++ 中的基础类型所需的存储量。  
  
### <a name="sizes-of-fundamental-types"></a>基础类型的大小  
  
|类型|大小|  
|----------|----------|  
|`bool`, `char`, `unsigned char`, `signed char`, `__int8`|1 个字节|  
|`__int16`, `short`, `unsigned short`, `wchar_t`, `__wchar_t`|2 个字节|  
|`float`、 `__int32`、 `int`、 `unsigned int`、 `long`、 `unsigned long`|4 个字节|  
|`double`, `__int64`, `long double`, `long long`|8 个字节|  
  
 **结束 Microsoft 专用**  
  
 有关每个类型的值的范围的摘要，请参阅 [数据类型范围](../cpp/data-type-ranges.md) 。  
  
 有关类型转换的详细信息，请参阅 [标准转换](../cpp/standard-conversions.md)。  
  
## <a name="see-also"></a>另请参阅  
 [数据类型范围](../cpp/data-type-ranges.md)