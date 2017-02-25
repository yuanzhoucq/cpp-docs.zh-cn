---
title: "编译器错误 C2223 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2223"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2223"
ms.assetid: e4506f0f-0317-4a96-8a90-877a156d7939
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C2223
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\-\>表示符”的左侧必须指向结构\/联合  
  
 `->` 左边的操作数不是指向类、结构或联合的指针。  
  
 导致此错误的原因可能是由于左边的操作数是未定义的变量（因此为 `int` 类型）。