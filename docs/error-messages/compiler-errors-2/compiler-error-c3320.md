---
title: "编译器错误 C3320 | Microsoft Docs"
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
  - "C3320"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3320"
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3320
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”：类型不能和模块的“name”属性同名  
  
 导出的用户定义类型 \(UDT\)（可以是结构、类、枚举、联合或 [\_\_value](../../misc/value.md)）不能与传递到 [module](../../windows/module-cpp.md) 特性的名称属性的参数具有相同名称。  
  
 以下示例生成 C3320：  
  
```  
// C3320.cpp #include "unknwn.h" [module(name="xx")]; [export] struct xx {   // C3320 // Try the following line instead // [export] struct yy { int i; };  
```