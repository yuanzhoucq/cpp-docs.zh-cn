---
title: "LOCAL (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Local"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LOCAL directive"
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LOCAL (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在第一个指令，在宏中， **本地** 定义于宏的每个实例都是唯一的标签。  
  
## 语法  
  
```  
  
      LOCAL localname [[, localname]]...  
LOCAL label [[ [count ] ]] [[:type]] [[, label [[ [count] ]] [[type]]]]...  
```  
  
## 备注  
 在第二个指令，在过程定义 \(**PROC**\) 中， **本地** 创建为程序的持续时间存在的基于堆栈的变量。  该 *标签* 既可以是非独占 *计数* 元素的简单变量或数组。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)