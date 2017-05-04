---
title: "UnorderedMap::GetView 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::GetView"
ms.assetid: 41a12802-3f42-461c-a6fc-a35fc34517f2
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::GetView 方法
返回当前 UnorderedMap 的只读视图；即实现 [Windows::Foundation::Collections::IMapView::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) 接口的 [Platform::Collections::UnorderedMapView 类](../cppcx/platform-collections-unorderedmapview-class.md)。  
  
## 语法  
  
```scr  
  
Windows::Foundation::Collections::IMapView<K, V>^   
   GetView();  
```  
  
## 返回值  
 一个 `UnorderedMapView` 对象。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [集合](../cppcx/collections-c-cx.md)   
 [Platform::Collections::UnorderedMap 类](../cppcx/platform-collections-unorderedmap-class.md)   
 [Platform::Collections::UnorderedMapView 类](../cppcx/platform-collections-unorderedmapview-class.md)