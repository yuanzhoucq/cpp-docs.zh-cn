---
title: "编译器警告（等级 4）C4516 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4516"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4516"
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 4）C4516
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class::symbol”: 否决访问声明；成员 using 声明提供更好的选择  
  
 ANSI C\+\+ 委员会已经宣布访问声明（不使用 [using](../../cpp/using-declaration.md) 关键字而更改派生类中的成员访问）已过期。  C\+\+ 的未来版本可能不支持访问声明。  
  
 下面的示例生成 C4516：  
  
```  
// C4516.cpp  
// compile with: /W4  
class A  
{  
public:  
   void x(char);  
};  
  
class B : protected A  
{  
public:  
   A::x;  // C4516 on access-declaration  
   // use the following line instead  
   // using A::x; // using-declaration, ok  
};  
  
int main()  
{  
}  
```