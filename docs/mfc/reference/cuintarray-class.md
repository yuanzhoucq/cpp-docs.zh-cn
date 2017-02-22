---
title: "CUIntArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CUIntArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++], 索引的"
  - "CUIntArray class"
  - "indexed arrays"
  - "INT"
  - "UINT"
  - "WORD data type"
ms.assetid: d71f3d8f-ef9f-4e48-9b69-7782c0e2ddf7
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CUIntArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持无符号整数。  
  
## 语法  
  
```  
class CUIntArray : public CObject  
```  
  
## 成员  
 `CUIntArray` 的成员函数类似于选件类 [CObArray](../../mfc/reference/cobarray-class.md)的成员函数。  因此相似性，可以使用 `CObArray` 引用成员函数特定的文档。  无论在何处参见 `CObject` 指针作为函数参数或返回值，请替换 **UINT**。  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 例如，转换  
  
 `UINT CUIntArray::GetAt( int <nIndex> ) const;`  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CObArray::CObArray](../Topic/CObArray::CObArray.md)|构造一个空数组。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CObArray::Add](../Topic/CObArray::Add.md)|将元素添加到数组的结尾;如果需要，增长数组。|  
|[CObArray::Append](../Topic/CObArray::Append.md)|追加另一个数组传递给数组;如果需要，增长数组。|  
|[CObArray::Copy](../Topic/CObArray::Copy.md)|复制另一个数组传递给数组;如果需要，增长数组。|  
|[CObArray::ElementAt](../Topic/CObArray::ElementAt.md)|返回临时对数组中的元素指针。|  
|[CObArray::FreeExtra](../Topic/CObArray::FreeExtra.md)|释放在当前上限的任何未使用的内存。|  
|[CObArray::GetAt](../Topic/CObArray::GetAt.md)|返回值在给定索引。|  
|[CObArray::GetCount](../Topic/CObArray::GetCount.md)|获取元素的数目该数组中的。|  
|[CObArray::GetData](../Topic/CObArray::GetData.md)|允许对组件的访问该数组。  可以是 **NULL**。|  
|[CObArray::GetSize](../Topic/CObArray::GetSize.md)|获取元素的数目该数组中的。|  
|[CObArray::GetUpperBound](../Topic/CObArray::GetUpperBound.md)|返回最大的有效的索引。|  
|[CObArray::InsertAt](../Topic/CObArray::InsertAt.md)|插入元素\(或在其他元素中的所有元素数组\)在指定的索引。|  
|[CObArray::IsEmpty](../Topic/CObArray::IsEmpty.md)|确定数组是否为空。|  
|[CObArray::RemoveAll](../Topic/CObArray::RemoveAll.md)|从此数组中移除所有元素。|  
|[CObArray::RemoveAt](../Topic/CObArray::RemoveAt.md)|移除元素在一个枚举索引。|  
|[CObArray::SetAt](../Topic/CObArray::SetAt.md)|为特定的索引值;不允许的数组增大。|  
|[CObArray::SetAtGrow](../Topic/CObArray::SetAtGrow.md)|为特定的索引值;如果需要，增长数组。|  
|[CObArray::SetSize](../Topic/CObArray::SetSize.md)|设置该数组将包含的元素的数目。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CObArray::operator](../Topic/CObArray::operator.md)|设置或获取元素位于指定索引处。|  
  
## 备注  
 无符号整数或 **UINT**，以单词和双字的不同之处在于 **UINT** 的实际大小可以根据目标运行环境的更改。  **UINT** 大小相同。双字。  
  
 `CUIntArray` 合并 [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md) 宏支持运行时类型访问和转储到 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 对象。  如果需要各个无符号整数元素转储，必须将转储上下文的深度为1或更大。  无法对无符号整数数组。  
  
> [!NOTE]
>  在使用数组之前，请使用 `SetSize` 建立它的大小并将其分配的内存。  如果不使用 `SetSize`，将元素添加到的数组使其最频繁分配和复制。  常见的重新分配和复制是低效的，并且可能产生内存碎片。  
  
 有关使用 `CUIntArray`的更多信息，请参见文章 [集合](../../mfc/collections.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CUIntArray`  
  
## 要求  
 **Header:** afxcoll.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)