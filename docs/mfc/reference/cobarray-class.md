---
title: "CObArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CObArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++], 对象类型"
  - "数组 [C++], 指针"
  - "CObArray class"
  - "对象数组, CObArray class"
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CObArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持某些 `CObject` 指针。  
  
## 语法  
  
```  
class CObArray : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CObArray::CObArray](../Topic/CObArray::CObArray.md)|构造 `CObject` 指针的空数组。|  
  
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
 这些对象数组类似于C数组，但是，它们可以动态缩小且根据需要增大。  
  
 数组索引始终是开始在位置0。  当添加通过当前区域时，的元素是否可以决定修复了上限或允许数组展开。  连续内存分配给上限，因此，即使某些元素为空。  
  
 在Win32下，`CObArray` 对象的范围仅限于可用内存。  
  
 具有c.数组，`CObArray` 索引的元素的访问时间是常数是数组大小无关。  
  
 `CObArray` 合并 `IMPLEMENT_SERIAL` 宏支持序列化和转储其元素。  如果数组 `CObject` 指针存储到存档，与重载、运算符或与 `Serialize` 成员函数，每个 `CObject` 元素与其数组索引。，反过来，序列化。  
  
 如果在数组需要各个 `CObject` 元素转储，必须设置 `CDumpContext` 对象的深度为1或更大。  
  
 当 `CObArray` 对象被删除，或者，如果移除元素，因此，只有这些引用移除的 `CObject` 指针，而不是对象。  
  
> [!NOTE]
>  在使用数组之前，请使用 `SetSize` 建立它的大小并将其分配的内存。  如果不使用 `SetSize`，将元素添加到的数组使其最频繁分配和复制。  常见的重新分配和复制是低效的，并且可能产生内存碎片。  
  
 数组选件类派生类似的列表派生。  有关在派生的详细信息私有列表选件类，请参见一 [集合](../../mfc/collections.md)文章。  
  
> [!NOTE]
>  因此，如果您希望序列化数组，已在派生类中实现必须使用 `IMPLEMENT_SERIAL` 宏。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObArray`  
  
## 要求  
 **Header:** afxcoll.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CStringArray Class](../../mfc/reference/cstringarray-class.md)   
 [CPtrArray Class](../../mfc/reference/cptrarray-class.md)   
 [CByteArray Class](../../mfc/reference/cbytearray-class.md)   
 [CWordArray Class](../../mfc/reference/cwordarray-class.md)   
 [CDWordArray Class](../../mfc/reference/cdwordarray-class.md)