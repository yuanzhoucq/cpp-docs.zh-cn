---
title: "UnorderedMapView::First 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView::First"
ms.assetid: 385f2a46-90ee-412b-817b-b5a0f2f57022
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMapView::First 方法
返回指定无序映射中第一个 [Windows::Foundation::Collections::IKeyValuePair\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) 元素的迭代器。  
  
## 语法  
  
```cpp  
  
virtual Windows::Foundation::Collections::IIterator<  
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^   
First();  
```  
  
## 返回值  
 指定映射视图中第一个元素的迭代器。  
  
## 备注  
 保留 First\(\) 返回的迭代器的一种简便方式是将返回值分配给用 [auto](../Topic/auto%20\(C++\).md) 类型推导关键字声明的变量。 例如 `auto x = myMapView->First();`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::UnorderedMapView 类](../cppcx/platform-collections-unorderedmapview-class.md)