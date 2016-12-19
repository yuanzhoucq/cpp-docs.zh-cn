---
title: "编译器警告（等级 4）C4710 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4710"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4710"
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4710
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 函数未内联  
  
 为内联展开选定了给定函数，但编译器没有执行内联。  
  
 内联由编译器自行执行。  **inline** 关键字与 **register** 关键字一样，被用作编译器的提示。  编译器使用试探法确定它是应内联某特定函数以在为争取速度而进行编译时加快代码速度，还是应内联某特定函数以在为争取空间而进行编译时使代码变小。  编译器将只在为争取空间而进行编译时内联非常小的函数。  
  
 在某些情况下，编译器将会因为机理上的原因而不内联某个特定函数。  对于编译器可能不内联函数的原因列表，请参见 [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。