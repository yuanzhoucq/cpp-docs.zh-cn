---
title: "编译器警告（等级 1）C4945 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4945"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4945"
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4945
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”: 无法从“assembly2”导入符号: 因为“symbol”已从另一个程序集“assembly1”导入  
  
 从引用的程序集中导入了符号，但该符号已从另一个引用的程序集导入。  或者不引用这些程序集之一，或者更改其中一个程序集中的符号名称。  
  
 下面的示例生成 C4945。  
  
```  
// C4945a.cs  
// compile with: /target:library  
// C# source code to create a dll  
public class ClassA {  
   public int i;  
}  
```  
  
 然后，  
  
```  
// C4945b.cs  
// compile with: /target:library  
// C# source code to create a dll  
public class ClassA {  
   public int i;  
}  
```  
  
 然后，  
  
```  
// C4945c.cpp  
// compile with: /clr /LD /W1  
#using "C4945a.dll"  
#using "C4945b.dll"   // C4945  
```