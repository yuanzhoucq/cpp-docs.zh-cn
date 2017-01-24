---
title: "编译器错误 C2995 | Microsoft Docs"
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
  - "C2995"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2995"
ms.assetid: a57cdfe0-b40b-4a67-a95c-1a49ace4842b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2995
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”：函数模板已经定义  
  
 确保模板类的每个成员函数只有一个定义。  
  
 以下示例生成 C2995：  
  
```  
// C2995.cpp // compile with: /c template <class T> void Test(T x){} template <class T> void Test(T x){}   // C2995 template <class T> void Test2(T x){}   // OK  
```