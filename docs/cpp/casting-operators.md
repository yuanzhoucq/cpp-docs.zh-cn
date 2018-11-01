---
title: 强制转换运算符
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: 4d6c8a0dc448e08ae2f344faeeb27756cdd27eff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549740"
---
# <a name="casting-operators"></a>强制转换运算符

有几种特定于 C++ 语言的转换运算符。 这些运算符用于删除旧式 C 语言转换中的一些多义性和危险继承。 这些运算符是：

- [dynamic_cast](../cpp/dynamic-cast-operator.md)用于多态类型的转换。

- [static_cast](../cpp/static-cast-operator.md)用于非多态类型的转换。

- [const_cast](../cpp/const-cast-operator.md)用于删除**const**，**易失性**，并且 **__unaligned**属性。

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md)用于位的简单重新解释。

- [safe_cast](../windows/safe-cast-cpp-component-extensions.md)用于生成可验证的 MSIL。

使用**const_cast**并**reinterpret_cast**作为最后的手段，因为这些运算符带来的危险相同为旧的样式转换。 但是，若要完全替换旧的样式转换，仍必须使用它们。

## <a name="see-also"></a>请参阅

[强制转换](../cpp/casting.md)