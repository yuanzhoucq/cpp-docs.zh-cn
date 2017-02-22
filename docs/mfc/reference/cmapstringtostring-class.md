---
title: "CMapStringToString Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMapStringToString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMapStringToString class"
  - "集合类, string mapping"
  - "字符串 [C++], class for mapping"
  - "字符串 [C++], 映射"
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMapStringToString Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持 `CString` 对象映射 `CString` 对象密钥的。  
  
## 语法  
  
```  
class CMapStringToString : public CObject  
```  
  
## 成员  
 `CMapStringToString` 的成员函数类似于选件类 [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)的成员函数。  因此相似性，可以使用 `CMapStringToOb` 引用成员函数特定的文档。  无论在何处参见 `CObject` 指针，因为返回值或“输出”函数参数，并指向 `char`。  无论在何处参见 `CObject` 指针为“输入”函数参数，请替换指向 `char`。  
  
 `BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`  
  
 例如，转换  
  
 `BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`  
  
### 公共结构  
  
|名称|说明|  
|--------|--------|  
|[CMapStringToString::CPair](../Topic/CMapStringToString::CPair.md)|包含键值和关联的字符串对象的值嵌套结构。|  
  
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
|[CMapStringToString::PGetFirstAssoc](../Topic/CMapStringToString::PGetFirstAssoc.md)|获取一个指向在映射的第一 `CString`。|  
|[CMapStringToString::PGetNextAssoc](../Topic/CMapStringToString::PGetNextAssoc.md)|获取一个指向重复的下 `CString`。|  
|[CMapStringToString::PLookup](../Topic/CMapStringToString::PLookup.md)|返回指向值与此指定值的 `CString`。|  
|[CMapStringToOb::RemoveAll](../Topic/CMapStringToOb::RemoveAll.md)|从此映射中移除所有元素。|  
|[CMapStringToOb::RemoveKey](../Topic/CMapStringToOb::RemoveKey.md)|移除项指定的元素。|  
|[CMapStringToOb::SetAt](../Topic/CMapStringToOb::SetAt.md)|将元素插入到映射中;，如果找到，替换现有元素匹配键。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CMapStringToOb::operator](../Topic/CMapStringToOb::operator.md)|将元素插入到映射中— `SetAt`的运算符替换。|  
  
## 备注  
 `CMapStringToString` 合并 `IMPLEMENT_SERIAL` 宏支持序列化和转储其元素。  又序列化每个元素，如果将存储到存档，与重载中插入 \(**\<\<**\) 运算符或与 `Serialize` 成员函数。  
  
 如果需要转储单个 `CString`\-`CString` 元素，则必须将转储上下文的深度为1或更大。  
  
 当 `CMapStringToString` 对象中移除时，或者，如果移除了其元素，`CString` 对象中移除根据需要。  
  
 有关 `CMapStringToString`的更多信息，请参见文章 [集合](../../mfc/collections.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToString`  
  
## 要求  
 **Header:** afxcoll.h  
  
## 请参阅  
 [MFC示例集合](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)