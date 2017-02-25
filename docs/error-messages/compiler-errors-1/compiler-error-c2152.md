---
title: "编译器错误 C2152 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2152"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2152"
ms.assetid: a9ea2b0c-d55d-41c7-ba9f-dd75592ffc8a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C2152
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 指向有不同特性的函数的指针  
  
 指向具有某个调用约定（`__cdecl`、`__stdcall` 或 `__fastcall`）的函数的指针被分配给了指向具有另一个调用约定的函数的指针。