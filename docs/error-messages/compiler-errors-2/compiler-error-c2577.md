---
title: "编译器错误 C2577 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2577"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2577"
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2577
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”: 析构函数\/终结器不能具有返回类型  
  
 析构函数或终结器不能返回 `void` 或任何其他类型的值。  请从析构函数定义移除 `return` 语句。  
  
## 示例  
 下面的示例生成 C2577。  
  
```  
// C2577.cpp  
// compile with: /c  
class A {  
public:  
   A() {}  
   ~A(){  
      return 0;   // C2577  
   }  
};  
```