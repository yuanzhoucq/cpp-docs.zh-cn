---
title: "编译器警告（等级 4）C4366 | Microsoft Docs"
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
  - "C4366"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4366"
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4366
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

二元“operator”运算符的结果可能未对齐  
  
 如果结构成员由于封装而未能对齐，当将该成员的地址分配给一个对齐指针时，编译器将发出警告。  默认情况下，所有指针都是对齐的。  
  
 要消除 C4366，要么更改结构的对齐方式，要么用 [\_\_unaligned](../../cpp/unaligned.md) 关键字声明指针。  
  
 有关更多信息，请参见 \_\_unaligned 和 [pack](../../preprocessor/pack.md)。  
  
## 示例  
 下面的示例生成 C4366。  
  
```  
// C4366.cpp  
// compile with: /W4 /c  
// processor: IPF x64  
#pragma pack(1)  
struct X {  
   short s1;  
   int s2;  
};  
  
int main() {  
   X x;  
   short * ps1 = &x.s1;   // OK  
   int * ps2 = &x.s2;   // C4366  
}  
```