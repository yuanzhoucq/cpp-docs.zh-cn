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
ms.openlocfilehash: e481cb9de7c80d147179efceab2fda9b160f3c21
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638121"
---
# <a name="bool-c"></a>bool (C++)

此关键字是内置类型。 此类型的变量可以具有值[，则返回 true](../cpp/true-cpp.md)并[false](../cpp/false-cpp.md)。 条件表达式具有类型**bool** ，因此拥有类型的值**bool**。 例如，`i!=0`现在具有 TRUE 或 FALSE，具体取决于值`i`。

**Visual Studio 2017 15.3 及更高版本**(适用于[/std:C++ 17](../build/reference/std-specify-language-standard-version.md)): 操作数的后缀或前缀递增或递减运算符不能为类型**bool**。 换而言之，给定变量`b`类型的**bool**，不再允许两个表达式：

```cpp
    b++;
    ++b;
    b--;
    --b;
```

TRUE 和 FALSE 的值具有以下关系：

```cpp
!false == true
!true == false
```

在下面的语句中：

```cpp
if (condexpr1) statement1;
```

如果`condexpr1`为 TRUE 时，`statement1`时始终执行; 如果`condexpr1`为 FALSE，`statement1`永远不会执行。

当后缀或前缀**++** 运算符应用于类型的变量**bool**，将变量设置为 TRUE。
**Visual Studio 2017 版本 15.3 及更高版本**： 的 operator + + **bool**从该语言已被删除，不再受支持。

后缀或前缀**--** 运算符不能应用于此类型的变量。

**Bool**类型参与了整型提升。 类型的右值**bool**可转换为类型为右值**int**、 与 FALSE 成为零和 TRUE 变为 1。 作为截然不同的类型， **bool**参与重载决策。

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[基本类型](../cpp/fundamental-types-cpp.md)