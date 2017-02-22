---
title: "编译器错误 C2683 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2683"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2683"
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2683
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“cast”:“type”不是多态类型  
  
 无法使用 [dynamic\_cast](../../cpp/dynamic-cast-operator.md) 从非多态类（没有虚函数的类）进行转换。  
  
 可以使用 [static\_cast](../../cpp/static-cast-operator.md) 执行非多态类型的转换。  但是，`static_cast` 不执行运行时检查。  
  
 下面的示例生成 C2683：  
  
```  
// C2683.cpp  
// compile with: /c  
class B { };  
class D : public B { };  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  // C2683  
   D* pd1 = static_cast<D*>(pb);   // OK  
}  
```