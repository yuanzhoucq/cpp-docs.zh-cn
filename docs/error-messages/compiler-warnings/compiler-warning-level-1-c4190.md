---
title: "编译器警告（等级 1）C4190 | Microsoft Docs"
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
  - "C4190"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4190"
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4190
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier1”有指定的 C 链接，但返回了与 C 不兼容的 UDT“identifier2”  
  
 函数或指向函数的指针将 UDT（用户定义的类型，即：类类型、结构类型、枚举类型、联合类型或 [\_\_value](../../misc/value.md) 类型）作为返回类型和 `extern`“C”链接。  这在以下情况下是合法的：  
  
-   所有对该函数的调用均从 C\+\+ 发生。  
  
-   函数的定义使用 C\+\+。  
  
## 示例  
  
```  
// C4190.cpp  
// compile with: /W1 /LD  
struct X  
{  
   int i;  
   X ();  
   virtual ~X ();  
};  
  
extern "C" X func ();   // C4190  
```