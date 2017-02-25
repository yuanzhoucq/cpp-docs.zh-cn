---
title: "编译器错误 C2192 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2192"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2192"
ms.assetid: a147197e-e72d-4620-939b-f9e08d7c7c12
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2192
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

参数“number”声明不同  
  
 用另一个参数列表再次声明了 C 函数。  C 不支持重载函数。  
  
 下面的示例生成 C2192：  
  
```  
// C2192.c  
// compile with: /Za /c  
void func( float, int );  
void func( int, float );   // C2192, different parameter list  
void func2( int, float );   // OK  
```