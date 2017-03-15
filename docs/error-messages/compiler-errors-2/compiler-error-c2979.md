---
title: "编译器错误 C2979 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2979"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2979"
ms.assetid: 98bd9043-ec44-451e-a482-3a8e35fc7464
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器错误 C2979
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

泛型中不支持显式专用化  
  
 未正确声明泛型类。  有关更多信息，请参见[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C2979。  
  
```  
// C2979.cpp // compile with: /clr /c generic <> ref class Utils {};   // C2979 error generic <class T> ref class Utils2 {};   // OK  
```