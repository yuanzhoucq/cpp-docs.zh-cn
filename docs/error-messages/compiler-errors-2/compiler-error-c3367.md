---
title: "编译器错误 C3367 | Microsoft Docs"
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
  - "C3367"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3367"
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3367
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“static\_member\_function”: 不能使用静态函数创建未绑定的委托  
  
 当你调用未绑定的委托时，必须传递对象的实例。 由于通过类名称调用静态成员函数，因此仅能通过实例成员函数实例化未绑定的委托。  
  
 有关详细信息，请参阅[未绑定的委托](../../misc/unbound-delegates.md)。  
  
## 示例  
 以下示例生成 C3367。  
  
```  
// C3367.cpp // compile with: /clr ref struct R { void b() {} static void f() {} }; delegate void Del(R^); int main() { Del ^ a = gcnew Del(&R::b);   // OK Del ^ b = gcnew Del(&R::f);   // C3367 }  
```