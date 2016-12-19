---
title: "修复发行版本问题 | Microsoft Docs"
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
  - "调试版本, 内存改写"
  - "内存, 改写"
  - "发行版本, 疑难解答"
  - "发行版本疑难解答"
  - "Visual C++ 疑难解答, 发行版本"
ms.assetid: a0c0818e-4c47-4fe0-a611-50d61a41bd88
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 修复发行版本问题
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果从调试版本切换到发布版本后代码生成编译错误，有几个方面应该检查。  
  
 在优化的（发布）版本过程中可能会收到编译器警告，而在调试版本过程中却未收到。  
  
-   [检查 ASSERT 语句](../../build/reference/using-verify-instead-of-assert.md)  
  
-   [使用调试版本检查内存覆盖](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)  
  
-   [为发布版本打开调试信息的生成](../../build/reference/how-to-debug-a-release-build.md)  
  
-   [检查内存覆盖](../../build/reference/checking-for-memory-overwrites.md)  
  
## 请参阅  
 [发行版本](../../build/reference/release-builds.md)   
 [创建发行版本时遇到的常见问题](../../build/reference/common-problems-when-creating-a-release-build.md)   
 [优化代码](../../build/reference/optimizing-your-code.md)