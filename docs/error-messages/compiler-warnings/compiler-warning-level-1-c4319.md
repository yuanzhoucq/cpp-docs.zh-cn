---
title: "编译器警告（等级 1）C4319 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4319"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4319"
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4319
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”：将“type”零扩展到更大的“type”  
  
 ~（按位求补）运算符的结果无符号，然后在转换为更大的类型时进行零扩展。  
  
 在下面的示例中，~\(a \- 1\) 按 32 位无符号 long 表达式进行计算，然后通过零扩展转换为 64 位。  这会导致意外的运算结果。  
  
```  
// C4319.cpp  
// compile with: cl /W4 C4319.cpp  
int main() {  
   unsigned long a = 0;  
   unsigned long long q = 42;  
   q = q & ~(a - 1);    // C4319 expected  
}  
```