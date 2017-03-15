---
title: "编译器错误 C3202 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3202"
ms.assetid: 23528a0c-5493-4804-9789-cd3c38e49fb9
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器错误 C3202
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“arg name”：模板参数“parameter”的默认参数无效，应为类模板  
  
 你向模板参数传递的默认参数无效。  
  
 下面的示例生成 C3202：  
  
```  
// C3202.cpp template<typename T> class X { }; class Z { }; template<template<typename U> class T1 = Z, typename T2> // C3202 class Y { };  
```