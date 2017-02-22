---
title: "编译器错误 C2831 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2831"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2831"
ms.assetid: c8c04288-0889-4265-a077-17f94cbcdcc9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2831
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator operator”不能有默认参数  
  
 只有三个运算符可具有默认参数：  
  
-   [new](../../cpp/new-operator-cpp.md)  
  
-   赋值 \=  
  
-   左圆括号 \(  
  
 下面的示例生成 C2831：  
  
```  
// C2831.cpp  
// compile with: /c  
#define BINOP <=  
class A {  
public:  
   int i;  
   int operator BINOP(int x = 1) {   // C2831  
   // try the following line instead  
   // int operator BINOP(int x) {  
      return i+x;  
   }  
};  
```