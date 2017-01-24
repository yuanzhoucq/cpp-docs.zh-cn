---
title: "CMapStringToOb Class | Microsoft Docs"
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
  - "CMapStringToOb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMapStringToOb class"
  - "集合类, string mapping"
  - "字符串 [C++], class for mapping"
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMapStringToOb Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

该字典集合的选件类为 `CObject` 指针的映射唯一 `CString` 对象。  
  
## 语法  
  
```  
class CMapStringToOb : public CObject  
```  
  
## 成员  
  
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
 一旦已插入 `CString`\-`CObject*` 对\(元素\)添加到映射，可以有效地检索或删除对使用字符串或 `CString` 值为资源键。  还可以循环访问在映射中的所有元素。  
  
 类型 **POSITION** 的变量为备用项通过使用在所有映射变体。  可以使用 **POSITION** “记得”项并将映射重复。  您可能认为此迭代由键值是连续的;它不是。  检索的元素顺序是不确定的。  
  
 `CMapStringToOb` 合并 `IMPLEMENT_SERIAL` 宏支持序列化和转储其元素。  又序列化每个元素，如果将存储到存档，与重载中插入 \(**\<\<**\) 运算符或与 `Serialize` 成员函数。  
  
 如果在映射\( `CString` 值和 `CObject` 内容\)需要各个元素的诊断转储，必须将转储上下文的深度为1或更大。  
  
 当 `CMapStringToOb` 对象中移除时，或者，如果移除了其元素，移除 `CString` 对象和 `CObject` 指针。  销毁 `CObject` 指针所引用的对象。  
  
 映射选件类派生类似的列表派生。  为派生的插图参见中的文章 [集合](../../mfc/collections.md) 私有列表选件类。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToOb`  
  
## 要求  
 **Header:** afxcoll.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr Class](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord Class](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapStringToPtr Class](../../mfc/reference/cmapstringtoptr-class.md)   
 [CMapStringToString Class](../../mfc/reference/cmapstringtostring-class.md)   
 [CMapWordToOb Class](../../mfc/reference/cmapwordtoob-class.md)   
 [CMapWordToPtr Class](../../mfc/reference/cmapwordtoptr-class.md)