---
title: "VectorViewIterator::operator++ 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator++ 运算符"
ms.assetid: 5391e6e2-a7ee-4dab-8cee-b2237894246f
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator++ 运算符
递增当前 VectorViewIterator。  
  
## 语法  
  
```  
  
VectorViewIterator& operator++();  
VectorViewIterator operator++(  
   int  
);  
```  
  
## 返回值  
 第一个语法先递增然后返回当前 VectorViewIterator。 第二个语法返回当前 VectorViewIterator 的副本然后递增当前 VectorViewIterator。  
  
## 备注  
 第一个 VectorViewIterator 语法预先递增当前 VectorViewIterator。  
  
 第二个语法后递增当前 VectorViewIterator。 第二个语法中的 `int` 类型指示后递增操作，而不是实际整数操作数。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)