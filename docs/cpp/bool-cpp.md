---
title: bool (C++)
ms.date: 11/04/2016
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
ms.openlocfilehash: 8cd035686a07285f52fe24aa7ab4f360619d5e1f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229072"
---
# <a name="bool-c"></a>bool (C++)

此关键字是内置类型。 此类型的变量可以具有值 [`true`](../cpp/true-cpp.md) 和 [`false`](../cpp/false-cpp.md) 。 条件表达式的类型为 **`bool`** ，因此具有类型的值 **`bool`** 。 例如， `i != 0` 现在具有 **`true`** 或， **`false`** 具体取决于的值 `i` 。

**Visual Studio 2017 版本15.3 及更高版本**（可用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）：后缀或前缀递增或递减运算符的操作数的类型不能为 **`bool`** 。 换而言之，假设有一个 `b` 类型为的变量 **`bool`** ，则不再允许使用这些表达式：

```cpp
    b++;
    ++b;
    b--;
    --b;
```

值 **`true`** 和 **`false`** 具有以下关系：

```cpp
!false == true
!true == false
```

在下面的语句中：

```cpp
if (condexpr1) statement1;
```

如果 `condexpr1` 为 **`true`** ， `statement1` 则始终执行; 如果 `condexpr1` 为 **`false`** ，则永远不会 `statement1` 执行。

当后缀或前缀 **`++`** 运算符应用于类型的变量时 **`bool`** ，该变量将设置为 **`true`** 。

**Visual Studio 2017 版本15.3 及更高版本**： `operator++` for **`bool`** 已从语言中删除，不再受支持。

后缀或前缀 **`--`** 运算符不能应用于此类型的变量。

**`bool`** 类型参与默认整数提升。 类型的 r 值 **`bool`** 可以转换为类型的 r 值 **`int`** ，其值为零， **`false`** **`true`** 变成一。 作为一个独特的类型， **`bool`** 参与重载决策。

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[内置类型](../cpp/fundamental-types-cpp.md)
