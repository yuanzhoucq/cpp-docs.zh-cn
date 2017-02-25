---
title: "编译器错误 C3236 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3236"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3236"
ms.assetid: 4ef1871f-a348-44ae-922b-1e2081de20d0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3236
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允许显式实例化泛型  
  
 编译器不允许泛型类的显式实例化。  
  
 下面的示例生成 C3236：  
  
```  
// C3236.cpp // compile with: /clr generic<class T> public ref class X {}; generic ref class X<int>;   // C3236  
```  
  
 以下示例演示了可能的解决方法：  
  
```  
// C3236b.cpp // compile with: /clr /c generic<class T> public ref class X {};  
```