---
title: "VectorIterator::operator-- 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator--"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator-- 运算符"
ms.assetid: 650a3037-2984-4110-9d7c-cd3756e5f4b9
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator-- 运算符
递减当前 VectorIterator。  
  
## 语法  
  
```  
  
VectorIterator& operator--();  
VectorIterator operator--(  
   int  
);  
```  
  
## 返回值  
 第一个语法先递减，然后返回当前 VectorIterator。 第二个语法返回当前 VectorIterator 的副本，然后递减当前 VectorIterator。  
  
## 备注  
 第一个 VectorIterator 语法预先递减当前 VectorIterator。  
  
 第二个语法后递减当前 VectorIterator。 第二个语法中的 `int` 类型指示后递减操作，而不是实际整数操作数。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorIterator 类](../cppcx/platform-collections-vectoriterator-class.md)