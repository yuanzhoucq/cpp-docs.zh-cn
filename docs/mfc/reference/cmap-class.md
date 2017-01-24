---
title: "CMap Class | Microsoft Docs"
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
  - "CMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMap class"
  - "集合类, dictionary mapping"
  - "dictionary mapping class"
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

该字典集合的选件类映射唯一键的值。  
  
## 语法  
  
```  
template< class KEY, class ARG_KEY, class VALUE, class ARG_VALUE >class CMap : public CObject  
```  
  
#### 参数  
 `KEY`  
 作为键使用对象的选件类为映射。  
  
 `ARG` *\_* `KEY`  
 用于 `KEY` 参数的数据类型;通常为 `KEY`的引用。  
  
 `VALUE`  
 在映射中存储的对象选件类。  
  
 `ARG` *\_* `VALUE`  
 用于 `VALUE` 参数的数据类型;通常为 `VALUE`的引用。  
  
## 成员  
  
### 公共结构  
  
|名称|说明|  
|--------|--------|  
|[CMap::CPair](../Topic/CMap::CPair.md)|包含键值和关联的对象的值嵌套结构。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMap::CMap](../Topic/CMap::CMap.md)|构造集合一个键的值。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMap::GetCount](../Topic/CMap::GetCount.md)|返回元素数此映射。|  
|[CMap::GetHashTableSize](../Topic/CMap::GetHashTableSize.md)|返回元素数。哈希表中。|  
|[CMap::GetNextAssoc](../Topic/CMap::GetNextAssoc.md)|获取重复的下一个元素。|  
|[CMap::GetSize](../Topic/CMap::GetSize.md)|返回元素数此映射。|  
|[CMap::GetStartPosition](../Topic/CMap::GetStartPosition.md)|返回第一个元素的位置。|  
|[CMap::InitHashTable](../Topic/CMap::InitHashTable.md)|初始化哈希表并指定其大小。|  
|[CMap::IsEmpty](../Topic/CMap::IsEmpty.md)|测试空地图情况\(而不是元素）。|  
|[CMap::Lookup](../Topic/CMap::Lookup.md)|查找该值映射到特定键。|  
|[CMap::PGetFirstAssoc](../Topic/CMap::PGetFirstAssoc.md)|返回指向第一个元素。|  
|[CMap::PGetNextAssoc](../Topic/CMap::PGetNextAssoc.md)|获取一个指向重复的下一个元素。|  
|[CMap::PLookup](../Topic/CMap::PLookup.md)|返回指向值与此指定值的键。|  
|[CMap::RemoveAll](../Topic/CMap::RemoveAll.md)|从此映射中移除所有元素。|  
|[CMap::RemoveKey](../Topic/CMap::RemoveKey.md)|移除项指定的元素。|  
|[CMap::SetAt](../Topic/CMap::SetAt.md)|将元素插入到映射中;，如果找到，替换现有元素匹配键。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CMap::operator](../Topic/CMap::operator.md)|将元素插入到映射中— `SetAt`的运算符替换。|  
  
## 备注  
 一旦已插入键值对\(元素\)添加到映射，可以有效地检索或删除对使用键访问它。  还可以循环访问在映射中的所有元素。  
  
 类型 **POSITION** 的变量为项的备用访问使用。  可以使用 **POSITION** “记得”项并将映射重复。  您可能认为此迭代由键值是连续的;它不是。  检索的元素顺序是不确定的。  
  
 此选件类的某些成员函数调用必须自定义为 `CMap` 选件类的大多数使用的全局helper函数。  在参见 `MFC``Reference`的宏和Globals部分的 [集合选件帮助器类](../../mfc/reference/collection-class-helpers.md)。  
  
 `CMap` 重写 [CObject::Serialize](../Topic/CObject::Serialize.md) 支持序列化和转储其元素。  使用 `Serialize`，如果将存储到存档，又序列化每个映射元素。  `SerializeElements` helper函数的默认实现执行按位一编写。  有关指针从 `CObject` 或其他用户定义的类型派生的集合项的序列化信息，请参见 [如何：创建类型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。  
  
 如果在映射需要各个元素的诊断转储\(键和值\)，则必须将转储上下文的深度为1或更大。  
  
 当 `CMap` 对象中移除时，或者，如果移除了其元素，移除键和值两个。  
  
 映射选件类派生类似的列表派生。  为派生的插图参见中的文章 [集合](../../mfc/collections.md) 私有列表选件类。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## 要求  
 **Header:** afxtempl.h  
  
## 请参阅  
 [MFC示例集合](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)