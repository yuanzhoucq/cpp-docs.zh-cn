---
title: "编译器错误 C3413 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3413"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3413"
ms.assetid: de6c9b05-c373-4bd8-8cb0-12c2cd2e5674
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3413
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“name”：显式实例化无效  
  
 编译器检测到格式不正确的显式实例化。  
  
 下面的示例生成 C3413：  
  
```  
// C3413.cpp template class MyClass {};   // C3413  
```  
  
 可能的解决方法：  
  
```  
// C3413b.cpp // compile with: /c template <class T> class MyClass {}; template <> class MyClass<int> {};  
```