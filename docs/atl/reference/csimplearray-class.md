---
title: "CSimpleArray Class | Microsoft Docs"
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
  - "ATL.CSimpleArray"
  - "ATL::CSimpleArray"
  - "CSimpleArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleArray class"
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类用于管理一个简单数组的方法。  
  
## 语法  
  
```  
  
      template <  
   class T,  
   class TEqual = CSimpleArrayEqualHelper< T >  
>   
class CSimpleArray  
```  
  
#### 参数  
 `T`  
 存储的数据的类型在数组。  
  
 `TEqual`  
 特征的对象，定义相等测试类型 `T`的元素。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSimpleArray::CSimpleArray](../Topic/CSimpleArray::CSimpleArray.md)|简单数组的构造函数。|  
|[CSimpleArray::~CSimpleArray](../Topic/CSimpleArray::~CSimpleArray.md)|简单数组的析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSimpleArray::Add](../Topic/CSimpleArray::Add.md)|添加新元素。数组。|  
|[CSimpleArray::Find](../Topic/CSimpleArray::Find.md)|查找该数组的元素。|  
|[CSimpleArray::GetData](../Topic/CSimpleArray::GetData.md)|返回指向该数组存储的数据。|  
|[CSimpleArray::GetSize](../Topic/CSimpleArray::GetSize.md)|返回数组中存储的元素的数目。|  
|[CSimpleArray::Remove](../Topic/CSimpleArray::Remove.md)|从数组中移除某个特定元素。|  
|[CSimpleArray::RemoveAll](../Topic/CSimpleArray::RemoveAll.md)|从数组中移除所有元素。|  
|[CSimpleArray::RemoveAt](../Topic/CSimpleArray::RemoveAt.md)|从数组中移除指定的元素。|  
|[CSimpleArray::SetAtIndex](../Topic/CSimpleArray::SetAtIndex.md)|设置该数组中指定的元素。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CSimpleArray::operator](../Topic/CSimpleArray::operator.md)|从数组检索元素。|  
|[CSimpleArray::operator \=](../Topic/CSimpleArray::operator%20=.md)|赋值运算符。|  
  
## 备注  
 `CSimpleArray` 为创建和管理简单的提供一些方法，任何给定类型 `T`。  
  
 该参数 `TEqual` 为类型提供定义相等性函数方法 `T`的两个元素。  通过创建选件类类似于 [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)，更改相等的行为测试对于任何给定数组是可能的。  例如，在中，当处理数组指针，根据值时定义相等可能很有用的指针引用。  默认实现使用 **operator\=\(\)**。  
  
 `CSimpleArray` 和 [CSimpleMap](../../atl/reference/csimplemap-class.md) 为少量组件模型。  [CAtlArray](../../atl/reference/catlarray-class.md) 和 [CAtlMap](../../atl/reference/catlmap-class.md)，当数组包含大量元素时，应使用。  
  
## 要求  
 **Header:** atlsimpcoll.h  
  
## 示例  
 [!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/CPP/csimplearray-class_1.cpp)]  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)