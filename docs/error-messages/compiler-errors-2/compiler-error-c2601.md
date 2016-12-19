---
title: "编译器错误 C2601 | Microsoft Docs"
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
  - "C2601"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2601"
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2601
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 本地函数定义是非法的  
  
 代码尝试在函数内定义函数。  
  
 或者，在该 C2601 错误位置前的源代码中有一个额外的大括号。  
  
 下面的示例生成 C2601：  
  
```  
// C2601.cpp  
int main() {  
   int i = 0;  
  
   void funcname(int j) {   // C2601  
      j++;  
   }  
}  
```