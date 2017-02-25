---
title: "编译器错误 C3264 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3264"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3264"
ms.assetid: 94ece687-2364-4f7a-8ebb-7afd3ae9d63d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3264
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: Class 构造函数不能有返回类型  
  
 Class 构造函数不能有返回类型。  
  
 下面的示例生成 C3264：  
  
```  
// C3264_2.cpp // compile with: /clr ref class X { public: static int X()   { // C3264 } /* use the code below to resolve the error static X() { } */ }; int main() { }  
```  
  
 下面的示例生成 C3264：  
  
```  
// C3264.cpp // compile with: /clr:oldSyntax #using <mscorlib.dll> __gc class X { public: static int X()   { // C3264 } /* use the code below to resolve the error static X() { } */ }; int main() { }  
```