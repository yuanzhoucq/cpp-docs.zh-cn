---
title: "WriteOnlyArray::end 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::WriteOnlyArray::end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WriteOnlyArray::end 方法"
ms.assetid: 045045fe-f210-400b-b688-7abb95fc702a
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WriteOnlyArray::end 方法
返回一个指向数组中最后一个元素的下一位置的指针。  
  
## 语法  
  
```cpp  
T* end() const;  
```  
  
## 返回值  
 指向数组中最后一个元素的下一位置的指针迭代器。  
  
## 备注  
 此迭代器可与 STL 算法（如 `std::sort`）一起使用以对数组元素执行操作。  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [Platform::WriteOnlyArray 类](../cppcx/platform-writeonlyarray-class.md)   
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)