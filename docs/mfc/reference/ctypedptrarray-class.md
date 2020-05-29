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
ms.openlocfilehash: 20cf147e955b6b19919f35750b0f46a8b5a67ad0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752060"
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
类型化指针数组类的基类;必须是数组类 （`CObArray`或`CPtrArray`。

*类型*<br/>
存储在基类数组中的元素的类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CTypedPtrarray：：添加](#add)|向数组的末尾添加新元素。 如有必要，增大数组|
|[CTypedPtrarray：：追加](#append)|将一个数组的内容添加到另一个数组的末尾。 如有必要，增大数组|
|[CTypedPtrarray：：复制](#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CTypedPtrarray：：元素At](#elementat)|在该数组中返回对元素指针的临时引用。|
|[CTypedPtrarray：：获取At](#getat)|返回给定索引位置处的值。|
|[CTypedPtrarray：：插入At](#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CTypedPtrarray：：SetAt](#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CTypedPtrarray：：SetAt增长](#setatgrow)|设置给定索引的值；根据需要扩展该数组。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CTypedPtrarray：：运算符\[\]](#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

使用`CTypedPtrArray`而不是`CPtrArray`或`CObArray`时，C++类型检查工具有助于消除由不匹配的指针类型引起的错误。

此外，`CTypedPtrArray`包装器执行使用`CObArray`或`CPtrArray`时所需的大部分强制转换。

由于所有`CTypedPtrArray`函数都是内联的，因此使用此模板不会显著影响代码的大小或速度。

有关 使用`CTypedPtrArray`的详细信息，请参阅文章[集合](../../mfc/collections.md)和[基于模板的类](../../mfc/template-based-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrarray：：添加

此成员函数调用`BASE_CLASS` **：：添加**。

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>参数

*类型*<br/>
指定要添加到数组的元素类型的模板参数。

*新元素*<br/>
要添加到此数组的元素。

### <a name="return-value"></a>返回值

添加元素的索引。

### <a name="remarks"></a>备注

有关更详细的注释，请参阅[CObarray：：：添加](../../mfc/reference/cobarray-class.md#add)。

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrarray：：追加

此成员函数调用`BASE_CLASS`：：附加_。

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>参数

*BASE_CLASS*<br/>
类型化指针数组类的基类;必须是数组类[（CObarray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md)）。

*类型*<br/>
存储在基类数组中的元素的类型。

*src*<br/>
要追加到数组的元素的源。

### <a name="return-value"></a>返回值

第一个附加元素的索引。

### <a name="remarks"></a>备注

有关更详细的注释，请参阅[CObarray：：：附加 。](../../mfc/reference/cobarray-class.md#append)

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrarray：：复制

此成员函数调用`BASE_CLASS` **：：复制**。

```cpp
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>参数

*BASE_CLASS*<br/>
类型化指针数组类的基类;必须是数组类[（CObarray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md)）。

*类型*<br/>
存储在基类数组中的元素的类型。

*src*<br/>
要复制到数组的元素的源。

### <a name="remarks"></a>备注

有关更详细的注释，请参阅[CObarray：：：复制](../../mfc/reference/cobarray-class.md#copy)。

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrarray：：元素At

此内联函数调用`BASE_CLASS` **：：ElementAt**。

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>参数

*类型*<br/>
指定存储在此数组中的元素类型的模板参数。

*nIndex*<br/>
大于或等于 0 且小于或等于`BASE_CLASS`**：：getUpperBound**返回的值的整数索引。

### <a name="return-value"></a>返回值

对*nIndex*指定位置的元素的临时引用。 此元素的类型由模板参数*TYPE*指定。

### <a name="remarks"></a>备注

有关更详细的注释，请参阅[CObarray：：elementat](../../mfc/reference/cobarray-class.md#elementat)。

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrarray：：获取At

此内联函数调用`BASE_CLASS` **：：GetAt**。

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数，指定存储在数组中的元素的类型。

*nIndex*<br/>
大于或等于 0 且小于或等于`BASE_CLASS`**：：getUpperBound**返回的值的整数索引。

### <a name="return-value"></a>返回值

*在 nIndex*指定的位置的元素的副本。 此元素的类型由模板参数*TYPE*指定。

### <a name="remarks"></a>备注

有关更详细的注释，请参阅[CObarray：：GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrarray：：插入At

此成员函数调用`BASE_CLASS` **：：InsertAt**。

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
可能大于 CObarray 返回的值的整数索引[：：GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。

*类型*<br/>
存储在基类数组中的元素的类型。

*新元素*<br/>
要放置在此数组中的对象指针。 允许*新的*值**NULL**元素。

*nCount*<br/>
应插入此元素的次数（默认值为 1）。

*nStartIndex*<br/>
可能大于 返回`CObArray::GetUpperBound`的值的整数索引。

*BASE_CLASS*<br/>
类型化指针数组类的基类;必须是数组类[（CObarray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md)）。

*pNewArray*<br/>
另一个包含要添加到此数组的元素的数组。

### <a name="remarks"></a>备注

有关更详细的注释，请参阅[CObarray：：插入At](../../mfc/reference/cobarray-class.md#insertat)。

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrarray：：运算符 |

这些内联运算符调用`BASE_CLASS` **：： 运算符 ***。

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数，指定存储在数组中的元素的类型。

*nIndex*<br/>
大于或等于 0 且小于或等于`BASE_CLASS`**：：getUpperBound**返回的值的整数索引。

### <a name="remarks"></a>备注

第一个运算符（称为非**const**数组）可以在赋值语句的右侧（r 值）或左侧（l 值）上使用。 第二个调用为**const**数组，只能在右侧使用。

库的调试版本断言下标（在赋值语句的左侧或右侧）是否超出边界。

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrarray：：SetAt

此成员函数调用`BASE_CLASS` **：：SetAt**。

```cpp
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 且小于或等于 CObArray 返回的值的整数索引[：：getUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。

*类型*<br/>
存储在基类数组中的元素的类型。

*Ptr*<br/>
指向要在 nIndex 的数组中插入的元素的指针。 允许 NULL 值。

### <a name="remarks"></a>备注

有关更详细的注释，请参阅[CObarray：：setat](../../mfc/reference/cobarray-class.md#setat)。

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrarray：：SetAt增长

此成员函数调用`BASE_CLASS` **：：SetAtGrow**。

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
大于或等于 0 的整数索引。

*类型*<br/>
存储在基类数组中的元素的类型。

*新元素*<br/>
要添加到此数组的对象指针。 允许**NULL**值。

### <a name="remarks"></a>备注

有关更详细的注释，请参阅[CObarray：：SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)。

## <a name="see-also"></a>请参阅

[MFC 样品收集](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray 类](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray 类](../../mfc/reference/cobarray-class.md)
