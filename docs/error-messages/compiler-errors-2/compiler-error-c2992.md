---
title: "编译器错误 C2992 | Microsoft Docs"
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
  - "C2992"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2992"
ms.assetid: 01b16447-43fe-4e91-9a5a-af884a166a31
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2992
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“类”: 参数列表无效或缺失  
  
 此类前加 `template` 或 **generic** 关键字，存在缺失或无效的参数。  
  
## 示例  
 以下示例生成 C2992:  
  
```  
// C2992.cpp // compile with: /c template <class T> struct TC1 { template <class U> struct TC2; }; template <class T>   struct TC1<T>::TC2 {};   // C2992 // OK template <class T> template <class U> struct TC1<T>::TC2 {}; // C2992 can also occur when using generics: // C2992c.cpp // compile with: /clr /c generic <class T> ref struct GC1 { generic <class U> ref struct GC2; }; generic <class T> ref struct GC1<T>::GC2 {};   // C2992 // OK generic <class T> generic <class U> ref struct GC1<T>::GC2 {};  
```