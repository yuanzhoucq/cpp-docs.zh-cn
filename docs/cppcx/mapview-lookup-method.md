---
title: "MapView::Lookup 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView::Lookup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView::Lookup 方法"
ms.assetid: 93090ac3-3f1d-4b7e-b80e-164b8c65cd29
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# MapView::Lookup 方法
检索与类型 K 的指定键关联的类型 V 的值。  
  
## 语法  
  
```  
V Lookup(  
   K key  
);  
```  
  
#### 参数  
 `key`  
 用于定位 MapView 中的元素的键。`key` 的类型名称为 *K*。  
  
## 返回值  
 与 `key` 配对的值。 返回值的类型名称为 *V*。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::MapView 类](../cppcx/platform-collections-mapview-class.md)