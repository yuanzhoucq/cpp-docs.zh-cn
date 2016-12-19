---
title: "编译器警告（等级 1）C4717 | Microsoft Docs"
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
  - "C4717"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4717"
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4717
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 递归所有控件路径，函数将导致运行时堆栈溢出  
  
 每个涉及函数的路径都包含对该函数的调用。  因为无法在没有首次递归调用函数本身的情况下退出该函数，所以函数将永远不退出。  
  
 下面的示例生成 C4717：  
  
```  
// C4717.cpp  
// compile with: /W1 /c  
// C4717 expected  
int func(int x) {  
   if (x > 1)  
      return func(x - 1); // recursive call  
   else {  
      int y = func(0) + 1; // recursive call  
      return y;  
   }  
}  
  
int main(){  
   func(1);  
}  
```