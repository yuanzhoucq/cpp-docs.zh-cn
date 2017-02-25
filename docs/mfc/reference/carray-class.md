---
title: "CArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++], 类"
  - "CArray class"
  - "集合类, template-based"
  - "模板, 集合类"
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 34
---
# CArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持与C数组的数组，但是，可以动态地减少并根据需要增大。  
  
## 语法  
  
```  
template < class TYPE, class ARG_TYPE = const TYPE& >   
class CArray :   
   public CObject  
```  
  
#### 参数  
 `TYPE`  
 指定对象的类型的模板参数数组中存储状态。  `TYPE` 由 `CArray`返回的参数。  
  
 `ARG` *\_* `TYPE`  
 指定参数类型用于访问对象的模板参数数组中存储状态。  通常为 `TYPE`的引用。  `ARG_TYPE` 是传递给 `CArray`的参数。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CArray::CArray](../Topic/CArray::CArray.md)|构造一个空数组。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CArray::Add](../Topic/CArray::Add.md)|将元素添加到数组的结尾;如果需要，增长数组。|  
|[CArray::Append](../Topic/CArray::Append.md)|追加另一个数组传递给数组;如果需要，增长数组|  
|[CArray::Copy](../Topic/CArray::Copy.md)|复制另一个数组传递给数组;如果需要，增长数组。|  
|[CArray::ElementAt](../Topic/CArray::ElementAt.md)|返回临时对数组中的元素指针。|  
|[CArray::FreeExtra](../Topic/CArray::FreeExtra.md)|释放在当前上限的任何未使用的内存。|  
|[CArray::GetAt](../Topic/CArray::GetAt.md)|返回值在给定索引。|  
|[CArray::GetCount](../Topic/CArray::GetCount.md)|获取元素的数目该数组中的。|  
|[CArray::GetData](../Topic/CArray::GetData.md)|允许对组件的访问该数组。  可以是 **NULL**。|  
|[CArray::GetSize](../Topic/CArray::GetSize.md)|获取元素的数目该数组中的。|  
|[CArray::GetUpperBound](../Topic/CArray::GetUpperBound.md)|返回最大的有效的索引。|  
|[CArray::InsertAt](../Topic/CArray::InsertAt.md)|插入元素\(或在其他元素中的所有元素数组\)在指定的索引。|  
|[CArray::IsEmpty](../Topic/CArray::IsEmpty.md)|确定数组是否为空。|  
|[CArray::RemoveAll](../Topic/CArray::RemoveAll.md)|从此数组中移除所有元素。|  
|[CArray::RemoveAt](../Topic/CArray::RemoveAt.md)|移除元素在一个枚举索引。|  
|[CArray::SetAt](../Topic/CArray::SetAt.md)|为特定的索引值;不允许的数组增大。|  
|[CArray::SetAtGrow](../Topic/CArray::SetAtGrow.md)|为特定的索引值;如果需要，增长数组。|  
|[CArray::SetSize](../Topic/CArray::SetSize.md)|设置该数组将包含的元素的数目。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CArray::operator](../Topic/CArray::operator.md)|设置或获取元素位于指定索引处。|  
  
## 备注  
 数组索引始终是开始在位置0。  当添加通过当前区域时，的元素是否可以决定修复了上限或使该数组展开。  连续内存分配给上限，因此，即使某些元素为空。  
  
> [!NOTE]
>  调整 `CArray` 对象或将元素添加到它使用 [memcpy\_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) 到移动元素的大多数方法。  这是问题，因为 `memcpy_s` 不是使用需要构造函数调用的任何对象交互操作。  如果在 `CArray` 的项是不与 `memcpy_s`CLS，则必须创建适当的范围的新 `CArray`。  因为这些方法使用赋值运算符\(而不是 `memcpy_s`，然后必须使用 [CArray::Copy](../Topic/CArray::Copy.md) 和 [CArray::SetAt](../Topic/CArray::SetAt.md) 填充新数组。  
  
 具有c.数组，`CArray` 索引的元素的访问时间是常数是数组大小无关。  
  
> [!TIP]
>  在使用数组之前，请使用 [SetSize](../Topic/CArray::SetSize.md) 建立它的大小并将其分配的内存。  如果不使用 `SetSize`，将元素添加到的数组使其最频繁分配和复制。  常见的重新分配和复制是低效的，并且可能产生内存碎片。  
  
 如果在数组需要各个元素转储，必须设置 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 对象的深度为1或更大。  
  
 此选件类的某些成员函数调用必须自定义为 `CArray` 选件类的大多数使用的全局helper函数。  参见MFC宏和Globals节中的主题 [集合选件帮助器类](../../mfc/reference/collection-class-helpers.md)。  
  
 数组选件类派生象列表派生。  
  
 有关如何使用 `CArray`的更多信息，请参见文章 [集合](../../mfc/collections.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CArray`  
  
## 要求  
 `Header:` afxtempl.h  
  
## 请参阅  
 [MFC示例集合](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CObArray Class](../../mfc/reference/cobarray-class.md)   
 [集合类帮助器](../../mfc/reference/collection-class-helpers.md)