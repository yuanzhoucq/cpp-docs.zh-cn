---
title: 数据类型说明符和等效项
ms.date: 11/04/2016
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
ms.openlocfilehash: cc8ba746bea7f6ea885beb625de414d83367b53f
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520676"
---
# <a name="data-type-specifiers-and-equivalents"></a>数据类型说明符和等效项

本书通常使用下表中列出的类型说明符的形式（而不是长形式），并且假定 `char` 类型在默认情况下是带符号的。 因此，在本书中，`char` 与 `signed char` 等效。

## <a name="type-specifiers-and-equivalents"></a>类型说明符和等效项

| 类型说明符 | 等效项 |
|--|--|
| `signed char`<sup>1</sup> | **`char`** |
| **`signed int`** | **`signed`** , **`int`** |
| **`signed short int`** | **`short`** , **`signed short`** |
| **`signed long int`** | **`long`** , **`signed long`** |
| **`unsigned char`** | — |
| **`unsigned int`** | **`unsigned`** |
| **`unsigned short int`** | **`unsigned short`** |
| **`unsigned long int`** | **`unsigned long`** |
| **`float`** | — |
| `long double`<sup>2</sup> | — |

<sup>1</sup> 当在默认情况下将 `char` 类型设为无符号时（通过指定 `/J` 编译器选项），无法将 `signed char` 缩写为 `char`。

<sup>2</sup> 在 32 位和 64 位操作系统中，Microsoft C 编译器将 `long double` 映射到类型 `double`。

**Microsoft 专用**

可以通过指定 `/J` 编译器选项，将默认 `char` 类型从 `signed char` 更改为 `unsigned char`。 当此选项生效时，`char` 的含义与 `unsigned char` 相同，你必须使用 `signed` 关键字来声明带符号字符值。 如果 `char` 值被显式声明为 `signed`，则 `/J` 选项不影响它，并且当加宽为 `int` 类型时，值是符号扩展的。 当加宽为 `int` 类型时，`char` 类型是零扩展的。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[C 类型说明符](../c-language/c-type-specifiers.md)
