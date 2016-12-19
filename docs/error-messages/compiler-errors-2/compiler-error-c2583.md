---
title: "编译器错误 C2583 | Microsoft Docs"
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
  - "C2583"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2583"
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2583
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”:“const\/volatile”“this”指针对于构造函数\/析构函数是非法的  
  
 构造函数或析构函数被声明为 `const` 或 `volatile`。  这是不允许的。  
  
 下面的示例生成 C2583：  
  
```  
// C2583.cpp  
// compile with: /c  
class A {  
public:  
   int i;  
   A() const;   // C2583  
  
   // try the following line instead  
   // A();  
};  
```