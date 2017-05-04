---
title: "Array::get 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::Array::get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Array::get 方法"
ms.assetid: 3bbcd829-35e7-4912-99ba-6ab9de407287
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Array::get 方法
检索对指定索引位置上数组元素的引用。  
  
## 语法  
  
```  
  
T& get(  
unsigned int index  
)  const;  
```  
  
#### 参数  
 `index`  
 从零开始的索引，用来标识数组元素。 最小索引为 0，最大索引由 [数组构造函数](../cppcx/array-constructors.md)中的 `size` 参数指定。  
  
## 返回值  
 `index` 参数指定的数组元素。  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [Platform::Array 类](../cppcx/platform-array-class.md)