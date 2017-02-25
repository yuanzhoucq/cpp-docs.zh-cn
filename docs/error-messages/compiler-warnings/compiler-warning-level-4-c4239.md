---
title: "编译器警告（等级 4）C4239 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4239"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4239"
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器警告（等级 4）C4239
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展:“token”: 从“type”转换到“type”  
  
 C\+\+ 标准不允许此类型转换，但此转换在这里可以用作扩展。  此警告后面总是至少有一行解释描述所违反的语言规则。  
  
## 示例  
 下面的示例生成 C4239。  
  
```  
// C4239.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
void func(void) {  
   C & rC = C();   // C4239  
   const C & rC2 = C();   // OK  
   rC2;  
}  
```  
  
## 示例  
 绝对不允许从整型转换为枚举类型。  
  
 下面的示例生成 C4239。  
  
```  
// C4239b.cpp  
// compile with: /W4 /c  
enum E { value };   
struct S {   
   E e : 2;   
} s = { 5 };   // C4239   
// try the following line instead  
// } s = { (E)5 };  
```