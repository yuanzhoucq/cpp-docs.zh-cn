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
- long keyword [C++]
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: daa2ad2680a9d7d0239a70ed37ec1d90a3d96d97
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857536"
---
# <a name="fundamental-types--c"></a>基本类型 (C++)

C++ 中的基础类型分为三个类别：整数、浮点和 void。 整数类型能够处理整数。 浮点类型能够指定可具有小数部分的值。

[void](../cpp/void-cpp.md) 类型描述了值的空集。 不能指定**void**类型的变量-它主要用于声明不返回值的函数或声明指向非类型化或任意类型数据的泛型指针。 任何表达式都可以显式转换或强制转换为类型**void**。 但是，此类表达式仅限于下列用途：

- 表达式语句。 （有关详细信息，请参阅 [表达式](../cpp/expressions-cpp.md)。）

- 逗号运算符的左操作数。 （有关详细信息，请参阅 [逗号运算符](../cpp/comma-operator.md) 。）

- 条件运算符 (`? :`) 的第二个或第三个操作数。 （有关详细信息，请参阅 [带条件运算符的表达式](../cpp/conditional-operator-q.md) 。）

下表说明了类型大小的限制。 这些限制与 Microsoft 实现无关。

### <a name="fundamental-types-of-the-c-language"></a>C++ 语言的基础类型

|类别|类型|内容|
|--------------|----------|--------------|
|整数|**char**|类型**char**是通常包含基本执行字符集成员的整数类型-默认情况下，这是 Microsoft C++中的 ASCII。<br /><br /> 编译器C++将**char**、**带符号 char**和**无符号字符**类型的变量视为具有不同的类型。 除非使用/J 编译选项，否则**char**类型的变量将提升为**int** ，就像它们是类型**有符号 char** 。 在这种情况下，它们被视为类型**无符号字符**，并在没有符号扩展的情况下提升为**int** 。|
||**bool**|类型**bool**是整数类型，它可以是以下两个值之一： **true**或**false**。 其大小未指定。|
||**short**|类型**short int** （简称**short**）是大于或等于**char**类型的大小且小于或等于**int**类型的大小的整数类型。<br /><br /> **Short**类型的对象可声明为**有符号 short**或**无符号 short**。 **带符号 short**是**short**的同义词。|
||**int**|类型**int**是大于或等于**short int**类型的大小且小于或等于类型**long**的大小的整数类型。<br /><br /> **Int**类型的对象可声明为**有符号 int**或**无符号整数**。**带符号 int**是**int**的同义词。|
||**__int8**、 **__int16**、 **__int32** **__int64**|固定大小的整数 `__int n`，其中 `n` 是整数变量的大小（以比特为单位）。 **__int8**、 **__int16**、 **__int32**和 **__int64**是 Microsoft 特定的关键字。 并非所有类型在所有体系结构上都可用。 （不支持 **__int128** 。）|
||**long**|类型**long** （或**long int**）是大于或等于**int**类型的大小的整数类型。（在 Windows **long**上，的大小与**int**相同。）<br /><br /> **Long**类型的对象可声明为**有符号 long**或**无符号长整数**。 **带符号的 long**是**long**的同义词。|
||**long long**|大于无符号**长**整数。<br /><br /> **Long long**类型的对象可声明为**有符号长**整型或**无符号长**整数。 **带符号长**整型是**长**时间的同义词。|
||**wchar_t**， **__wchar_t**|**Wchar_t**类型的变量指定宽字符或多字节字符类型。 默认情况下， **wchar_t**是本机类型，但你可以使用[/zc： wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)将**wchar_t** typedef 设置为**无符号短**。 **__Wchar_t**类型是特定于 Microsoft 的同义词，适用于本机**wchar_t**类型。<br /><br /> 在字符或字符串文本前使用 L 前缀可指定宽字符类型。|
|浮点|**float**|类型**float**是最小的浮点类型。|
||**双精度**|类型**double**是大于或等于**float**类型但小于或等于类型**long double**的大小的浮点类型。<br /><br /> 特定于 Microsoft 的： **long double**和**double**的表示形式相同。 不过，**长双精度**型和**双精度**型是单独的类型。|
||**long double**|类型**long double**是大于或等于**double**类型的浮点类型。|

**Microsoft 专用**

下表列出了 Microsoft C++ 中的基础类型所需的存储量。

### <a name="sizes-of-fundamental-types"></a>基础类型的大小

|类型|大小|
|----------|----------|
|**bool**、 **char**、**无符号 char**、**带符号 char**、 **__int8**|1 个字节|
|**__int16**， **short**，**无符号 short**， **wchar_t**， **__wchar_t**|2 个字节|
|**float**， **__int32**， **int**，**无符号整数**，**长**，**无符号长**|4 个字节|
|**double**、 **__int64**、 **long double**、 **long long**|8 个字节|

**结束 Microsoft 专用**

有关每个类型的值的范围的摘要，请参阅 [数据类型范围](../cpp/data-type-ranges.md) 。

有关类型转换的详细信息，请参阅 [标准转换](../cpp/standard-conversions.md)。

## <a name="see-also"></a>另请参阅

[数据类型范围](../cpp/data-type-ranges.md)