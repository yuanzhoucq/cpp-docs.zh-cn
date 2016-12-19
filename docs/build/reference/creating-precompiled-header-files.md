---
title: "创建预编译的头文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 文件, 创建"
  - "cl.exe 编译器, 预编译代码"
  - "PCH 文件, 创建"
  - "预编译的头文件, 创建"
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 创建预编译的头文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft C 和 C\+\+ 编译器提供了用于预编译任何 C 或 C\+\+ 代码（包括内联代码）的选项。  利用此性能特性，可以编译稳定的代码体，将已编译状态的代码存储在文件中，以及在随后的编译中将预编译的代码与仍在开发的代码结合起来。  由于不需要重新编译稳定代码，因此后面每次编译的速度都要快一些。  
  
 本节阐述以下预编译头问题：  
  
-   [何时需要预编译源代码](../../build/reference/when-to-precompile-source-code.md)  
  
-   [两种预编译代码方法](../../build/reference/two-choices-for-precompiling-code.md)  
  
-   [预编译头一致性规则](../../build/reference/precompiled-header-consistency-rules.md)  
  
-   [在项目中使用预编译头](../../build/reference/using-precompiled-headers-in-a-project.md)  
  
 有关与预编译头相关的编译器选项的参考信息，请参见 [\/Y（预编译头）](../../build/reference/y-precompiled-headers.md)。  
  
## 请参阅  
 [C\/C\+\+ 生成参考](../../build/reference/c-cpp-building-reference.md)   
 [编译器选项](../../build/reference/compiler-options.md)