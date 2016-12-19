---
title: "编译器错误 C2923 | Microsoft Docs"
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
  - "C2923"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2923"
ms.assetid: 6b92933b-13ef-4124-99d9-b89f9fdae030
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2923
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 对于参数“param”，“identifier”不是有效的模板类型参数  
  
 参数列表缺少实例化模板或泛型所需的类型。 检查模板或泛型声明。  
  
 下面的示例生成 C2923：  
  
```  
// C2923.cpp template <class T> struct TC {}; int x; int main() { TC<x>* tc2;   // C2923 TC<int>* tc2;   // OK }  
```  
  
 使用泛型时，也可能会发生 C2923：  
  
```  
// C2923b.cpp // compile with: /clr /c generic <class T> ref struct GC {}; int x; int main() { GC<x>^ gc2;   // C2923 GC<int>^ gc2;   // OK }  
```