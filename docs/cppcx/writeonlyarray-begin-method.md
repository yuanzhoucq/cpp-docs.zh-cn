---
title: "WriteOnlyArray::begin 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::WriteOnlyArray::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WriteOnlyArray::begin 方法"
ms.assetid: 25025fa0-8f55-4abf-93ad-71db45ddfae3
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WriteOnlyArray::begin 方法
返回一个指向数组中第一个元素的指针。  
  
## 语法  
  
```cpp  
T* begin() const;  
```  
  
## 返回值  
 指向数组中第一个元素的指针。  
  
## 备注  
 此迭代器可与 STL 算法（如 `std::sort`）一起使用以操作数组中的元素。  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [Platform::WriteOnlyArray 类](../cppcx/platform-writeonlyarray-class.md)   
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)