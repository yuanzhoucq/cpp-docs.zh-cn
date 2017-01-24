---
title: "错误 C1905 | Microsoft Docs"
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
  - "C1905"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1905"
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1905
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

前端和后端不兼容（必须面向同一处理器）  
  
 当 .obj 文件由以一个处理器（如 x86、ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]）为目标的编译器前端 \(C1.dll\) 生成，但由以另一个处理器为目标的后端 \(C2.dll\) 读取时，将发生此错误。  
  
 若要解决此问题，请确保你使用的前端和后端相匹配。  对于 Visual Studio 中创建的项目，这是默认的。  如果已编辑该项目文件并使用通向编译器工具的不同路径，则可能会出现此错误。  如果未特别设置编译器工具的路径，则你的 Visual Studio 安装损坏时可能发生此错误。  例如，你可能已将编译器 .dll 文件从一个位置复制到另一个位置。  使用 Windows 控制面板中的“程序和功能”修复或重新安装 Visual Studio。