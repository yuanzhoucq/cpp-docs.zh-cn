---
title: "编译器警告（等级 1）C4548 | Microsoft Docs"
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
  - "C4548"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4548"
ms.assetid: 2cee817e-e463-4d90-bbd2-de120d48c101
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4548
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

逗号前的表达式不起任何作用；应输入带副作用的表达式  
  
 编译器检测到一个格式错误的逗号表达式。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4548：  
  
```  
// C4548.cpp  
// compile with: /W1  
#pragma warning (default : 4548)  
int main()  
{  
   int i = 0, k = 0;  
  
   if ( i, k )   // C4548  
   // try the following line instead  
   // if ( i = 0, k )  
      i++;  
}  
```