---
title: "编译器警告（等级 1）C4020 | Microsoft Docs"
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
  - "C4020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4020"
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 实参太多  
  
 函数调用中实参的数目超过函数原型或函数定义中形参的数目。  编译器根据函数的调用约定传递多余的实参。  
  
 下面的示例生成 C4020：  
  
```  
// C4020.c  
// compile with: /W1 /c  
void f(int);  
int main() {  
   f(1,2);   // C4020  
}  
```  
  
 可能的解决方案：  
  
```  
// C4020b.c  
// compile with: /c  
void f(int);  
int main() {  
   f(1);  
}  
```