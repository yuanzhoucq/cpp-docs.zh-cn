---
title: "编译器错误 C2917 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2917"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2917"
ms.assetid: ec9da9ee-0f37-47b3-87dd-19ef5a14dc4c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2917
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“name”：无效的模板参数  
  
 模板参数列表包含不是一个模板参数的标识符。  
  
## 示例  
 以下示例生成 C2917。  
  
```  
// C2917.cpp // compile with: /c template<class T> class Vector { void sort(); }; template<class T*> void Vector<T>::sort() {}   // C2917 // try the following line instead // template<class T> void Vector<T>::sort() {}  
```