---
title: "编译器错误 C2533 | Microsoft Docs"
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
  - "C2533"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2533"
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2533
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 构造函数不能有返回类型  
  
 构造函数不能具有返回类型（甚至不能是 `void` 返回类型）。  
  
 此错误的常见来源是类定义结尾与第一个构造函数实现之间缺少分号。  编译器会将类视为构造函数返回类型的定义，会生成 C2533。  
  
 下面的示例生成 C2533，并演示如何修复此错误：  
  
```  
// C2533.cpp  
// compile with: /c  
class X {  
public:  
   X();     
};  
  
int X::X() {}   // C2533 - constructor return type not allowed  
X::X() {}   // OK - fix by using no return type  
```