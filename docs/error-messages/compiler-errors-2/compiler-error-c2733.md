---
title: "编译器错误 C2733 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2733"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2733"
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2733
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允许重载函数“function”的第二个 C 链接  
  
 用 C 链接声明了多个重载函数。  使用 C 链接时，只有一种形式的指定函数可以是外部的。  因为重载函数具有相同的未修饰名，所以它们无法用于 C 程序。  
  
 下面的示例生成 C2733：  
  
```  
// C2733.cpp  
extern "C" {  
   void F1(int);  
}  
  
extern "C" {  
   void F1();   // C2733  
   // try the following line instead  
   // void F2();  
}  
```