---
title: "CSimpleMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CSimpleMap"
  - "ATL.CSimpleMap"
  - "CSimpleMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleMap class"
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供一个简单的映射数组支持。  
  
## 语法  
  
```  
  
      template <   
   class TKey,  
   class TVal,  
   class TEqual = CSimpleMapEqualHelper< TKey, TVal >   
>   
class CSimpleMap  
```  
  
#### 参数  
 `TKey`  
 关键元素类型。  
  
 `TVal`  
 值元素类型。  
  
 `TEqual`  
 特征的对象，定义相等测试类型 `T`的元素。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CSimpleMap::\_ArrayElementType](../Topic/CSimpleMap::_ArrayElementType.md)|值类型的Typedef。|  
|[CSimpleMap::\_ArrayKeyType](../Topic/CSimpleMap::_ArrayKeyType.md)|关键类型的Typedef。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSimpleMap::CSimpleMap](../Topic/CSimpleMap::CSimpleMap.md)|构造函数。|  
|[CSimpleMap::~CSimpleMap](../Topic/CSimpleMap::~CSimpleMap.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSimpleMap::Add](../Topic/CSimpleMap::Add.md)|添加一个键和关联的值更改为映射数组。|  
|[CSimpleMap::FindKey](../Topic/CSimpleMap::FindKey.md)|查找特定键。|  
|[CSimpleMap::FindVal](../Topic/CSimpleMap::FindVal.md)|查找特定值。|  
|[CSimpleMap::GetKeyAt](../Topic/CSimpleMap::GetKeyAt.md)|检索指定键的。|  
|[CSimpleMap::GetSize](../Topic/CSimpleMap::GetSize.md)|返回项的数目是在映射的数组。|  
|[CSimpleMap::GetValueAt](../Topic/CSimpleMap::GetValueAt.md)|检索此指定值。|  
|[CSimpleMap::Lookup](../Topic/CSimpleMap::Lookup.md)|返回值与特定键。|  
|[CSimpleMap::Remove](../Topic/CSimpleMap::Remove.md)|移除键和匹配的值。|  
|[CSimpleMap::RemoveAll](../Topic/CSimpleMap::RemoveAll.md)|移除所有键和值。|  
|[CSimpleMap::RemoveAt](../Topic/CSimpleMap::RemoveAt.md)|移除一个特定键和匹配的值。|  
|[CSimpleMap::ReverseLookup](../Topic/CSimpleMap::ReverseLookup.md)|返回键与该特定值。|  
|[CSimpleMap::SetAt](../Topic/CSimpleMap::SetAt.md)|将值与特定键。|  
|[CSimpleMap::SetAtIndex](../Topic/CSimpleMap::SetAtIndex.md)|将给定键和值。|  
  
## 备注  
 `CSimpleMap` 提供简单的映射的一些任何给定类型支持 `T`，管理无序的关键元素及其关联的值。  
  
 该参数 `TEqual` 为类型提供定义相等性函数方法 `T`的两个元素。  通过创建选件类类似于 [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)，更改相等的行为测试对于任何给定数组是可能的。  例如，在中，当处理数组指针，根据值时定义相等可能很有用的指针引用。  默认实现使用 **operator\=\=\(\)**。  
  
 `CSimpleMap` 和 [CSimpleArray](../../atl/reference/csimplearray-class.md) 的目的是前面ATL版本，并且，[CAtlArray](../../atl/reference/catlarray-class.md) 和 [CAtlMap](../../atl/reference/catlmap-class.md)提供更完整、更高效集合实现。  
  
 不同于ATL和MFC的其他映射的集合，此选件类实现一个简单的数组，并且，查找搜索需要使用线性搜索。  `CAtlMap`，当数组包含大量元素时，应使用。  
  
## 要求  
 **Header:** atlsimpcoll.h  
  
## 示例  
 [!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/CPP/csimplemap-class_1.cpp)]  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)