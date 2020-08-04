---
title: 基本类型的存储
ms.date: 10/02/2019
helpviewer_keywords:
- specifiers [C++], type
- integral types, storage
- storage [C++], types
- floating-point numbers, storage
- type specifiers [C++], sizes
- arithmetic operations [C++], types
- int data type
- short data type
- signed types [C++], storage
- long double keyword [C], storage
- long keyword [C]
- double data type, storage
- types [C], arithmetic
- integral types
- data types [C], specifiers
- storing types [C++]
- unsigned types [C++], storage
- data types [C], storage
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
ms.openlocfilehash: 973866a912b694510d587df765ac8dd54176638e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211666"
---
# <a name="storage-of-basic-types"></a>基本类型的存储

下表汇总了与每个基本类型关联的存储。

## <a name="sizes-of-fundamental-types"></a>基础类型的大小

|类型|存储|
|----------|-------------|
|**`char`** , **`unsigned char`** , **`signed char`**|1 个字节|
|**`short`** , **`unsigned short`**|2 个字节|
|**`int`** , **`unsigned int`**|4 个字节|
|**`long`** , **`unsigned long`**|4 个字节|
|**`long long`** , **`unsigned long long`**|8 个字节|
|**`float`**|4 个字节|
|**`double`**|8 个字节|
|**`long double`**|8 个字节|

C 数据类型属于常规类别。 整型类型包括 `int`、`char`、`short`、`long` 和 `long long`。 这些类型可使用 `signed` 或 `unsigned` 进行限定，`unsigned` 本身可以用作 `unsigned int` 的简写。 枚举类型 (`enum`) 在大多数情况下也被视为整型类型。 浮点类型包括 `float`、`double` 和 `long double`。 “算术类型”包括所有浮点型和整型类型  。

## <a name="see-also"></a>请参阅

[声明和类型](../c-language/declarations-and-types.md)
