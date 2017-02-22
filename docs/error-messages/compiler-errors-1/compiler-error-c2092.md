---
title: "编译器错误 C2092 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2092"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2092"
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2092
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“array name”数组元素类型不能是函数  
  
 不允许使用函数数组。  请使用指向函数的指针的数组。  
  
## 示例  
 下面的示例生成 C2092：  
  
```  
// C2092.cpp  
typedef void (F) ();  
typedef F AT[10];   // C2092  
```  
  
## 示例  
 可能的解决方案：  
  
```  
// C2092b.cpp  
// compile with: /c  
typedef void (F) ();  
typedef F * AT[10];  
```