---
title: "编译器错误 C2909 | Microsoft Docs"
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
  - "C2909"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2909"
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2909
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 函数模板的显式实例化需要返回类型  
  
 函数模板的显式实例化需要显式指定返回类型。 隐式返回类型指定不起作用。  
  
 下面的示例生成 C2909：  
  
```  
// C2909.cpp // compile with: /c template<class T> int f(T); template f<int>(int);         // C2909 template int f<int>(int);   // OK  
```