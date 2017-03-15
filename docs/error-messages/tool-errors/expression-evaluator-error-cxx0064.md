---
title: "表达式计算器错误 CXX0064 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0064"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0064"
  - "CXX0064"
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 表达式计算器错误 CXX0064
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不能在绑定的虚拟成员函数上设置断点  
  
 通过指向对象的指针在虚拟成员函数上设置了断点，例如：  
  
```  
pClass->vfunc( int );  
```  
  
 可以通过输入类在虚拟函数上设置断点，例如：  
  
```  
Class::vfunc( int );  
```  
  
 该错误与 CAN0064 相同。