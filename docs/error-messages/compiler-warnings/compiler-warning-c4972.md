---
title: "编译器警告 C4972 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4972"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4972"
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 编译器警告 C4972
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

直接修改取消装箱操作的结果或将其视为左值是不可验证的  
  
 取消引用值类型的句柄（也称为取消装箱），然后为其赋值，是不可验证的。  
  
 有关详细信息，请参阅[装箱](../../windows/boxing-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C4972。  
  
```  
// C4972.cpp // compile with: /clr:safe using namespace System; ref struct R { int ^ p;   // a value type }; int main() { R ^ r = gcnew R; *(r->p) = 10;   // C4972 // OK r->p = 10; Console::WriteLine( r->p ); Console::WriteLine( *(r->p) ); }  
```