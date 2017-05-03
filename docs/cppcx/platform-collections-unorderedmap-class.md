---
title: "Platform::Collections::UnorderedMap 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap"
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Collections::UnorderedMap 类
表示一个无序映射，它是键值对的集合。  
  
## 语法  
  
```scr  
template <  
   typename K,  
   typename V,  
   typename C = std::equal_to<K>  
>  
ref class Map sealed;  
```  
  
#### 参数  
 `K`  
 键值对中键的类型。  
  
 `V`  
 键值对中值的类型。  
  
 `C`  
 提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在映射中的相对顺序。 默认为 [std::equal\_to\<K\>](../standard-library/equal-to-struct.md)。  
  
## 备注  
 允许的类型包括：  
  
-   整数  
  
-   接口类 ^  
  
-   公共 ref 类  
  
-   value struct  
  
-   公共枚举类  
  
 UnorderedMap 基本上是支持 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 类型存储的 [std::unordered\_map](../standard-library/unordered-map-class.md) 的包装器。 这是在公共 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 接口之间传递的 [Windows::Foundation::Collections::IMap](http://go.microsoft.com/fwlink/p/?LinkId=262408) 和 [IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) 类型的 C\+\+ 具体实现。 如果你尝试在公共返回值或参数中使用 Platform::Collections::UnorderedMap 类型，则将引发编译器错误 C3986。 通过将参数或返回值的类型更改为 [Windows::Foundation::Collections::IMap](http://go.microsoft.com/fwlink/p/?LinkId=262408) 可修复该错误。  
  
 有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|UnorderedMap::UnorderedMap 构造函数|初始化 Map 类的新实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[UnorderedMap::Clear 方法](../cppcx/unorderedmap-clear-method.md)|从当前 Map 对象中移除所有键值对。|  
|[UnorderedMap::First 方法](../cppcx/unorderedmap-first-method.md)|返回指定映射中第一个元素的迭代器。|  
|[UnorderedMap::GetView 方法](../cppcx/unorderedmap-getview-method.md)|返回当前 Map 的只读视图，即 Platform::Collections::UnorderedMapView 类。|  
|[UnorderedMap::HasKey 方法](../cppcx/unorderedmap-haskey-method.md)|确定当前 Map 中是否包含指定键。|  
|[UnorderedMap::Insert 方法](../cppcx/unorderedmap-insert-method.md)|将指定的键值对添加到当前 Map 对象中。|  
|[UnorderedMap::Lookup 方法](../cppcx/unorderedmap-lookup-method.md)|检索当前 Map 对象中指定键处的元素。|  
|[UnorderedMap::Remove 方法](../cppcx/unorderedmap-remove-method.md)|从当前 Map 对象中删除指定的键值对。|  
|[UnorderedMap::Size 方法](../cppcx/unorderedmap-size-method.md)|返回当前 Map 对象中的元素数目。|  
  
### 事件  
  
|||  
|-|-|  
|名称|描述|  
|[Map::MapChanged 事件](../cppcx/map-mapchanged-event.md) `event`|当映射更改时发生。|  
  
## 继承层次结构  
 `UnorderedMap`  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [Platform::Collections 命名空间](../cppcx/platform-collections-namespace.md)   
 [Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md)   
 [Platform::Collections::UnorderedMapView 类](../cppcx/platform-collections-unorderedmapview-class.md)   
 [集合](../cppcx/collections-c-cx.md)   
 [用 C\+\+ 创建 Windows 运行时组件](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)