---
title: "UnorderedMap::Lookup 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::Lookup"
ms.assetid: 6f9bb393-3791-423d-bfee-925e0531e1a5
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::Lookup 方法
检索与类型 K 的指定键关联的类型 V 的值。  
  
## 语法  
  
```scr  
V Lookup(  
   K key  
);  
```  
  
#### 参数  
 `key`  
 用于定位 UnorderedMap 中的元素的键。`key` 的类型名称为 *K*。  
  
## 返回值  
 与 `key` 配对的值。 返回值的类型名称为 *V*。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [集合](../cppcx/collections-c-cx.md)   
 [Platform::Collections::UnorderedMap 类](../cppcx/platform-collections-unorderedmap-class.md)