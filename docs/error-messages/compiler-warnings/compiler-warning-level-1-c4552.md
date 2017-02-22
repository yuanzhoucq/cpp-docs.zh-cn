---
title: "编译器警告（等级 1）C4552 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4552"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4552"
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4552
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 运算符无效；应输入带副作用的运算符  
  
 如果表达式语句在表达式顶部有一个没有任何副作用的运算符，则它可能是错误。  
  
 若要重写此警告，请将表达式置于圆括号中。  
  
 下面的示例生成 C4552：  
  
```  
// C4552.cpp  
// compile with: /W1  
int main() {  
   int i, j;  
   i + j;   // C4552  
   // try the following line instead  
   // (i + j);  
}  
```