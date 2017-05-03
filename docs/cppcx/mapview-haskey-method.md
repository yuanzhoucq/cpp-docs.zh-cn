---
title: "MapView::HasKey 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView::HasKey"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView::HasKey 方法"
ms.assetid: c1a24f63-e6fd-4cfd-90ce-b89352b98324
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# MapView::HasKey 方法
确定当前 MapView 中是否包含指定键。  
  
## 语法  
  
```  
  
bool HasKey(  
   K key  
);  
```  
  
#### 参数  
 `key`  
 用于定位 MapView 元素的键。`key` 的类型名称为 *K*。  
  
## 返回值  
 如果找到该键，则为 `true`；否则为 `false`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::MapView 类](../cppcx/platform-collections-mapview-class.md)