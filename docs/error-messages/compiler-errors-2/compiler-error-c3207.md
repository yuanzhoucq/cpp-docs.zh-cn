---
title: "编译器错误 C3207 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3207"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3207"
ms.assetid: 4a28b976-142a-4cff-aa2f-480b892c50ca
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3207
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”：“arg”的模板参数无效，应当是类模板  
  
 将模板函数定义为采用模板模板参数。 但是，传递的是模板类型参数。  
  
 以下示例生成 C3207：  
  
```  
// C3207.cpp template <template <class T> class TT> void f(){} template <class T> struct S { }; void f1() { f<S<int> >();   // C3207 // try the following line instead // f<S>(); }  
```