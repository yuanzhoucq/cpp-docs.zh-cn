---
title: "编译器错误 C2815 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2815"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2815"
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2815
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator delete”: 第一个形参必须为“void \*”，但使用的是“param”  
  
 任何用户定义的 [delete 运算符](../Topic/operator%20delete%20\(%3Cnew%3E\).md)函数都必须采用 `void *` 类型的第一个形参。  
  
 下面的示例生成 C2815：  
  
```  
// C2815.cpp  
// compile with: /c  
class CMyClass {  
public:  
   void mf1(int *a);  
   void operator delete(CMyClass *);   // C2815  
   void operator delete(void *);   
};  
```