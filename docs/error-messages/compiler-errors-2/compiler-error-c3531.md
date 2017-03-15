---
title: "编译器错误 C3531 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3531"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3531"
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3531
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”: 其类型包含“auto”的符号必须具有初始值设定项  
  
 指定的变量没有初始值设定项表达式。  
  
### 更正此错误  
  
1.  在声明变量时，指定初始值设定项表达式（如使用等号语法的简单赋值表达式）。  
  
## 示例  
 下面的示例会产生 C3531，因为变量 `x1`、`y1, y2, y3` 和 `z2` 未初始化。  
  
```  
// C3531.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto x1;                  // C3531  
   auto y1, y2, y3;          // C3531  
   auto z1 = 1, z2, z3 = -1; // C3531  
   return 0;  
}  
```  
  
## 请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)