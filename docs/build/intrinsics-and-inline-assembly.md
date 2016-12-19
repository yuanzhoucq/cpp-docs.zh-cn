---
title: "内部和内联程序集 | Microsoft Docs"
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
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 内部和内联程序集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 编译器的约束之一是不具有内联汇编支持。  这意味着必须将不能用 C 或 C\+\+ 编写的函数编写为编译器支持的子例程或内部函数。  有些函数是性能敏感的，而有些则不是。  应将性能敏感的函数实现为内部函数。  
  
 在[编译器内部函数](../intrinsics/compiler-intrinsics.md)中对编译器支持的内部函数进行了介绍。  
  
## 请参阅  
 [x64 软件约定](../build/x64-software-conventions.md)