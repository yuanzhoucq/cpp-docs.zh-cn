---
title: "COleSafeArray Class | Microsoft Docs"
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
  - "COleSafeArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++], safe"
  - "COleSafeArray class"
  - "ODBC, safe arrays"
  - "safe arrays"
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleSafeArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

的选件类与任意类型和维度一起使用。  
  
## 语法  
  
```  
class COleSafeArray : public tagVARIANT  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleSafeArray::COleSafeArray](../Topic/COleSafeArray::COleSafeArray.md)|构造 `COleSafeArray` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleSafeArray::AccessData](../Topic/COleSafeArray::AccessData.md)|检索指向数组数据。|  
|[COleSafeArray::AllocData](../Topic/COleSafeArray::AllocData.md)|为该数组分配内存。|  
|[COleSafeArray::AllocDescriptor](../Topic/COleSafeArray::AllocDescriptor.md)|分配安全数组描述符的内存。|  
|[COleSafeArray::Attach](../Topic/COleSafeArray::Attach.md)|为现有 **VARIANT** 数组的控件 `COleSafeArray` 对象。|  
|[COleSafeArray::Clear](../Topic/COleSafeArray::Clear.md)|释放在基础 **VARIANT**的所有数据。|  
|[COleSafeArray::Copy](../Topic/COleSafeArray::Copy.md)|创建现有数组的副本。|  
|[COleSafeArray::Create](../Topic/COleSafeArray::Create.md)|创建一个安全数组。|  
|[COleSafeArray::CreateOneDim](../Topic/COleSafeArray::CreateOneDim.md)|创建一个一维 `COleSafeArray` 对象。|  
|[COleSafeArray::Destroy](../Topic/COleSafeArray::Destroy.md)|销毁现有数组。|  
|[COleSafeArray::DestroyData](../Topic/COleSafeArray::DestroyData.md)|销毁在安全数组的数据。|  
|[COleSafeArray::DestroyDescriptor](../Topic/COleSafeArray::DestroyDescriptor.md)|销毁一个安全数组的类型描述符。|  
|[COleSafeArray::Detach](../Topic/COleSafeArray::Detach.md)|分离 `COleSafeArray` 对象的 **VARIANT** 数组\(以便数据不会释放）。|  
|[COleSafeArray::GetByteArray](../Topic/COleSafeArray::GetByteArray.md)|复制安全数组的内容。[CByteArray](../../mfc/reference/cbytearray-class.md)。|  
|[COleSafeArray::GetDim](../Topic/COleSafeArray::GetDim.md)|返回中的维数。数组的。|  
|[COleSafeArray::GetElement](../Topic/COleSafeArray::GetElement.md)|检索安全数组的一个元素。|  
|[COleSafeArray::GetElemSize](../Topic/COleSafeArray::GetElemSize.md)|返回的大小，以字节为单位\)，在一个安全数组的元素。|  
|[COleSafeArray::GetLBound](../Topic/COleSafeArray::GetLBound.md)|返回一个安全数组的所有维度的下限。|  
|[COleSafeArray::GetOneDimSize](../Topic/COleSafeArray::GetOneDimSize.md)|返回元素数对一维 `COleSafeArray` 对象的。|  
|[COleSafeArray::GetUBound](../Topic/COleSafeArray::GetUBound.md)|返回一个安全数组的所有维度的上限。|  
|[COleSafeArray::Lock](../Topic/COleSafeArray::Lock.md)|增加数组的锁计数并将指向数组数据在数组描述符。|  
|[COleSafeArray::PtrOfIndex](../Topic/COleSafeArray::PtrOfIndex.md)|返回指向该索引的元素。|  
|[COleSafeArray::PutElement](../Topic/COleSafeArray::PutElement.md)|将一个元素为数组。|  
|[COleSafeArray::Redim](../Topic/COleSafeArray::Redim.md)|更改最不重要\(最右侧\)限制为安全数组。|  
|[COleSafeArray::ResizeOneDim](../Topic/COleSafeArray::ResizeOneDim.md)|更改元素数在一个一维 `COleSafeArray` 对象的。|  
|[COleSafeArray::UnaccessData](../Topic/COleSafeArray::UnaccessData.md)|递减数组的锁计数和无效 `AccessData`检索的指针。|  
|[COleSafeArray::Unlock](../Topic/COleSafeArray::Unlock.md)|递减数组的锁计数，从而可将其释放或调整其大小。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[COleSafeArray::operator LPCVARIANT](../Topic/COleSafeArray::operator%20LPCVARIANT.md)|访问 `COleSafeArray` 对象的基础 **VARIANT** 结构。|  
|[COleSafeArray::operator LPVARIANT](../Topic/COleSafeArray::operator%20LPVARIANT.md)|访问 `COleSafeArray` 对象的基础 **VARIANT** 结构。|  
|[COleSafeArray::operator \=](../Topic/COleSafeArray::operator%20=.md)|将值复制到 `COleSafeArray` 对象\(**SAFEARRAY**、 **VARIANT**、 `COleVariant`或 `COleSafeArray` 数组\)中。|  
|[COleSafeArray::operator \=\=](../Topic/COleSafeArray::operator%20==.md)|比较两个不同的数组\(**SAFEARRAY**、 **VARIANT**、 `COleVariant`或 `COleSafeArray` 数组）。|  
|[COleSafeArray::operator \<\<](../Topic/COleSafeArray::operator%20%3C%3C.md)|输出一 `COleSafeArray` 对象的内容转储上下文。|  
  
## 备注  
 `COleSafeArray` 从OLE **VARIANT** 不要求。  OLE **SAFEARRAY** 成员函数通过 `COleSafeArray`，以及可用设置专门设计的成员函数对一维字节。  
  
## 继承层次结构  
 `tagVARIANT`  
  
 `COleSafeArray`  
  
## 要求  
 **Header:** afxdisp.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)