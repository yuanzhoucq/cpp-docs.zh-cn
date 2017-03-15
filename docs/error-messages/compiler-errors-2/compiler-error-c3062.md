---
title: "编译器错误 C3062 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3062"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3062"
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3062
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“enum”: 枚举数需要值，因为基础类型为“type”  
  
 可以为枚举数指定基础类型。  但是，某些类型要求对每个枚举数分配值。  
  
 有关枚举的更多信息，请参见[枚举类](../../windows/enum-class-cpp-component-extensions.md)。  
  
 下面的示例生成 C3062：  
  
```  
// C3062.cpp  
// compile with: /clr  
  
enum class MyEnum : bool { a };   // C3062  
enum class MyEnum2 : bool { a = true};   // OK  
```