---
title: 基本类型的存储
ms.date: 11/04/2016
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
ms.openlocfilehash: 51b67b375cf7a4608d3080e5922cabbf3135ddfe
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152243"
---
# <a name="storage-of-basic-types"></a>基本类型的存储

下表汇总了与每个基本类型关联的存储。

### <a name="sizes-of-fundamental-types"></a>基础类型的大小

|类型|存储|
|----------|-------------|
|`char`、`unsigned char`、signed char|1 个字节|
|short、unsigned short|2 个字节|
|`int`， `unsigned int`|4 个字节|
|long、`unsigned long`|4 个字节|
|**float**|4 个字节|
|**double**|8 个字节|
|`long double`|8 个字节|

C 数据类型属于常规类别。 “整型类型”包括 `char`、`int`、short、long、signed、`unsigned` 和 `enum`。 “浮点型”包括 float、double 和 `long double`。 “算术类型”包括所有浮点型和整型。

## <a name="see-also"></a>请参阅

[声明和类型](../c-language/declarations-and-types.md)
