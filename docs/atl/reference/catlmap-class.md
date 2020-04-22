---
title: CAtlMap 类
ms.date: 11/04/2016
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
ms.openlocfilehash: 8954eeae28f13fb50643646b41c032588ecc278f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748665"
---
# <a name="catlmap-class"></a>CAtlMap 类

此类提供创建和管理地图对象的方法。

## <a name="syntax"></a>语法

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
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
|[CAtlMap：：金纳格](#kinargtype)|当将键作为输入参数传递时使用的类型|
|[CAtlMap：库塔格格](#koutargtype)|当将键返回为输出参数时使用的类型。|
|[CAtlMap：：维纳格](#vinargtype)|当值作为输入参数传递时使用的类型。|
|[CAtlMap：：VOUTARGTYPE](#voutargtype)|当值作为输出参数传递时使用的类型。|

### <a name="public-classes"></a>公共类

|名称|说明|
|----------|-----------------|
|[CAtlMap：CPair 类](#cpair_class)|包含键和值元素的类。|

### <a name="cpair-data-members"></a>CPair 数据成员

|名称|说明|
|----------|-----------------|
|[CPair：：m_key](#m_key)|存储键元素的数据成员。|
|[CPair：m_value](#m_value)|存储值元素的数据成员。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlMap：CAtlMap](#catlmap)|构造函数。|
|[CAtlMap：_CAtlMap](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlMap：：断言有效](#assertvalid)|如果 无效，`CAtlMap`请调用此方法以引起 ASSERT。|
|[CAtlMap：:D可自动重新哈希](#disableautorehash)|调用此方法以禁用`CAtlMap`对象的自动重新哈希。|
|[CAtlMap：启用自动恢复哈希](#enableautorehash)|调用此方法以启用`CAtlMap`对象的自动重新哈希。|
|[CAtlMap：GetAt](#getat)|调用此方法以在地图中指定位置返回元素。|
|[CAtlMap：获取计数](#getcount)|调用此方法以检索映射中的元素数。|
|[CAtlMap：获取哈希表大小](#gethashtablesize)|调用此方法以确定地图哈希表中的条柱数。|
|[CAtlMap：获取键](#getkeyat)|调用此方法以检索存储在对象中给定位置的`CAtlMap`键。|
|[CAtlMap：获取下一个](#getnext)|调用此方法以获取指向存储在对象中的下一个元素对的`CAtlMap`指针。|
|[CAtlMap：getNextAssoc](#getnextassoc)|获取下一个迭代元素。|
|[CAtlMap：获取下一个键](#getnextkey)|调用此方法从对象检索下一个`CAtlMap`键。|
|[CAtlMap：获取下一个值](#getnextvalue)|调用此方法从`CAtlMap`对象获取下一个值。|
|[CAtlMap：获取起始位置](#getstartposition)|调用此方法以启动映射迭代。|
|[CAtlMap：获取价值At](#getvalueat)|调用此方法以检索存储在`CAtlMap`对象中给定位置的值。|
|[CAtlMap：initHashTable](#inithashtable)|调用此方法以初始化哈希表。|
|[CAtlMap：：空](#isempty)|调用此方法以测试空地图对象。|
|[CAtlMap：：查找](#lookup)|调用此方法以查找对象中的`CAtlMap`键或值。|
|[CAtlMap：rehash](#rehash)|调用此方法以重新哈希`CAtlMap`对象。|
|[CAtlMap：删除所有](#removeall)|调用此方法从`CAtlMap`对象中删除所有元素。|
|[CAtlMap：：删除AtPos](#removeatpos)|调用此方法以删除对象中给定位置的元素`CAtlMap`。|
|[CAtlMap：：删除键](#removekey)|调用此方法以在给定键的情况下从`CAtlMap`对象中删除元素。|
|[CAtlMap：setat](#setat)|调用此方法以将元素对插入到地图中。|
|[CAtlMap：：设置最佳加载](#setoptimalload)|调用此方法以设置`CAtlMap`对象的最佳负载。|
|[CAtlMap：：设置价值At](#setvalueat)|调用此方法以更改存储在对象中给定位置的值`CAtlMap`。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|替换 或向 添加新`CAtlMap`元素。|

## <a name="remarks"></a>备注

`CAtlMap`支持任何给定类型的映射数组，管理键元素及其关联值的无序数组。 元素（由键和值组成）使用哈希算法存储，从而能够高效地存储和检索大量数据。

*KTraits*和*VTraits*参数是包含复制或移动元素所需的任何补充代码的特征类。

`CAtlMap` [CRBMap](../../atl/reference/crbmap-class.md)类提供了替代项。 `CRBMap`还存储键/值对，但表现出不同的性能特征。 插入项、查找键或从`CRBMap`对象中删除键所花时间是顺序*日志（n），* 其中*n*是元素数。 对于`CAtlMap`，所有这些操作通常需要恒定的时间，尽管最坏情况可能是顺序*为 n*。 因此，在典型情况下，`CAtlMap`速度更快。

和`CRBMap``CAtlMap`之间的另一个区别在遍历存储的元素时变得明显。 在`CRBMap`中，按排序的顺序访问元素。 在`CAtlMap`中，元素未排序，无法推断任何顺序。

当需要存储少量元素时，请考虑改用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap：：断言有效

如果对象无效，`CAtlMap`调用此方法以导致 ASSERT。

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>备注

在调试生成中，如果对象无效，`CAtlMap`此方法将导致 ASSERT。

### <a name="example"></a>示例

请参阅[CAtlMap：：CAtlMap](#catlmap)的示例。

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap：CAtlMap

构造函数。

```
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>参数

*n宾斯*<br/>
提供指向存储元素的指针的条柱数。 有关 bin 的说明，请参阅本主题后面的备注。

*f优负荷*<br/>
最佳负载比。

*fLo阈值*<br/>
负载比的较低阈值。

*fHiThreshold*<br/>
负载比的上限。

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

`CAtlMap`通过首先在键上使用哈希算法创建索引来引用其所有存储的元素。 此索引引用包含指向存储元素的指针的"bin"。 如果 bin 已在使用中，则创建链接列表以访问后续元素。 遍历列表比直接访问正确的元素要慢，因此映射结构需要平衡存储要求和性能。 在大多数情况下，选择默认参数以提供良好的结果。

负载比率是条柱数与存储在地图对象中的元素数的比率。 重新计算地图结构时 *，fOptimalLoad*参数值将用于计算所需的条柱数。 可以使用[CAtlMap：set 优加载](#setoptimalload)方法更改此值。

*fLoThreshold*参数是负载比可以达到的较低值，在重新`CAtlMap`计算地图的最佳大小之前。

*fHiThreshold*参数是负载比在`CAtlMap`对象重新计算地图的最佳大小之前可以达到的上限值。

默认情况下，此重新计算过程（称为重新哈希）处于启用状态。 如果要禁用此过程（也许在一次输入大量数据时），请调用[CAtlMap：:D可自动重新哈希](#disableautorehash)方法。 使用[CAtlMap：：启用自动重哈希](#enableautorehash)方法重新激活它。

*nBlockSize*参数是需要新元素时分配的内存量的度量。 较大的块大小减少了对内存分配例程的调用，但使用的资源更多。

在存储任何数据之前，必须使用调用[CAtlMap：：：initHashTable](#inithashtable)来初始化哈希表。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap：_CAtlMap

析构函数。

```
~CAtlMap() throw();
```

### <a name="remarks"></a>备注

释放任何分配的资源。

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap：CPair 类

包含键和值元素的类。

```
class CPair : public __POSITION
```

### <a name="remarks"></a>备注

类由[CAtlMap：：GetNext](#getnext)和[CAtlMap：查找](#lookup)来访问映射结构中存储的键和值元素的方法。

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap：:D可自动重新哈希

调用此方法以禁用`CAtlMap`对象的自动重新哈希。

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>备注

启用自动重新哈希时（默认情况下，如果负载值（条柱数与数组中存储的元素数的比率）超过创建映射时指定的最大值或最小值，则哈希表中的条柱数将自动重新计算。

`DisableAutoRehash`当大量元素一次添加到地图中时，最有用。 在每次超出限制时，不要触发重新哈希过程，而是更高效地调用`DisableAutoRehash`、添加元素，最后调用[CAtlMap：：启用AutoRehash](#enableautorehash)。

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap：启用自动恢复哈希

调用此方法以启用`CAtlMap`对象的自动重新哈希。

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>备注

启用自动重新哈希时（默认情况下，如果负载值（条柱数与数组中存储的元素数的比率）超过创建地图时指定的最大值或最小值，则哈希表中的条柱数将自动重新计算。

`EnableAutoRefresh`最常在调用[CAtlMap：:D可自动恢复哈希](#disableautorehash)后使用。

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap：GetAt

调用此方法以在地图中指定位置返回元素。

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由之前调用[CAtlMap 返回：：获取NextAssoc](#getnextassoc)或[CAtlMap：：获取起始位置](#getstartposition)。

*键*<br/>
指定地图键类型的模板参数。

*value*<br/>
指定地图值类型的模板参数。

### <a name="return-value"></a>返回值

返回指向地图中存储的当前键/值元素对的指针。

### <a name="remarks"></a>备注

在调试生成中，如果*pos*等于 NULL，则会发生断言错误。

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap：获取计数

调用此方法以检索映射中的元素数。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回地图对象中的元素数。 单个元素是键/值对。

### <a name="example"></a>示例

请参阅[CAtlMap：：CAtlMap](#catlmap)的示例。

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap：获取哈希表大小

调用此方法以确定地图哈希表中的条柱数。

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>返回值

返回哈希表中的条柱数。 有关说明，请参阅[CAtlMap：CAtlMap。](#catlmap)

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap：获取键

调用此方法以检索存储在对象中给定位置的`CAtlMap`键。

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由之前调用[CAtlMap 返回：：获取NextAssoc](#getnextassoc)或[CAtlMap：：获取起始位置](#getstartposition)。

### <a name="return-value"></a>返回值

返回对存储在对象中给定位置的键的`CAtlMap`引用。

### <a name="example"></a>示例

请参阅[CAtlMap：：CAtlMap](#catlmap)的示例。

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap：获取下一个

调用此方法以获取指向存储在对象中的下一个元素对的`CAtlMap`指针。

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由之前调用[CAtlMap 返回：：获取NextAssoc](#getnextassoc)或[CAtlMap：：获取起始位置](#getstartposition)。

### <a name="return-value"></a>返回值

返回指向存储在地图中的下一对键/值元素的指针。 每次调用后，将更新*pos*位置计数器。 如果检索到的元素是地图中的最后一个元素，*则 pos*设置为 NULL。

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap：getNextAssoc

获取下一个迭代元素。

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由之前调用[CAtlMap 返回：：获取NextAssoc](#getnextassoc)或[CAtlMap：：获取起始位置](#getstartposition)。

*键*<br/>
指定地图键类型的模板参数。

*value*<br/>
指定地图值类型的模板参数。

### <a name="remarks"></a>备注

每次调用后，将更新*pos*位置计数器。 如果检索到的元素是地图中的最后一个元素，*则 pos*设置为 NULL。

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap：获取下一个键

调用此方法从对象检索下一个`CAtlMap`键。

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由之前调用[CAtlMap 返回：：获取NextAssoc](#getnextassoc)或[CAtlMap：：获取起始位置](#getstartposition)。

### <a name="return-value"></a>返回值

返回对地图中下一个键的引用。

### <a name="remarks"></a>备注

更新当前位置计数器，*位置*。如果地图中没有更多的条目，则位置计数器将设置为 NULL。

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap：获取下一个值

调用此方法从`CAtlMap`对象获取下一个值。

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由之前调用[CAtlMap 返回：：获取NextAssoc](#getnextassoc)或[CAtlMap：：获取起始位置](#getstartposition)。

### <a name="return-value"></a>返回值

返回对地图中下一个值的引用。

### <a name="remarks"></a>备注

更新当前位置计数器，*位置*。如果地图中没有更多的条目，则位置计数器将设置为 NULL。

### <a name="example"></a>示例

请参阅[CAtlMap：：CAtlMap](#catlmap)的示例。

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap：获取起始位置

调用此方法以启动映射迭代。

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>返回值

返回起始位置，如果地图为空，则返回 NULL。

### <a name="remarks"></a>备注

调用此方法通过返回可以传递给`GetNextAssoc`方法的"位置"值来启动映射迭代。

> [!NOTE]
> 迭代序列是不可预测的

### <a name="example"></a>示例

请参阅[CAtlMap：：CAtlMap](#catlmap)的示例。

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap：获取价值At

调用此方法以检索存储在`CAtlMap`对象中给定位置的值。

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由之前调用[CAtlMap 返回：：获取NextAssoc](#getnextassoc)或[CAtlMap：：获取起始位置](#getstartposition)。

### <a name="return-value"></a>返回值

返回对存储在对象中给定位置的值的`CAtlMap`引用。

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap：initHashTable

调用此方法以初始化哈希表。

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>参数

*n宾斯*<br/>
哈希表使用的条柱数。 有关说明，请参阅[CAtlMap：CAtlMap。](#catlmap)

*巴洛克现在*<br/>
应分配内存的标志指示。

### <a name="return-value"></a>返回值

成功初始化时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

`InitHashTable`在哈希表中存储任何元素之前，必须调用。  如果未显式调用此方法，则首次使用`CAtlMap`构造函数指定的 bin 计数添加元素时将自动调用它。  否则，将使用*nBins*参数指定的新 bin 计数初始化地图。

如果*bAllocNow*参数为 false，则哈希表所需的内存在首次需要之前不会分配。 如果不确定是否将使用地图，则此功能非常有用。

### <a name="example"></a>示例

请参阅[CAtlMap：：CAtlMap](#catlmap)的示例。

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap：：空

调用此方法以测试空地图对象。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果地图为空，则返回 TRUE，否则返回 FALSE。

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap：：金纳格

当将键作为输入参数传递时使用的类型。

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap：库塔格格

当将键返回为输出参数时使用的类型。

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap：：查找

调用此方法以查找对象中的`CAtlMap`键或值。

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*键*<br/>
指定标识要备份的元素的键。

*value*<br/>
接收上值的变量。

### <a name="return-value"></a>返回值

如果找到键，则方法的第一种形式返回 true，否则为 false。 第二个和第三个窗体返回指向[CPair](#cpair_class)的指针，该指针可用作调用[CAtlMap：：getNext](#getnext)等的位置。

### <a name="remarks"></a>备注

`Lookup`使用散列算法快速查找包含与给定键参数完全匹配的键的映射元素。

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap：：运算符\[\]

替换 或向 添加新`CAtlMap`元素。

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>参数

*键*<br/>
要添加或替换的元素的键。

### <a name="return-value"></a>返回值

返回对与给定键关联的值的引用。

### <a name="example"></a>示例

如果密钥已存在，则替换该元素。 如果密钥不存在，则添加新元素。 请参阅[CAtlMap：：CAtlMap](#catlmap)的示例。

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap：rehash

调用此方法以重新哈希`CAtlMap`对象。

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>参数

*n宾斯*<br/>
要在哈希表中使用的新条柱数。 有关说明，请参阅[CAtlMap：CAtlMap。](#catlmap)

### <a name="remarks"></a>备注

如果*nBins*为`CAtlMap`0，则根据地图中的元素数和最佳负载设置计算合理的数字。 通常，重新哈希过程是自动的，但如果调用[了 CAtlMap：:D可自动重新哈希](#disableautorehash)，则此方法将执行必要的调整大小。

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap：删除所有

调用此方法从`CAtlMap`对象中删除所有元素。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>备注

清除对象，`CAtlMap`释放用于存储元素的内存。

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap：：删除AtPos

调用此方法以删除对象中给定位置的元素`CAtlMap`。

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由之前调用[CAtlMap 返回：：获取NextAssoc](#getnextassoc)或[CAtlMap：：获取起始位置](#getstartposition)。

### <a name="remarks"></a>备注

删除存储在指定位置的键/值对。 释放用于存储元素的内存。 *pos*引用的定位将变为无效，虽然地图中任何其他元素的定位仍然有效，但它们不一定保留相同的顺序。

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap：：删除键

调用此方法以在给定键的情况下从`CAtlMap`对象中删除元素。

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*键*<br/>
与要删除的元素对对应的键。

### <a name="return-value"></a>返回值

如果找到并删除密钥，则返回 TRUE，在发生故障时返回 FALSE。

### <a name="example"></a>示例

请参阅[CAtlMap：：CAtlMap](#catlmap)的示例。

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap：setat

调用此方法以将元素对插入到地图中。

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>参数

*键*<br/>
要添加到`CAtlMap`对象的键值。

*value*<br/>
要添加到对象的值`CAtlMap`。

### <a name="return-value"></a>返回值

返回键/值元素对在对象中`CAtlMap`的位置。

### <a name="remarks"></a>备注

`SetAt`如果找到匹配的键，则替换现有元素。 如果未找到该键，则创建新的键/值对。

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap：：设置最佳加载

调用此方法以设置`CAtlMap`对象的最佳负载。

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>参数

*f优负荷*<br/>
最佳负载比。

*fLo阈值*<br/>
负载比的较低阈值。

*fHiThreshold*<br/>
负载比的上限。

*b 雷哈什现在*<br/>
指示是否应重新计算哈希表的标志。

### <a name="remarks"></a>备注

此方法重新定义`CAtlMap`对象的最佳负载值。 有关各种参数的讨论，请参阅[CAtlMap：CAtlMap。](#catlmap) 如果*bRehashNow*为 true，并且元素数超出最小值和最大值，则重新计算哈希表。

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap：：设置价值At

调用此方法以更改存储在对象中给定位置的值`CAtlMap`。

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>参数

*Pos*<br/>
位置计数器，由之前调用[CAtlMap 返回：：获取NextAssoc](#getnextassoc)或[CAtlMap：：获取起始位置](#getstartposition)。

*value*<br/>
要添加到对象的值`CAtlMap`。

### <a name="remarks"></a>备注

更改存储在`CAtlMap`对象中给定位置的值元素。

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap：：维纳格

当值作为输入参数传递时使用的类型。

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap：：VOUTARGTYPE

当值作为输出参数传递时使用的类型。

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap：CPair：：m_key

存储键元素的数据成员。

```
const K m_key;
```

### <a name="parameters"></a>参数

*K*<br/>
键元素类型。

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap：CPair：：m_value

存储值元素的数据成员。

```
V  m_value;
```

### <a name="parameters"></a>参数

*五*<br/>
值元素类型。

## <a name="see-also"></a>请参阅

[选框示例](../../overview/visual-cpp-samples.md)<br/>
[更新PV示例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[类概述](../../atl/atl-class-overview.md)
