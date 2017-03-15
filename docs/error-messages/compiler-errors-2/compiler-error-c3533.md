---
title: "编译器错误 C3533 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3533"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3533"
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3533
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 参数不能是包含“auto”的类型  
  
 如果默认 [\/Zc:auto](../../build/reference/zc-auto-deduce-variable-type.md) 编译器选项有效，则不能使用 `auto` 关键字声明方法或模板参数。  
  
### 更正此错误  
  
1.  从参数声明中移除 `auto` 关键字。  
  
## 示例  
 下面的示例会产生 C3535，因为它使用 `auto` 关键字声明函数参数，并使用 **\/Zc:auto** 进行编译。  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j){} // C3533  
```  
  
## 示例  
 下面的示例会产生 C3535，因为它使用 `auto` 关键字声明模板参数，并使用 **\/Zc:auto** 进行编译。  
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C{}; // C3533  
```  
  
## 请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)   
 [\/Zc:auto（推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)