---
title: "Map::HasKey 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::HasKey"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::HasKey 方法"
ms.assetid: ba7864af-056a-4b7b-843d-08c45b7f7394
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::HasKey 方法
确定当前 Map 中是否包含指定键。  
  
## 语法  
  
```  
  
bool HasKey(  
   K key  
);  
```  
  
#### 参数  
 `key`  
 用于定位 Map 元素的键。`key` 的类型名称为 *K*。  
  
## 返回值  
 如果找到该键，则为 `true`；否则为 `false`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md)