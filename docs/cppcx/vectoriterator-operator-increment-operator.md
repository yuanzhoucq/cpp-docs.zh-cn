---
title: "VectorIterator::operator++ 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator++ 运算符"
ms.assetid: c46b18ff-45be-436a-8f31-b3a5ecc19b77
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator++ 运算符
递增当前 VectorIterator。  
  
## 语法  
  
```  
  
VectorIterator& operator++();  
VectorIterator operator++(  
   int  
);  
```  
  
## 返回值  
 第一个语法先递增然后返回当前 VectorIterator。 第二个语法返回当前 VectorIterator 的副本然后递增当前 VectorIterator。  
  
## 备注  
 第一个 VectorIterator 语法预先递增当前 VectorIterator。  
  
 第二个语法后递增当前 VectorIterator。 第二个语法中的 `int` 类型指示后递增操作，而不是实际整数操作数。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorIterator 类](../cppcx/platform-collections-vectoriterator-class.md)