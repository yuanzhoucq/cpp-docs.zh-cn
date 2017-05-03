---
title: "Map::Lookup 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::Lookup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::Lookup 方法"
ms.assetid: c56773ae-2df0-4d21-a6ab-9603529547b0
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::Lookup 方法
检索与类型 K 的指定键关联的类型 V 的值（如果键存在）。  
  
## 语法  
  
```  
V Lookup(  
   K key  
);  
```  
  
#### 参数  
 `key`  
 用于定位映射中的元素的键。`key` 的类型名称为 *K*。  
  
## 返回值  
 与 `key` 配对的值。 返回值的类型名称为 *V*。  
  
## 备注  
 如果键不存在，则将引发 [Platform::OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md)。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md)   
 [集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)