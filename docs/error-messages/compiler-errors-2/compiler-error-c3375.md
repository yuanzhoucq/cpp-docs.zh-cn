---
title: "编译器错误 C3375 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3375"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3375"
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3375
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”：不明确的委托函数  
  
 委托实例化可能已为静态成员函数，或为实例函数未绑定的委托，因此编译器出现此错误。  
  
 有关详细信息，请参阅[委托](../../windows/delegate-cpp-component-extensions.md)。  
  
## 示例  
 以下示例生成 C3375：  
  
```  
// C3375.cpp // compile with: /clr ref struct R { static void f(R^) {} void f() {} }; delegate void Del(R^); int main() { Del ^ a = gcnew Del(&R::f);   // C3375 }  
```