---
title: "CTypedPtrArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTypedPtrArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTypedPtrArray class"
  - "pointer arrays"
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CTypedPtrArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为选件类提供类型安全的“包装” `CPtrArray` 或 `CObArray`对象。  
  
## 语法  
  
```  
template< class BASE_CLASS, class TYPE >  
class CTypedPtrArray : public BASE_CLASS  
```  
  
#### 参数  
 `BASE_CLASS`  
 类型化指针数组选件类的基类;必须为数组选件类\(`CObArray` 或 `CPtrArray`）。  
  
 `TYPE`  
 在基类的数组存储元素的类型。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CTypedPtrArray::Add](../Topic/CTypedPtrArray::Add.md)|添加新元素。数组的末尾。  如果需要，增长数组|  
|[CTypedPtrArray::Append](../Topic/CTypedPtrArray::Append.md)|添加一个数组内容粘贴到另一个的末尾。  如果需要，增长数组|  
|[CTypedPtrArray::Copy](../Topic/CTypedPtrArray::Copy.md)|复制另一个数组传递给数组;如果需要，增长数组。|  
|[CTypedPtrArray::ElementAt](../Topic/CTypedPtrArray::ElementAt.md)|返回临时对数组中的元素指针。|  
|[CTypedPtrArray::GetAt](../Topic/CTypedPtrArray::GetAt.md)|返回值在给定索引。|  
|[CTypedPtrArray::InsertAt](../Topic/CTypedPtrArray::InsertAt.md)|插入元素\(或在其他元素中的所有元素数组\)在指定的索引。|  
|[CTypedPtrArray::SetAt](../Topic/CTypedPtrArray::SetAt.md)|为特定的索引值;不允许的数组增大。|  
|[CTypedPtrArray::SetAtGrow](../Topic/CTypedPtrArray::SetAtGrow.md)|为特定的索引值;如果需要，增长数组。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CTypedPtrArray::operator](../Topic/CTypedPtrArray::operator.md)|设置或获取元素位于指定索引处。|  
  
## 备注  
 当您使用 `CTypedPtrArray` 而不是 `CPtrArray` 或 `CObArray`时，类型检查计算机帮助的C\+\+消除不匹配的指针类型引起的错误。  
  
 此外，`CTypedPtrArray` 包装执行所需的大部分强制转换是否使用了 `CObArray` 或 `CPtrArray`。  
  
 由于所有 `CTypedPtrArray` 函数内联，该模板的使用不显着影响您的代码的大小或速度。  
  
 有关使用 `CTypedPtrArray`的更多信息，请参见位于 [集合](../../mfc/collections.md) 和 [基于模板的选件类](../../mfc/template-based-classes.md)。  
  
## 继承层次结构  
 `BASE_CLASS`  
  
 `CTypedPtrArray`  
  
## 要求  
 **Header:** afxtempl.h  
  
## 请参阅  
 [MFC示例集合](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPtrArray Class](../../mfc/reference/cptrarray-class.md)   
 [CObArray Class](../../mfc/reference/cobarray-class.md)