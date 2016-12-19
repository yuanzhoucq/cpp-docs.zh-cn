---
title: "编译器警告（等级 1）C4028 | Microsoft Docs"
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
  - "C4028"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4028"
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4028
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

形参“number”与声明不同  
  
 形参的类型与声明中对应的参数不一致。  使用原始声明中的类型。  
  
 此警告只对 C 源代码有效。  
  
## 示例  
 下面的示例生成 C4028。  
  
```  
// C4028.c  
// compile with: /W1 /Za  
void f(int , ...);  
void f(int i, int j) {}   // C4028  
  
void g(int , int);  
void g(int i, int j) {}   // OK  
  
int main() {}  
```