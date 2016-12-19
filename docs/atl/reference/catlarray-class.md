---
title: "CAtlArray Class | Microsoft Docs"
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
  - "ATL::CAtlArray"
  - "ATL.CAtlArray"
  - "CAtlArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlArray class"
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现数组对象。  
  
## 语法  
  
```  
  
      template<   
   typename E,  
   class ETraits = CElementTraits< E >   
>  
class CAtlArray  
```  
  
#### 参数  
 *E*  
 在数组中存储的数据类型。  
  
 *ETraits*  
 用于的代码复制或移动元素。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[添加](../Topic/CAtlArray::Add.md)|调用此方法将元素添加到数组对象。|  
|[Append](../Topic/CAtlArray::Append.md)|调用此方法将一个数组内容粘贴到另一个的末尾。|  
|[AssertValid](../Topic/CAtlArray::AssertValid.md)|调用此方法确认数组对象是有效的。|  
|[CAtlArray](../Topic/CAtlArray::CAtlArray.md)|构造函数。|  
|[~CAtlArray](../Topic/CAtlArray::~CAtlArray.md)|该析构函数。|  
|[复制](../Topic/CAtlArray::Copy.md)|调用此方法将一个数组的元素向另一个。|  
|[FreeExtra](../Topic/CAtlArray::FreeExtra.md)|调用此方法从数组中移除所有空元素。|  
|[GetAt](../Topic/CAtlArray::GetAt.md)|调用此方法从数组对象检索一个元素。|  
|[GetCount](../Topic/CAtlArray::GetCount.md)|调用此方法返回该数组存储的元素的数目。|  
|[GetData](../Topic/CAtlArray::GetData.md)|调用此方法返回指向该数组中的第一个元素。|  
|[InsertArrayAt](../Topic/CAtlArray::InsertArrayAt.md)|调用此方法以插入一个数组赋给另一个。|  
|[InsertAt](../Topic/CAtlArray::InsertAt.md)|调用此方法将插入一个新元素\(或组件的多个副本\)到数组对象中。|  
|[IsEmpty](../Topic/CAtlArray::IsEmpty.md)|如果数组为空，则调用此方法测试。|  
|[RemoveAll](../Topic/CAtlArray::RemoveAll.md)|调用此方法从数组对象中移除所有元素。|  
|[RemoveAt](../Topic/CAtlArray::RemoveAt.md)|调用此方法从数组中移除一个或多个元素。|  
|[SetAt](../Topic/CAtlArray::SetAt.md)|调用此方法设置一个元素的值在数组对象的。|  
|[SetAtGrow](../Topic/CAtlArray::SetAtGrow.md)|调用此方法设置一个元素的值在数组对象，展开该数组根据要求。|  
|[SetCount](../Topic/CAtlArray::SetCount.md)|调用此方法设置数组对象的大小。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator &#91;&#93;](../Topic/CAtlArray::operator.md)|调用此运算符返回对数组的元素。|  
  
### Typedef  
  
|||  
|-|-|  
|[INARGTYPE](../Topic/CAtlArray::INARGTYPE.md)|使用的数据类型对于将元素添加到数组。|  
|[OUTARGTYPE](../Topic/CAtlArray::OUTARGTYPE.md)|使用的数据类型对于检索元素从数组。|  
  
## 备注  
 **CAtlArray** 为创建和管理一组方法提供一个用户定义的类型的元素。  虽然类似于标准C数组，**CAtlArray** 对象可以动态缩小且根据需要增大。  数组索引始终是开始在位置0，这样，个上限修复或允许展开，同时新元素添加。  
  
 对于使用少量元素的数组，可使用ATL选件类 [CSimpleArray](../../atl/reference/csimplearray-class.md)。  
  
 **CAtlArray** 是紧密相关。MFC的 **CArray** 选件类，并继续在MFC项目，但不支持序列化。  
  
 有关更多信息，请参见 [ATL集合选件类](../../atl/atl-collection-classes.md)。  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [MMXSwarm示例](../../top/visual-cpp-samples.md)   
 [DynamicConsumer示例](../../top/visual-cpp-samples.md)   
 [UpdatePV示例](../../top/visual-cpp-samples.md)   
 [marquee示例](../../top/visual-cpp-samples.md)   
 [CArray Class](../../mfc/reference/carray-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)