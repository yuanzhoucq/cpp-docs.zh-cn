---
title: "Platform::Collections::MapView 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView 类"
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Platform::Collections::MapView 类
将一个只读视图表示为一个映射，这是键值对的集合。  
  
## 语法  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = ::std::less<K>  
>  
ref class MapView sealed;  
```  
  
#### 参数  
 `K`  
 键值对中键的类型。  
  
 `V`  
 键值对中值的类型。  
  
 `C`  
 提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在 MapView 中的相对顺序。 默认情况下为 [::std::less\<K\>](../standard-library/less-struct.md)。  
  
## 备注  
 MapView 是跨应用程序二进制接口 \(ABI\) 传递的 [Windows::Foundation::Collections::IMapView \<K,V\>](http://go.microsoft.com/fwlink/p/?LinkId=262409) 接口的具体 C\+\+ 实现。 有关更多信息，请参见[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[MapView::MapView 构造函数](../cppcx/mapview-mapview-constructor.md)|初始化 MapView 类的新实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[MapView::First 方法](../cppcx/mapview-first-method.md)|返回初始化为映射视图中第一个元素的迭代器。|  
|[MapView::HasKey 方法](../cppcx/mapview-haskey-method.md)|确定当前 MapView 中是否包含指定键。|  
|[MapView::Lookup 方法](../cppcx/mapview-lookup-method.md)|检索当前 MapView 对象中指定键处的元素。|  
|[MapView::Size 方法](../cppcx/mapview-size-method.md)|返回当前 MapView 对象中的元素数目。|  
|[MapView::Split 方法](../cppcx/mapview-split-method.md)|将原始 MapView 对象拆分成两个 MapView 对象。|  
  
## 继承层次结构  
 `MapView`  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)