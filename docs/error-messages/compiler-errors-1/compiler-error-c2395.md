---
title: "Compiler Error C2395 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2395"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2395"
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Compiler Error C2395
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“your\_type::operator'op'”：CLR 或 WinRT 运算符无效。至少一个参数必须是以下类型：“T”、“T%”、“T&”、“T^”、“T^%”、“T^&”，其中 T \=“your\_type”  
  
 Windows 运行时或托管的类型中的一个运算符没有至少一个类型与运算符返回值的类型相同的参数。  
  
 下面的示例生成 C2395，并演示如何修复此错误：  
  
```  
// C2395.cpp  
// compile with: /clr /c  
value struct V {  
   static V operator *(int i, char c);   // C2395  
  
   // OK  
   static V operator *(V v, char c);  
   // or  
   static V operator *(int i, V& rv);  
};  
```