---
title: "编译器警告（等级 1）C4794 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4794"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4794"
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4794
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

线程本地存储区变量“variable”的段由“section name”改为“.tls$”  
  
 你使用了 [\#pragma data\_seg](../../preprocessor/data-seg.md) 向未以 .tls$ 开始的节中放置 tls 变量。  
  
 .Tls$*x* 节将出现在定义了 [\_\_declspec \(thread\)](../../cpp/thread.md) 变量的对象文件中。 EXE 或 DLL 中的 .tls 节将从这些节中产生。  
  
## 示例  
 下面的示例生成 C4794：  
  
```  
// C4794.cpp // compile with: /W1 /c #pragma data_seg(".someseg") __declspec(thread) int i;   // C4794 // OK #pragma data_seg(".tls$9") __declspec(thread) int j;  
```