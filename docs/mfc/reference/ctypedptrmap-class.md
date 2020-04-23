---
title: CTypedPtrMap Class
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
ms.openlocfilehash: 410f0101fd0f8cda271fe0f2353b06b9e8d773b8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754362"
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap Class

为 `CMapPtrToPtr`、 `CMapPtrToWord`、 `CMapWordToPtr`和 `CMapStringToPtr`指针映射类的对象提供安全类型“包装器”。

## <a name="syntax"></a>语法

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>参数

*BASE_CLASS*<br/>
类型化指针映射类的基类;必须是指针`CMapPtrToPtr`映射类 （、、、`CMapWordToPtr``CMapStringToPtr``CMapPtrToWord`或 ）。

*关键*<br/>
用作映射键的对象的类。

*价值*<br/>
存储在地图中的对象的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CTypedPtrMap：：获取NextAssoc](#getnextassoc)|获取下一个迭代元素。|
|[CTypedPtrMap：：查找](#lookup)|返回`KEY`基于 的`VALUE`。|
|[CTypedPtrMap：：删除键](#removekey)|删除由键指定的元素。|
|[CTypedPtrMap：：SetAt](#setat)|将元素插入到地图中;如果找到匹配的键，则替换现有元素。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CTypedPtrMap：：运算符\[\]](#operator_at)|将元素插入到地图中。|

## <a name="remarks"></a>备注

使用`CTypedPtrMap`时，C++类型检查工具有助于消除由不匹配的指针类型引起的错误。

由于所有`CTypedPtrMap`函数都是内联的，因此使用此模板不会显著影响代码的大小或速度。

有关 使用`CTypedPtrMap`的详细信息，请参阅文章[集合](../../mfc/collections.md)和[基于模板的类](../../mfc/template-based-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

## <a name="ctypedptrmapgetnextassoc"></a><a name="getnextassoc"></a>CTypedPtrMap：：获取NextAssoc

在 中检索地图元素`rNextPosition`，然后更新`rNextPosition`以引用地图中的下一个元素。

```cpp
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>参数

*r定位*<br/>
指定对上一个`GetNextAssoc`或`BASE_CLASS` **：： GetStart位置**调用返回的定位值的引用。

*关键*<br/>
指定地图键类型的模板参数。

*rKey*<br/>
指定检索到的元素的返回键。

*价值*<br/>
指定地图值类型的模板参数。

*rValue*<br/>
指定检索到的元素的返回值。

### <a name="remarks"></a>备注

此函数对于迭代地图中的所有元素最有用。 请注意，位置序列不一定与键值序列相同。

如果检索到的元素是地图中的最后一个元素，则 的新`rNextPosition`值将设置为 NULL。

此内联函数调用`BASE_CLASS` **：：GetNextAssoc**。

## <a name="ctypedptrmaplookup"></a><a name="lookup"></a>CTypedPtrMap：：查找

`Lookup`使用哈希算法快速查找具有完全匹配的键的映射元素。

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>参数

*BASE_CLASS*<br/>
指定此映射类的基类的模板参数。

*键*<br/>
要抬起来的元素的键。

*价值*<br/>
指定此映射中存储的值类型的模板参数。

*rValue*<br/>
指定检索到的元素的返回值。

### <a name="return-value"></a>返回值

如果找到元素，则非零;否则 0。

### <a name="remarks"></a>备注

此内联函数调用`BASE_CLASS` **：：查找**。

## <a name="ctypedptrmapoperator--"></a><a name="operator_at"></a>CTypedPtrMap：：运算符 |

此运算符只能在赋值语句（l 值）的左侧使用。

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>参数

*价值*<br/>
指定此映射中存储的值类型的模板参数。

*BASE_CLASS*<br/>
指定此映射类的基类的模板参数。

*键*<br/>
要在地图中备份或创建的元素的键。

### <a name="remarks"></a>备注

如果没有具有指定键的地图元素，则创建新元素。 没有等效于此运算符的"右侧"（r 值），因为在地图中可能找不到键。 使用`Lookup`成员函数进行元素检索。

## <a name="ctypedptrmapremovekey"></a><a name="removekey"></a>CTypedPtrMap：：删除键

此成员函数调用`BASE_CLASS` **：：删除键**。

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>参数

*关键*<br/>
指定地图键类型的模板参数。

*键*<br/>
要删除的元素的键。

### <a name="return-value"></a>返回值

如果发现并成功删除条目，则非零;否则 0。

### <a name="remarks"></a>备注

有关更详细的注释，请参阅[CMapStringToOb：：：删除键](../../mfc/reference/cmapstringtoob-class.md#removekey)。

## <a name="ctypedptrmapsetat"></a><a name="setat"></a>CTypedPtrMap：：SetAt

此成员函数调用`BASE_CLASS` **：：SetAt**。

```cpp
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>参数

*关键*<br/>
指定地图键类型的模板参数。

*键*<br/>
指定新值的键值。

*newValue*<br/>
指定作为新元素值的对象指针。

### <a name="remarks"></a>备注

有关更详细的注释，请参阅[CMapStringToOb：：setat](../../mfc/reference/cmapstringtoob-class.md#setat)。

## <a name="see-also"></a>请参阅

[MFC 样品收集](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrPtr 类](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord 类](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr 类](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr 类](../../mfc/reference/cmapstringtoptr-class.md)
