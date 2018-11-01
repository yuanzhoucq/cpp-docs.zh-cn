---
title: CTypedPtrList 类
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
ms.openlocfilehash: 485550fbd4d3fc483303cd6ba73d74e29cc7a006
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555868"
---
# <a name="ctypedptrlist-class"></a>CTypedPtrList 类

为 `CPtrList`类的对象提供安全类型“包装器”。

## <a name="syntax"></a>语法

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>参数

*BASE_CLASS*<br/>
基的类的类型化的指针列表;必须是指针列表类 (`CObList`或`CPtrList`)。

*类型*<br/>
存储在基类列表中的元素的类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CTypedPtrList::AddHead](#addhead)|将一个元素 （或另一个列表中的所有元素） 添加到 （使新头） 了列表的开头。|
|[CTypedPtrList::AddTail](#addtail)|将一个元素 （或另一个列表中的所有元素） 添加到列表 （使新结尾） 的尾部。|
|[CTypedPtrList::GetAt](#getat)|获取位于给定位置的元素。|
|[CTypedPtrList::GetHead](#gethead)|返回的列表 （不能为空） 的头元素。|
|[CTypedPtrList::GetNext](#getnext)|获取用于循环的下一个元素。|
|[CTypedPtrList::GetPrev](#getprev)|获取循环访问的上一个元素。|
|[CTypedPtrList::GetTail](#gettail)|返回 （不能为空） 的列表的结尾元素。|
|[CTypedPtrList::RemoveHead](#removehead)|从列表的开头移除的元素。|
|[CTypedPtrList::RemoveTail](#removetail)|从列表的结尾移除的元素。|
|[CTypedPtrList::SetAt](#setat)|设置给定位置处的元素。|

## <a name="remarks"></a>备注

当你使用`CTypedPtrList`而非`CObList`或`CPtrList`，c + + 类型检查功能可帮助消除错误引起的不匹配的指针类型。

此外，`CTypedPtrList`包装执行大量的强制转换，如果您使用，则将需要`CObList`或`CPtrList`。

因为所有`CTypedPtrList`函数是内联的使用此模板不会严重影响的大小或代码的速度。

列表派生自`CObList`可序列化，而是派生自`CPtrList`不能。

当删除 `CTypedPtrList` 对象或其元素时，仅删除指针而不是指针引用的实体。

有关使用的详细信息`CTypedPtrList`，请参阅文章[集合](../../mfc/collections.md)并[基于模板的类](../../mfc/template-based-classes.md)。

## <a name="example"></a>示例

此示例中创建的实例`CTypedPtrList`、 添加了一个对象，序列化到磁盘，列表，然后删除该对象：

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

##  <a name="addhead"></a>  CTypedPtrList::AddHead

此成员函数将调用`BASE_CLASS` **:: AddHead**。

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>参数

*类型*<br/>
存储在基类列表中的元素的类型。

*newElement*<br/>
要添加到此列表的对象指针。 允许 NULL 值。

*BASE_CLASS*<br/>
基的类的类型化的指针列表;必须是指针列表类 ( [CObList](../../mfc/reference/coblist-class.md)或[CPtrList](../../mfc/reference/cptrlist-class.md))。

*pNewList*<br/>
指向另一个[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)对象。 中的元素*pNewList*将添加到此列表。

### <a name="return-value"></a>返回值

第一个版本返回新插入的元素的位置值。

### <a name="remarks"></a>备注

第一个版本添加了列表的开头之前新元素。 第二个版本将添加另一个列表的开头之前的元素。

##  <a name="addtail"></a>  CTypedPtrList::AddTail

此成员函数将调用`BASE_CLASS` **:: AddTail**。

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>参数

*类型*<br/>
存储在基类列表中的元素的类型。

*newElement*<br/>
要添加到此列表的对象指针。 允许 NULL 值。

*BASE_CLASS*<br/>
基的类的类型化的指针列表;必须是指针列表类 ( [CObList](../../mfc/reference/coblist-class.md)或[CPtrList](../../mfc/reference/cptrlist-class.md))。

*pNewList*<br/>
指向另一个[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)对象。 中的元素*pNewList*将添加到此列表。

### <a name="return-value"></a>返回值

第一个版本返回新插入的元素的位置值。

### <a name="remarks"></a>备注

第一个版本后的列表的结尾添加新元素。 第二个版本的列表的结尾后添加元素的另一个的列表。

##  <a name="getat"></a>  CTypedPtrList::GetAt

位置类型的变量是列表的键。

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定存储在列表中的元素类型模板参数。

*位置*<br/>
返回先前的位置值`GetHeadPosition`或`Find`成员函数调用。

### <a name="return-value"></a>返回值

如果通过到指针访问列表`const CTypedPtrList`，然后`GetAt`返回模板参数指定的类型的指针*类型*。 这允许使用仅在赋值语句右侧的函数，因此，从修改保护列表。

如果直接或通过指针向访问列表`CTypedPtrList`，然后`GetAt`返回对指定模板参数的类型的指针的引用*类型*。 这允许使用赋值语句的任何一侧的函数，因此允许列表条目，以进行修改。

### <a name="remarks"></a>备注

不是索引，请与相同和您无法对位置值自己。 `GetAt` 检索`CObject`与给定位置相关联的指针。

您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。

此内联函数将调用`BASE_CLASS` **:: GetAt**。

##  <a name="gethead"></a>  CTypedPtrList::GetHead

获取表示此列表的头元素的指针。

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定存储在列表中的元素类型模板参数。

### <a name="return-value"></a>返回值

如果通过到指针访问列表`const CTypedPtrList`，然后`GetHead`返回模板参数指定的类型的指针*类型*。 这允许使用仅在赋值语句右侧的函数，因此，从修改保护列表。

如果直接或通过指针向访问列表`CTypedPtrList`，然后`GetHead`返回对指定模板参数的类型的指针的引用*类型*。 这允许使用赋值语句的任何一侧的函数，因此允许列表条目，以进行修改。

### <a name="remarks"></a>备注

必须确保该列表不是空之前调用`GetHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表中包含的元素。

##  <a name="getnext"></a>  CTypedPtrList::GetNext

获取标识的列表元素*rPosition*，然后设置*rPosition*到列表中的下一个条目的位置值。

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定此列表中包含的元素类型模板参数。

*rPosition*<br/>
对先前返回的位置值的引用`GetNext`， `GetHeadPosition`，或其他成员函数调用。

### <a name="return-value"></a>返回值

如果通过到指针访问列表`const CTypedPtrList`，然后`GetNext`返回模板参数指定的类型的指针*类型*。 这允许使用仅在赋值语句右侧的函数，因此，从修改保护列表。

如果直接或通过指针向访问列表`CTypedPtrList`，然后`GetNext`返回对指定模板参数的类型的指针的引用*类型*。 这允许使用赋值语句的任何一侧的函数，因此允许列表条目，以进行修改。

### <a name="remarks"></a>备注

可以使用`GetNext`中如果建立调用一次的初始位置的向前迭代循环`GetHeadPosition`或[CPtrList::Find](../../mfc/reference/coblist-class.md#find)。

您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。

如果检索的元素的是在列表中，最后再的新值*rPosition*设置为 NULL。

就可以执行迭代的过程中删除元素。 有关示例，请参阅[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)。

##  <a name="getprev"></a>  CTypedPtrList::GetPrev

获取标识的列表元素*rPosition*，然后设置*rPosition*列表的上一项的位置值。

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定此列表中包含的元素类型模板参数。

*rPosition*<br/>
对先前返回的位置值的引用`GetPrev`或其他成员函数调用。

### <a name="return-value"></a>返回值

如果通过到指针访问列表`const CTypedPtrList`，然后`GetPrev`返回模板参数指定的类型的指针*类型*。 这允许使用仅在赋值语句右侧的函数，因此，从修改保护列表。

如果直接或通过指针向访问列表`CTypedPtrList`，然后`GetPrev`返回对指定模板参数的类型的指针的引用*类型*。 这允许使用赋值语句的任何一侧的函数，因此允许列表条目，以进行修改。

### <a name="remarks"></a>备注

可以使用`GetPrev`在反向迭代循环中，如果建立初始位置通过调用`GetTailPosition`或`Find`。

您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。

如果检索的元素的为第一个在列表中，则新值的*rPosition*设置为 NULL。

##  <a name="gettail"></a>  CTypedPtrList::GetTail

获取表示此列表的头元素的指针。

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定存储在列表中的元素类型模板参数。

### <a name="return-value"></a>返回值

如果通过到指针访问列表`const CTypedPtrList`，然后`GetTail`返回模板参数指定的类型的指针*类型*。 这允许使用仅在赋值语句右侧的函数，因此，从修改保护列表。

如果直接或通过指针向访问列表`CTypedPtrList`，然后`GetTail`返回对指定模板参数的类型的指针的引用*类型*。 这允许使用赋值语句的任何一侧的函数，因此允许列表条目，以进行修改。

### <a name="remarks"></a>备注

必须确保该列表不是空之前调用`GetTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表中包含的元素。

##  <a name="removehead"></a>  CTypedPtrList::RemoveHead

从列表的开头移除的元素并将其返回。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>参数

*类型*<br/>
指定存储在列表中的元素类型模板参数。

### <a name="return-value"></a>返回值

以前位于列表的头指针。 此指针为模板参数指定的类型*类型*。

### <a name="remarks"></a>备注

必须确保该列表不是空之前调用`RemoveHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表中包含的元素。

##  <a name="removetail"></a>  CTypedPtrList::RemoveTail

从列表的结尾移除的元素并将其返回。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>参数

*类型*<br/>
指定存储在列表中的元素类型模板参数。

### <a name="return-value"></a>返回值

以前位于列表的尾指针。 此指针为模板参数指定的类型*类型*。

### <a name="remarks"></a>备注

必须确保该列表不是空之前调用`RemoveTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表中包含的元素。

##  <a name="setat"></a>  CTypedPtrList::SetAt

此成员函数将调用`BASE_CLASS` **:: SetAt**。

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>参数

*pos*<br/>
若要设置的元素的位置。

*类型*<br/>
存储在基类列表中的元素的类型。

*newElement*<br/>
要写入到列表的对象指针。

### <a name="remarks"></a>备注

位置类型的变量是列表的键。 不是索引，请与相同和您无法对位置值自己。 `SetAt` 将对象指针写入到列表中的指定位置。

您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。

有关更多详细说明，请参阅[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)。

## <a name="see-also"></a>请参阅

[MFC 示例收集](../../visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPtrList 类](../../mfc/reference/cptrlist-class.md)<br/>
[CObList 类](../../mfc/reference/coblist-class.md)
