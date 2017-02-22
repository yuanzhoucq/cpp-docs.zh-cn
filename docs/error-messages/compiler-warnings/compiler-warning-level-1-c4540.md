---
title: "编译器警告（等级 1）C4540 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4540"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4540"
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4540
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

dynamic\_cast 用于转换为不可访问或不明确的基；运行时测试将失败\(“type1”到“type2”\)  
  
 您使用了 `dynamic_cast` 从一种类型转换为另一种类型。  编译器确定此转换会总是失败（返回 **NULL**），因为基类不可访问（例如为 `private`）或不明确（例如在类层次结构中出现多次）。  
  
 下列显示的是此警告的示例。  类 **B** 是从类 **A** 派生的。  程序使用 `dynamic_cast` 从类 **B**（派生类）强制转换为类 **A**，这将始终失败，因为类 **B** 是 `private`，从而是不可访问的。  将对 **A** 的访问更改为 **public** 可解决此警告。  
  
```  
// C4540.cpp  
// compile with: /W1  
  
struct A {   
   virtual void g() {}  
};  
  
struct B : private A {  
   virtual void g() {}  
};  
  
int main() {  
   B b;  
   A * ap = dynamic_cast<A*>(&b);   // C4540  
}  
```