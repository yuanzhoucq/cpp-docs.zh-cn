---
title: "输入/输出替换选项 | Microsoft Docs"
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
  - "I/O [C++], 替代"
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 输入/输出替换选项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 为 I\/O 编程提供几种选择：  
  
-   简单的 C 运行库，则缓冲的 I\/O。  
  
-   ANSI C 运行库流 I\/O。  
  
-   控制台和端口直接 I\/O。  
  
-   Microsoft 基础类 \(MFC\) 库。  
  
-   Microsoft 标准 C\+\+ 库。  
  
 iostream 类来缓存是有用，格式化文本 I\/O。  如果需要一 . C\+\+ 编程接口并决定不使用 Microsoft 基础类 \(MFC\) \(MFC\) 库，因此它们可提供针对未缓冲或二进制 I\/O 也很有用。  iostream 类是面向对象的、I\/O 替代 C 运行时函数。  
  
 您可以使用与 Microsoft Windows 操作系统 iostream 的类。  字符串和文件流是否按未绑定，但是，字母数字流模式对象的 `cin`、`cout`、`cerr`和 `clog` 与 Windows 图形用户界面不一致的。  还可以直接派生与 Windows 环境交互的自定义类。流  
  
## 请参阅  
 [流的定义](../standard-library/what-a-stream-is.md)