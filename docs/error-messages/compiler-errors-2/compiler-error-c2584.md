---
title: "编译器错误 C2584 | Microsoft Docs"
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
  - "C2584"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2584"
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2584
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“Class”: 直接基“Base2”不可访问；已是“Base1”的基  
  
 `Class` 已经直接从 `Base1` 派生。  `Base2` 也从 `Base1` 派生。  `Class` 无法从 `Base2` 派生，因为这将意味着又从 `Base1` 继承（间接），由于 `Base1` 已是直接基类，所以这是非法的。  
  
## 示例  
 下面的示例生成 C2584。  
  
```  
// C2584.cpp  
// compile with: /c  
struct A1 {  
   virtual int MyFunction();  
};  
  
struct A2 {  
    virtual int MyFunction();  
};  
  
struct B1: public virtual A1, virtual A2 {  
    virtual int MyFunction();  
};  
  
struct B2: public virtual A2, virtual A1 {  
    virtual int MyFunction();  
};  
  
struct C: virtual B1, B2 {  
    virtual int MyFunction();  
};  
  
struct Z : virtual B2, virtual C {   // C2584  
// try the following line insted  
// struct Z : virtual C {  
    virtual int MyFunction();  
};  
```