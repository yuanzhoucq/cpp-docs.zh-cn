---
title: "编译器错误 C3163 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3163"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3163"
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3163
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“construct”: 特性与以前的声明不一致  
  
 应用于定义的特性与应用于声明的特性发生冲突。  
  
 解决 C3163 的一种方法是消除前向声明上的特性。  前向声明上的任何特性都应小于定义上的特性，或至多等于这些特性。  
  
 C3163 错误的一个可能原因涉及 Microsoft 源代码注释语言 \(SAL\)。  除非使用 **\/analyze** 标志编译项目，否则 SAL 宏不会展开。  如果尝试使用 \/analyze 选项重新编译，则未使用 \/analyze 而进行明确编译的程序可能会引发 C3163。  有关 SAL 的更多信息，请参见 [SAL 批注](../../c-runtime-library/sal-annotations.md)。  
  
## 示例  
 下面的示例生成 C3163。  
  
```  
// C3163.cpp  
// compile with: /clr /c  
using namespace System;  
  
[CLSCompliant(true)] void f();  
[CLSCompliant(false)] void f() {}   // C3163  
// try the following line instead  
// [CLSCompliant(true)] void f() {}  
```  
  
## 请参阅  
 [SAL 批注](../../c-runtime-library/sal-annotations.md)