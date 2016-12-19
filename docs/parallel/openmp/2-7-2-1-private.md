---
title: "2.7.2.1 private | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.1 private
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`private` 子句声明变量变量列表是私有的。在团队的每个线程。  `private` 子句的语法如下所示:  
  
```  
private(variable-list)  
```  
  
 在 `private` 子句指定变量的行为如下所示。  具有自动存储持续时间的新对象用于构造分配。  新对象的大小和对齐取决于变量的类型。  此分配在团队中的每个线程都发生一次，并且，默认构造函数为类对象如果需要，调用;否则原始值是不确定的。  该变量引用的原始对象封送在项对构造，所需的不确定的值不在构造中的动态区域被修改，并具有一个不确定的值从构造退出。  
  
 在指令中构造的词法区域，该变量引用线程分配的新私有对象。  
  
 为 `private` 子句的限制如下所示:  
  
-   与 `private` 子句中指定的类类型的变量必须有一个可访问，明确的默认构造函数。  
  
-   ，除非它具有 `mutable` 成员，的类类型在 `private` 子句中指定的变量不能有 **const**\- 限定类型。  
  
-   在 `private` 子句中指定的变量不能包含不完整类型或引用类型。  
  
-   显示 **并行** 指令的 `reduction` 子句的变量。 `private` 子句不能指定在绑定到并行构造的工作划分指令。