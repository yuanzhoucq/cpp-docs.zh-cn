---
title: 命名空间
ms.date: 11/04/2016
helpviewer_keywords:
- union keyword [C], tags
- enumeration tags
- structure tags
- names [C++], declared elements
- name spaces [C++]
- tags, structure tags
- union keyword [C]
ms.assetid: b4bda1d1-cb5e-4f60-ac2b-29af93d8a9a2
ms.openlocfilehash: 76ad9b797a4f192e8f22f8c040f5a308371a461b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325762"
---
# <a name="name-spaces"></a>命名空间

编译器设置“命名空间”来区分用于各种项的标识符。 每个命名空间中的名称必须是唯一的以避免冲突，但相同的名称可出现在多个命名空间中。 这意味着，可以对两个或更多不同的项使用同一个标识符，前提是这些项位于不同的命名空间中。 编译器可以基于程序中标识符的语义上下文来解析引用。

> [!NOTE]
> 不要将命名空间的有限 C 概念与 C++“命名空间”功能混淆。 有关详细信息，请参阅“C++ 语言参考”中的[命名空间](../cpp/namespaces-cpp.md)。

此列表描述了 C 中使用的命名空间。

语句标签 命名的语句标签是语句的一部分。 语句标签的定义始终后跟冒号，但不是 **case** 标签的一部分。 语句标签始终紧跟在关键字 goto  后面。 语句标签不必与其他名称或其他函数中的标签名称有所不同。

结构、联合和枚举这些标记属于结构、联合和枚举类型说明符。如果有的话，这些标记始终紧跟在保留字 struct  、union  或 enum  后面。 标记名称必须不同于具有相同可见性的所有其他结构、枚举或联合标记。

结构或联合的成员 成员名称分配在与各结构和联合类型关联的命名空间中。 即，同一标识符可以同时为任意数量的结构或联合的组件名称。 组件名称的定义总是出现在结构或联合类型说明符中。 组件名称的使用总是紧跟在成员选择运算符（ **->** 和 **.** ）之后。 成员的名称在结构或联合中必须是唯一的，但它无需不同于程序中的其他名称（包括不同的结构和联合的成员或结构本身的名称）。

普通标识符 所有其他名称都属于一个包含变量、函数（包括形参和局部变量）和枚举常量的命名空间。 标识符名称具有嵌套可见性，因此您可以在块内重新定义它们。

Typedef 名称 Typedef 名称不能用作同一作用域内的标识符。

例如，由于结构标记、结构成员和变量名位于三个不同的命名空间中，因此该示例中名为 `student` 的三个项不会发生冲突。 在该程序中，每个项的上下文允许对 `student` 的每个匹配项进行正确解释。 （有关结构的信息，请参阅[结构声明](../c-language/structure-declarations.md)。）

```C
struct student {
   char student[20];
   int class;
   int id;
   } student;
```

如果 `student` 跟在 struct  关键字后面，编译器会将它识别为结构标记。 当 `student` 出现在成员选择运算符 ( **->** 或 **.** ) 的后面时，名称将引用结构成员。 在其他上下文中，`student` 引用结构变量。 但是，建议不要重载标记命名空间，因为它会使含义变得模糊。

## <a name="see-also"></a>请参阅

[程序结构](../c-language/program-structure.md)
