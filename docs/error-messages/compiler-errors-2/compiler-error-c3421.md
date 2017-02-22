---
title: "编译器错误 C3421 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3421"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3421"
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器错误 C3421
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 由于该类的终结器不可访问或不存在，因此无法调用它  
  
 终结器属于隐式专用，因此无法从其封闭类型外调用它。  
  
 有关详细信息，请参阅[Visual C\+\+ 中的析构函数和终结器](../../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
## 示例  
 下面的示例生成 C3421。  
  
```  
// C3421.cpp // compile with: /clr ref class A {}; ref class B { !B() {} public: ~B() {} }; int main() { A a; a.!A();   // C3421 B b; b.!B();   // C3421 }  
```