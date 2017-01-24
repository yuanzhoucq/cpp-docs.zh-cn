---
title: "编译器警告 C4746 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告 C4746
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\<表达式\>'的不稳定的访问“受 \/volatile:\<iso&#124;ms\> 设置的限制；请考虑使用 \_\_iso\_volatile\_load\/store 内部函数  
  
 发出 C4746 当直接访问可变变量时。  旨在帮助开发人员标识受当前指定的特定 volatile 模型的影响 \(可控制与 [\/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) 编译器选项\) 的代码位置。  具体而言，当使用 \/volatile:ms时，它对于定位编译器生成的硬件内存屏障很有用。  
  
 \_\_iso\_volatile\_load\/store 内部可用来显式访问易失存储器，无需受影响变量模型的。  使用这些内部函数不会触发 C4746。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。