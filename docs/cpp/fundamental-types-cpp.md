---
title: 基本类型 (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: f4af392ed559349b0e49fd26f3ecb4406a70b74b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601365"
---
# <a name="fundamental-types--c"></a>基本类型 (C++)

C++ 中的基础类型分为三个类别：整数、浮点和 void。 整数类型能够处理整数。 浮点类型能够指定可具有小数部分的值。

[void](../cpp/void-cpp.md) 类型描述了值的空集。 类型的变量**void**可以指定-它主要用于声明不返回任何值的函数或声明泛型指针到非类型化或任意类型的数据。 任何表达式可以显式转换或强制转换为类型**void**。 但是，此类表达式仅限于下列用途：

- 表达式语句。 （有关详细信息，请参阅 [表达式](../cpp/expressions-cpp.md)。）

- 逗号运算符的左操作数。 （有关详细信息，请参阅 [逗号运算符](../cpp/comma-operator.md) 。）

- 条件运算符 (`? :`) 的第二个或第三个操作数。 （有关详细信息，请参阅 [带条件运算符的表达式](../cpp/conditional-operator-q.md) 。）

下表说明了类型大小的限制。 这些限制与 Microsoft 实现无关。

### <a name="fundamental-types-of-the-c-language"></a>C++ 语言的基础类型

|类别|类型|内容|
|--------------|----------|--------------|
|整数|**char**|类型**char**是一种整型类型通常包含基本执行字符集的成员，默认情况下，这是 Microsoft c + + 中的 ASCII。<br /><br /> C + + 编译器将类型的变量**char**，**签名 char**，并**unsigned char**不同类型。 类型的变量**char**升级到**int** ，就好像它们是类型**签名 char**默认情况下，除非使用 /J 编译选项。 在这种情况下将它们视为类型**unsigned char**并提升为**int**没有符号扩展。|
||**bool**|类型**bool**是一种整型类型可以具有两个值之一**true**或**false**。 其大小未指定。|
||**short**|类型**短整型**(或简称**短**) 是大于或等于类型的大小的整型类型**char**，但小于或等于类型大小**int**。<br /><br /> 类型的对象**短**可以声明为**short 签名**或**unsigned short**。 **简单地说签名**是的同义词**短**。|
||**int**|类型**int**是大于或等于类型的大小的整型类型**short int**，但小于或等于类型的大小**长**。<br /><br /> 类型的对象**int**可以声明为**带符号整型**或**无符号的 int**。**带符号整型**是的同义词**int**。|
||**__int8**， **__int16**， **__int32**， **__int64**|固定大小的整数 `__int n`，其中 `n` 是整数变量的大小（以比特为单位）。 **__int8**， **__int16**， **__int32**并 **__int64**是 Microsoft 专用的关键字。 并非所有类型在所有体系结构上都都可用。 (**__int128**不受支持。)|
||**long**|类型**长**(或**long int**) 是大于或等于类型的大小的整型类型**int**。<br /><br /> 类型的对象**长**可以声明为**长签名**或**无符号长**。 **签名长**是的同义词**长**。|
||**long long**|大于 unsigned**长**。<br /><br /> 类型的对象**超长**可以声明为**长长签名**或**无符号长长**。 **长时间长签名**是的同义词**超长**。|
||**wchar_t**， **__wchar_t**|类型的变量**wchar_t**指定宽字符或多字节字符类型。 默认情况下**wchar_t**是本机类型，但你可以使用[/zc: wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)以使**wchar_t**的 typedef **unsigned short**。 **__Wchar_t**类型是本机的 Microsoft 专用同义词**wchar_t**类型。<br /><br /> 在字符或字符串文本前使用 L 前缀可指定宽字符类型。|
|浮点|**float**|类型**float**是最小的浮点类型。|
||**double**|类型**双**浮动点类型是大于或等于类型**float**，但小于或等于类型的大小**长双精度型**。<br /><br /> Microsoft 专用： 的表示形式**长双精度**并**double**完全相同。 但是，**长双精度**并**double**是不同的类型。|
||**long double**|类型**长双精度**浮动点类型是大于或等于类型**double**。|

**Microsoft 专用**

下表列出了 Microsoft C++ 中的基础类型所需的存储量。

### <a name="sizes-of-fundamental-types"></a>基础类型的大小

|类型|大小|
|----------|----------|
|**bool**， **char**， **unsigned char**，**签名 char**， **__int8**|1 个字节|
|**__int16**，**短**， **unsigned short**， **wchar_t**， **__wchar_t**|2 个字节|
|**float**， **__int32**， **int**，**无符号的 int**，**长**，**无符号长**|4 个字节|
|**双精度**， **__int64**，**长双精度型**，**长时间长**|8 个字节|

**结束 Microsoft 专用**

有关每个类型的值的范围的摘要，请参阅 [数据类型范围](../cpp/data-type-ranges.md) 。

有关类型转换的详细信息，请参阅 [标准转换](../cpp/standard-conversions.md)。

## <a name="see-also"></a>请参阅

[数据类型范围](../cpp/data-type-ranges.md)