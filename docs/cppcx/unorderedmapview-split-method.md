---
title: "UnorderedMapView::Split 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView::Split"
ms.assetid: b759d254-40c9-40f1-9838-106ffb2c5626
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMapView::Split 方法
将当前 UnorderedMapView 对象分成两个 UnorderedMapView 对象。 此方法为非操作性的。  
  
## 语法  
  
```cpp  
void Split(  
   Windows::Foundation::Collections::IMapView<  
                         K,  
                         V>^ * firstPartition,  
   Windows::Foundation::Collections::IMapView<  
                         K,  
                         V>^ * secondPartition  
);  
```  
  
#### 参数  
 `firstPartition`  
 原始 UnorderedMapView 对象的第一部分。  
  
 `secondPartition`  
 原始 UnorderedMapView 对象的第二部分。  
  
## 备注  
 此方法为非操作性的，它不执行任何操作。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::UnorderedMapView 类](../cppcx/platform-collections-unorderedmapview-class.md)