---
title: "汇编语言注释 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 关键字 [C++], 指令"
  - "汇编语言 [C++], 注释"
  - "注释 [C++], 汇编语言"
  - "宏 [C++], 汇编语言"
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 汇编语言注释
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定  
 说明在`__asm`块可以使用程序集语言注释：  
  
```  
__asm mov ax, offset buff ; Load address of buff  
```  
  
 因为到一个逻辑行扩展 C 宏，避免在宏中使用程序集语言注释。  （请参阅[定义为 C 宏 \_\_asm 块](../../assembler/inline/defining-asm-blocks-as-c-macros.md)。）  `__asm`块还可以包含 C 样式注释。 有关详细信息，请参阅[使用 C 或 c \+ \+ 中 \_\_asm 块](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。  
  
 **最终 Microsoft 特定**  
  
## 请参阅  
 [在 \_\_asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)