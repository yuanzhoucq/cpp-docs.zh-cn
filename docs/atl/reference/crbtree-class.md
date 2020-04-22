---
title: CRBTree 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
ms.openlocfilehash: 58c001ccef35d4265ef5b7fe200654781f130872
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746577"
---
# <a name="crbtree-class"></a>CRBTree 类

此类提供了创建和使用红黑树的方法。

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
键元素类型。

*五*<br/>
值元素类型。

*克瓦次克*<br/>
用于复制或移动关键元素的代码。 有关详细信息[，请参阅 CElementTraits 类](../../atl/reference/celementtraits-class.md)。

*VTraits*<br/>
用于复制或移动值元素的代码。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CRBTree：：金纳格](#kinargtype)|当将键作为输入参数传递时使用的类型。|
|[CRBTree：：库塔格格](#koutargtype)|当将键返回为输出参数时使用的类型。|
|[CRBTree：：维纳格](#vinargtype)|当值作为输入参数传递时使用的类型。|
|[CRBTree：：VOUTARGTYPE](#voutargtype)|当值作为输出参数传递时使用的类型。|

### <a name="public-classes"></a>公共类

|名称|说明|
|----------|-----------------|
|[CRBTree：CPair 类](#cpair_class)|包含键和值元素的类。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CRBTree：*CRBTree](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CRBTree：：查找第一键后](#findfirstkeyafter)|调用此方法以查找使用下一个可用键的元素的位置。|
|[CRBTree：：获取](#getat)|调用此方法以获取树中给定位置的元素。|
|[CRBTree：获取计数](#getcount)|调用此方法获取树中的元素数。|
|[CRBTree：获取头位置](#getheadposition)|调用此方法以获取树头处元素的位置值。|
|[CRBTree：：获取键](#getkeyat)|调用此方法从树中的给定位置获取密钥。|
|[CRBTree：：获取下一个](#getnext)|调用此方法以获取指向存储在对象中的元素的`CRBTree`指针，并将位置推进到下一个元素。|
|[CRBTree：：获取NextAssoc](#getnextassoc)|调用此方法获取存储在地图中的元素的键和值，并将位置推进到下一个元素。|
|[CRBTree：：获取下一个密钥](#getnextkey)|调用此方法获取存储在树中的元素的键，并将位置推进到下一个元素。|
|[CRBTree：获取下一个价值](#getnextvalue)|调用此方法获取存储在树中的元素的值，并将位置推进到下一个元素。|
|[CRBTree：：GetPrev](#getprev)|调用此方法以获取指向存储在对象中的元素的`CRBTree`指针，然后将位置更新为上一个元素。|
|[CRBTree：：获取尾部位置](#gettailposition)|调用此方法以获取树尾处元素的位置值。|
|[CRBTree：：获取价值](#getvalueat)|调用此方法以检索存储在`CRBTree`对象中给定位置的值。|
|[CRBTree：：空](#isempty)|调用此方法以测试空树对象。|
|[CRBTree：：删除所有](#removeall)|调用此方法从`CRBTree`对象中删除所有元素。|
|[CRBTree：：删除At](#removeat)|调用此方法以删除对象中给定位置的元素`CRBTree`。|
|[CRBTree：：设置价值](#setvalueat)|调用此方法以更改存储在对象中给定位置的值`CRBTree`。|

## <a name="remarks"></a>备注

红黑树是一种二进制搜索树，它每个节点使用额外的信息，以确保它保持"平衡"，也就是说，树的高度不会增长过大，并影响性能。

此模板类被设计为由[CRBMap](../../atl/reference/crbmap-class.md)和[CRBMultiMap](../../atl/reference/crbmultimap-class.md)使用。 构成这些派生类的大部分方法由 提供`CRBTree`。

有关各种集合类及其特性和性能特征的更完整的讨论，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a>CRBTree：CPair 类

包含键和值元素的类。

```
class CPair : public __POSITION
```

### <a name="remarks"></a>备注

此类由[CRBTree：getAt、CRBTree：getNext](#getat)和[CRBTree：GetPrev](#getprev)的方法使用，以访问存储在树结构中的键和值元素。 [CRBTree::GetNext](#getnext)

成员如下：

|||
|-|-|
|`m_key`|存储键元素的数据成员。|
|`m_value`|存储值元素的数据成员。|

## <a name="crbtreecrbtree"></a><a name="dtor"></a>CRBTree：*CRBTree

析构函数。

```
~CRBTree() throw();
```

### <a name="remarks"></a>备注

释放任何分配的资源。 调用[CRBTree：：删除所有](#removeall)元素以删除所有元素。

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a>CRBTree：：查找第一键后

调用此方法以查找使用下一个可用键的元素的位置。

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>参数

*键*<br/>
键值。

### <a name="return-value"></a>返回值

返回使用下一个可用键的元素的位置值。 如果没有更多元素，则返回 NULL。

### <a name="remarks"></a>备注

此方法便于遍历树，而无需事先计算位置值。

## <a name="crbtreegetat"></a><a name="getat"></a>CRBTree：：获取

调用此方法以获取树中给定位置的元素。

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置值。

*键*<br/>
接收密钥的变量。

*value*<br/>
接收值的变量。

### <a name="return-value"></a>返回值

前两个窗体返回指向[CPair](#cpair_class)的指针。 第三种形式获取给定位置的键和值。

### <a name="remarks"></a>备注

位置值以前可以通过调用[CRBTree：获取头位置](#getheadposition)或[CRBTree：：获取尾位](#gettailposition)等方法来确定。

在调试生成中，如果*pos*等于 NULL，则会发生断言失败。

## <a name="crbtreegetcount"></a><a name="getcount"></a>CRBTree：获取计数

调用此方法获取树中的元素数。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回树中存储的元素数（每个键/值对是一个元素）。

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a>CRBTree：获取头位置

调用此方法以获取树头处元素的位置值。

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>返回值

返回树头处元素的位置值。

### <a name="remarks"></a>备注

返回`GetHeadPosition`的值可用于[CRBTree：getKeyAt](#getkeyat)或[CRBTree：GetNext](#getnext)遍历树并检索值等方法。

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a>CRBTree：：获取键

调用此方法从树中的给定位置获取密钥。

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置值。

### <a name="return-value"></a>返回值

返回存储在树中*位置位置*的键。

### <a name="remarks"></a>备注

如果*pos*不是有效的位置值，则结果不可预测。 在调试生成中，如果*pos*等于 NULL，则会发生断言失败。

## <a name="crbtreegetnext"></a><a name="getnext"></a>CRBTree：：获取下一个

调用此方法以获取指向存储在对象中的元素的`CRBTree`指针，并将位置推进到下一个元素。

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由以前对[CRBTree 方法的调用返回：获取头位置](#getheadposition)或[CRBTree：：查找第一键后](#findfirstkeyafter)。

### <a name="return-value"></a>返回值

返回指向树中下一个[CPair](#cpair_class)值的指针。

### <a name="remarks"></a>备注

每次调用后，将更新*pos*位置计数器。 如果检索到的元素是树中的最后一个元素，*则 pos*设置为 NULL。

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a>CRBTree：：获取NextAssoc

调用此方法获取存储在地图中的元素的键和值，并将位置推进到下一个元素。

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由以前对[CRBTree 方法的调用返回：获取头位置](#getheadposition)或[CRBTree：：查找第一键后](#findfirstkeyafter)。

*键*<br/>
指定树键类型的模板参数。

*value*<br/>
指定树值类型的模板参数。

### <a name="remarks"></a>备注

每次调用后，将更新*pos*位置计数器。 如果检索到的元素是树中的最后一个元素，*则 pos*设置为 NULL。

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a>CRBTree：：获取下一个密钥

调用此方法获取存储在树中的元素的键，并将位置推进到下一个元素。

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由以前对[CRBTree 方法的调用返回：获取头位置](#getheadposition)或[CRBTree：：查找第一键后](#findfirstkeyafter)。

### <a name="return-value"></a>返回值

返回对树中下一个键的引用。

### <a name="remarks"></a>备注

更新当前位置计数器，*位置*。如果树中不再有条目，则位置计数器将设置为 NULL。

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a>CRBTree：获取下一个价值

调用此方法获取存储在树中的元素的值，并将位置推进到下一个元素。

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由以前对[CRBTree 方法的调用返回：获取头位置](#getheadposition)或[CRBTree：：查找第一键后](#findfirstkeyafter)。

### <a name="return-value"></a>返回值

返回对树中下一个值的引用。

### <a name="remarks"></a>备注

更新当前位置计数器，*位置*。如果树中不再有条目，则位置计数器将设置为 NULL。

## <a name="crbtreegetprev"></a><a name="getprev"></a>CRBTree：：GetPrev

调用此方法以获取指向存储在对象中的元素的`CRBTree`指针，然后将位置更新为上一个元素。

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由以前对[CRBTree 方法的调用返回：获取头位置](#getheadposition)或[CRBTree：：查找第一键后](#findfirstkeyafter)。

### <a name="return-value"></a>返回值

返回指向树中存储的上一个[CPair](#cpair_class)值的指针。

### <a name="remarks"></a>备注

更新当前位置计数器，*位置*。如果树中不再有条目，则位置计数器将设置为 NULL。

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a>CRBTree：：获取尾部位置

调用此方法以获取树尾处元素的位置值。

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>返回值

返回树尾处元素的位置值。

### <a name="remarks"></a>备注

返回`GetTailPosition`的值可用于[CRBTree：getKeyAt](#getkeyat)或[CRBTree：GetPrev](#getprev)遍历树并检索值等方法。

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a>CRBTree：：获取价值

调用此方法以检索存储在`CRBTree`对象中给定位置的值。

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由以前对[CRBTree 方法的调用返回：获取头位置](#getheadposition)或[CRBTree：：查找第一键后](#findfirstkeyafter)。

### <a name="return-value"></a>返回值

返回对存储在对象中给定位置的值的`CRBTree`引用。

## <a name="crbtreeisempty"></a><a name="isempty"></a>CRBTree：：空

调用此方法以测试空树对象。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果树为空，则返回 TRUE，否则返回 FALSE。

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a>CRBTree：：金纳格

当将键作为输入参数传递时使用的类型。

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a>CRBTree：：库塔格格

当将键返回为输出参数时使用的类型。

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a>CRBTree：：删除所有

调用此方法从`CRBTree`对象中删除所有元素。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>备注

清除对象，`CRBTree`释放用于存储元素的内存。

## <a name="crbtreeremoveat"></a><a name="removeat"></a>CRBTree：：删除At

调用此方法以删除对象中给定位置的元素`CRBTree`。

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由以前对[CRBTree 方法的调用返回：获取头位置](#getheadposition)或[CRBTree：：查找第一键后](#findfirstkeyafter)。

### <a name="remarks"></a>备注

删除存储在指定位置的键/值对。 释放用于存储元素的内存。 *pos*引用的定位将变为无效，虽然树中任何其他元素的定位仍然有效，但它们不一定保留相同的顺序。

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a>CRBTree：：设置价值

调用此方法以更改存储在对象中给定位置的值`CRBTree`。

```cpp
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由以前对[CRBTree 方法的调用返回：获取头位置](#getheadposition)或[CRBTree：：查找第一键后](#findfirstkeyafter)。

*value*<br/>
要添加到对象的值`CRBTree`。

### <a name="remarks"></a>备注

更改存储在`CRBTree`对象中给定位置的值元素。

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a>CRBTree：：维纳格

当值作为输入参数传递时使用的类型。

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a>CRBTree：：VOUTARGTYPE

当值作为输出参数传递时使用的类型。

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
