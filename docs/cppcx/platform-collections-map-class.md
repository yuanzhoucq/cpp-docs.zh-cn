---
title: "Platform::Collections::Map 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map 类 (C++/Cx)"
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
caps.latest.revision: 19
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 19
---
# Platform::Collections::Map 类
表示一个*映射*，它是键值对的集合。  
  
## 语法  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = std::less<K>  
ref class Map sealed;  
```  
  
#### 参数  
 `K`  
 键值对中键的类型。  
  
 `V`  
 键值对中值的类型。  
  
 `C`  
 提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在映射中的相对顺序。 默认情况下为 [std::less\<K\>](../standard-library/less-struct.md)。  
  
 \_\_is\_valid\_winrt\_type\(\)  
 编译器生成的函数，用于验证 K 和 V 类型，并在此类型无法存储在映射中时提供友好错误消息。  
  
## 备注  
 允许的类型包括：  
  
-   整数  
  
-   接口类 ^  
  
-   公共 ref 类  
  
-   value struct  
  
-   公共枚举类  
  
 映射基本上是 [std::map](../standard-library/map-class.md) 的包装器。 这是在公共 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 接口之间传递的 [Windows::Foundation::Collections::IMap\<Windows::Foundation::Collections::IKeyValuePair\<K,V\>\>](http://go.microsoft.com/fwlink/p/?LinkId=262408) 和 [IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) 类型的 C\+\+ 具体实现。 如果你尝试在公共返回值或参数中使用 `Platform::Collections::Map` 类型，则将引发编译器错误 C3986。 通过将参数或返回值的类型更改为 [Windows::Foundation::Collections::IMap\<K,V\>](http://go.microsoft.com/fwlink/p/?LinkId=262408) 可修复该错误。  
  
 有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[Map::Map 构造函数](../cppcx/map-map-constructor.md)|初始化 Map 类的新实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[Map::Clear 方法](../cppcx/map-clear-method.md)|从当前 Map 对象中移除所有键值对。|  
|[Map::First 方法](../cppcx/map-first-method.md)|返回指定映射中第一个元素的迭代器。|  
|[Map::GetView 方法](../cppcx/map-getview-method.md)|返回当前映射的只读视图，即 [Platform::Collections::MapView 类](../cppcx/platform-collections-mapview-class.md)。|  
|[Map::HasKey 方法](../cppcx/map-haskey-method.md)|确定当前 Map 中是否包含指定键。|  
|[Map::Insert 方法](../cppcx/map-insert-method.md)|将指定的键值对添加到当前 Map 对象中。|  
|[Map::Lookup 方法](../cppcx/map-lookup-method.md)|检索当前 Map 对象中指定键处的元素。|  
|[Map::Remove 方法](../cppcx/map-remove-method.md)|从当前 Map 对象中删除指定的键值对。|  
|[Map::Size 方法](../cppcx/map-size-method.md)|返回当前 Map 对象中的元素数目。|  
  
### 事件  
  
|||  
|-|-|  
|名称|描述|  
|[Map::MapChanged 事件](../cppcx/map-mapchanged-event.md) `event`|当映射更改时发生。|  
  
## 继承层次结构  
 `Map`  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [用 C\+\+ 创建 Windows 运行时组件](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf)