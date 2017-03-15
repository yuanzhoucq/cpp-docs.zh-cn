---
title: "编译器错误 C2939 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2939"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2939"
ms.assetid: 455b050b-f2dc-4b5b-bd6a-e1f81d3d1644
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2939
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：type\-class\-id 重新定义为局部数据变量  
  
 不能将泛型或模板类用作局部数据变量。  
  
 如果大括号匹配不正确，则可能导致此错误。  
  
 下面的示例生成 C2939：  
  
```  
// C2939.cpp template<class T> struct TC { }; int main() { int TC<int>;   // C2939 int TC;   // OK }  
```  
  
 使用 generic 时，也可能发生 C2939：  
  
```  
// C2939b.cpp // compile with: /clr generic<class T> ref struct GC { }; int main() { int GC<int>;   // C2939 int GC;   // OK }  
```