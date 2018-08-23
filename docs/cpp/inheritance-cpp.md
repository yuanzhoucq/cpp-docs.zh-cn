---
title: 继承 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b75140879f44423e73c343f7567cc830d97a7b5e
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403123"
---
# <a name="inheritance--c"></a>继承 (C++)
本节解释如何使用派生类生成可扩展的程序。  
  
## <a name="overview"></a>概述  
 可以从现有类使用名为"继承"一种机制派生新类 (请参阅开头中的信息[单一继承](../cpp/single-inheritance.md))。 用于派生的类称为特定派生类的“基类”。 使用以下语法声明派生类：  
  
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
  
在类的标记（名称）后面，显示了一个后跟基本规范列表的冒号。  以这种方式命名的基类必须已提前声明。  基本规范可能包含访问说明符，它是一个关键字**公共**，**保护**或**专用**。  这些访问说明符显示在基类名称的前面并且仅适用于该基类。  这些说明符控制要对基类的成员使用的派生类的权限。  请参阅[成员访问控制](../cpp/member-access-control-cpp.md)有关基类成员的访问权限的信息。  如果访问说明符被省略，则认为此基本访问权限**专用**。  基本规范可能包含关键字**虚拟**以指示虚拟继承。  此关键字可能出现在访问说明符前面或后面（如果有）。  如果使用虚拟继承，则基类称为虚拟基类。  
  
 可指定多个基类，并用逗号分隔。  如果指定一个基类，则继承模式是[单一继承](../cpp/single-inheritance.md)。如果指定多个基类，则继承模式称为[多重继承](../cpp/multiple-base-classes.md)。  
  
 包含以下主题：  
  
-   [单一继承](../cpp/single-inheritance.md)  
  
-   [多个基类](../cpp/multiple-base-classes.md)  
  
-   [虚函数](../cpp/virtual-functions.md)  
  
-   [显式重写](../cpp/explicit-overrides-cpp.md)  
  
-   [抽象类](../cpp/abstract-classes-cpp.md)  
  
-   [范围规则摘要](../cpp/summary-of-scope-rules.md)  
  
 [__Super](../cpp/super.md)并[__interface](../cpp/interface.md)关键字在本部分中进行了说明。  
  
## <a name="see-also"></a>请参阅  
 [C++ 语言参考](../cpp/cpp-language-reference.md)