---
title: "命令行错误 D8027 | Microsoft Docs"
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
  - "D8027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D8027"
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令行错误 D8027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法执行“component”  
  
 编译器未能运行给定的编译器组件或链接器。  
  
### 通过检查以下可能的原因进行修复  
  
1.  内存不足，无法加载该组件。  如果 NMAKE 调用了编译器，则在生成文件外部运行编译器。  
  
2.  当前的操作系统未能运行该组件。  确保路径指向适合您的操作系统的可执行文件。  
  
3.  该组件已损坏。  使用 SETUP 程序从分发磁盘上重新复制该组件。  
  
4.  选项被错误指定。  例如：  
  
    ```  
    cl /B1 file1.c  
    ```