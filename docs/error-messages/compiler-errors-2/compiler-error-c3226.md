---
title: "编译器错误 C3226 | Microsoft Docs"
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
  - "C3226"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3226"
ms.assetid: 636106ca-6f4e-4303-a6a0-8803221ec67d
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3226
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

泛型声明内不允许出现模板声明  
  
 在泛型类中使用泛型声明。  
  
 以下示例生成 C3226：  
  
```  
// C3226.cpp // compile with: /clr generic <class T> ref class C { template <class T1>   // C3226 ref struct S1 {}; };  
```  
  
 以下示例演示了可能的解决方法：  
  
```  
// C3226b.cpp // compile with: /clr /c generic <class T> ref class C { generic <class T1> ref struct S1 {}; };  
```