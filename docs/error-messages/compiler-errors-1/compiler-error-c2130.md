---
title: "编译器错误 C2130 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2130"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2130"
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2130
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#line 应为包含文件名的字符串，却找到“标记”  
  
 在 [\#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` 后面的可选文件名标记必须是字符串。  
  
 以下示例生成 C2130:  
  
```  
// C2130.cpp int main() { #line 1000 test   // C2130 #line 1000 "test"   // OK }  
```