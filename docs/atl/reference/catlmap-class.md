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
ms.openlocfilehash: b79e6cbd796569e6ba11c96158099de6c30b310a
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168054"
---
# <a name="catlmap-class"></a>CAtlMap 类

此类提供用于创建和管理地图对象的方法。

## <a name="syntax"></a>语法

```cpp
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

### <a name="parameters"></a>参数

*温度*<br/>
键元素类型。

*向量*<br/>
值元素类型。

*KTraits*<br/>
用于复制或移动关键元素的代码。 有关更多详细信息，请参阅[CElementTraits 类](../../atl/reference/celementtraits-class.md)。

*VTraits*<br/>
用于复制或移动值元素的代码。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CAtlMap：： KINARGTYPE](#kinargtype)|键作为输入参数传递时使用的类型|
|[CAtlMap：： KOUTARGTYPE](#koutargtype)|当键作为输出参数返回时使用的类型。|
|[CAtlMap：： VINARGTYPE](#vinargtype)|将值作为输入参数传递时使用的类型。|
|[CAtlMap：： VOUTARGTYPE](#voutargtype)|将值作为输出参数传递时使用的类型。|

### <a name="public-classes"></a>公共类

|名称|说明|
|----------|-----------------|
|[CAtlMap：： CPair 类](#cpair_class)|一个包含键和值元素的类。|

### <a name="cpair-data-members"></a>CPair 数据成员

|名称|说明|
|----------|-----------------|
|[CPair：： m_key](#m_key)|存储密钥元素的数据成员。|
|[CPair：： m_value](#m_value)|存储 value 元素的数据成员。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlMap：： CAtlMap](#catlmap)|构造函数。|
|[CAtlMap：： ~ CAtlMap](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlMap：： AssertValid](#assertvalid)|如果`CAtlMap`无效，则调用此方法以引发断言。|
|[CAtlMap：:D isableAutoRehash](#disableautorehash)|调用此方法可禁用`CAtlMap`对象的自动 rehashing。|
|[CAtlMap：： EnableAutoRehash](#enableautorehash)|调用此方法以启用`CAtlMap`对象的自动 rehashing。|
|[CAtlMap：： GetAt](#getat)|调用此方法可在映射中的指定位置返回元素。|
|[CAtlMap：： GetCount](#getcount)|调用此方法可检索映射中的元素数。|
|[CAtlMap：： GetHashTableSize](#gethashtablesize)|调用此方法以确定地图的哈希表中的储箱数。|
|[CAtlMap：： GetKeyAt](#getkeyat)|调用此方法可以检索存储在`CAtlMap`对象中的给定位置的键。|
|[CAtlMap：： GetNext](#getnext)|调用此方法以获取指向存储在`CAtlMap`对象中的下一个元素对的指针。|
|[CAtlMap：： GetNextAssoc](#getnextassoc)|获取用于循环访问的下一个元素。|
|[CAtlMap：： GetNextKey](#getnextkey)|调用此方法从`CAtlMap`对象中检索下一个键。|
|[CAtlMap：： GetNextValue](#getnextvalue)|调用此方法可从`CAtlMap`对象获取下一个值。|
|[CAtlMap：： GetStartPosition](#getstartposition)|调用此方法以启动地图迭代。|
|[CAtlMap：： GetValueAt](#getvalueat)|调用此方法可以检索存储在`CAtlMap`对象中的指定位置的值。|
|[CAtlMap：： InitHashTable](#inithashtable)|调用此方法可初始化哈希表。|
|[CAtlMap：： IsEmpty](#isempty)|调用此方法可测试空的地图对象。|
|[CAtlMap：： Lookup](#lookup)|调用此方法可查找对象中的`CAtlMap`键或值。|
|[CAtlMap：： Rehash](#rehash)|调用此方法来 rehash `CAtlMap`对象。|
|[CAtlMap：： RemoveAll](#removeall)|调用此方法可从`CAtlMap`对象中移除所有元素。|
|[CAtlMap：： RemoveAtPos](#removeatpos)|调用此方法可删除`CAtlMap`对象中给定位置的元素。|
|[CAtlMap：： RemoveKey](#removekey)|调用此方法可从`CAtlMap`对象中删除元素（给定键）。|
|[CAtlMap：： SetAt](#setat)|调用此方法可将元素对插入到映射中。|
|[CAtlMap：： SetOptimalLoad](#setoptimalload)|调用此方法可设置`CAtlMap`对象的最佳负载。|
|[CAtlMap：： SetValueAt](#setvalueat)|调用此方法可更改存储在`CAtlMap`对象中指定位置的值。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|替换或将新元素添加到中`CAtlMap`。|

## <a name="remarks"></a>备注

`CAtlMap`提供对任意给定类型的映射数组的支持，并管理关键元素的无序数组及其关联值。 使用哈希算法存储元素（包含键和值），允许有效地存储和检索大量数据。

*KTraits*和*VTraits*参数是包含复制或移动元素所需的任何补充代码的特征类。

CRBMap 类提供`CAtlMap`的替代方法。 [CRBMap](../../atl/reference/crbmap-class.md) `CRBMap`还存储键/值对，但具有不同的性能特征。 插入项、查找项或从`CRBMap`对象中删除键所需的时间为 order *log （n）*，其中*n*是元素的数目。 对于`CAtlMap`，所有这些操作通常会花费很长时间，但最糟糕的情况是订单*n*。 因此，在典型情况下， `CAtlMap`速度更快。

循环访问存储的`CRBMap`元素`CAtlMap`时，和之间的另一个差异变得明显。 在中`CRBMap`，按排序顺序访问元素。 在中`CAtlMap`，不会对元素进行排序，并且不能推断顺序。

需要存储少量的元素时，请考虑改用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。

有关详细信息，请参阅[ATL Collection 类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap：： AssertValid

如果`CAtlMap`对象无效，则调用此方法以引发断言。

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>备注

在调试版本中，如果`CAtlMap`对象无效，此方法将导致断言。

### <a name="example"></a>示例

请参阅[CAtlMap：： CAtlMap](#catlmap)的示例。

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap：： CAtlMap

构造函数。

```cpp
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>参数

*nBins*<br/>
提供指向存储元素的指针的箱数。 有关 bin 的说明，请参阅本主题后面的 "备注"。

*fOptimalLoad*<br/>
最佳负载比。

*fLoThreshold*<br/>
负载比率的下限阈值。

*fHiThreshold*<br/>
负载比阈值的上限。

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

`CAtlMap`通过先使用密钥的哈希算法创建索引，引用其所有存储元素。 此索引引用 "bin"，其中包含指向存储元素的指针。 如果 bin 已在使用，则将创建一个链接列表来访问后续元素。 遍历列表比直接访问正确的元素更慢，因此，地图结构需要根据性能来平衡存储要求。 在大多数情况下，已选择默认参数以获得良好的结果。

负载比是地图对象中存储的元素数的比率。 重新计算地图结构时，将使用*fOptimalLoad*参数值计算所需的储箱数。 可以使用[CAtlMap：： SetOptimalLoad](#setoptimalload)方法更改此值。

*FLoThreshold*参数是负载比在重新计算地图的最佳大小之前`CAtlMap`可以达到的较小值。

*FHiThreshold*参数是在`CAtlMap`对象重新计算地图的最佳大小之前，负载比可以达到的上限值。

默认情况下，将启用此重新计算过程（称为 rehashing）。 如果要禁用此进程，可能在一次输入大量数据时调用[CAtlMap：:D isableautorehash](#disableautorehash)方法。 用[CAtlMap：： EnableAutoRehash](#enableautorehash)方法重新激活它。

*NBlockSize*参数是在需要新元素时分配的内存量的度量值。 较大的块大小可减少对内存分配例程的调用，但会占用更多资源。

在可以存储任何数据之前，必须使用对[CAtlMap：： InitHashTable](#inithashtable)的调用来初始化哈希表。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap：： ~ CAtlMap

析构函数。

```cpp
~CAtlMap() throw();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap：： CPair 类

一个包含键和值元素的类。

```cpp
class CPair : public __POSITION
```

### <a name="remarks"></a>备注

此类由[CAtlMap：： GetNext](#getnext)和[CAtlMap：： Lookup](#lookup)方法用来访问存储在映射结构中的键和值元素。

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap：:D isableAutoRehash

调用此方法可禁用`CAtlMap`对象的自动 rehashing。

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>备注

启用自动 rehashing 时（默认设置），如果负载值（储箱数到数组中存储的元素数的比率）超过创建映射时指定的最大值或最小值，则将自动重新计算哈希表中的储箱数。

`DisableAutoRehash`当将大量元素同时添加到地图时，最有用。 不会在每次超出限制时触发 rehashing 进程，调用`DisableAutoRehash`、添加元素以及最后调用[CAtlMap：： EnableAutoRehash](#enableautorehash)更有效。

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap：： EnableAutoRehash

调用此方法以启用`CAtlMap`对象的自动 rehashing。

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>备注

启用自动 rehashing 时（默认设置），如果负载值（储箱数到数组中存储的元素数的比率）超过创建映射时指定的最大值或最小值，则将自动重新计算哈希表中的储箱数。

`EnableAutoRefresh`在调用[CAtlMap：:D isableautorehash](#disableautorehash)后，最常使用。

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap：： GetAt

调用此方法可在映射中的指定位置返回元素。

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
位置计数器，由先前对[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的调用返回。

*键*<br/>
指定地图键类型的模板参数。

*value*<br/>
指定地图值类型的模板参数。

### <a name="return-value"></a>返回值

返回一个指针，该指针指向存储在映射中的键/值元素的当前对。

### <a name="remarks"></a>备注

在调试版本中，如果*pos*等于 NULL，将发生断言错误。

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap：： GetCount

调用此方法可检索映射中的元素数。

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回 map 对象中的元素数目。 单个元素是键/值对。

### <a name="example"></a>示例

请参阅[CAtlMap：： CAtlMap](#catlmap)的示例。

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap：： GetHashTableSize

调用此方法以确定地图的哈希表中的储箱数。

```cpp
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>返回值

返回哈希表中的储箱数。 有关说明，请参阅[CAtlMap：： CAtlMap](#catlmap) 。

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap：： GetKeyAt

调用此方法可以检索存储在`CAtlMap`对象中的给定位置的键。

```cpp
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
位置计数器，由先前对[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的调用返回。

### <a name="return-value"></a>返回值

返回对存储在`CAtlMap`对象中的给定位置的键的引用。

### <a name="example"></a>示例

请参阅[CAtlMap：： CAtlMap](#catlmap)的示例。

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap：： GetNext

调用此方法以获取指向存储在`CAtlMap`对象中的下一个元素对的指针。

```cpp
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
位置计数器，由先前对[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的调用返回。

### <a name="return-value"></a>返回值

返回一个指向存储在映射中的下一对键/值元素的指针。 每次调用后， *pos*位置计数器就会更新。 如果检索到的元素是映射中的最后一个，则*pos*将设置为 NULL。

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap：： GetNextAssoc

获取用于循环访问的下一个元素。

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>参数

*位置*<br/>
位置计数器，由先前对[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的调用返回。

*键*<br/>
指定地图键类型的模板参数。

*value*<br/>
指定地图值类型的模板参数。

### <a name="remarks"></a>备注

每次调用后， *pos*位置计数器就会更新。 如果检索到的元素是映射中的最后一个，则*pos*将设置为 NULL。

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap：： GetNextKey

调用此方法从`CAtlMap`对象中检索下一个键。

```cpp
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
位置计数器，由先前对[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的调用返回。

### <a name="return-value"></a>返回值

返回对映射中下一个键的引用。

### <a name="remarks"></a>备注

更新当前位置计数器， *pos*。如果映射中没有更多条目，则位置计数器设置为 NULL。

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap：： GetNextValue

调用此方法可从`CAtlMap`对象获取下一个值。

```cpp
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
位置计数器，由先前对[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的调用返回。

### <a name="return-value"></a>返回值

返回对映射中下一个值的引用。

### <a name="remarks"></a>备注

更新当前位置计数器， *pos*。如果映射中没有更多条目，则位置计数器设置为 NULL。

### <a name="example"></a>示例

请参阅[CAtlMap：： CAtlMap](#catlmap)的示例。

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap：： GetStartPosition

调用此方法以启动地图迭代。

```cpp
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>返回值

返回起始位置，如果映射为空，则返回 NULL。

### <a name="remarks"></a>备注

调用此方法可通过返回可传递给`GetNextAssoc`方法的位置值来启动映射迭代。

> [!NOTE]
> 迭代顺序不可预测

### <a name="example"></a>示例

请参阅[CAtlMap：： CAtlMap](#catlmap)的示例。

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap：： GetValueAt

调用此方法可以检索存储在`CAtlMap`对象中的指定位置的值。

```cpp
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
位置计数器，由先前对[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的调用返回。

### <a name="return-value"></a>返回值

返回对存储在`CAtlMap`对象中的给定位置的值的引用。

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap：： InitHashTable

调用此方法可初始化哈希表。

```cpp
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>参数

*nBins*<br/>
哈希表使用的箱数。 有关说明，请参阅[CAtlMap：： CAtlMap](#catlmap) 。

*bAllocNow*<br/>
应分配内存时的标志指示。

### <a name="return-value"></a>返回值

如果成功初始化，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

`InitHashTable`在哈希表中存储任何元素之前，必须先调用。  如果未显式调用此方法，则在第一次使用`CAtlMap`构造函数指定的 bin 计数添加元素时，将自动调用此方法。  否则，将使用*nBins*参数指定的新 bin 计数来初始化该映射。

如果*bAllocNow*参数为 false，则在第一次需要哈希表之前，不会分配哈希表所需的内存。 如果不确定是否将使用映射，这会很有用。

### <a name="example"></a>示例

请参阅[CAtlMap：： CAtlMap](#catlmap)的示例。

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap：： IsEmpty

调用此方法可测试空的地图对象。

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果映射为空，则返回 TRUE，否则返回 FALSE。

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap：： KINARGTYPE

当键作为输入参数传递时使用的类型。

```cpp
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap：： KOUTARGTYPE

当键作为输出参数返回时使用的类型。

```cpp
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap：： Lookup

调用此方法可查找对象中的`CAtlMap`键或值。

```cpp
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*键*<br/>
指定标识要查找的元素的键。

*value*<br/>
接收查找值的变量。

### <a name="return-value"></a>返回值

如果找到该键，则该方法的第一种形式将返回 true，否则返回 false。 第二个和第三个窗体返回指向[CPair](#cpair_class)的指针，该指针可用作调用[CAtlMap：： GetNext](#getnext)等的位置。

### <a name="remarks"></a>备注

`Lookup`使用哈希算法快速查找包含与给定键参数完全匹配的键的 map 元素。

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap：： operator\[\]

替换或将新元素添加到中`CAtlMap`。

```cpp
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>参数

*键*<br/>
要添加或替换的元素的键。

### <a name="return-value"></a>返回值

返回对与给定键关联的值的引用。

### <a name="example"></a>示例

如果该键已存在，则将替换该元素。 如果该键不存在，则添加新的元素。 请参阅[CAtlMap：： CAtlMap](#catlmap)的示例。

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap：： Rehash

调用此方法来 rehash `CAtlMap`对象。

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>参数

*nBins*<br/>
要在哈希表中使用的新箱数。 有关说明，请参阅[CAtlMap：： CAtlMap](#catlmap) 。

### <a name="remarks"></a>备注

如果*nBins*为0， `CAtlMap`则根据映射中的元素数和最佳负载设置计算合理的数字。 通常，rehashing 进程是自动的，但是如果已调用[CAtlMap：:D isableautorehash](#disableautorehash) ，则此方法将执行必要的大小调整。

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap：： RemoveAll

调用此方法可从`CAtlMap`对象中移除所有元素。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>备注

清除`CAtlMap`对象，释放用于存储元素的内存。

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap：： RemoveAtPos

调用此方法可删除`CAtlMap`对象中给定位置的元素。

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*位置*<br/>
位置计数器，由先前对[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的调用返回。

### <a name="remarks"></a>备注

删除存储在指定位置的键/值对。 将释放用于存储元素的内存。 *Pos*引用的位置变为无效，而映射中任何其他元素的位置保持有效，则不一定要保持相同的顺序。

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap：： RemoveKey

调用此方法可从`CAtlMap`对象中删除元素（给定键）。

```cpp
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*键*<br/>
与要移除的元素对相对应的键。

### <a name="return-value"></a>返回值

如果找到并移除该键，则返回 TRUE; 如果失败，则返回 FALSE。

### <a name="example"></a>示例

请参阅[CAtlMap：： CAtlMap](#catlmap)的示例。

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap：： SetAt

调用此方法可将元素对插入到映射中。

```cpp
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>参数

*键*<br/>
要添加到`CAtlMap`对象的键值。

*value*<br/>
要添加到`CAtlMap`对象的值。

### <a name="return-value"></a>返回值

返回`CAtlMap`对象中键/值元素对的位置。

### <a name="remarks"></a>备注

`SetAt`如果找到匹配的键，则替换现有元素。 如果未找到该键，则创建一个新的键/值对。

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap：： SetOptimalLoad

调用此方法可设置`CAtlMap`对象的最佳负载。

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>参数

*fOptimalLoad*<br/>
最佳负载比。

*fLoThreshold*<br/>
负载比率的下限阈值。

*fHiThreshold*<br/>
负载比阈值的上限。

*bRehashNow*<br/>
指示是否应重新计算哈希表的标志。

### <a name="remarks"></a>备注

此方法将重定义`CAtlMap`对象的最佳负载值。 有关各个参数的讨论，请参阅[CAtlMap：： CAtlMap](#catlmap) 。 如果*bRehashNow*为 true，且元素数超出了最小值和最大值，则重新计算哈希表。

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap：： SetValueAt

调用此方法可更改存储在`CAtlMap`对象中指定位置的值。

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>参数

*位置*<br/>
位置计数器，由先前对[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的调用返回。

*value*<br/>
要添加到`CAtlMap`对象的值。

### <a name="remarks"></a>备注

更改存储在`CAtlMap`对象中给定位置的值元素。

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap：： VINARGTYPE

将值作为输入参数传递时使用的类型。

```cpp
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap：： VOUTARGTYPE

将值作为输出参数传递时使用的类型。

```cpp
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap：： CPair：： m_key

存储密钥元素的数据成员。

```cpp
const K m_key;
```

### <a name="parameters"></a>参数

*温度*<br/>
键元素类型。

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap：： CPair：： m_value

存储 value 元素的数据成员。

```cpp
V  m_value;
```

### <a name="parameters"></a>参数

*向量*<br/>
值元素类型。

## <a name="see-also"></a>另请参阅

[天棚示例](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV 示例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[类概述](../../atl/atl-class-overview.md)
