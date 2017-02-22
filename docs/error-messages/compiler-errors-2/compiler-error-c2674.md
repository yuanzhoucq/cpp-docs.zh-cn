---
title: "编译器错误 C2674 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2674"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2674"
ms.assetid: 7cbd70d8-d992-44d7-a5cb-dd8cf9c759d2
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2674
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在此上下文中不允许泛型声明  
  
 错误地声明了泛型。  有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C2674。  
  
```  
// C2674.cpp  
// compile with: /clr /c  
void F(generic <class T> ref class R1);   // C2674  
generic <class T> ref class R2 {};   // OK  
```