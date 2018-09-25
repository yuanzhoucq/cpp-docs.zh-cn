---
title: CTypedPtrMap 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85f44473237a17a83aae2377e63a4e35d43483b9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433785"
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
类型化的指针映射类; 基类的必须是指针映射类 ( `CMapPtrToPtr`， `CMapPtrToWord`， `CMapWordToPtr`，或`CMapStringToPtr`)。

*KEY*<br/>
用作映射的键的对象的类。

*值*<br/>
在映射中存储的对象的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|获取用于循环的下一个元素。|
|[CTypedPtrMap::Lookup](#lookup)|返回`KEY`基于`VALUE`。|
|[CTypedPtrMap::RemoveKey](#removekey)|移除由键指定的元素。|
|[CTypedPtrMap::SetAt](#setat)|将元素插入到映射;如果找到匹配项，将替换现有元素。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CTypedPtrMap::operator]](#operator_at)|将元素插入到映射。|

## <a name="remarks"></a>备注

当你使用`CTypedPtrMap`，c + + 类型检查功能可帮助消除错误引起的不匹配的指针类型。

因为所有`CTypedPtrMap`函数是内联的使用此模板不会严重影响的大小或代码的速度。

有关使用的详细信息`CTypedPtrMap`，请参阅文章[集合](../../mfc/collections.md)并[基于模板的类](../../mfc/template-based-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

##  <a name="getnextassoc"></a>  CTypedPtrMap::GetNextAssoc

检索处的地图元素`rNextPosition`，然后更新`rNextPosition`来指代在映射中的下一个元素。

```
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>参数

*rPosition*<br/>
指定对先前返回的位置值的引用`GetNextAssoc`或`BASE_CLASS` **:: GetStartPosition**调用。

*KEY*<br/>
指定地图的键的类型的模板参数。

*rKey*<br/>
指定返回检索到的元素的键。

*值*<br/>
指定地图的值的类型的模板参数。

*rValue*<br/>
指定检索的元素的返回的值。

### <a name="remarks"></a>备注

此函数是最适用于通过映射中的所有元素。 请注意，位置序列不一定与密钥值序列相同。

如果检索的元素在映射中上, 一次然后的新值`rNextPosition`设置为 NULL。

此内联函数将调用`BASE_CLASS` **:: GetNextAssoc**。

##  <a name="lookup"></a>  CTypedPtrMap::Lookup

`Lookup` 使用哈希算法来快速查找完全匹配的密钥的地图元素。

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>参数

*BASE_CLASS*<br/>
指定此地图的类的基类的模板参数。

*key*<br/>
要查找的元素的键。

*值*<br/>
指定的值存储在此映射中的类型的模板参数。

*rValue*<br/>
指定检索的元素的返回的值。

### <a name="return-value"></a>返回值

如果找到该元素; 非零值否则为 0。

### <a name="remarks"></a>备注

此内联函数将调用`BASE_CLASS` **:: 查找**。

##  <a name="operator_at"></a>  CTypedPtrMap::operator]

仅在左侧和右侧的赋值语句 （左值） 上，可以使用此运算符。

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>参数

*值*<br/>
指定的值存储在此映射中的类型的模板参数。

*BASE_CLASS*<br/>
指定此地图的类的基类的模板参数。

*key*<br/>
要查找或创建在映射中的元素的键。

### <a name="remarks"></a>备注

如果不存在具有指定键映射元素，则会创建一个新的元素。 没有等效于此运算符的任何"右侧"（右值），因为可能可能映射中找到密钥。 使用`Lookup`元素检索的成员函数。

##  <a name="removekey"></a>  CTypedPtrMap::RemoveKey

此成员函数将调用`BASE_CLASS` **:: RemoveKey**。

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>参数

*KEY*<br/>
指定地图的键的类型的模板参数。

*key*<br/>
要移除的元素键。

### <a name="return-value"></a>返回值

如果找到该条目并将其成功移除，则非零值否则为 0。

### <a name="remarks"></a>备注

有关更多详细说明，请参阅[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)。

##  <a name="setat"></a>  CTypedPtrMap::SetAt

此成员函数将调用`BASE_CLASS` **:: SetAt**。

```
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>参数

*KEY*<br/>
指定地图的键的类型的模板参数。

*key*<br/>
指定 newValue 的键值。

*newValue*<br/>
指定是将新元素的值的对象指针。

### <a name="remarks"></a>备注

有关更多详细说明，请参阅[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)。

## <a name="see-also"></a>请参阅

[MFC 示例收集](../../visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr 类](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord 类](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr 类](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr 类](../../mfc/reference/cmapstringtoptr-class.md)
