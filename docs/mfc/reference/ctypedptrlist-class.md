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
ms.openlocfilehash: 40dbfb822e71309e9675aba14d46d333ffa4ee06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373264"
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
类型化指针列表类的基类;必须是指针列表类 （`CObList`或`CPtrList`。

*类型*<br/>
存储在基类列表中的元素的类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CTypedPtrlist：：添加头](#addhead)|将元素（或其他列表中的所有元素）添加到列表的头部（制作新头）。|
|[CTypedPtrlist：：添加尾数](#addtail)|将元素（或其他列表中的所有元素）添加到列表的尾部（制作新尾部）。|
|[CTypedPtrlist：：获取At](#getat)|获取给定位置的元素。|
|[CTypedPtrlist：获取头](#gethead)|返回列表的头元素（不能为空）。|
|[CTypedPtrList：：获取下一个](#getnext)|获取下一个迭代元素。|
|[CTypedPtrList：GetPrev](#getprev)|获取用于迭代的前一个元素。|
|[CTypedPtrlist：GetTail](#gettail)|返回列表的尾部元素（不能为空）。|
|[CTypedPtrlist：：删除头](#removehead)|从列表的头部中删除元素。|
|[CTypedPtrlist：：删除尾翼](#removetail)|从列表尾部中删除元素。|
|[CTypedPtrlist：：SetAt](#setat)|将元素设置在给定位置。|

## <a name="remarks"></a>备注

使用`CTypedPtrList`而不是`CObList`或`CPtrList`时，C++类型检查工具有助于消除由不匹配的指针类型引起的错误。

此外，`CTypedPtrList`包装器执行使用`CObList`或`CPtrList`时所需的大部分强制转换。

由于所有`CTypedPtrList`函数都是内联的，因此使用此模板不会显著影响代码的大小或速度。

派生自的列表`CObList`可以序列化，但派生自`CPtrList`的列表不能。

当删除 `CTypedPtrList` 对象或其元素时，仅删除指针而不是指针引用的实体。

有关 使用`CTypedPtrList`的详细信息，请参阅文章[集合](../../mfc/collections.md)和[基于模板的类](../../mfc/template-based-classes.md)。

## <a name="example"></a>示例

本示例创建`CTypedPtrList`的实例，添加一个对象，将列表序列化到磁盘，然后删除该对象：

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

## <a name="ctypedptrlistaddhead"></a><a name="addhead"></a>CTypedPtrlist：：添加头

此成员函数调用`BASE_CLASS` **：：AddHead**。

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>参数

*类型*<br/>
存储在基类列表中的元素的类型。

*新元素*<br/>
要添加到此列表的对象指针。 允许 NULL 值。

*BASE_CLASS*<br/>
类型化指针列表类的基类;必须是指针列表类[（CObList](../../mfc/reference/coblist-class.md)或[CPtrList）。](../../mfc/reference/cptrlist-class.md)

*pNewlist*<br/>
指向另一个[CTypedPtrList 对象的指针](../../mfc/reference/ctypedptrlist-class.md)。 *pNewList*中的元素将添加到此列表中。

### <a name="return-value"></a>返回值

第一个版本返回新插入的元素的"位置"值。

### <a name="remarks"></a>备注

第一个版本在列表的头部之前添加新元素。 第二个版本在头之前添加另一个元素列表。

## <a name="ctypedptrlistaddtail"></a><a name="addtail"></a>CTypedPtrlist：：添加尾数

此成员函数调用`BASE_CLASS` **：：AddTail**。

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>参数

*类型*<br/>
存储在基类列表中的元素的类型。

*新元素*<br/>
要添加到此列表的对象指针。 允许 NULL 值。

*BASE_CLASS*<br/>
类型化指针列表类的基类;必须是指针列表类[（CObList](../../mfc/reference/coblist-class.md)或[CPtrList）。](../../mfc/reference/cptrlist-class.md)

*pNewlist*<br/>
指向另一个[CTypedPtrList 对象的指针](../../mfc/reference/ctypedptrlist-class.md)。 *pNewList*中的元素将添加到此列表中。

### <a name="return-value"></a>返回值

第一个版本返回新插入的元素的"位置"值。

### <a name="remarks"></a>备注

第一个版本在列表尾号后添加新元素。 第二个版本在列表尾号之后添加另一个元素列表。

## <a name="ctypedptrlistgetat"></a><a name="getat"></a>CTypedPtrlist：：获取At

位置类型的变量是列表的键。

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数，指定存储在列表中的元素的类型。

*位置*<br/>
由上一个`GetHeadPosition`或`Find`成员函数调用返回的定位值。

### <a name="return-value"></a>返回值

如果列表通过指向`const CTypedPtrList`的指针访问，则`GetAt`返回模板参数*TYPE*指定的类型的指针。 这允许函数仅在赋值语句的右侧使用，从而保护列表不进行修改。

如果直接或通过指向 的指针访问列表`CTypedPtrList`，则`GetAt`返回对模板参数*TYPE*指定的类型的指针的引用。 这允许在赋值语句的任意一侧使用函数，从而允许修改列表条目。

### <a name="remarks"></a>备注

它与索引不同，并且不能自己对位置值进行操作。 `GetAt`检索与`CObject`给定位置关联的指针。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

此内联函数调用`BASE_CLASS` **：：GetAt**。

## <a name="ctypedptrlistgethead"></a><a name="gethead"></a>CTypedPtrlist：获取头

获取表示此列表头元素的指针。

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数，指定存储在列表中的元素的类型。

### <a name="return-value"></a>返回值

如果列表通过指向`const CTypedPtrList`的指针访问，则`GetHead`返回模板参数*TYPE*指定的类型的指针。 这允许函数仅在赋值语句的右侧使用，从而保护列表不进行修改。

如果直接或通过指向 的指针访问列表`CTypedPtrList`，则`GetHead`返回对模板参数*TYPE*指定的类型的指针的引用。 这允许在赋值语句的任意一侧使用函数，从而允许修改列表条目。

### <a name="remarks"></a>备注

在调用`GetHead`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表是否包含元素。

## <a name="ctypedptrlistgetnext"></a><a name="getnext"></a>CTypedPtrList：：获取下一个

获取*r定位*标识的列表元素，然后将*r定位*设置到列表中下一个条目的"位置"值。

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定此列表中包含的元素类型的模板参数。

*r定位*<br/>
对前`GetNext``GetHeadPosition`一个成员函数调用返回的"位置"值的引用。

### <a name="return-value"></a>返回值

如果列表通过指向`const CTypedPtrList`的指针访问，则`GetNext`返回模板参数*TYPE*指定的类型的指针。 这允许函数仅在赋值语句的右侧使用，从而保护列表不进行修改。

如果直接或通过指向 的指针访问列表`CTypedPtrList`，则`GetNext`返回对模板参数*TYPE*指定的类型的指针的引用。 这允许在赋值语句的任意一侧使用函数，从而允许修改列表条目。

### <a name="remarks"></a>备注

如果使用调用`GetNext``GetHeadPosition`或[CPtrList 建立](../../mfc/reference/coblist-class.md#find)初始位置，则可以在转发迭代循环中使用：查找 。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

如果检索到的元素是列表中的最后一个元素，则*rValue*的新值将设置为 NULL。

可以在迭代期间删除元素。 请参阅[COblist 的示例：：删除At。](../../mfc/reference/coblist-class.md#removeat)

## <a name="ctypedptrlistgetprev"></a><a name="getprev"></a>CTypedPtrList：GetPrev

获取*rPosition*标识的列表元素，然后将*r定位*设置到列表中上一个条目的"位置"值。

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*类型*<br/>
指定此列表中包含的元素类型的模板参数。

*r定位*<br/>
对前`GetPrev`一个成员或其他成员函数调用返回的定位值的引用。

### <a name="return-value"></a>返回值

如果列表通过指向`const CTypedPtrList`的指针访问，则`GetPrev`返回模板参数*TYPE*指定的类型的指针。 这允许函数仅在赋值语句的右侧使用，从而保护列表不进行修改。

如果直接或通过指向 的指针访问列表`CTypedPtrList`，则`GetPrev`返回对模板参数*TYPE*指定的类型的指针的引用。 这允许在赋值语句的任意一侧使用函数，从而允许修改列表条目。

### <a name="remarks"></a>备注

如果使用`GetPrev`调用`GetTailPosition`或`Find`建立初始位置，则可以在反向迭代循环中使用。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

如果检索到的元素是列表中的第一个元素，则*rValue*的新值将设置为 NULL。

## <a name="ctypedptrlistgettail"></a><a name="gettail"></a>CTypedPtrlist：GetTail

获取表示此列表头元素的指针。

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数，指定存储在列表中的元素的类型。

### <a name="return-value"></a>返回值

如果列表通过指向`const CTypedPtrList`的指针访问，则`GetTail`返回模板参数*TYPE*指定的类型的指针。 这允许函数仅在赋值语句的右侧使用，从而保护列表不进行修改。

如果直接或通过指向 的指针访问列表`CTypedPtrList`，则`GetTail`返回对模板参数*TYPE*指定的类型的指针的引用。 这允许在赋值语句的任意一侧使用函数，从而允许修改列表条目。

### <a name="remarks"></a>备注

在调用`GetTail`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表是否包含元素。

## <a name="ctypedptrlistremovehead"></a><a name="removehead"></a>CTypedPtrlist：：删除头

从列表的头部删除元素并返回它。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数，指定存储在列表中的元素的类型。

### <a name="return-value"></a>返回值

以前位于列表头的指针。 此指针的类型由模板参数*TYPE*指定。

### <a name="remarks"></a>备注

在调用`RemoveHead`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表是否包含元素。

## <a name="ctypedptrlistremovetail"></a><a name="removetail"></a>CTypedPtrlist：：删除尾翼

从列表的尾部删除元素并返回它。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>参数

*类型*<br/>
模板参数，指定存储在列表中的元素的类型。

### <a name="return-value"></a>返回值

以前位于列表尾部分的指针。 此指针的类型由模板参数*TYPE*指定。

### <a name="remarks"></a>备注

在调用`RemoveTail`之前，必须确保列表不为空。 如果列表为空，则 Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表是否包含元素。

## <a name="ctypedptrlistsetat"></a><a name="setat"></a>CTypedPtrlist：：SetAt

此成员函数调用`BASE_CLASS` **：：SetAt**。

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>参数

*Pos*<br/>
要设置的元素的位置。

*类型*<br/>
存储在基类列表中的元素的类型。

*新元素*<br/>
要写入列表的对象指针。

### <a name="remarks"></a>备注

位置类型的变量是列表的键。 它与索引不同，并且不能自己对位置值进行操作。 `SetAt`将对象指针写入列表中的指定位置。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

有关更详细的注释，请参阅[COblist：：setat](../../mfc/reference/coblist-class.md#setat)。

## <a name="see-also"></a>另请参阅

[MFC 样品收集](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CPtrList 类](../../mfc/reference/cptrlist-class.md)<br/>
[COblist 类](../../mfc/reference/coblist-class.md)
