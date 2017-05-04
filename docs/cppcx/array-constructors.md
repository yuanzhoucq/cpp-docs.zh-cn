---
title: "Array 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::Array::Array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Array::Array"
ms.assetid: befb8088-3915-4b5c-b7fd-90f79961412d
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Array 构造函数
初始化类模板参数 *T* 指定的类型的一维可修改数组。  
  
## 语法  
  
```  
  
Array(unsigned int size);  
Array(T* data, unsigned int size);  
  
```  
  
#### 参数  
 `T`  
 类模板参数。  
  
 `size`  
 数组中的元素数。  
  
 `data`  
 指向用于初始化该数组对象的类型 `T` 的数据数组的指针。  
  
## 备注  
 有关如何创建 Platform::Array 实例的更多信息，请参见 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [Platform::Array 类](../cppcx/platform-array-class.md)