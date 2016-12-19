---
title: "错误 C1126 | Microsoft Docs"
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
  - "C1126"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1126"
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1126
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 自动分配超过 size  
  
 分配给函数局部变量的空间（以及限制编译器使用的空间量，例如用于可交换函数的额外 20 字节）超过限制。  
  
 若要更正此错误，请使用 `malloc` 或 `new` 来分配大量数据。