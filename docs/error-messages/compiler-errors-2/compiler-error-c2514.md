---
title: "编译器错误 C2514 | Microsoft Docs"
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
  - "C2514"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2514"
ms.assetid: 4b7085e5-6714-4261-80b7-bc72e64ab3e8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2514
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 类没有构造函数  
  
 该类、结构或联合没有这样的构造函数：该构造函数具有与要用来实例化该类、结构或联合的参数匹配的参数列表。  
  
 必须完全声明类，才能将它实例化。  
  
 下面的示例生成 C2514：  
  
```  
// C2514.cpp  
// compile with: /c  
class f;  
  
class g {  
public:  
    g (int x);  
};  
  
class fmaker {  
   f *func1() {  
      return new f(2);   // C2514  
   }  
  
   g *func2() {  
      return new g(2);   // OK  
   }  
};   
```