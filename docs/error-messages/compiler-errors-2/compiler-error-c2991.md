---
title: "编译器错误 C2991 | Microsoft Docs"
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
  - "C2991"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2991"
ms.assetid: a87e4404-26e8-4927-b3ee-5d02b3b8bee1
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2991
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重定义类型形参“parameter”  
  
 `parameter` 的两个泛型或模板定义之间存在类型冲突。 定义多个泛型参数或模板参数时，必须使用等效类型。  
  
 下面的示例生成 C2991：  
  
```  
// C2991.cpp // compile with: /c template<class T, class T> struct TC {};   // C2991 // try the following line instead // template<class T, class T2> struct TC {};  
```  
  
 使用泛型时，也可能发生 C2991：  
  
```  
// C2991b.cpp // compile with: /clr /c generic<class T,class T> ref struct GC {};   // C2991 // try the following line instead // generic<class T,class T2> ref struct GC {};  
```