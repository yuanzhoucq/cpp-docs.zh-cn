---
title: "编译器错误 C2021 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2021"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2021"
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2021
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

应输入指数值，而非“character”  
  
 用作浮点常数的指数的字符是一个无效数字。  确保使用的指数在范围之内。  
  
## 示例  
 下面的示例生成 C2021：  
  
```  
// C2021.cpp  
float test1=1.175494351E;   // C2021  
```  
  
## 示例  
 可能的解决方案：  
  
```  
// C2021b.cpp  
// compile with: /c  
float test2=1.175494351E8;  
```