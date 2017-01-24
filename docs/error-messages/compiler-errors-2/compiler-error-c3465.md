---
title: "编译器错误 C3465 | Microsoft Docs"
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
  - "C3465"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3465"
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3465
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要使用类型“type”，必须引用程序集“assembly”  
  
 在重新编译客户端之前，类型转发都将适用于客户端应用程序。 重新编译时，包含客户端应用程序中所用类型定义的每个程序集都将需要一个引用。  
  
 有关更多信息，请参见[类型转发 \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md)。  
  
## 示例  
 以下示例生成包含类型新位置的程序集。  
  
```  
// C3465.cpp // compile with: /clr /LD public ref class R { public: ref class N {}; };  
```  
  
## 示例  
 以下示例生成用来包含类型定义的程序集，但现在却包含此类型的转发语法。  
  
```  
// C3465_b.cpp // compile with: /clr /LD #using "C3465.dll" [ assembly:TypeForwardedTo(R::typeid) ];  
```  
  
## 示例  
 下面的示例生成 C3465。  
  
```  
// C3465_c.cpp // compile with: /clr // C3465 expected #using "C3465_b.dll" // Uncomment the following line to resolve. // #using "C3465.dll" int main() { R^ r = gcnew R(); }  
```