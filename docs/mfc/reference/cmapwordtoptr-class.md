---
title: "CMapWordToPtr Class | Microsoft Docs"
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
  - "CMapWordToPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "16-bit word mapping"
  - "CMapWordToPtr class"
ms.assetid: b204d87f-6427-43e1-93e3-a4b1bb41099f
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMapWordToPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持16位签名密钥的无效指针映射。  
  
## 语法  
  
```  
class CMapWordToPtr : public CObject  
```  
  
## 成员  
 `CMapWordToPtr` 的成员函数类似于选件类 [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)的成员函数。  因此相似性，可以使用 `CMapStringToOb` 引用成员函数特定的文档。  无论在何处参见 `CObject` 指针作为函数参数或返回值，请替换指向 `void`。  无论在何处参见 `CString` 或 **const** 指向 `char` 作为函数参数或返回值，替代 **WORD**。  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 例如，转换  
  
 `BOOL CMapWordToPtr::Lookup( WORD <key>, void*& <rValue> ) const;`  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMapStringToOb::CMapStringToOb](../Topic/CMapStringToOb::CMapStringToOb.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMapStringToOb::GetCount](../Topic/CMapStringToOb::GetCount.md)|返回元素数此映射。|  
|[CMapStringToOb::GetHashTableSize](../Topic/CMapStringToOb::GetHashTableSize.md)|确定元素的当前在哈希表中。|  
|[CMapStringToOb::GetNextAssoc](../Topic/CMapStringToOb::GetNextAssoc.md)|获取重复的下一个元素。|  
|[CMapStringToOb::GetSize](../Topic/CMapStringToOb::GetSize.md)|返回元素数此映射。|  
|[CMapStringToOb::GetStartPosition](../Topic/CMapStringToOb::GetStartPosition.md)|返回第一个元素的位置。|  
|[CMapStringToOb::HashKey](../Topic/CMapStringToOb::HashKey.md)|计算指定的键的哈希值。|  
|[CMapStringToOb::InitHashTable](../Topic/CMapStringToOb::InitHashTable.md)|初始化哈希表。|  
|[CMapStringToOb::IsEmpty](../Topic/CMapStringToOb::IsEmpty.md)|测试空地图情况\(而不是元素）。|  
|[CMapStringToOb::Lookup](../Topic/CMapStringToOb::Lookup.md)|查找基于无效指针键的无效的指针。  它指向，对密钥进行比较使用的指针值，而不是实体。|  
|[CMapStringToOb::LookupKey](../Topic/CMapStringToOb::LookupKey.md)|返回对密钥与指定的键值。|  
|[CMapStringToOb::RemoveAll](../Topic/CMapStringToOb::RemoveAll.md)|从此映射中移除所有元素。|  
|[CMapStringToOb::RemoveKey](../Topic/CMapStringToOb::RemoveKey.md)|移除项指定的元素。|  
|[CMapStringToOb::SetAt](../Topic/CMapStringToOb::SetAt.md)|将元素插入到映射中;，如果找到，替换现有元素匹配键。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CMapStringToOb::operator](../Topic/CMapStringToOb::operator.md)|将元素插入到映射中— `SetAt`的运算符替换。|  
  
## 备注  
 `CMapWordToPtr` 合并 `IMPLEMENT_DYNAMIC` 宏支持运行时类型访问和转储到 `CDumpContext` 对象。  如果需要各个组件映射转储，必须将转储上下文的深度为1或更大。  
  
 不可序列化的Word指向映射。  
  
 当 `CMapWordToPtr` 对象中移除时，或者，如果移除了其元素，移除单词和指针。  不移除指针引用的实体。  
  
 有关 `CMapWordToPtr`的更多信息，请参见文章 [集合](../../mfc/collections.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapWordToPtr`  
  
## 要求  
 **Header:** afxcoll.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)