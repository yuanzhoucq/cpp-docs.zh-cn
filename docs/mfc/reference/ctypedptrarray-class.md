---
title: CTypedPtrArray 类
ms.date: 11/04/2016
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
ms.openlocfilehash: da31f6eef95364ad010d9c9aeb19225d42a42283
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452320"
---
# <a name="ctypedptrarray-class"></a>CTypedPtrArray 类

为 `CPtrArray` 类或 `CObArray`类的对象提供安全类型“包装器”。

## <a name="syntax"></a>语法

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>参数

*BASE_CLASS*<br/>
基的类的类型化的指针数组;必须为数组类 (`CObArray`或`CPtrArray`)。

*类型*<br/>
存储基类数组中的元素的类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CTypedPtrArray::Add](#add)|将新元素添加到数组的末尾。 如有必要，扩展该数组|
|[CTypedPtrArray::Append](#append)|将一个数组的内容添加到另一个结束。 如有必要，扩展该数组|
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

当你使用`CTypedPtrArray`而非`CPtrArray`或`CObArray`，c + + 类型检查功能可帮助消除错误引起的不匹配的指针类型。

此外，`CTypedPtrArray`包装执行大量的强制转换，如果您使用，则将需要`CObArray`或`CPtrArray`。

因为所有`CTypedPtrArray`函数是内联的使用此模板不会严重影响的大小或代码的速度。

有关使用的详细信息`CTypedPtrArray`，请参阅文章[集合](../../mfc/collections.md)并[基于模板的类](../../mfc/template-based-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

##  <a name="add"></a>  CTypedPtrArray::Add

此成员函数将调用`BASE_CLASS` **:: 添加**。

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>参数

*类型*<br/>
指定要添加到数组元素类型模板参数。

*newElement*<br/>
要添加到该数组的元素。

### <a name="return-value"></a>返回值

添加的元素的索引。

### <a name="remarks"></a>备注

有关更多详细说明，请参阅[CObArray::Add](../../mfc/reference/cobarray-class.md#add)。

##  <a name="append"></a>  CTypedPtrArray::Append

此成员函数调用`BASE_CLASS`:: Append * *。

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>参数

*BASE_CLASS*<br/>
基的类的类型化的指针数组;必须为数组类 ( [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md))。

*类型*<br/>
存储基类数组中的元素的类型。

*src*<br/>
要追加到数组的元素的源。

### <a name="return-value"></a>返回值

第一个追加的元素的索引。

### <a name="remarks"></a>备注

有关更多详细说明，请参阅[CObArray::Append](../../mfc/reference/cobarray-class.md#append)。

##  <a name="copy"></a>  CTypedPtrArray::Copy

此成员函数将调用`BASE_CLASS` **:: 复制**。

```
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>参数

*BASE_CLASS*<br/>
基的类的类型化的指针数组;必须为数组类 ( [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md))。

*类型*<br/>
存储基类数组中的元素的类型。

*src*<br/>
要复制到数组的元素的源。

### <a name="remarks"></a>备注

有关更多详细说明，请参阅[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)。

##  <a name="elementat"></a>  CTypedPtrArray::ElementAt

此内联函数将调用`BASE_CLASS` **:: ElementAt**。

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>参数

*类型*<br/>
指定此数组中存储的元素类型模板参数。

*nIndex*<br/>
大于或等于 0 的整数索引且小于或等于返回的值`BASE_CLASS` **:: GetUpperBound**。

### <a name="return-value"></a>返回值

对指定的位置处的元素的临时引用*nIndex*。 此元素是模板参数指定的类型的*类型*。

### <a name="remarks"></a>备注

有关更多详细说明，请参阅[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)。

##  <a name="getat"></a>  CTypedPtrArray::GetAt

此内联函数将调用`BASE_CLASS` **:: GetAt**。

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定数组中存储的元素类型模板参数。

*nIndex*<br/>
大于或等于 0 的整数索引且小于或等于返回的值`BASE_CLASS` **:: GetUpperBound**。

### <a name="return-value"></a>返回值

指定的位置处的元素的副本*nIndex*。 此元素是模板参数指定的类型的*类型*。

### <a name="remarks"></a>备注

有关更多详细说明，请参阅[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)

##  <a name="insertat"></a>  CTypedPtrArray::InsertAt

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

*nIndex*<br/>
可能会高于返回的值的整数索引[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。

*类型*<br/>
存储基类数组中的元素的类型。

*newElement*<br/>
要放置此数组中的对象指针。 一个*newElement*的值**NULL**允许。

*nCount*<br/>
此元素应为次数插入 （默认值为 1）。

*nStartIndex*<br/>
可能会高于返回的值的整数索引`CObArray::GetUpperBound`。

*BASE_CLASS*<br/>
基的类的类型化的指针数组;必须为数组类 ( [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md))。

*pNewArray*<br/>
另一个数组，其中包含要添加到该数组的元素。

### <a name="remarks"></a>备注

有关更多详细说明，请参阅[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)。

##  <a name="operator_at"></a>  CTypedPtrArray::operator]

这些内联运算符调用`BASE_CLASS` **:: 运算符 []**。

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定数组中存储的元素类型模板参数。

*nIndex*<br/>
大于或等于 0 的整数索引且小于或等于返回的值`BASE_CLASS` **:: GetUpperBound**。

### <a name="remarks"></a>备注

第一个运算符为数组不是调用**const**，可以在右侧 （右值） 或赋值语句左侧 （左值） 上使用。 第二个，为调用**const**数组，可以使用仅在右侧。

在库的调试版本断言的下标 （无论在左侧或右侧的赋值语句） 是否超出界限。

##  <a name="setat"></a>  CTypedPtrArray::SetAt

此成员函数将调用`BASE_CLASS` **:: SetAt**。

```
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 的整数索引且小于或等于返回的值[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。

*类型*<br/>
存储基类数组中的元素的类型。

*ptr*<br/>
指向要插入 nIndex 在数组中的元素的指针。 允许 NULL 值。

### <a name="remarks"></a>备注

有关更多详细说明，请参阅[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)。

##  <a name="setatgrow"></a>  CTypedPtrArray::SetAtGrow

此成员函数将调用`BASE_CLASS` **:: SetAtGrow**。

```
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
一个大于或等于 0 的整数索引。

*类型*<br/>
存储基类数组中的元素的类型。

*newElement*<br/>
要添加到该数组的对象指针。 一个**NULL**允许值。

### <a name="remarks"></a>备注

有关更多详细说明，请参阅[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)。

## <a name="see-also"></a>请参阅

[MFC 示例收集](../../visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray 类](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray 类](../../mfc/reference/cobarray-class.md)
