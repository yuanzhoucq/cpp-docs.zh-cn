---
title: 内置类型（c + +）
ms.date: 07/22/2020
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- char8_t_cpp
- char16_t_cpp
- char32_t_cpp
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
ms.openlocfilehash: 73486dd4d81fc91007f078ec5c509bcb963d2706
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232269"
---
# <a name="built-in-types-c"></a>内置类型（c + +）

内置类型（也称为*基本类型*）由 c + + 语言标准指定，并内置于编译器。 未在任何标头文件中定义内置类型。 内置类型分为三个主要类别：*整数*、*浮点*和*void*。 整数类型表示整数。 浮点类型可以指定可能包含小数部分的值。 编译器将大多数内置类型视为不同类型。 但是，某些类型是*同义词*，或由编译器视为等效类型。

## <a name="void-type"></a>Void 类型

[`void`](void-cpp.md)类型描述了一组空值。 不能指定类型的变量 **`void`** 。 此 **`void`** 类型主要用于声明不返回值的函数或声明指向非类型化或任意类型数据的泛型指针。 任何表达式都可以显式转换或强制转换为类型 **`void`** 。 但是，此类表达式仅限于下列用途：

- 表达式语句。 （有关详细信息，请参阅[表达式](expressions-cpp.md)。）

- 逗号运算符的左操作数。 （有关详细信息，请参阅[逗号运算符](comma-operator.md)。）

- 条件运算符 (`? :`) 的第二个或第三个操作数。 （有关详细信息，请参阅[带条件运算符的表达式](conditional-operator-q.md)。）

## <a name="stdnullptr_t"></a>std：： nullptr_t

关键字 **`nullptr`** 是类型的 null 指针常量 `std::nullptr_t` ，它可转换为任何原始指针类型。 有关详细信息，请参阅 [`nullptr`](nullptr.md)。

## <a name="boolean-type"></a>布尔类型

[`bool`](bool-cpp.md)类型可以包含值 [`true`](../cpp/true-cpp.md) 和 [`false`](../cpp/false-cpp.md) 。 类型的大小 **`bool`** 是特定于实现的。 有关特定于 Microsoft 的实现的详细信息，请参阅[内置类型的大小](#sizes-of-built-in-types)。

## <a name="character-types"></a>字符类型

**`char`** 类型是一种用于有效地对基本执行字符集的成员进行编码的字符表示形式。 C + + 编译器将、和类型的变量视为 **`char`** **`signed char`** **`unsigned char`** 具有不同的类型。

**特定于 Microsoft**的： **`char`** **`int`** **`signed char`** 除非使用了编译选项，否则类型为的变量将作为 from type 的默认值升级为 [`/J`](../build/reference/j-default-char-type-is-unsigned.md) 。 在这种情况下，它们被视为类型 **`unsigned char`** 并提升为， **`int`** 无需签名扩展名。

类型为的变量 **`wchar_t`** 是宽字符或多字节字符类型。 在 **`L`** 字符或字符串文本前使用前缀以指定宽字符类型。

**Microsoft 专用**：默认情况下， **`wchar_t`** 是本机类型，但你可以使用 [`/Zc:wchar_t-`](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 为创建 **`wchar_t`** 一个 typedef **`unsigned short`** 。 **`__wchar_t`** 类型是本机类型的 Microsoft 专用同义词 **`wchar_t`** 。

**`char8_t`** 类型用于 utf-8 字符表示形式。 它与具有相同的表示形式 **`unsigned char`** ，但编译器将其视为不同的类型。 **`char8_t`** 类型是 c + + 20 中的新类型。 **Microsoft 专用**：的使用 **`char8_t`** 需要 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) 编译器选项。

**`char16_t`** 类型用于 utf-16 字符表示形式。 它必须足够大，以表示任何 UTF-16 代码单元。 编译器会将其视为不同的类型。

**`char32_t`** 类型用于32字符表示形式。 它必须足够大才能表示任何 UTF-32 代码单元。 编译器会将其视为不同的类型。

## <a name="floating-point-types"></a>浮点类型

浮点类型使用 IEEE-754 表示形式，在各种度上提供大致的小数值。 下表列出了 c + + 中的浮点类型以及对浮点类型大小的比较限制。 这些限制由 c + + 标准强制要求，并与 Microsoft 实现无关。 不在标准中指定内置浮点类型的绝对大小。

| 类型 | 目录 |
|--|--|
| **`float`** | 类型 **`float`** 是 c + + 中的最小浮点类型。 |
| **`double`** | 类型 **`double`** 是大于或等于类型 **`float`** 但小于或等于类型的大小的浮点类型 **`long double`** 。 |
| **`long double`** | 类型 **`long double`** 是大于或等于类型的浮点类型 **`double`** 。 |

**Microsoft 专用**：和的表示形式 **`long double`** **`double`** 完全相同。 但 **`long double`** **`double`** 编译器会将和视为不同的类型。 Microsoft c + + 编译器使用4字节和8字节 IEEE-754 浮点表示形式。 有关详细信息，请参阅[IEEE 浮点表示形式](../build/ieee-floating-point-representation.md)。

## <a name="integer-types"></a>整数类型

**`int`** 类型为默认的基本整数类型。 它可以表示特定于实现的范围内的所有整数。

*带符号*的整数表示形式可以同时包含正值和负值。 它在默认情况下使用，或者当 **`signed`** 修饰符关键字存在时使用。 **`unsigned`** 修饰符关键字指定只能保存非负值的*无符号*表示形式。

大小修饰符指定使用的整数表示形式的宽度（以位为单位）。 该语言支持 **`short`** 、 **`long`** 和 **`long long`** 修饰符。 **`short`** 类型的宽度必须至少为16位。 **`long`** 类型的宽度必须至少为32位。 **`long long`** 类型的宽度必须至少为64位。 标准指定整型类型之间的大小关系：

`1 == sizeof(char) <= sizeof(short) <= sizeof(int) <= sizeof(long) <= sizeof(long long)`

实现必须同时维护每种类型的最小大小要求和大小关系。 不过，实际大小和不同实现之间的差异。 有关特定于 Microsoft 的实现的详细信息，请参阅[内置类型的大小](#sizes-of-built-in-types)。

**`int`** 如果 **`signed`** **`unsigned`** 指定了、或大小修饰符，则可以省略关键字。 修饰符和 **`int`** 类型（如果有）可能以任意顺序出现。 例如， **`short unsigned`** 和 **`unsigned int short`** 引用同一类型。

### <a name="integer-type-synonyms"></a>整数类型同义词

编译器会将以下类型组视为同义词：

- **`short`**, **`short int`**, **`signed short`**, **`signed short int`**

- **`unsigned short`**, **`unsigned short int`**

- **`int`**, **`signed`**, **`signed int`**

- **`unsigned`**, **`unsigned int`**

- **`long`**, **`long int`**, **`signed long`**, **`signed long int`**

- **`unsigned long`**, **`unsigned long int`**

- **`long long`**, **`long long int`**, **`signed long long`**, **`signed long long int`**

- **`unsigned long long`**, **`unsigned long long int`**

特定于**Microsoft**的整数类型包括特定宽度 **`__int8`** 、、 **`__int16`** **`__int32`** 和 **`__int64`** 类型。 这些类型可以使用 **`signed`** 和 **`unsigned`** 修饰符。 **`__int8`** 数据类型与类型同义，它是与类型的同义词，与类型同义， **`char`** **`__int16`** **`short`** **`__int32`** **`int`** 并且 **`__int64`** 与类型同义 **`long long`** 。

## <a name="sizes-of-built-in-types"></a>内置类型的大小

大多数内置类型都具有实现定义的大小。 下表列出了 Microsoft c + + 中内置类型所需的存储量。 特别是， **`long`** 即使在64位操作系统上，也是4个字节。

| 类型 | 大小 |
|--|--|
| **`bool`**, **`char`**, **`char8_t`**, **`unsigned char`**, **`signed char`**, **`__int8`** | 1 字节 |
| **`char16_t`**, **`__int16`**, **`short`**, **`unsigned short`**, **`wchar_t`**, **`__wchar_t`** | 2 个字节 |
| **`char32_t`**, **`float`**, **`__int32`**, **`int`**, **`unsigned int`**, **`long`**, **`unsigned long`** | 4 个字节 |
| **`double`**, **`__int64`**, **`long double`**, **`long long`**, **`unsigned long long`** | 8 字节 |

有关每种类型的值的范围的摘要，请参阅[数据类型范围](data-type-ranges.md)。

有关类型转换的详细信息，请参阅[标准转换](standard-conversions.md)。

## <a name="see-also"></a>另请参阅

[数据类型范围](data-type-ranges.md)
