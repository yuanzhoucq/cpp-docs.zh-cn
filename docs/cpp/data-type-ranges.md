---
title: 数据类型范围
ms.date: 05/07/2019
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int [C++]
- enum keyword [C++]
- unsigned char keyword [C++]
- integer data type [C++], data type ranges
- int data type
- data types [C++], ranges
- unsigned int [C++]
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type [C++], data type ranges
- signed short int [C++]
- unsigned short
- sized integer types
- signed int [C++]
- signed long int [C++]
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers [C++]
- data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int [C++]
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
ms.openlocfilehash: 8b4031eccccb432342790fef4da809542e77d669
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180259"
---
# <a name="data-type-ranges"></a>数据类型范围

Microsoft C++ 32 位和64位编译器可识别本文后面的表中的类型。

- `int` (`unsigned int`)

- `__int8` (`unsigned __int8`)

- `__int16` (`unsigned __int16`)

- `__int32` (`unsigned __int32`)

- `__int64` (`unsigned __int64`)

- `short` (`unsigned short`)

- `long` (`unsigned long`)

- `long` `long` （`unsigned long long`）

如果其名称以两个下划线 (`__`) 开始，则数据类型是非标准的。

下表中指定的范围均包含起始值和结束值。

|类型名称|字节|其他名称|值的范围|
|---------------|-----------|-----------------|---------------------|
|**int**|4|**signed**|-2,147,483,648 到 2,147,483,647|
|**unsigned int**|4|**unsigned**|0 到 4,294,967,295|
|**__int8**|1|**char**|-128 到 127|
|**未签名 __int8**|1|**unsigned char**|0 到 255|
|**__int16**|2|**short**、 **short int**、**带符号的短整型**|-32,768 到 32,767|
|**未签名 __int16**|2|**无符号短**整型，**无符号短整型**|0 到 65,535|
|**__int32**|4|**带**符号的有**符号 int**、 **int**|-2,147,483,648 到 2,147,483,647|
|**未签名 __int32**|4|**无符号**无**符号整数**|0 到 4,294,967,295|
|**__int64**|8|**长**长，**有符号长**长|-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|
|unsigned __int64|8|**无符号长长**|0 到 18,446,744,073,709,551,615|
|**bool**|1|none|**false**或**true**|
|**char**|1|none|-默认为-128 到127<br /><br /> 0 到 255（当使用 [/J](../build/reference/j-default-char-type-is-unsigned.md) 编译时）|
|**带符号字符**|1|none|-128 到 127|
|**unsigned char**|1|none|0 到 255|
|**short**|2|**short int**，**有符号短整型**|-32,768 到 32,767|
|**unsigned short**|2|**unsigned short int**|0 到 65,535|
|**long**|4|**long int**，**带符号长整型**|-2,147,483,648 到 2,147,483,647|
|**unsigned long**|4|**unsigned long int**|0 到 4,294,967,295|
|**long long**|8|无（但等效于 **__int64**）|-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|
|**无符号长长**|8|无（但等效于**未签名的 __int64**）|0 到 18,446,744,073,709,551,615|
|**enum**|多种多样|none| |
|**float**|4|none|3.4E +/- 38（7 位数）|
|**double**|8|none|1.7E +/- 308（15 位数）|
|**long double**|与**双精度**相同|none|与**双精度**相同|
|wchar_t|2|**__wchar_t**|0 到 65,535|

根据使用方式， **__wchar_t**的变量指定宽字符类型或多字节字符类型。 在字符或字符串常量前使用 `L` 前缀以指定宽字符类型常量。

**带符号**和**无符号**是可以与除**bool**以外的任何整型一起使用的修饰符。 请注意，对于重载和模板等机制而言， **char**、**有符号字符**和**无符号字符**是三种不同的类型。

**Int**和**无符号 int**类型的大小为四个字节。 但是，可移植代码不应依赖于**int**的大小，因为语言标准允许实现特定的。

Visual Studio 中的 C/C++ 还支持按大小分类的整型。 有关详细信息，请参阅 [__int8、\__int16、 \__int32、 \__int64](../cpp/int8-int16-int32-int64.md) 和 [整数限制](../cpp/integer-limits.md)。

有关每种类型的大小限制的详细信息，请参阅[内置类型](../cpp/fundamental-types-cpp.md)。

枚举类型的范围因语言上下文和指定的编译器标志而异。 有关详细信息，请参阅 [C 枚举声明](../c-language/c-enumeration-declarations.md) 和 [枚举](../cpp/enumerations-cpp.md)。

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[内置类型](../cpp/fundamental-types-cpp.md)
