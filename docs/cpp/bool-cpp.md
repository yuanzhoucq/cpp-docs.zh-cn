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
ms.openlocfilehash: db246cda79c778f37c5afbfda4a68c191c474e12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190490"
---
# <a name="bool-c"></a>bool (C++)

此关键字是内置类型。 此类型的变量可以具有值[true](../cpp/true-cpp.md)和[false](../cpp/false-cpp.md)。 条件表达式的类型为**bool** ，因此具有类型为**bool**的值。 例如，`i!=0` 现在具有 TRUE 或 FALSE，具体取决于 `i`的值。

**Visual Studio 2017 版本15.3 及更高版本**（可用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）：后缀或前缀递增或递减运算符的操作数的类型不能为**bool**。 换言之，在给定变量 `b` 类型为**bool**后，将不再允许使用以下表达式：

```cpp
    b++;
    ++b;
    b--;
    --b;
```

值 TRUE 和 FALSE 具有以下关系：

```cpp
!false == true
!true == false
```

在下面的语句中：

```cpp
if (condexpr1) statement1;
```

如果 `condexpr1` 为 TRUE，则始终执行 `statement1`;如果 `condexpr1` 为 FALSE，则永远不会执行 `statement1`。

将后缀或前缀 **++** 运算符应用到类型为**bool**的变量时，该变量将设置为 TRUE。
**Visual Studio 2017 版本15.3 及更高版本**：已从该语言中删除了用于**bool**的 operator + +，不再受支持。

后缀或前缀 **--** 运算符不能应用于此类型的变量。

**Bool**类型参与了整型提升。 **Bool**类型的 r 值可以转换为**int**类型的 r 值，而 FALSE 将变为零，并且 TRUE 变为一。 作为一种独特的类型， **bool**参与重载决策。

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[内置类型](../cpp/fundamental-types-cpp.md)
