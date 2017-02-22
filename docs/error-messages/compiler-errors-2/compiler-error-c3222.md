---
title: "编译器错误 C3222 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3222"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3222"
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C3222
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“parameter”: 无法为托管或 WinRT 类型或泛型函数的成员函数声明默认参数  
  
 不允许声明具有默认实参的方法形参。  方法的重载形式是一种用于解决此问题的方式。  也就是说，定义具有相同名称但不带参数的方法，然后在方法体中初始化变量。  
  
 以下示例生成 C3222：  
  
```  
// C3222_2.cpp  
// compile with: /clr  
public ref class G {  
   void f( int n = 0 );   // C3222  
};  
```  
  
 以下示例生成 C3222：  
  
```  
// C3222.cpp  
// compile with: /clr:oldSyntax  
public __gc class G {  
   void f( int n = 0 );   // C3222  
};  
```