---
title: "UnorderedMap::MapChanged | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::MapChanged"
ms.assetid: 6863781e-35af-4e77-9a11-277bd00f5d41
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::MapChanged
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