---
title: "编译器错误 C2692 | Microsoft Docs"
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
  - "C2692"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2692"
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2692
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function\_name”: 具有“\/clr”选项的 C 编译器要求完全保持原型的函数  
  
 编译 .NET 托管代码时，C 编译器需要 ANSI 函数声明。  另外，如果函数不采用参数，则它必须将 `void` 显式声明为参数类型。