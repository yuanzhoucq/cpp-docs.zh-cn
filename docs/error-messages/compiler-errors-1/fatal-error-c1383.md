---
title: "错误 C1383 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1383"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1383"
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 错误 C1383
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器选项 \/GL 与安装的公共语言运行时版本不兼容  
  
 将以前版本的公共语言运行时与较新编译器结合使用时，以及使用 **\/clr** 和 **\/GL.** 进行编译时，会发生 C1383。  
  
 要进行解决，请勿将 **\/GL** 与 **\/clr** 结合使用，或是安装随你的编译器附带的公共语言运行时版本。  
  
 有关详细信息，请参阅[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)和[\/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)。