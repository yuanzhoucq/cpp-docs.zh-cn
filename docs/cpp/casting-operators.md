---
title: 强制转换运算符
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: eac274a0207be675b8d13532c3110c6e71bd55c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190089"
---
# <a name="casting-operators"></a>强制转换运算符

有几种特定于 C++ 语言的转换运算符。 这些运算符用于删除旧式 C 语言转换中的一些多义性和危险继承。 这些运算符是：

- [dynamic_cast](../cpp/dynamic-cast-operator.md)用于多态类型的转换。

- [static_cast](../cpp/static-cast-operator.md)用于非多态类型的转换。

- [const_cast](../cpp/const-cast-operator.md)用于删除**const**、 **volatile**和 **__unaligned**特性。

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md)用于位的简单 reinterpretation。

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md)在/Cli C++中用于生成可验证的 MSIL。

使用**const_cast**和**reinterpret_cast**作为最后的手段，因为这些运算符与旧的样式转换存在相同的危险。 但是，若要完全替换旧的样式转换，仍必须使用它们。

## <a name="see-also"></a>另请参阅

[强制转换](../cpp/casting.md)
