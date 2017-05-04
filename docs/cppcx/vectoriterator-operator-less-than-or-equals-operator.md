---
title: "VectorIterator::operator&lt;= 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator<="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator<= 运算符"
ms.assetid: 57d3c269-77a5-4731-a3b4-dcda2758da19
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator&lt;= 运算符
指示当前 VectorIterator 是否小于或等于指定的 VectorIterator。  
  
## 语法  
  
```cpp  
  
bool operator<=(  
   const VectorIterator& other  
) const   
```  
  
#### 参数  
 `other`  
 另一 VectorIterator。  
  
## 返回值  
 如果当前 VectorIterator 小于或等于 `other`，则为 `true`；否则为 `false`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorIterator 类](../cppcx/platform-collections-vectoriterator-class.md)