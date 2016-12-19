---
title: "发行版本 | Microsoft Docs"
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
helpviewer_keywords: 
  - "调试版本, 转换为发行版本"
  - "调试 [C++], 发行版本"
  - "发行版本"
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 发行版本
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

发布版本使用优化。  当使用优化创建发布版本时，编译器不会产生符号调试信息。  没有符号调试信息，以及不为 TRACE 和 ASSERT 调用生成代码的事实，意味着可执行文件的大小将减小并由此运行得更快。  
  
 本节介绍有关为什么以及何时需要将调试版本更改为发布版本的信息。  还讨论将调试版本更改为发布版本时可能碰到的一些问题：  
  
-   [创建发布版本](../../build/reference/how-to-create-a-release-build.md)  
  
-   [创建发布版本时遇到的常见问题](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
-   [修复发布版本问题](../../build/reference/fixing-release-build-problems.md)  
  
    -   [检查 ASSERT 语句](../../build/reference/using-verify-instead-of-assert.md)  
  
    -   [使用调试版本检查内存覆盖](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)  
  
    -   [调试发布版本](../../build/reference/how-to-debug-a-release-build.md)  
  
    -   [检查内存覆盖](../../build/reference/checking-for-memory-overwrites.md)  
  
## 请参阅  
 [在 Visual Studio 中生成 C\+\+ 项目](../../ide/building-cpp-projects-in-visual-studio.md)   
 [C\/C\+\+ 生成参考](../../build/reference/c-cpp-building-reference.md)