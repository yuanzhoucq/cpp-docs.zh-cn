---
title: "nothrow_t 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "nothrow_t"
  - "std.nothrow_t"
  - "std::nothrow_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nothrow_t 类"
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# nothrow_t 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

而不是引发异常，则结构，用于在对新运算符的函数参数指示函数应返回空指针分配报告失败。  
  
## 语法  
  
```  
struct std::nothrow_t {};  
```  
  
## 备注  
 帮助构造结构编译器选择函数的正确版本。  [nothrow](../Topic/nothrow%20\(%3Cnew%3E\).md)`std::nothrow_t`对象类型是的同义词处理。  
  
## 示例  
 参见 [new 运算符](../Topic/operator%20new%20\(%3Cnew%3E\).md)[operator new&#91;&#93;](../Topic/operator%20new\(%3Cnew%3E\).md) 和说明 `std::nothrow_t` 如何作为示例用作函数参数。  
  
## 要求  
 新 \<的**页眉：** \>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)