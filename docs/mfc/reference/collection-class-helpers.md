---
title: 集合类帮助器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6607f70a18734310d184c5cdd05d1e87f1b82d35
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852332"
---
# <a name="collection-class-helpers"></a>集合类帮助器
集合类`CMap`， `CList`，和`CArray`模板化的全局帮助器函数用于比较、 复制和序列化元素作为此类目的。 作为基于类的实现的一部分`CMap`， `CList`，和`CArray`，必须使用版本适用于地图、 列表或数组中存储的数据类型重写这些函数根据需要。 有关信息，如重写帮助器函数`SerializeElements`，请参阅文章[集合： 如何创建类型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。 请注意，`ConstructElements`和`DestructElements`已弃用。  
  
 Microsoft 基础类库提供了 afxtempl.h 以帮助您自定义集合类中的以下全局函数：  
  
### <a name="collection-class-helpers"></a>集合类帮助器  
  
|||  
|-|-|  
|[CompareElements](#compareelements)|指示元素是否相同。|  
|[CopyElements](#copyelements)|将元素从一个数组复制到另一个。|  
|[DumpElements](#dumpelements)|提供面向流的诊断输出。|  
|[HashKey](#hashkey)|计算哈希键。|  
|[SerializeElements](#serializeelements)|将存储或检索到或从存档的元素。|  
  
##  <a name="compareelements"></a>  CompareElements  
 直接调用 [CList::Find] (clist class.md #not_found.md #clist__find 和间接[cmap__lookup](cmap-class.md#lookup)并[cmap__operator &#91; &#93; ](cmap-class.md#operator_at)。  
  
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
  
 *pElement1*  
 要比较的第一个元素的指针。  
  
 *ARG_TYPE*  
 要进行比较的第二个元素的类型。  
  
 *pElement2*  
 指向要进行比较的第二个元素的指针。  
  
### <a name="return-value"></a>返回值  
 如果指向的对象的非零*pElement1*是否与指向的对象相等*pElement2*; 否则为 0。  
  
### <a name="remarks"></a>备注  
 `CMap`调用使用`CMap`模板参数*密钥*并*ARG_KEY*。  
  
 默认实现返回的比较的结果 *\*pElement1*并 *\*pElement2*。 重写此函数，以便它将一种方法适合于你的应用程序中的元素进行比较。  
  
 C + + 语言定义比较运算符 ( `==`) 的简单类型 (**char**， **int**， **float**，依此类推)，但不定义比较运算符类和结构。 如果你想要使用`CompareElements`或若要实例化一个使用它的集合类，必须定义比较运算符或重载`CompareElements`返回适当的值的版本。  
  
### <a name="requirements"></a>要求  
   **标头：** afxtempl.h   
  
##  <a name="copyelements"></a>  CopyElements  
 调用此函数可直接通过[carray:: Append](carray-class.md#append)并[carray:: Copy](carray-class.md#copy)。  
  
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
  
 *pDest*  
 指向将复制元素的目标位置。  
  
 *pSrc*  
 指向要复制的元素的源。  
  
 *nCount*  
 要复制的元素的数量。  
  
### <a name="remarks"></a>备注  
 默认实现使用简单的赋值运算符 ( **=** ) 执行复制操作。 如果复制类型没有重载操作符 =，则默认实现将执行按位复制。  
  
 有关实现此函数及其他帮助器函数的信息，请参阅文章[集合： 如何创建类型安全集合](../how-to-make-a-type-safe-collection.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxtempl.h  
  
##  <a name="dumpelements"></a>  DumpElements  
 元素的集合中重写时，提供了面向流的文本形式的诊断输出。  
  
```   
template<class TYPE>  
void  AFXAPI DumpElements(
    CDumpContext& dc,  
    const TYPE* pElements,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>参数  
 *dc*  
 转储转储元素的上下文。  
  
 *类型*  
 指定的元素的类型的模板参数。  
  
 *pElements*  
 指向要转储的元素的指针。  
  
 *nCount*  
 要转储的元素数。  
  
### <a name="remarks"></a>备注  
 `CArray::Dump`， `CList::Dump`，和`CMap::Dump`函数调用此如果转储的深度大于 0。  
  
 默认实现不执行任何操作。 如果在集合中的元素派生自`CObject`，重写将通常循环访问集合的元素，调用`Dump`中打开每个元素。  
  

### <a name="requirements"></a>要求  
  **标头**afxtempl.h  
  
##  <a name="hashkey"></a>  HashKey  
 计算给定键的哈希值。  
  
```  
template<class ARG_KEY>  
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key); 
```  
  
### <a name="parameters"></a>参数  
 *ARG_KEY*  
 指定用于访问映射键的数据类型的模板参数。  
  
 *key*  
 将计算其哈希值的键。  
  
### <a name="return-value"></a>返回值  
 键的哈希值。  
  
### <a name="remarks"></a>备注  
 调用此函数可直接通过[CMap::RemoveKey](cmap-class.md#removekey)和间接[CMap::Lookup](cmap-class.md#lookup)并[CMap::Operator &#91; &#93; ](cmap-class.md#operator_at)。
  
 默认实现通过转换将创建一个哈希值*密钥*右按四个位置。 重写此函数，以便其返回哈希值适用于你的应用程序。  
  
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
  
##  <a name="serializeelements"></a>  SerializeElements  
 [CArray](carray-class.md)， [CList](clist-class.md)，和[CMap](cmap-class.md)调用此函数可序列化元素。  
  
```   
template<class TYPE>  
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定的元素的类型的模板参数。  
  
 *ar*  
 若要存档或从存档对象。  
  
 *pElements*  
 指向要存档的元素的指针。  
  
 *nCount*  
 要存档的元素数  
  
### <a name="remarks"></a>备注  
 默认实现 does 的按位读取或写入。  
  
 有关实现此函数及其他帮助器函数的信息，请参阅文章[集合： 如何创建类型安全集合](../how-to-make-a-type-safe-collection.md)。  
  
### <a name="example"></a>示例  
 请参阅文章中的示例[集合： 如何创建类型安全集合](../how-to-make-a-type-safe-collection.md)。  
 
### <a name="requirements"></a>要求  
  **标头**afxtempl.h 
    
## <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [CMap 类](cmap-class.md)   
 [CList 类](clist-class.md)   
 [CArray 类](carray-class.md)