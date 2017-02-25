---
title: "编译器错误 C3470 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3470"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3470"
ms.assetid: 170c7a9d-214d-41b1-8f15-d4a4fc38aaa5
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 编译器错误 C3470
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”：类不能同时具有索引器（默认索引属性）和运算符 \[\]  
  
 类型不能定义默认索引器和运算符 \[\]。  
  
## 示例  
 以下示例生成 C3470  
  
```  
// C3470.cpp // compile with: /clr using namespace System; ref class R { public: property int default[int] { int get(int i) { return i+1; } } int operator[](String^ s) { return Convert::ToInt32(s); }   // C3470 }; int main() { R ^ r = gcnew R; // return r[9] + r["32"] - 42; }  
```