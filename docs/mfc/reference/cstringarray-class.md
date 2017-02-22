---
title: "CStringArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStringArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++], 字符串"
  - "CStringArray class"
  - "string arrays"
  - "字符串 [C++], 集合"
ms.assetid: 6c637e06-bba8-4c08-b0fc-cf8cb067ce34
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CStringArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持 [CString](../../atl-mfc-shared/using-cstring.md) 对象数组。  
  
## 语法  
  
```  
class CStringArray : public CObject  
```  
  
## Members  
 `CStringArray` 的成员函数类似于类 [CObArray](../../mfc/reference/cobarray-class.md) 的成员函数。  由于此相似性，因此你可以使用 `CObArray` 参考文档获取成员函数细节。  无论你在何处看到作为返回值的 `CObject` 指针，都请替换 [CString](../../atl-mfc-shared/using-cstring.md) 对象（而非 [CString](../../atl-mfc-shared/using-cstring.md) 指针）。  无论你在何处看到作为函数参数的 `CObject` 指针，都请替换 `LPCTSTR`。  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 例如，转换为  
  
 `CString CStringArray::GetAt( int <nIndex> ) const;`  
  
 和  
  
 `void SetAt( int <nIndex>, CObject* <newElement> )`  
  
 转换为  
  
 `void SetAt( int <nIndex>, LPCTSTR <newElement> )`  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CObArray::CObArray](../Topic/CObArray::CObArray.md)|构造一个空数组。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CObArray::Add](../Topic/CObArray::Add.md)|向数组的末尾添加一个元素；根据需要扩展该数组。|  
|[CObArray::Append](../Topic/CObArray::Append.md)|将另一个数组追加到该数组中；根据需要扩展该数组。|  
|[CObArray::Copy](../Topic/CObArray::Copy.md)|将另一个数组复制到该数组；根据需要扩展该数组。|  
|[CObArray::ElementAt](../Topic/CObArray::ElementAt.md)|在该数组中返回对元素指针的临时引用。|  
|[CObArray::FreeExtra](../Topic/CObArray::FreeExtra.md)|若高于当前的上限，则将释放所有未使用的内存。|  
|[CObArray::GetAt](../Topic/CObArray::GetAt.md)|返回给定索引位置处的值。|  
|[CObArray::GetCount](../Topic/CObArray::GetCount.md)|获取此数组中的元素数。|  
|[CObArray::GetData](../Topic/CObArray::GetData.md)|允许访问该数组中的元素。  可以为 **NULL**。|  
|[CObArray::GetSize](../Topic/CObArray::GetSize.md)|获取此数组中的元素数。|  
|[CObArray::GetUpperBound](../Topic/CObArray::GetUpperBound.md)|返回最大的有效索引。|  
|[CObArray::InsertAt](../Topic/CObArray::InsertAt.md)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|  
|[CObArray::IsEmpty](../Topic/CObArray::IsEmpty.md)|确定数组是否为空。|  
|[CObArray::RemoveAll](../Topic/CObArray::RemoveAll.md)|从此数组中移除所有元素。|  
|[CObArray::RemoveAt](../Topic/CObArray::RemoveAt.md)|移除特定索引处的元素。|  
|[CObArray::SetAt](../Topic/CObArray::SetAt.md)|设置给定索引的值；不允许对该数组进行扩展。|  
|[CObArray::SetAtGrow](../Topic/CObArray::SetAtGrow.md)|设置给定索引的值；根据需要扩展该数组。|  
|[CObArray::SetSize](../Topic/CObArray::SetSize.md)|设置要在该数组中包含的元素数。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[CObArray::operator](../Topic/CObArray::operator.md)|设置或获取位于指定索引处的元素。|  
  
## 备注  
 `CStringArray` 包括用于支持其元素序列化和转储的 `IMPLEMENT_SERIAL` 宏。  如果将 `CString` 对象的数组存储到存档中（使用重载插入运算符或 `Serialize` 成员函数），则将依次序列化每个元素。  
  
> [!NOTE]
>  在使用数组之前，先使用 `SetSize` 建立其大小并为其分配内存。  如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。  经常重新分配和复制会降低效率而且会产生内存碎片。  
  
 如果你需要对数组中单个字符串元素进行转储，则必须将转储上下文的深度设置为等于或大于 1。  
  
 当删除 `CString` 数组或移除其元素时，将以适当方式释放字符串内存。  
  
 有关使用 `CStringArray` 的详细信息，请参阅文章[集合](../../mfc/collections.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringArray`  
  
## 要求  
 **标头：**afxcoll.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)