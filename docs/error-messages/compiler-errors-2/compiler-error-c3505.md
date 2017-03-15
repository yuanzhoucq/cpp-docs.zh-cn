---
title: "编译器错误 C3505 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3505"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3505"
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 编译器错误 C3505
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法加载类型库“guid”  
  
 如果在 64 位计算机上运行（32 位到）64 位的跨平台编译器，则会导致 C3505 错误，因为该编译器运行于 WOW64 之下，只能从 32 位注册表配置单元读取。  
  
 通过构建尝试要导入和注册的 32 位和 64 位版本类型库，可以解除此 C3505 错误。或者，可以使用本机 64 位编译器，但这可能要求更改 IDE 中的 VC\+\+ 目录，使其指向 64 位编译器。  
  
 有关详细信息，请参阅  
  
-   [如何：在命令行上启用 64 位 Visual C\+\+ 工具集](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [如何：在命令行上启用 64 位 Visual C\+\+ 工具集](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [如何：针对 64 位平台配置 Visual C\+\+ 项目](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)