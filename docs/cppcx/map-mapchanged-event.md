---
title: "Map::MapChanged 事件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::MapChanged"
ms.assetid: d14b5b93-36ff-47a5-b588-dd1dc6ea4364
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::MapChanged 事件
项目插入到映射中或从映射中移除时引发。  
  
## 语法  
  
```cpp  
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;  
```  
  
## 属性值\/返回值  
 包含与引发事件的对象和所发生更改的类型相关的信息的 [MapChangedEventHandler\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br206644.aspx)。 另请参见 [IMapChangedEventArgs\<K\>](http://msdn.microsoft.com/library/windows/apps/br226034.aspx) 和 [CollectionChange Enumeration](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx)。  
  
## .NET Framework 等效项  
 将 C\# 或 Visual Basic 项目 IMap\<K,V\> 用作 IDictionary\<K,V\> 的 Windows 应用商店应用。  
  
## 要求  
 Windows 8.0 或更高版本  
  
## 请参阅  
 [集合](../cppcx/collections-c-cx.md)