---
title: "编译器警告（等级 1）C4526 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4526"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4526"
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4526
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 静态成员函数无法重写虚函数“virtual function”，重写被忽略，将隐藏虚函数  
  
 静态成员函数满足重写虚函数的条件，使成员函数既是虚函数也是静态函数。  
  
 以下代码生成 C4526：  
  
```  
// C4526.cpp  
// compile with: /W1 /c  
// C4526 expected  
struct myStruct1 {  
   virtual void __stdcall func( int ) = 0;  
};  
  
struct myStruct2: public myStruct1 {  
   static void __stdcall func( int );  
};  
```  
  
 下列是可能的修复方法：  
  
-   如果函数用于重写基类虚函数，则移除静态说明符。  
  
-   如果函数用作静态成员函数，则重命名该函数，以便不与基类虚函数冲突。