---
title: "编译器警告（等级 4）C4706 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4706"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4706"
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 4）C4706
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

条件表达式内的赋值  
  
 条件表达式中的测试值是赋值结果。  
  
 赋值有一个可以在其他表达式、包括测试表达式中合法使用的值（该值在赋值的左侧）。  
  
 下面的示例生成 C4706：  
  
```  
// C4706a.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a  = b ) // C4706  
   {  
   }  
}  
```  
  
 即使在测试条件两边加了两个括号，此警告也会出现：  
  
```  
// C4706b.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a  =  b ) ) // C4706  
   {  
   }  
}  
```  
  
 如果您想测试关系但不进行赋值，请使用 `==` 运算符。  例如，下行将测试 a 和 b 是否相等：  
  
```  
// C4706c.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a == b )  
   {  
   }  
}  
```  
  
 如果您打算将测试值作为赋值结果，需进行测试以确保该赋值是非零且非空的。  例如，下列代码将生成此警告：  
  
```  
// C4706d.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a = b ) != 0 )  
   {  
   }  
}  
```