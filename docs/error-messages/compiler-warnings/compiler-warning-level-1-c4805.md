---
title: "编译器警告（等级 1）C4805 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4805"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4805"
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4805
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operation”: 在操作中将类型“type”与类型“type”混合不安全  
  
 对于 [bool](../../cpp/bool-cpp.md) 与 [int](../../c-language/integer-types.md) 之间的比较操作，会生成此警告。 下面的示例生成 C4805：  
  
```  
// C4805.cpp // compile with: /W1 int main() { int i = 1; bool b = true; if (i == b) {   // C4805, comparing bool and int variables } }  
```