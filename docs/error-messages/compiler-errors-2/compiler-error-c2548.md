---
title: "编译器错误 C2548 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2548"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2548"
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2548
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class::member”: 缺少 parameter 参数的默认参数  
  
 该默认参数列表缺少某个参数。  如果在参数列表中任意位置提供默认参数，则必须为所有后面的参数定义默认参数。  
  
## 示例  
 下面的示例生成 C2548：  
  
```  
// C2548.cpp  
// compile with: /c  
void func( int = 1, int, int = 3);  // C2548  
  
// OK  
void func2( int, int, int = 3);  
void func3( int, int = 2, int = 3);  
```