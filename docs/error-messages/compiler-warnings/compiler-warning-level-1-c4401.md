---
title: "编译器警告（等级 1）C4401 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4401"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4401"
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4401
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“bitfield”: 成员是位域  
  
 内联程序集代码尝试访问位域成员。  内联程序集无法访问位域成员，因此使用位域成员前的最后一个封装边界。  
  
 若要避免出现此警告，在内联程序集代码中进行引用之前请将位域转换为适当的类型。  下面的示例生成 C4401：  
  
```  
// C4401.cpp  
// compile with: /W1  
// processor: x86  
typedef struct bitfield {  
   signed bit : 1;  
} mybitfield;  
  
int main() {  
   mybitfield bf;  
   bf.bit = 0;  
   __asm {  
      mov bf.bit,0;   // C4401  
   }  
  
   /* use the following __asm block to resolve the warning  
   int i = (int)bf.bit;  
   __asm {  
      mov i,0;  
   }  
   */  
}  
```