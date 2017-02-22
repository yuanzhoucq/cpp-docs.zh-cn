---
title: "编译器错误 C3388 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3388"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3388"
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器错误 C3388
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 不允许作为约束，假定 "ref class" 继续进行分析  
  
 对泛型类型指定了约束，但是未正确地指定约束。 有关更多信息，请参见[约束](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 示例  
 下面的示例生成 C3388。  
  
```  
// C3388.cpp // compile with: /clr /c interface class AA {}; generic <class T> where T : interface class   // C3388 ref class C {}; // OK generic <class T> where T : AA ref class D {};  
```