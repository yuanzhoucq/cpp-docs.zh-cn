---
title: "CAtlMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlMap"
  - "CAtlMap"
  - "ATL::CAtlMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlMap class"
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAtlMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为创建和管理映射对象的方法。  
  
## 语法  
  
```  
  
      template<  
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >  
>  
class CAtlMap  
```  
  
#### 参数  
 `K`  
 关键元素类型。  
  
 V  
 值元素类型。  
  
 `KTraits`  
 用于的代码复制或移动关键元素。  有关详细信息 [CElementTraits选件类](../../atl/reference/celementtraits-class.md) 参见。  
  
 `VTraits`  
 用于的代码复制或移动值元素。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CAtlMap::KINARGTYPE](../Topic/CAtlMap::KINARGTYPE.md)|使用的类型的键，以将作为输入参数|  
|[CAtlMap::KOUTARGTYPE](../Topic/CAtlMap::KOUTARGTYPE.md)|使用的类型，而该返回作为输出参数。|  
|[CAtlMap::VINARGTYPE](../Topic/CAtlMap::VINARGTYPE.md)|使用的类型，该值作为输入参数。|  
|[CAtlMap::VOUTARGTYPE](../Topic/CAtlMap::VOUTARGTYPE.md)|使用的类型，该值将作为输出参数。|  
  
### 公共类  
  
|名称|说明|  
|--------|--------|  
|[CAtlMap::CPair Class](../Topic/CAtlMap::CPair%20Class.md)|一个包含键和值的元素的选件类。|  
  
### CPair数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPair::m\_key](../Topic/CAtlMap::CPair::m_key.md)|存储关键元素的数据成员。|  
|[CPair::m\_value](../Topic/CAtlMap::CPair::m_value.md)|存储值的元素的数据成员。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlMap::CAtlMap](../Topic/CAtlMap::CAtlMap.md)|构造函数。|  
|[CAtlMap::~CAtlMap](../Topic/CAtlMap::~CAtlMap.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlMap::AssertValid](../Topic/CAtlMap::AssertValid.md)|调用此方法会导致断言 `CAtlMap` 是否无效。|  
|[CAtlMap::DisableAutoRehash](../Topic/CAtlMap::DisableAutoRehash.md)|调用此方法禁用自动改作 `CAtlMap` 对象。|  
|[CAtlMap::EnableAutoRehash](../Topic/CAtlMap::EnableAutoRehash.md)|调用此方法启用自动改作 `CAtlMap` 对象。|  
|[CAtlMap::GetAt](../Topic/CAtlMap::GetAt.md)|调用此方法返回元素在映射中的指定位置。|  
|[CAtlMap::GetCount](../Topic/CAtlMap::GetCount.md)|调用此方法检索元素数。映射。|  
|[CAtlMap::GetHashTableSize](../Topic/CAtlMap::GetHashTableSize.md)|调用此方法来确定框数。映射的哈希表中。|  
|[CAtlMap::GetKeyAt](../Topic/CAtlMap::GetKeyAt.md)|调用此方法检索密钥存储在 `CAtlMap` 对象的特定位置。|  
|[CAtlMap::GetNext](../Topic/CAtlMap::GetNext.md)|调用此方法获取指向下一个元素对存储在 `CAtlMap` 对象。|  
|[CAtlMap::GetNextAssoc](../Topic/CAtlMap::GetNextAssoc.md)|获取重复的下一个元素。|  
|[CAtlMap::GetNextKey](../Topic/CAtlMap::GetNextKey.md)|调用此方法从 `CAtlMap` 对象检索下密钥。|  
|[CAtlMap::GetNextValue](../Topic/CAtlMap::GetNextValue.md)|调用此方法获取 `CAtlMap` 对象的下一个值。|  
|[CAtlMap::GetStartPosition](../Topic/CAtlMap::GetStartPosition.md)|调用此方法开始映射迭代。|  
|[CAtlMap::GetValueAt](../Topic/CAtlMap::GetValueAt.md)|调用此方法检索值存储在 `CAtlMap` 对象的特定位置。|  
|[CAtlMap::InitHashTable](../Topic/CAtlMap::InitHashTable.md)|调用此方法初始化哈希表。|  
|[CAtlMap::IsEmpty](../Topic/CAtlMap::IsEmpty.md)|调用此方法测试空控件对象。|  
|[CAtlMap::Lookup](../Topic/CAtlMap::Lookup.md)|调用此方法查找键或值。`CAtlMap` 对象。|  
|[CAtlMap::Rehash](../Topic/CAtlMap::Rehash.md)|调用此方法以改作 `CAtlMap` 对象。|  
|[CAtlMap::RemoveAll](../Topic/CAtlMap::RemoveAll.md)|调用此方法从 `CAtlMap` 对象中移除所有元素。|  
|[CAtlMap::RemoveAtPos](../Topic/CAtlMap::RemoveAtPos.md)|调用此方法会移除该元素在 `CAtlMap` 对象的特定位置。|  
|[CAtlMap::RemoveKey](../Topic/CAtlMap::RemoveKey.md)|调用此方法从 `CAtlMap` 对象中移除元素命名键。|  
|[CAtlMap::SetAt](../Topic/CAtlMap::SetAt.md)|调用此方法将一对元素添加到映射中插入。|  
|[CAtlMap::SetOptimalLoad](../Topic/CAtlMap::SetOptimalLoad.md)|调用此方法设置 `CAtlMap` 对象的最佳的负载。|  
|[CAtlMap::SetValueAt](../Topic/CAtlMap::SetValueAt.md)|调用此方法将值存储在 `CAtlMap` 对象的特定位置。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAtlMap::operator](../Topic/CAtlMap::operator.md)|替换或添加新元素。`CAtlMap`。|  
  
## 备注  
 `CAtlMap` 提供用于映射的一些任何给定类型的支持，管理无序的关键元素及其关联的值。  元素\(其中包括注册表项和值\)使用哈希算法，存储，允许大量数据有效地存储和检索。  
  
 `KTraits` 和 `VTraits` 参数是包含必需的全部将代码复制或移动元素的特征选件类。  
  
 [CRBMap](../../atl/reference/crbmap-class.md) 选件类提供对 `CAtlMap` 的替代方法。  还`CRBMap` 存储键\/值对，但是，显示不同的性能特征。  时所需的插入项，搜索一个键或从 `CRBMap` 对象中删除密钥是订单 *记录\(n\)*，其中 *n* 是元素的数目。  对于 `CAtlMap`，所有这些操作通常需要常量时，不过，最坏情况可能是顺序 *n。* 因此，在典型的情况下，`CAtlMap` 更快。  
  
 当循环存储元素时，在 `CRBMap` 和 `CAtlMap` 之间的另一个差异变得非常明显。  在 `CRBMap`，元素按排序顺序访问。  在 `CAtlMap`，元素未排序，并且，顺序不可推断。  
  
 当需要存储时少量元素，请考虑使用 [CSimpleMap](../../atl/reference/csimplemap-class.md) 选件类。  
  
 有关更多信息，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [marquee示例](../../top/visual-cpp-samples.md)   
 [UpdatePV示例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)