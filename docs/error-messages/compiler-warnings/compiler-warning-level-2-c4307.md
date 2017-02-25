---
title: "编译器警告（等级 2）C4307 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4307"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4307"
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 2）C4307
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 整型常数溢出  
  
 该运算符用在导致整型常数溢出为其分配的空间的表达式中。  可能需要对该常数使用更大的类型。  **signed int** 用一个位表示符号，因此 **signed int** 比 `unsigned int` 保存的值小。  
  
 下面的示例生成 C4307：  
  
```  
// C4307.cpp  
// compile with: /W2  
int i = 2000000000 + 2000000000;   // C4307  
int j = (unsigned)2000000000 + 2000000000;   // OK  
  
int main()  
{  
}  
```