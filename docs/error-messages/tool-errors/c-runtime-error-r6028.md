---
title: "C 运行时错误 R6028 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6028"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6028"
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# C 运行时错误 R6028
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法初始化堆  
  
 当操作系统未能为应用程序创建内存池时，将发生此错误。  具体来说，C 运行时 \(CRT\) 调用的 Win32 函数 `HeapCreate` 返回了指示失败的 NULL。  
  
 如果在应用程序启动期间发生此错误，则系统可能会因为加载了有缺陷的驱动程序而无法满足堆请求。  请在 Windows Update 或硬件供应商的网站中查看已更新的驱动程序。