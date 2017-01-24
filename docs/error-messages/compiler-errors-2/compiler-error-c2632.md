---
title: "编译器错误 C2632 | Microsoft Docs"
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
  - "C2632"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2632"
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2632
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type1”后面接“type2”是非法的  
  
 如果两个类型说明符之间缺少代码，则会导致此错误。  
  
 下面的示例生成 C2632：  
  
```  
// C2632.cpp  
int float i;   // C2632  
```  
  
 在 Visual Studio .NET 2003 中所做的编译器一致性工作也可能导致此错误。  `bool` 现在是正确的类型。  在早期版本中，`bool` 为 typedef，可以使用该名称创建标识符。  
  
 下面的示例生成 C2632：  
  
```  
// C2632_2.cpp  
// compile with: /LD  
void f(int bool);   // C2632  
```  
  
 若要解决此错误，以便代码在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中均有效，应重命名该标识符。