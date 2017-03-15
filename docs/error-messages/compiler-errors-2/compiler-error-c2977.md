---
title: "编译器错误 C2977 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2977"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2977"
ms.assetid: 3c4218e0-5d03-4a2b-b757-c507c35f3542
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2977
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：类型参数太多  
  
 泛型或模板的实参太多。 检查泛型或模板声明，以查找正确的参数数目。  
  
 下面的示例生成 C2977：  
  
```  
// C2977.cpp // compile with: /c template<class T, int i> class MyClass {}; template MyClass< int , 1, 1 >;   // C2977 template MyClass< int , 1 >;   // OK  
```  
  
 使用泛型时，也可能发生 C2977：  
  
```  
// C2977b.cpp // compile with: /clr // C2977 expected generic <class T, class U> void f(){} generic <class T> ref struct GC1 {}; int main() { // Delete the following 2 lines to resolve. GC1<int, char> ^ pgc1; f<int,int,int>(); // OK GC1<int> ^ pgc1; f<int, int>(); }  
```