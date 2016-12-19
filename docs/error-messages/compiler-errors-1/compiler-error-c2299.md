---
title: "编译器错误 C2299 | Microsoft Docs"
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
  - "C2299"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2299"
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2299
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 行为更改: 显式专用化不能是复制构造函数或复制赋值运算符  
  
 为 Visual C\+\+ 2005 执行的编译器一致性工作也可能导致此错误：Visual C\+\+ 的早期版本允许复制构造函数或复制赋值运算符的显式专用化。  
  
 若要解决 C2299，请不要使复制构造函数或赋值运算符成为模板函数，而使其成为采用类类型的非模板函数。  通过显式指定模板参数来调用复制构造函数或赋值运算符的任何代码都需要移除模板参数。  
  
 下面的示例生成 C2299：  
  
```  
// C2299.cpp  
// compile with: /c  
class C {  
   template <class T>  
   C (T t);  
  
   template <> C (const C&);   // C2299  
   C (const C&);   // OK  
};  
```