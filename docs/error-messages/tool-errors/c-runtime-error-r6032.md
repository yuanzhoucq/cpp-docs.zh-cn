---
title: "C 运行时错误 R6032 | Microsoft Docs"
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
  - "R6032"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6032"
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C 运行时错误 R6032
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

没有足够的空间存储区域设置信息  
  
 运行时在每个线程上维护有关区域设置的信息，以便可以处理对区域设置敏感的函数的调用。  如果为此信息分配内存失败，则运行时无法继续，因为它的很多基本功能都依赖此信息。