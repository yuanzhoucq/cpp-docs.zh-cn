---
title: CRBTree 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRBTree
- ATLCOLL/ATL::CRBTree
- ATLCOLL/ATL::CRBTree::KINARGTYPE
- ATLCOLL/ATL::CRBTree::KOUTARGTYPE
- ATLCOLL/ATL::CRBTree::VINARGTYPE
- ATLCOLL/ATL::CRBTree::VOUTARGTYPE
- ATLCOLL/ATL::CRBTree::FindFirstKeyAfter
- ATLCOLL/ATL::CRBTree::GetAt
- ATLCOLL/ATL::CRBTree::GetCount
- ATLCOLL/ATL::CRBTree::GetHeadPosition
- ATLCOLL/ATL::CRBTree::GetKeyAt
- ATLCOLL/ATL::CRBTree::GetNext
- ATLCOLL/ATL::CRBTree::GetNextAssoc
- ATLCOLL/ATL::CRBTree::GetNextKey
- ATLCOLL/ATL::CRBTree::GetNextValue
- ATLCOLL/ATL::CRBTree::GetPrev
- ATLCOLL/ATL::CRBTree::GetTailPosition
- ATLCOLL/ATL::CRBTree::GetValueAt
- ATLCOLL/ATL::CRBTree::IsEmpty
- ATLCOLL/ATL::CRBTree::RemoveAll
- ATLCOLL/ATL::CRBTree::RemoveAt
- ATLCOLL/ATL::CRBTree::SetValueAt
dev_langs:
- C++
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de307c1b4f3d910615061915a240bf7b2c61b337
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090355"
---
# <a name="crbtree-class"></a>CRBTree 类

此类提供用于创建和使用红黑树的方法。

## <a name="syntax"></a>语法

```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>>
class CRBTree
```

#### <a name="parameters"></a>参数

*K*<br/>
Key 元素类型。

*V*<br/>
值元素类型。

*KTraits*<br/>
用于复制或移动关键元素的代码。 请参阅[CElementTraits 类](../../atl/reference/celementtraits-class.md)的更多详细信息。

*VTraits*<br/>
用于复制或移动值元素的代码。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|[CRBTree::KINARGTYPE](#kinargtype)|作为输入参数传递一个键时所使用的类型。|
|[CRBTree::KOUTARGTYPE](#koutargtype)|作为输出参数返回一个密钥时所使用的类型。|
|[CRBTree::VINARGTYPE](#vinargtype)|将值传递作为输入参数时所使用的类型。|
|[CRBTree::VOUTARGTYPE](#voutargtype)|作为输出参数传递一个值时所使用的类型。|

### <a name="public-classes"></a>公共类

|名称|描述|
|----------|-----------------|
|[CRBTree::CPair 类](#cpair_class)|一个包含键和值元素的类。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CRBTree:: ~ CRBTree](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|调用此方法来查找使用的下一个可用键的元素的位置。|
|[CRBTree::GetAt](#getat)|调用此方法以获取在树中的给定位置的元素。|
|[CRBTree::GetCount](#getcount)|调用此方法以获取在树中的元素数。|
|[CRBTree::GetHeadPosition](#getheadposition)|调用此方法以获取位于树的头元素的位置值。|
|[CRBTree::GetKeyAt](#getkeyat)|调用此方法以获取从树中的给定位置的密钥。|
|[CRBTree::GetNext](#getnext)|调用此方法以获取指向存储中的元素的`CRBTree`对象，并转到下一个元素的位置。|
|[CRBTree::GetNextAssoc](#getnextassoc)|调用此方法以获取密钥和存储在映射中元素的值和前移到下一个元素的位置。|
|[CRBTree::GetNextKey](#getnextkey)|调用此方法以获取存储在树中的元素的键和前进到下一个元素的位置。|
|[CRBTree::GetNextValue](#getnextvalue)|调用此方法以获取存储在树中的元素的值并前进到下一个元素的位置。|
|[CRBTree::GetPrev](#getprev)|调用此方法以获取指向存储中的元素的`CRBTree`对象，然后再更新为上一个元素的位置。|
|[CRBTree::GetTailPosition](#gettailposition)|调用此方法以获取位于树的结尾处的元素的位置值。|
|[CRBTree::GetValueAt](#getvalueat)|调用此方法以检索在给定位置中存储的值`CRBTree`对象。|
|[CRBTree::IsEmpty](#isempty)|调用此方法来测试一个空的树对象。|
|[CRBTree::RemoveAll](#removeall)|调用此方法来删除中的所有元素`CRBTree`对象。|
|[CRBTree::RemoveAt](#removeat)|调用此方法来删除中的给定位置处的元素`CRBTree`对象。|
|[CRBTree::SetValueAt](#setvalueat)|调用此方法来更改存储中给定位置处的值`CRBTree`对象。|

## <a name="remarks"></a>备注

红黑树是使用一个额外的二进制搜索树的信息，每个节点以确保它保持"已平衡、，、 树高度不会变得不成比例大并且会影响性能。

此模板类旨在供[CRBMap](../../atl/reference/crbmap-class.md)并[CRBMultiMap](../../atl/reference/crbmultimap-class.md)。 提供构成这些派生类的方法的大容量`CRBTree`。

有关更完整的各种集合类及其功能和性能特征的讨论，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="cpair_class"></a>  CRBTree::CPair 类

一个包含键和值元素的类。

```
class CPair : public __POSITION
```

### <a name="remarks"></a>备注

方法使用此类[CRBTree::GetAt](#getat)， [CRBTree::GetNext](#getnext)，并[CRBTree::GetPrev](#getprev)访问存储在树状结构中的键和值元素。

成员是按如下所示：

|||
|-|-|
|`m_key`|存储密钥的元素，该数据成员。|
|`m_value`|存储值元素，该数据成员。|

##  <a name="dtor"></a>  CRBTree:: ~ CRBTree

析构函数。

```
~CRBTree() throw();
```

### <a name="remarks"></a>备注

释放任何已分配的资源。 调用[CRBTree::RemoveAll](#removeall)删除所有元素。

##  <a name="findfirstkeyafter"></a>  CRBTree::FindFirstKeyAfter

调用此方法来查找使用的下一个可用键的元素的位置。

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>参数

*key*<br/>
密钥的值。

### <a name="return-value"></a>返回值

返回使用的下一个可用键的元素的位置值。 如果没有更多元素，则返回 NULL。

### <a name="remarks"></a>备注

此方法可以轻松地遍历树，而无需预先计算的位置值。

##  <a name="getat"></a>  CRBTree::GetAt

调用此方法以获取在树中的给定位置的元素。

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>参数

*pos*<br/>
位置值。

*key*<br/>
变量来接收该密钥。

*value*<br/>
接收的值的变量。

### <a name="return-value"></a>返回值

前两个窗体返回一个指向[CPair](#cpair_class)。 第三种形式获取一个键和值的给定位置。

### <a name="remarks"></a>备注

位置值可以以前地确定对方法的调用如[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::GetTailPosition](#gettailposition)。

在调试版本中，如果出现断言失败*pos*等于 NULL。

##  <a name="getcount"></a>  CRBTree::GetCount

调用此方法以获取在树中的元素数。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回存储在树中 （每个键/值对是一个元素） 的元素数。

##  <a name="getheadposition"></a>  CRBTree::GetHeadPosition

调用此方法以获取位于树的头元素的位置值。

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>返回值

返回位于树的头元素的位置值。

### <a name="remarks"></a>备注

返回的值`GetHeadPosition`可以用于方法如[CRBTree::GetKeyAt](#getkeyat)或[CRBTree::GetNext](#getnext)遍历树和检索值。

##  <a name="getkeyat"></a>  CRBTree::GetKeyAt

调用此方法以获取从树中的给定位置的密钥。

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
位置值。

### <a name="return-value"></a>返回值

返回位置处存储的密钥*pos*在树中。

### <a name="remarks"></a>备注

如果*pos*不是有效的位置值，结果不可预知。 在调试版本中，如果出现断言失败*pos*等于 NULL。

##  <a name="getnext"></a>  CRBTree::GetNext

调用此方法以获取指向存储中的元素的`CRBTree`对象，并转到下一个元素的位置。

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
如以前调用方法所返回的位置计数器[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。

### <a name="return-value"></a>返回值

返回一个指向下一步[CPair](#cpair_class)在树中的值。

### <a name="remarks"></a>备注

*Pos*位置计数器在每次调用后被更新。 如果检索的元素是在树中，最后*pos*设置为 NULL。

##  <a name="getnextassoc"></a>  CRBTree::GetNextAssoc

调用此方法以获取密钥和存储在映射中元素的值和前移到下一个元素的位置。

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>参数

*pos*<br/>
如以前调用方法所返回的位置计数器[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。

*key*<br/>
指定的树的密钥类型模板参数。

*value*<br/>
指定的树的值的类型的模板参数。

### <a name="remarks"></a>备注

*Pos*位置计数器在每次调用后被更新。 如果检索的元素是在树中，最后*pos*设置为 NULL。

##  <a name="getnextkey"></a>  CRBTree::GetNextKey

调用此方法以获取存储在树中的元素的键和前进到下一个元素的位置。

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
如以前调用方法所返回的位置计数器[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。

### <a name="return-value"></a>返回值

返回树中的下一步的密钥的引用。

### <a name="remarks"></a>备注

更新当前的位置计数器， *pos*。如果在树中有没有更多的项，位置计数器设置为 NULL。

##  <a name="getnextvalue"></a>  CRBTree::GetNextValue

调用此方法以获取存储在树中的元素的值并前进到下一个元素的位置。

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
如以前调用方法所返回的位置计数器[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。

### <a name="return-value"></a>返回值

在树中返回到下一个值的引用。

### <a name="remarks"></a>备注

更新当前的位置计数器， *pos*。如果在树中有没有更多的项，位置计数器设置为 NULL。

##  <a name="getprev"></a>  CRBTree::GetPrev

调用此方法以获取指向存储中的元素的`CRBTree`对象，然后再更新为上一个元素的位置。

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
如以前调用方法所返回的位置计数器[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。

### <a name="return-value"></a>返回值

返回到上一个指针[CPair](#cpair_class)存储在树中的值。

### <a name="remarks"></a>备注

更新当前的位置计数器， *pos*。如果在树中有没有更多的项，位置计数器设置为 NULL。

##  <a name="gettailposition"></a>  CRBTree::GetTailPosition

调用此方法以获取位于树的结尾处的元素的位置值。

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>返回值

返回位于树的结尾处的元素的位置值。

### <a name="remarks"></a>备注

返回的值`GetTailPosition`可以用于方法如[CRBTree::GetKeyAt](#getkeyat)或[CRBTree::GetPrev](#getprev)遍历树和检索值。

##  <a name="getvalueat"></a>  CRBTree::GetValueAt

调用此方法以检索在给定位置中存储的值`CRBTree`对象。

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
如以前调用方法所返回的位置计数器[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。

### <a name="return-value"></a>返回值

返回对存储中的指定位置的值的引用`CRBTree`对象。

##  <a name="isempty"></a>  CRBTree::IsEmpty

调用此方法来测试一个空的树对象。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果在树格式不为空，则返回 FALSE，则返回 TRUE。

##  <a name="kinargtype"></a>  CRBTree::KINARGTYPE

作为输入参数传递一个键时所使用的类型。

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CRBTree::KOUTARGTYPE

作为输出参数返回一个密钥时所使用的类型。

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="removeall"></a>  CRBTree::RemoveAll

调用此方法来删除中的所有元素`CRBTree`对象。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>备注

清除`CRBTree`对象，释放内存用于存储元素。

##  <a name="removeat"></a>  CRBTree::RemoveAt

调用此方法来删除中的给定位置处的元素`CRBTree`对象。

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
如以前调用方法所返回的位置计数器[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。

### <a name="remarks"></a>备注

删除存储在指定位置处的键/值对。 释放用于将元素存储的内存。 位置引用*pos*将变为无效，并在树中任何其他元素的位置保持有效，它们不一定是执行操作时保留相同的顺序。

##  <a name="setvalueat"></a>  CRBTree::SetValueAt

调用此方法来更改存储中给定位置处的值`CRBTree`对象。

```
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>参数

*pos*<br/>
如以前调用方法所返回的位置计数器[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。

*value*<br/>
要添加到值`CRBTree`对象。

### <a name="remarks"></a>备注

更改存储中的指定位置的值元素`CRBTree`对象。

##  <a name="vinargtype"></a>  CRBTree::VINARGTYPE

将值传递作为输入参数时所使用的类型。

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CRBTree::VOUTARGTYPE

作为输出参数传递一个值时所使用的类型。

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
