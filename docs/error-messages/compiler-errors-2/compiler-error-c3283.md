---
title: "编译器错误 C3283 | Microsoft Docs"
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
  - "C3283"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3283"
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3283
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“类型”: 接口不能包含实例构造函数  
  
 CLR [接口](../../windows/interface-class-cpp-component-extensions.md)不能包含实例构造函数。  允许使用静态构造函数。  
  
 以下示例生成 C3283:  
  
```  
// C3283.cpp // compile with: /clr interface class I { I();   // C3283 };  
```  
  
 可能的解决方法：  
  
```  
// C3283b.cpp // compile with: /clr /c interface class I { static I(){} };  
```