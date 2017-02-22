---
title: "编译器警告（等级 4）C4061 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4061"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4061"
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 4）C4061
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

枚举数“identifier”\(在枚举“enumeration”的 switch 中\)没有被 case 标签显式处理  
  
 枚举在 `switch` 语句中无关联的处理程序。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4061：  
  
```  
// C4061.cpp  
// compile with: /W4  
#pragma warning(default : 4061)  
  
enum E { a, b, c };  
void func ( E e )  
{  
   switch(e)  
   {  
      case a:  
      case b:  
      default:  
         break;  
   }   // C4061 c' not handled  
}  
  
int main()  
{  
}  
```