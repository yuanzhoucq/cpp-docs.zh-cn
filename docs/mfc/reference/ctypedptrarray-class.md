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
ms.openlocfilehash: db24e3992e5db70895ccc2908dba108de843bcdc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215941"
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
类型化指针数组类的基类;必须是一个数组类（ `CObArray` 或 `CPtrArray` ）。

*TYPE*<br/>
基类数组中存储的元素的类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CTypedPtrArray：： Add](#add)|将新元素添加到数组的末尾。 必要时增大数组|
|[CTypedPtrArray：： Append](#append)|将一个数组的内容添加到另一个数组的末尾。 必要时增大数组|
|[CTypedPtrArray：： Copy](#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CTypedPtrArray：： .Value.elementat](#elementat)|在该数组中返回对元素指针的临时引用。|
|[CTypedPtrArray：： GetAt](#getat)|返回给定索引位置处的值。|
|[CTypedPtrArray：： InsertAt](#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CTypedPtrArray：： SetAt](#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CTypedPtrArray：： SetAtGrow](#setatgrow)|设置给定索引的值；根据需要扩展该数组。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CTypedPtrArray：： operator \[\]](#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

当你使用 `CTypedPtrArray` 而不是时 `CPtrArray` `CObArray` ，c + + 类型检查功能可帮助消除不匹配指针类型引起的错误。

此外， `CTypedPtrArray` 如果您使用了或，则包装将执行很多强制转换 `CObArray` `CPtrArray` 。

由于所有 `CTypedPtrArray` 函数都是内联的，因此，使用此模板并不会对代码的大小或速度产生重大影响。

有关使用的详细信息 `CTypedPtrArray` ，请参阅文章[集合](../../mfc/collections.md)和[基于模板的类](../../mfc/template-based-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrArray：： Add

此成员函数调用 `BASE_CLASS` **：： Add**。

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定要添加到数组的元素类型的模板参数。

*（Newelement*<br/>
要添加到此数组的元素。

### <a name="return-value"></a>返回值

所添加的元素的索引。

### <a name="remarks"></a>备注

有关更详细的说明，请参阅[CObArray：： Add](../../mfc/reference/cobarray-class.md#add)。

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrArray：： Append

此成员函数调用 `BASE_CLASS` ：： Append * *。

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>参数

*BASE_CLASS*<br/>
类型化指针数组类的基类;必须是一个数组类（ [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md)）。

*TYPE*<br/>
基类数组中存储的元素的类型。

*src*<br/>
要追加到数组的元素的源。

### <a name="return-value"></a>返回值

第一个追加的元素的索引。

### <a name="remarks"></a>备注

有关更详细的说明，请参阅[CObArray：： Append](../../mfc/reference/cobarray-class.md#append)。

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrArray：： Copy

此成员函数调用 `BASE_CLASS` **：： Copy**。

```cpp
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>参数

*BASE_CLASS*<br/>
类型化指针数组类的基类;必须是一个数组类（ [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md)）。

*TYPE*<br/>
基类数组中存储的元素的类型。

*src*<br/>
要复制到数组的元素的源。

### <a name="remarks"></a>备注

有关更详细的说明，请参阅[CObArray：： Copy](../../mfc/reference/cobarray-class.md#copy)。

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrArray：： .Value.elementat

此内联函数调用 `BASE_CLASS` **：： .value.elementat**。

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定存储在此数组中的元素类型的模板参数。

*nIndex*<br/>
一个大于或等于0且小于或等于由 `BASE_CLASS` **：： system.array.getupperbound**返回的值的整数索引。

### <a name="return-value"></a>返回值

*NIndex*指定的位置处的元素的临时引用。 此元素的类型由模板参数*类型*指定。

### <a name="remarks"></a>备注

有关更详细的说明，请参阅[CObArray：： .value.elementat](../../mfc/reference/cobarray-class.md#elementat)。

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrArray：： GetAt

此内联函数调用 `BASE_CLASS` **：： GetAt**。

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定存储在数组中的元素类型的模板参数。

*nIndex*<br/>
一个大于或等于0且小于或等于由 `BASE_CLASS` **：： system.array.getupperbound**返回的值的整数索引。

### <a name="return-value"></a>返回值

*NIndex*指定的位置处的元素的副本。 此元素的类型由模板参数*类型*指定。

### <a name="remarks"></a>备注

有关更详细的说明，请参阅[CObArray：： GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrArray：： InsertAt

此成员函数调用 `BASE_CLASS` **：： InsertAt**。

```cpp
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
可能大于[CObArray：： system.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)返回的值的整数索引。

*TYPE*<br/>
基类数组中存储的元素的类型。

*（Newelement*<br/>
要放置在此数组中的对象指针。 允许值为**NULL**的 *(newelement* 。

*nCount*<br/>
应插入此元素的次数（默认值为1）。

*nStartIndex*<br/>
可能大于返回的值的整数索引 `CObArray::GetUpperBound` 。

*BASE_CLASS*<br/>
类型化指针数组类的基类;必须是一个数组类（ [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md)）。

*pNewArray*<br/>
包含要添加到此数组中的元素的另一个数组。

### <a name="remarks"></a>备注

有关更详细的说明，请参阅[CObArray：： InsertAt](../../mfc/reference/cobarray-class.md#insertat)。

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrArray：： operator []

这些内联运算符调用 `BASE_CLASS` **：： operator []**。

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定存储在数组中的元素类型的模板参数。

*nIndex*<br/>
一个大于或等于0且小于或等于由 `BASE_CLASS` **：： system.array.getupperbound**返回的值的整数索引。

### <a name="remarks"></a>备注

为 not 的数组调用的第一个运算符 **`const`** 可用于赋值语句右侧的（r 值）或左侧（左值）。 第二个为 **`const`** 数组调用，只能在右侧使用。

如果下标（在赋值语句的左侧或右侧）超出界限，则此库的调试版本将断言。

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrArray：： SetAt

此成员函数调用 `BASE_CLASS` **：： SetAt**。

```cpp
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
一个大于或等于0且小于或等于[CObArray：： system.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)返回的值的整数索引。

*TYPE*<br/>
基类数组中存储的元素的类型。

*ptr*<br/>
指向要插入到 nIndex 的数组中的元素的指针。 允许空值。

### <a name="remarks"></a>备注

有关更详细的说明，请参阅[CObArray：： SetAt](../../mfc/reference/cobarray-class.md#setat)。

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrArray：： SetAtGrow

此成员函数调用 `BASE_CLASS` **：： SetAtGrow**。

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于0的整数索引。

*TYPE*<br/>
基类数组中存储的元素的类型。

*（Newelement*<br/>
要添加到此数组的对象指针。 允许**空**值。

### <a name="remarks"></a>备注

有关更详细的说明，请参阅[CObArray：： SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)。

## <a name="see-also"></a>另请参阅

[MFC 示例收集](../../overview/visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray 类](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray 类](../../mfc/reference/cobarray-class.md)
