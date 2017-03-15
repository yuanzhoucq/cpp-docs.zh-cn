---
title: "常规语言更改 (C++/CLI) | Microsoft Docs"
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
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 常规语言更改 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，多种 CLR 语言功能已发生更改。  
  
 本节中介绍的更改是一种语言杂注。  它包括字符串处理中的更改、省略号与 `Param` 特性之间的重载决策中的更改、`typeof` 到 `typeid` 的更改、构造函数初始值设定项列表的调用的更改以及新的强制转换表示法（也就是 `safe_cast`）的引入。  
  
 [字符串](../dotnet/string-literal.md)  
 讨论字符串处理更改的方式。  
  
 [参数数组和省略号](../dotnet/param-array-and-ellipsis.md)  
 讨论现在如何使 `ParamArray` 优先于省略号 \(`…`\) 以便使用不同数目的参数来解析函数调用。  
  
 [typeof 转到 T::typeid](../dotnet/typeof-goes-to-t-typeid.md)  
 讨论 `typeof` 运算符由 `typeid` 取代的方式。  
  
 [初始值设定项列表](../dotnet/initializer-lists.md)  
 讨论初始值设定项列表的调用的更改。  
  
 [强制转换表示法和 safe\_cast\<\> 介绍](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)  
 讨论对强制转换表示法的更改，尤其是 `safe_cast` 的引入。  
  
## 请参阅  
 [C\+\+\/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)