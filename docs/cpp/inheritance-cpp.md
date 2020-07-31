---
title: 继承 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: ab8425a916eb96f6419c67a76fa401716ad84631
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232256"
---
# <a name="inheritance--c"></a>继承 (C++)

本节解释如何使用派生类生成可扩展的程序。

## <a name="overview"></a>概述

可以使用名为 "继承" 的机制从现有类派生新类（请参阅以[单一继承](../cpp/single-inheritance.md)开始的信息）。 用于派生的类称为特定派生类的“基类”。 使用以下语法声明派生类：

```cpp
class Derived : [virtual] [access-specifier] Base
{
   // member list
};
class Derived : [virtual] [access-specifier] Base1,
   [virtual] [access-specifier] Base2, . . .
{
   // member list
};
```

在类的标记（名称）后面，显示了一个后跟基本规范列表的冒号。  以这种方式命名的基类必须已提前声明。  基本规范可能包含一个访问说明符，该说明符为关键字 **`public`** **`protected`** 或 **`private`** 。  这些访问说明符显示在基类名称的前面并且仅适用于该基类。  这些说明符控制要对基类的成员使用的派生类的权限。  有关对基类成员的访问的信息，请参阅[成员访问控制](../cpp/member-access-control-cpp.md)。  如果省略访问说明符，则考虑访问该基类 **`private`** 。  基本规范可能包含 **`virtual`** 用于指示虚拟继承的关键字。  此关键字可能出现在访问说明符前面或后面（如果有）。  如果使用虚拟继承，则基类称为虚拟基类。

可指定多个基类，并用逗号分隔。  如果指定了单个基类，则继承模型为[单一继承](../cpp/single-inheritance.md)。如果指定了多个基类，则继承模型称为[多重继承](../cpp/multiple-base-classes.md)。

本文包含以下主题：

- [单个继承](../cpp/single-inheritance.md)

- [多个基类](../cpp/multiple-base-classes.md)

- [虚函数](../cpp/virtual-functions.md)

- [显式重写](../cpp/explicit-overrides-cpp.md)

- [抽象类](../cpp/abstract-classes-cpp.md)

- [范围规则摘要](../cpp/summary-of-scope-rules.md)

本部分介绍了[__super](../cpp/super.md)和[__interface](../cpp/interface.md)关键字。

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)
