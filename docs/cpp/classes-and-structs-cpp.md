---
title: "类和结构 （C++） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, classes
- structures, C++ classes
- user-defined types
- classes [C++]
- user-defined types, C++ classes
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ac15db222aed3abad980f4e1a0c715c099e2019c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="classes-and-structs-c"></a>类和结构 (C++)
此部分介绍 C++ 类和结构。 这两个构造在 C++ 中是相同的，只不过在结构中，默认可访问性是公共的，而在类中，默认值是私有的。  
  
 类和结构是用于定义你自己的类型的构造。 类和结构都可以包含数据成员和成员函数，使你可以描述类型的状态和行为。  
  
 包含以下主题：  
  
-   [类](../cpp/class-cpp.md)  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [类成员概述](../cpp/class-member-overview.md)  
  
-   [成员访问控制](../cpp/member-access-control-cpp.md)  
  
-   [继承](../cpp/inheritance-cpp.md)  
  
-   [静态成员](../cpp/static-members-cpp.md)  
  
-   [用户定义类型转换](../cpp/user-defined-type-conversions-cpp.md)  
  
-   [可变数据成员 （可变说明符）](../cpp/mutable-data-members-cpp.md)  
  
-   [嵌套类声明](../cpp/nested-class-declarations.md)  
  
-   [匿名类类型](../cpp/anonymous-class-types.md)  
  
-   [指向成员的指针](../cpp/pointers-to-members.md)  
  
-   [this 指针](../cpp/this-pointer.md)  
  
-   [C++ 位域](../cpp/cpp-bit-fields.md)  
  
 三种类类型是结构、类和联合。 它们使用声明[结构](../cpp/struct-cpp.md)，[类](../cpp/class-cpp.md)，和[联合](../cpp/unions.md)关键字 (请参阅[定义类类型](http://msdn.microsoft.com/en-us/e8c65425-0f3a-4dca-afc2-418c3b1e57da))。 下表显示三种类类型之间的差异。  
  
 有关联合的详细信息，请参阅[联合](../cpp/unions.md)。 有关托管的类和结构的信息，请参阅[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>结构、类和联合的访问控制和约束  
  
|结构|类|联合|  
|----------------|-------------|------------|  
|类别键是 `struct`|类别键是**类**|类别键是**联合**|  
|默认访问是公共的|默认访问是私有的|默认访问是公共的|  
|没有使用约束|没有使用约束|一次只使用一个成员|  
  
## <a name="see-also"></a>请参阅  
 [C++ 语言参考](../cpp/cpp-language-reference.md)