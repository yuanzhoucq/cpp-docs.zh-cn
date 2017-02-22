---
title: "编译器错误 C2316 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2316"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2316"
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C2316
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“exception”: 无法作为析构函数捕获，或者复制构造函数不可访问，或同时出现这两种情况  
  
 通过值或引用捕获了异常，但复制构造函数和\/或赋值运算符无法访问。  
  
 以前版本的编译器可接受此代码，但现在会导致错误。  
  
## 示例  
 下面的示例生成 C2316：  
  
```  
// C2316.cpp // compile with: /EHsc #include <stdio.h> extern "C" int printf_s(const char*, ...); struct B { public: B() {} // Delete the following line to resolve. private: // copy constructor B(const B&) { } }; void f(const B&) { } int main() { try { B aB; f(aB); } catch (B b) {   // C2316 printf_s("Caught an exception!\n"); } }  
```