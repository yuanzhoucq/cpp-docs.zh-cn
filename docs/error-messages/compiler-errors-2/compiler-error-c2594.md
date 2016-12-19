---
title: "编译器错误 C2594 | Microsoft Docs"
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
  - "C2594"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2594"
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2594
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 从“type1”到“type2”的转换不明确  
  
 从 *type1* 到 *type2* 的转换是最不明确的。  这里建议两种从 *type1*转换到 *type2*的可能的解决方案。  第一种选择是定义从 *type1* 到 *type2* 的直接转换，第二种选择是指定从 *type1* 到 *type2* 的转换序列。  
  
 下面的示例生成 C2594。  建议用来解决该错误的方法是指定一个转换序列：  
  
```  
// C2594.cpp  
// compile with: /c  
struct A{};  
struct I1 : A {};  
struct I2 : A {};  
struct D : I1, I2 {};  
  
A *f (D *p) {  
   return (A*) (p);    // C2594  
  
// try the following line instead  
// return static_cast<A *>(static_cast<I1 *>(p));  
}  
```