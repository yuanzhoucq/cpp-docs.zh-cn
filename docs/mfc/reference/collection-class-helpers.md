---
title: "集合类帮助器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes, helper functions
- helper functions collection class
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d2649ef9c8b0320a94ec28a2341baa0f768b07d0
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="collection-class-helpers"></a>集合类帮助器
集合类`CMap`， `CList`，和`CArray`模板化的全局帮助器函数用于比较、 复制和序列化元素等目的。 作为基于类的实现的一部分`CMap`， `CList`，和`CArray`，你必须使用版本适合您的映射、 列表或数组中存储的数据类型重写这些函数根据需要。 如需有关重写帮助器函数如`SerializeElements`，请参阅文章[集合︰ 如何生成类型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。 请注意， **ConstructElements**和**DestructElements**已被弃用。  
  
 Microsoft 基础类库提供了 afxtempl.h 帮助您自定义您的集合类中的以下全局函数︰  
  
### <a name="collection-class-helpers"></a>集合类帮助器  
  
|||  
|-|-|  
|[CompareElements](#compareelements)|指示元素是否相同。|  
|[CopyElements](#copyelements)|将元素从一个数组复制到另一个。|  
|[DumpElements](#dumpelements)|提供面向流的诊断输出。|  
|[HashKey](#hashkey)|计算哈希键。|  
|[SerializeElements](#serializeelements)|将存储或检索到或从存档的元素。|  
  
##  <a name="compareelements"></a>CompareElements  
 直接调用 [CList::Find] (clist class.md #not_found.md #clist__find 和间接[cmap__lookup](cmap-class.md#lookup)和[cmap__operator []](cmap-class.md#operator_at)。  
  
```   
template<class TYPE, class ARG_TYPE>  
BOOL AFXAPI  
CompareElements(
    const TYPE* pElement1,  
    const ARG_TYPE* pElement2);  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 要比较的第一个元素的类型。  
  
 `pElement1`  
 要比较的第一个元素的指针。  
  
 `ARG_TYPE`  
 要进行比较的第二个元素的类型。  
  
 `pElement2`  
 指向要进行比较的第二个元素的指针。  
  
### <a name="return-value"></a>返回值  
 如果指向的对象，则为非`pElement1`等于所指向的对象`pElement2`; 否则为 0。  
  
### <a name="remarks"></a>备注  
 `CMap`调用使用`CMap`模板参数*密钥*和`ARG_KEY`。  
  
 默认实现返回的比较的结果的* \*pElement1*和* \*pElement2*。 重写此函数，以便它将以一种适合于您的应用程序的元素进行比较。  
  
 C + + 语言定义的比较运算符 ( `==`) 对于简单类型 ( `char`， `int`， **float**，依此类推)，但不定义比较运算符中的类和结构。 如果您想要使用`CompareElements`或若要实例化一个使用它的集合类，必须定义比较运算符或重载`CompareElements`版本，返回适当的值。  
  
### <a name="requirements"></a>要求  
   **标头：** afxtempl.h   
  
##  <a name="copyelements"></a>CopyElements  
 调用此函数可直接通过[carray:: Append](carray-class.md#append)和[carray:: Copy](carray-class.md#copy)。  
  
```   
template<class TYPE>  
void AFXAPI CopyElements(
    TYPE* pDest,  
    const TYPE* pSrc,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定要复制的元素类型的模板参数。  
  
 `pDest`  
 指向将复制元素的目标位置。  
  
 `pSrc`  
 指向要复制的元素的源。  
  
 `nCount`  
 要复制的元素的数量。  
  
### <a name="remarks"></a>备注  
 默认实现使用简单的赋值运算符 ( ** = ** ) 来执行复制操作。 如果复制类型没有重载操作符 =，则默认实现将执行按位复制。  
  
 有关实现此函数及其他帮助器函数的信息，请参阅文章[集合︰ 如何生成类型安全集合](../how-to-make-a-type-safe-collection.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxtempl.h  
  
##  <a name="dumpelements"></a>DumpElements  
 在重写时集合的元素提供面向流的文本形式的诊断输出。  
  
```   
template<class TYPE>  
void  AFXAPI DumpElements(
    CDumpContext& dc,  
    const TYPE* pElements,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>参数  
 `dc`  
 转储上下文用于转储元素。  
  
 *类型*  
 指定的元素的类型的模板参数。  
  
 `pElements`  
 指向要转储的元素的指针。  
  
 `nCount`  
 要转储的元素数。  
  
### <a name="remarks"></a>备注  
 **CArray::Dump**， **CList::Dump**，和**CMap::Dump**函数调用此如果转储的深度为大于 0。  
  
 默认实现不执行任何操作。 如果您的集合的元素派生自`CObject`，重写中通常将循环访问集合的元素调用`Dump`中打开每个元素。  
  

### <a name="requirements"></a>要求  
  **标头**afxtempl.h  
  
##  <a name="hashkey"></a>HashKey  
 计算给定键的哈希值。  
  
```  
template<class ARG_KEY>  
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key); 
```  
  
### <a name="parameters"></a>参数  
 `ARG_KEY`  
 指定用来访问的映射键的数据类型的模板参数。  
  
 `key`  
 要计算其哈希值键。  
  
### <a name="return-value"></a>返回值  
 该键的哈希值。  
  
### <a name="remarks"></a>备注  
 调用此函数可直接通过[CMap::RemoveKey](cmap-class.md#removekey)和间接[CMap::Lookup](cmap-class.md#lookup)和[CMap::Operator []](cmap-class.md#operator_at)。
  
 默认实现将创建一个哈希值，通过将转移`key`右旋转四个位置。 重写此函数，从而使其返回哈希值适合于您的应用程序。  
  
### <a name="example"></a>示例
 ```cpp  
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number 
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
 ```
 
### <a name="requirements"></a>要求  
  **标头**afxtempl.h 
  
##  <a name="serializeelements"></a>SerializeElements  
 [CArray](carray-class.md)， [CList](clist-class.md)，和[CMap](cmap-class.md)调用此函数可将元素序列。  
  
```   
template<class TYPE>  
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定的元素的类型的模板参数。  
  
 `ar`  
 存档对象进行存档面向或源自。  
  
 `pElements`  
 指向要存档的元素的指针。  
  
 `nCount`  
 要存档的元素数  
  
### <a name="remarks"></a>备注  
 默认实现未按位读取或写入。  
  
 有关实现此函数及其他帮助器函数的信息，请参阅文章[集合︰ 如何生成类型安全集合](../how-to-make-a-type-safe-collection.md)。  
  
### <a name="example"></a>示例  
 请参阅本文的示例[集合︰ 如何生成类型安全集合](../how-to-make-a-type-safe-collection.md)。  
 
### <a name="requirements"></a>要求  
  **标头**afxtempl.h 
    
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [CMap 类](cmap-class.md)   
 [CList 类](clist-class.md)   
 [CArray 类](carray-class.md)
