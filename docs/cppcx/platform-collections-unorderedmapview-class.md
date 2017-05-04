---
title: "Platform::Collections::UnorderedMapView 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView"
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::Collections::UnorderedMapView 类
将一个只读视图表示为一个映射，这是键值对的集合。  
  
## 语法  
  
```cpp  
template <  
   typename K,  
   typename V,  
   typename C = ::std::equal_to<K>  
>  
ref class UnorderedMapView sealed;  
```  
  
#### 参数  
 `K`  
 键值对中键的类型。  
  
 `V`  
 键值对中值的类型。  
  
 `C`  
 提供可比较两个键值是否相等的函数对象的类型。 默认为 [std::equal\_to\<K\>](../standard-library/equal-to-struct.md)  
  
## 备注  
 UnorderedMapView 是跨应用程序二进制接口 \(ABI\) 传递的 [Windows::Foundation::Collections::IMapView\<K,V\>](http://go.microsoft.com/fwlink/p/?LinkId=262409) 接口的具体 C\+\+ 实现。 有关更多信息，请参见[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[UnorderedMapView::UnorderedMapView 构造函数](../cppcx/unorderedmapview-unorderedmapview-constructor.md)|初始化 UnorderedMapView 类的新实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[UnorderedMapView::First 方法](../cppcx/unorderedmapview-first-method.md)|返回初始化为映射视图中第一个元素的迭代器。|  
|[UnorderedMapView::HasKey 方法](../cppcx/unorderedmapview-haskey-method.md)|确定当前 UnorderedMapView 中是否包含指定键。|  
|[UnorderedMapView::Lookup 方法](../cppcx/unorderedmapview-lookup-method.md)|检索当前 UnorderedMapView 对象中指定键处的元素。|  
|[UnorderedMapView::Size 方法](../cppcx/unorderedmapview-size-method.md)|返回当前 UnorderedMapView 对象中的元素数目。|  
|[UnorderedMapView::Split 方法](../cppcx/unorderedmapview-split-method.md)|将原始 UnorderedMapView 对象拆分成两个 UnorderedMapView 对象。|  
  
## 继承层次结构  
 `UnorderedMapView`  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections 命名空间](../cppcx/platform-collections-namespace.md)   
 [Windows::Foundation::IMapView](http://go.microsoft.com/fwlink/p/?LinkId=262409)