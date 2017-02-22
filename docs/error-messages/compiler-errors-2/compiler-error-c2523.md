---
title: "编译器错误 C2523 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2523"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2523"
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2523
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class::~identifier”: 析构函数\/终结器标记不匹配  
  
 该析构函数的名称必须是前面带有代字号 \(`~`\) 的类名。  只有构造函数和析构函数是与类同名的成员。  
  
 下面的示例生成 C2523：  
  
```  
// C2523.cpp  
// compile with: /c  
class A {  
   ~B();    // C2523  
   ~A();   // OK  
};  
```