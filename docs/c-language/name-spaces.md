---
title: "命名空间 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- union keyword [C], tags
- enumeration tags
- structure tags
- names [C++], declared elements
- name spaces [C++]
- tags, structure tags
- union keyword [C]
ms.assetid: b4bda1d1-cb5e-4f60-ac2b-29af93d8a9a2
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 6b567d74b27e04c05f48f174f52f7f221cb4f154
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="name-spaces"></a>命名空间
编译器设置“命名空间”来区分用于各种项的标识符。 每个命名空间中的名称必须是唯一的以避免冲突，但相同的名称可出现在多个命名空间中。 这意味着，可以对两个或更多不同的项使用同一个标识符，前提是这些项位于不同的命名空间中。 编译器可以基于程序中标识符的语义上下文来解析引用。  
  
> [!NOTE]
>  不要将命名空间的有限 C 概念与 C++“命名空间”功能混淆。 有关详细信息，请参阅《C++ 语言参考》中的[命名空间](../cpp/namespaces-cpp.md)。  
  
 此列表描述了 C 中使用的命名空间。  
  
 语句标签  
 命名的语句标签是语句的一部分。 语句标签的定义始终后跟冒号，但不是 **case** 标签的一部分。 语句标签的使用始终后跟关键字 `goto`。 语句标签不必与其他名称或其他函数中的标签名称有所不同。  
  
 结构、联合和枚举标记  
 这些标记是结构、联合和枚举类型说明符的一部分，总是紧跟在保留字 `struct`、**union** 或 `enum` 的后面（如果有）。 标记名称必须不同于具有相同可见性的所有其他结构、枚举或联合标记。  
  
 结构或联合的成员  
 成员名称分配在与每个结构和联合类型关联的命名空间中。 即，同一标识符可以同时为任意数量的结构或联合的组件名称。 组件名称的定义总是出现在结构或联合类型说明符中。 组件名称的使用总是紧跟在成员选择运算符（**->** 和 **.**）之后。 成员的名称在结构或联合中必须是唯一的，但它无需不同于程序中的其他名称（包括不同的结构和联合的成员或结构本身的名称）。  
  
 普通标识符  
 所有其他名称都属于一个包含变量、函数（包括形参和局部变量）和枚举常量的命名空间。 标识符名称具有嵌套可见性，因此您可以在块内重新定义它们。  
  
 Typedef 名称  
 Typedef 名称不能用作同一范围内的标识符。  
  
 例如，由于结构标记、结构成员和变量名位于三个不同的命名空间中，因此该示例中名为 `student` 的三个项不会发生冲突。 在该程序中，每个项的上下文允许对 `student` 的每个匹配项进行正确解释。 （有关结构的信息，请参阅[结构声明](../c-language/structure-declarations.md)。）  
  
```  
struct student {  
   char student[20];  
   int class;  
   int id;  
   } student;  
```  
  
 当 `student` 出现在 `struct` 关键字的后面时，编译器会将其识别为结构标记。 当 `student` 出现在成员选择运算符 (**->** 或 **.**) 的后面时，名称将引用结构成员。 在其他上下文中，`student` 引用结构变量。 但是，建议不要重载标记命名空间，因为它会使含义变得模糊。  
  
## <a name="see-also"></a>另请参阅  
 [程序结构](../c-language/program-structure.md)
