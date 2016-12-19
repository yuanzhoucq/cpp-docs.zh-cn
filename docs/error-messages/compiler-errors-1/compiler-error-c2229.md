---
title: "编译器错误 C2229 | Microsoft Docs"
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
  - "C2229"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2229"
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2229
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类型“identifier”有非法的零大小的数组  
  
 结构的成员或位域包含零大小的数组，它不是最后一个成员。  
  
 由于可将零大小的数组作为结构的最后一个成员，因此分配结构时必须指定它的大小。  
  
 如果零大小的数组不是结构的最后一个成员，则编译器无法为其余的字段计算偏移量。  
  
 下面的示例生成 C2229：  
  
```  
// C2229.cpp  
struct S {  
   int a[0];  // C2229  zero-sized array  
   int b[1];  
};  
  
struct S2 {  
   int a;  
   int b[0];  
};  
  
int main() {  
   // allocate 7 elements for b field  
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];  
   s2->b[6] = 100;  
}  
```