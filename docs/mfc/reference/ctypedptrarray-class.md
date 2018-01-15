---
title: "CTypedPtrArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
dev_langs: C++
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e08749341bd7865c89e397e36aeff3a6ccc0d71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ctypedptrarray-class"></a>CTypedPtrArray 类
为 `CPtrArray` 类或 `CObArray`类的对象提供安全类型“包装器”。  
  
## <a name="syntax"></a>语法  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrArray : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>参数  
 `BASE_CLASS`  
 类的基类类型化的指针数组;必须为数组类 (`CObArray`或`CPtrArray`)。  
  
 `TYPE`  
 基类数组中存储的元素的类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CTypedPtrArray::Add](#add)|将新元素添加到数组末尾。 如有必要，请扩展该数组|  
|[CTypedPtrArray::Append](#append)|另一个的末尾添加一个数组的内容。 如有必要，请扩展该数组|  
|[CTypedPtrArray::Copy](#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|  
|[CTypedPtrArray::ElementAt](#elementat)|在该数组中返回对元素指针的临时引用。|  
|[CTypedPtrArray::GetAt](#getat)|返回给定索引位置处的值。|  
|[CTypedPtrArray::InsertAt](#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|  
|[CTypedPtrArray::SetAt](#setat)|设置给定索引的值；不允许对该数组进行扩展。|  
|[CTypedPtrArray::SetAtGrow](#setatgrow)|设置给定索引的值；根据需要扩展该数组。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CTypedPtrArray::operator]](#operator_at)|设置或获取位于指定索引处的元素。|  
  
## <a name="remarks"></a>备注  
 当你使用`CTypedPtrArray`而非`CPtrArray`或`CObArray`，c + + 类型检查工具可帮助消除错误引起的不匹配的指针类型。  
  
 此外，`CTypedPtrArray`包装执行大量如果你使用所需的强制转换`CObArray`或`CPtrArray`。  
  
 因为所有`CTypedPtrArray`函数内联，使用此模板不会显著影响大小或代码的速度。  
  
 有关详细信息使用`CTypedPtrArray`，请参阅文章[集合](../../mfc/collections.md)和[基于模板的类](../../mfc/template-based-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `BASE_CLASS`  
  
 `CTypedPtrArray`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxtempl.h  
  
##  <a name="add"></a>CTypedPtrArray::Add  
 此成员函数将调用`BASE_CLASS` **:: 添加**。  
  
```  
INT_PTR Add(TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数来指定要添加到数组的元素的类型。  
  
 `newElement`  
 要添加到该数组的元素。  
  
### <a name="return-value"></a>返回值  
 添加元素的索引。  
  
### <a name="remarks"></a>备注  
 有关详细说明，请参阅[CObArray::Add](../../mfc/reference/cobarray-class.md#add)。  
  
##  <a name="append"></a>CTypedPtrArray::Append  
 此成员函数将调用`BASE_CLASS` **:: 追加**。  
  
```  
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>参数  
 `BASE_CLASS`  
 类的基类类型化的指针数组;必须为数组类 ( [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md))。  
  
 *类型*  
 基类数组中存储的元素的类型。  
  
 *src*  
 要追加到一个数组的元素的源。  
  
### <a name="return-value"></a>返回值  
 第一个追加的元素的索引。  
  
### <a name="remarks"></a>备注  
 有关详细说明，请参阅[CObArray::Append](../../mfc/reference/cobarray-class.md#append)。  
  
##  <a name="copy"></a>CTypedPtrArray::Copy  
 此成员函数将调用`BASE_CLASS` **:: 复制**。  
  
```  
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>参数  
 `BASE_CLASS`  
 类的基类类型化的指针数组;必须为数组类 ( [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md))。  
  
 *类型*  
 基类数组中存储的元素的类型。  
  
 *src*  
 要复制到数组的元素的源。  
  
### <a name="remarks"></a>备注  
 有关详细说明，请参阅[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)。  
  
##  <a name="elementat"></a>CTypedPtrArray::ElementAt  
 此内联函数调用`BASE_CLASS` **:: ElementAt**。  
  
```  
TYPE& ElementAt(INT_PTR nIndex);
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数来指定存储在此数组中元素的类型。  
  
 `nIndex`  
 整数索引大于或等于 0 且小于或等于返回的值`BASE_CLASS` **:: GetUpperBound**。  
  
### <a name="return-value"></a>返回值  
 对指定的位置处的元素的临时引用`nIndex`。 此元素是由模板参数指定的类型*类型*。  
  
### <a name="remarks"></a>备注  
 有关详细说明，请参阅[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)。  
  
##  <a name="getat"></a>CTypedPtrArray::GetAt  
 此内联函数调用`BASE_CLASS` **:: GetAt**。  
  
```  
TYPE GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数来指定存储在数组中元素的类型。  
  
 `nIndex`  
 整数索引大于或等于 0 且小于或等于返回的值`BASE_CLASS` **:: GetUpperBound**。  
  
### <a name="return-value"></a>返回值  
 指定的位置处的元素的副本`nIndex`。 此元素是由模板参数指定的类型*类型*。  
  
### <a name="remarks"></a>备注  
 有关详细说明，请参阅[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)  
  
##  <a name="insertat"></a>CTypedPtrArray::InsertAt  
 此成员函数将调用`BASE_CLASS` **:: InsertAt**。  
  
```  
void InsertAt(
    INT_PTR nIndex,  
    TYPE newElement,  
    INT_PTR nCount = 1);

 
void InsertAt(
    INT_PTR nStartIndex,  
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 可能返回的值大于整数索引[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。  
  
 *类型*  
 基类数组中存储的元素的类型。  
  
 `newElement`  
 要放置此数组中的对象指针。 A`newElement`的值**NULL**允许。  
  
 `nCount`  
 此元素应为次数插入 （默认为 1）。  
  
 `nStartIndex`  
 可能返回的值大于整数索引`CObArray::GetUpperBound`。  
  
 `BASE_CLASS`  
 类的基类类型化的指针数组;必须为数组类 ( [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md))。  
  
 `pNewArray`  
 包含要添加到该数组的元素的另一个数组。  
  
### <a name="remarks"></a>备注  
 有关详细说明，请参阅[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)。  
  
##  <a name="operator_at"></a>CTypedPtrArray::operator]  
 这些内联运算符调用`BASE_CLASS` **:: 运算符 []**。  
  
```  
TYPE& operator[ ](int_ptr nindex);  
TYPE operator[ ](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数来指定存储在数组中元素的类型。  
  
 `nIndex`  
 整数索引大于或等于 0 且小于或等于返回的值`BASE_CLASS` **:: GetUpperBound**。  
  
### <a name="remarks"></a>备注  
 第一个运算符，为不数组调用**const**，可在右侧 （右值） 或赋值语句的左侧 （左值）。 第二个，为调用**const**数组，可以使用仅在右侧。  
  
 库的调试版本断言下标 （或者在左侧或赋值语句右侧） 是否超出界限。  
  
##  <a name="setat"></a>CTypedPtrArray::SetAt  
 此成员函数将调用`BASE_CLASS` **:: SetAt**。  
  
```  
void SetAt(
    INT_PTR nIndex,  
    TYPE ptr);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 整数索引大于或等于 0 且小于或等于返回的值[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。  
  
 *类型*  
 基类数组中存储的元素的类型。  
  
 *ptr*  
 指向数组中的位置 nIndex 插入的元素的指针。 允许 NULL 值。  
  
### <a name="remarks"></a>备注  
 有关详细说明，请参阅[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)。  
  
##  <a name="setatgrow"></a>CTypedPtrArray::SetAtGrow  
 此成员函数将调用`BASE_CLASS` **:: SetAtGrow**。  
  
```  
void SetAtGrow(
    INT_PTR nIndex,  
    TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 大于或等于 0 的整数索引。  
  
 *类型*  
 基类数组中存储的元素的类型。  
  
 `newElement`  
 要添加到该数组的对象指针。 A **NULL**允许值。  
  
### <a name="remarks"></a>备注  
 有关详细说明，请参阅[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例收集](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPtrArray 类](../../mfc/reference/cptrarray-class.md)   
 [CObArray 类](../../mfc/reference/cobarray-class.md)
