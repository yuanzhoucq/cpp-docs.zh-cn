---
title: "VectorViewIterator::operatorOperator | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator[] 运算符"
ms.assetid: 41bf327d-2037-457c-83df-6338fc1abbc2
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operatorOperator
检索对偏移当前 VectorViewIterator 指定量的元素的引用。  
  
## 语法  
  
```  
reference operator[](difference_type n) const;  
```  
  
#### 参数  
 `n`  
 整数偏移。  
  
## 返回值  
 `n` 元素从当前 VectorViewIterator 移置开的元素。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)