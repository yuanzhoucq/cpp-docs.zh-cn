---
title: "编译器错误 C2380 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2380"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2380"
ms.assetid: 717b1e6e-ddfe-4bac-a5f3-7f9a4dcb1572
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2380
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”前的类型\(构造函数有返回类型或是当前类名称的重定义非法？\)  
  
 构造函数返回值或重新定义类名。  
  
 下面的示例生成 C2326：  
  
```  
// C2380.cpp  
// compile with: /c  
class C {  
public:  
   int C();   // C2380, specifies an int return  
   int C;   // C2380, redefinition of i  
   C();   // OK  
};  
```