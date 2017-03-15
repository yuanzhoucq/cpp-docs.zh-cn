---
title: "编译器警告（等级 1）C4230 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4230"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4230"
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4230
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了记时错误 : 修饰符\/限定符交错；忽略限定符  
  
 在 Microsoft 修饰符（如 `__cdecl`）的前面使用限定符是已过时的做法。  
  
## 示例  
  
```  
// C4230.cpp  
// compile with: /W1 /LD  
int __cdecl const function1();   // C4230 const ignored  
```