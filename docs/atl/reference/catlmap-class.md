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
ms.openlocfilehash: 1821532a4d5a3078202f180273b02945b8d8e4ba
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774550"
---
# <a name="catlmap-class"></a>CAtlMap 类

此类提供用于创建和管理 map 对象的方法。

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
|[CAtlMap::KINARGTYPE](#kinargtype)|密钥传递作为输入参数时使用的类型|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|作为输出参数返回一个密钥时所使用的类型。|
|[CAtlMap::VINARGTYPE](#vinargtype)|将值传递作为输入参数时所使用的类型。|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|作为输出参数传递一个值时所使用的类型。|

### <a name="public-classes"></a>公共类

|名称|描述|
|----------|-----------------|
|[CAtlMap::CPair 类](#cpair_class)|一个包含键和值元素的类。|

### <a name="cpair-data-members"></a>CPair 数据成员

|名称|描述|
|----------|-----------------|
|[CPair::m_key](#m_key)|存储密钥的元素，该数据成员。|
|[CPair::m_value](#m_value)|存储值元素，该数据成员。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|构造函数。|
|[CAtlMap::~CAtlMap](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|调用此方法以引发断言，如果`CAtlMap`无效。|
|[CAtlMap::DisableAutoRehash](#disableautorehash)|调用此方法来禁用自动重复讨论这个的`CAtlMap`对象。|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|调用此方法以启用自动重复讨论这个的`CAtlMap`对象。|
|[CAtlMap::GetAt](#getat)|调用此方法以返回映射中指定位置处的元素。|
|[CAtlMap::GetCount](#getcount)|调用此方法来检索该映射中的元素数。|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|调用此方法来确定地图的哈希表中的箱数。|
|[CAtlMap::GetKeyAt](#getkeyat)|调用此方法以检索在给定位置中存储的密钥`CAtlMap`对象。|
|[CAtlMap::GetNext](#getnext)|调用此方法以获取对存储中的下一个元素的指针`CAtlMap`对象。|
|[CAtlMap::GetNextAssoc](#getnextassoc)|获取用于循环的下一个元素。|
|[CAtlMap::GetNextKey](#getnextkey)|调用此方法以检索下一步密钥`CAtlMap`对象。|
|[CAtlMap::GetNextValue](#getnextvalue)|调用此方法以获取下一个值从`CAtlMap`对象。|
|[CAtlMap::GetStartPosition](#getstartposition)|调用此方法以启动映射迭代。|
|[CAtlMap::GetValueAt](#getvalueat)|调用此方法以检索在给定位置中存储的值`CAtlMap`对象。|
|[CAtlMap::InitHashTable](#inithashtable)|调用此方法来初始化哈希表。|
|[CAtlMap::IsEmpty](#isempty)|调用此方法来测试空映射对象。|
|[CAtlMap::Lookup](#lookup)|调用此方法来查找键或值中的`CAtlMap`对象。|
|[CAtlMap::Rehash](#rehash)|调用此方法以 rehash`CAtlMap`对象。|
|[CAtlMap::RemoveAll](#removeall)|调用此方法来删除中的所有元素`CAtlMap`对象。|
|[CAtlMap::RemoveAtPos](#removeatpos)|调用此方法来删除中的给定位置处的元素`CAtlMap`对象。|
|[CAtlMap::RemoveKey](#removekey)|调用此方法来删除从元素`CAtlMap`给定键的对象。|
|[CAtlMap::SetAt](#setat)|调用此方法要插入到映射的元素对。|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|调用此方法以设置的最佳的负载`CAtlMap`对象。|
|[CAtlMap::SetValueAt](#setvalueat)|调用此方法来更改存储中给定位置处的值`CAtlMap`对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|替换或添加到新元素`CAtlMap`。|

## <a name="remarks"></a>备注

`CAtlMap` 为管理的关键元素和相关联的值的无序的数组任意给定类型的映射数组提供支持。 使用哈希算法，从而允许大量的数据来高效地存储和检索存储 （由一个键和值组成） 的元素。

*KTraits*并*VTraits*参数是包含要复制或移动元素所需的任何补充代码的特征类。

一种替代方法`CAtlMap`提供了[CRBMap](../../atl/reference/crbmap-class.md)类。 `CRBMap` 此外存储键/值对，但表现出不同的性能特征。 将某个项插入所用的时间查找密钥，或删除的密钥`CRBMap`对象是顺序*log(n)*，其中*n*是元素的数目。 有关`CAtlMap`，所有这些操作通常采用常量时间内，尽管最坏情况可能的顺序*n*。 因此，在通常的情况下，`CAtlMap`速度更快。

之间的其他区别`CRBMap`和`CAtlMap`变得明显时循环访问存储的元素。 在`CRBMap`，按排序顺序访问元素。 在`CAtlMap`、 未排序元素，并可以推断任何顺序。

如果需要存储少量元素，请考虑使用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="assertvalid"></a>  CAtlMap::AssertValid

调用此方法以引发断言，如果`CAtlMap`对象无效。

```
void AssertValid() const;
```

### <a name="remarks"></a>备注

在调试版本中，如果该方法将导致断言`CAtlMap`对象无效。

### <a name="example"></a>示例

有关示例，请参阅[CAtlMap::CAtlMap](#catlmap)。

##  <a name="catlmap"></a>  CAtlMap::CAtlMap

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

*nBins*<br/>
提供指向存储元素的指针的箱数。 请参阅的箱说明本主题后面的备注。

*fOptimalLoad*<br/>
最佳的负载之比。

*fLoThreshold*<br/>
负载比率的阈值下限。

*fHiThreshold*<br/>
负载比率的阈值上限。

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

`CAtlMap` 通过首先创建使用基于该键的哈希算法的索引引用的所有存储元素。 此索引引用"bin"其中包含指向存储的元素。 如果 bin 已在使用中，会创建一个链接列表访问后续元素。 遍历列表的速度将慢于直接访问正确的元素，并因此站点地图结构，需要平衡对性能的存储要求。 已选择的默认参数在大多数情况下提供较好的结果。

负载为存储在 map 对象中的元素数目的箱数的比率。 站点地图结构被重新计算，时更新*fOptimalLoad*参数值将用于计算所需的箱数。 可以使用更改该值[CAtlMap::SetOptimalLoad](#setoptimalload)方法。

*FLoThreshold*参数是较低的值之前可以达到负载比`CAtlMap`将重新计算该映射的最佳大小。

*FHiThreshold*参数是较大的值之前可以达到负载比`CAtlMap`对象将重新计算该映射的最佳大小。

默认情况下启用此重新计算进程 （称为重复讨论这个）。 如果你想要禁用此过程中，可能是输入大量数据，一次调用时[CAtlMap::DisableAutoRehash](#disableautorehash)方法。 重新激活它与[CAtlMap::EnableAutoRehash](#enableautorehash)方法。

*NBlockSize*参数是分配新元素时所需的内存量的度量值。 更大的块大小降低对内存分配例程的调用，但使用更多的资源。

可以存储任何数据之前，有必要初始化哈希表通过调用[CAtlMap::InitHashTable](#inithashtable)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

##  <a name="dtor"></a>  CAtlMap::~CAtlMap

析构函数。

```
~CAtlMap() throw();
```

### <a name="remarks"></a>备注

释放任何已分配的资源。

##  <a name="cpair_class"></a>  CAtlMap::CPair 类

一个包含键和值元素的类。

```
class CPair : public __POSITION
```

### <a name="remarks"></a>备注

方法使用此类[CAtlMap::GetNext](#getnext)并[CAtlMap::Lookup](#lookup)访问存储在映射结构的键和值元素。

##  <a name="disableautorehash"></a>  CAtlMap::DisableAutoRehash

调用此方法来禁用自动重复讨论这个的`CAtlMap`对象。

```
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>备注

启用自动重复讨论这个后 （即它默认情况下），哈希表中的箱数将自动重新计算如果负载值 （存储在数组中的元素数目的箱数的比率） 超出了最大或最小值指定在创建代码图的时间。

`DisableAutoRehash` 当大量元素将添加到地图在一次，则会十分有用。 而不是触发 rehashing 进程，每次超出限制时，它是调用效率更高`DisableAutoRehash`，添加元素，并最后调用[CAtlMap::EnableAutoRehash](#enableautorehash)。

##  <a name="enableautorehash"></a>  CAtlMap::EnableAutoRehash

调用此方法以启用自动重复讨论这个的`CAtlMap`对象。

```
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>备注

启用自动重复讨论这个后 （即它默认情况下），哈希表中的箱数将自动重新计算如果负载值 （存储在数组中的元素数目的箱数的比率） 超出了最大或最小值在创建映射时指定。

`EnableAutoRefresh` 最常用于调用后[CAtlMap::DisableAutoRehash](#disableautorehash)。

##  <a name="getat"></a>  CAtlMap::GetAt

调用此方法以返回映射中指定位置处的元素。

```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
通过以前调用返回的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。

*key*<br/>
指定地图的键的类型的模板参数。

*值*<br/>
指定地图的值的类型的模板参数。

### <a name="return-value"></a>返回值

返回指向当前对存储在映射中的键/值元素的指针。

### <a name="remarks"></a>备注

在调试版本中，如果出现断言错误*pos*等于 NULL。

##  <a name="getcount"></a>  CAtlMap::GetCount

调用此方法来检索该映射中的元素数。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>返回值

Map 对象中返回元素的数。 单个元素都是键/值对。

### <a name="example"></a>示例

有关示例，请参阅[CAtlMap::CAtlMap](#catlmap)。

##  <a name="gethashtablesize"></a>  CAtlMap::GetHashTableSize

调用此方法来确定地图的哈希表中的箱数。

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>返回值

哈希表中返回箱的数。 请参阅[CAtlMap::CAtlMap](#catlmap)的说明。

##  <a name="getkeyat"></a>  CAtlMap::GetKeyAt

调用此方法以检索在给定位置中存储的密钥`CAtlMap`对象。

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
通过以前调用返回的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="return-value"></a>返回值

返回位于给定位置中存储的密钥对的引用`CAtlMap`对象。

### <a name="example"></a>示例

有关示例，请参阅[CAtlMap::CAtlMap](#catlmap)。

##  <a name="getnext"></a>  CAtlMap::GetNext

调用此方法以获取对存储中的下一个元素的指针`CAtlMap`对象。

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
通过以前调用返回的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="return-value"></a>返回值

返回指向下一步对存储在映射中的键/值元素的指针。 *Pos*位置计数器在每次调用后被更新。 如果检索的元素是在映射中，最后*pos*设置为 NULL。

##  <a name="getnextassoc"></a>  CAtlMap::GetNextAssoc

获取用于循环的下一个元素。

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>参数

*pos*<br/>
通过以前调用返回的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。

*key*<br/>
指定地图的键的类型的模板参数。

*值*<br/>
指定地图的值的类型的模板参数。

### <a name="remarks"></a>备注

*Pos*位置计数器在每次调用后被更新。 如果检索的元素是在映射中，最后*pos*设置为 NULL。

##  <a name="getnextkey"></a>  CAtlMap::GetNextKey

调用此方法以检索下一步密钥`CAtlMap`对象。

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
通过以前调用返回的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="return-value"></a>返回值

在映射中返回的下一步的密钥对的引用。

### <a name="remarks"></a>备注

更新当前的位置计数器， *pos*。如果在映射中没有更多的项，位置计数器设置为 NULL。

##  <a name="getnextvalue"></a>  CAtlMap::GetNextValue

调用此方法以获取下一个值从`CAtlMap`对象。

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
通过以前调用返回的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="return-value"></a>返回值

在映射中返回到下一个值的引用。

### <a name="remarks"></a>备注

更新当前的位置计数器， *pos*。如果在映射中没有更多的项，位置计数器设置为 NULL。

### <a name="example"></a>示例

有关示例，请参阅[CAtlMap::CAtlMap](#catlmap)。

##  <a name="getstartposition"></a>  CAtlMap::GetStartPosition

调用此方法以启动映射迭代。

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>返回值

返回如果映射为空，则返回的起始位置或为 NULL。

### <a name="remarks"></a>备注

可以将调用此方法可通过返回位置启动映射迭代值传递给`GetNextAssoc`方法。

> [!NOTE]
>  迭代序列不是可预测

### <a name="example"></a>示例

有关示例，请参阅[CAtlMap::CAtlMap](#catlmap)。

##  <a name="getvalueat"></a>  CAtlMap::GetValueAt

调用此方法以检索在给定位置中存储的值`CAtlMap`对象。

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
通过以前调用返回的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="return-value"></a>返回值

返回对存储中的指定位置的值的引用`CAtlMap`对象。

##  <a name="inithashtable"></a>  CAtlMap::InitHashTable

调用此方法来初始化哈希表。

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>参数

*nBins*<br/>
使用的哈希表的箱数。 请参阅[CAtlMap::CAtlMap](#catlmap)的说明。

*bAllocNow*<br/>
标志指示应分配内存时。

### <a name="return-value"></a>返回值

在成功初始化，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

`InitHashTable` 必须在调用之前的任何元素存储在哈希表中。  如果不显式调用此方法，它将自动调用使用指定的容器计数添加一个元素的第一次`CAtlMap`构造函数。  否则，该映射将初始化使用指定的新容器计数*nBins*参数。

如果*bAllocNow*参数为 false 时，将不再分配所需的哈希表的内存，直到第一次所需。 这可以是不确定，如果将使用该映射是否有用。

### <a name="example"></a>示例

有关示例，请参阅[CAtlMap::CAtlMap](#catlmap)。

##  <a name="isempty"></a>  CAtlMap::IsEmpty

调用此方法来测试空映射对象。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果映射为空，则返回 FALSE 否则，则返回 TRUE。

##  <a name="kinargtype"></a>  CAtlMap::KINARGTYPE

作为输入参数传递一个键时所使用的类型。

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CAtlMap::KOUTARGTYPE

作为输出参数返回一个密钥时所使用的类型。

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="lookup"></a>  CAtlMap::Lookup

调用此方法来查找键或值中的`CAtlMap`对象。

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*key*<br/>
指定用于标识要查找的元素的键。

*值*<br/>
未接收到查找值的变量。

### <a name="return-value"></a>返回值

第一种形式的方法返回 true，如果找到键，否则为 false。 第二个和第三个窗体返回一个指向[CPair](#cpair_class)可以对的调用的位置作为使用[CAtlMap::GetNext](#getnext) ，依此类推。

### <a name="remarks"></a>备注

`Lookup` 使用哈希算法来快速查找包含与给定键参数完全匹配的键的地图元素。

##  <a name="operator_at"></a>  CAtlMap::operator \[\]

替换或添加到新元素`CAtlMap`。

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>参数

*key*<br/>
要添加或替换的元素的键。

### <a name="return-value"></a>返回值

返回与给定键关联的值的引用。

### <a name="example"></a>示例

如果该键已存在，该元素将被替换。 如果不存在该键，添加新元素。 有关示例，请参阅[CAtlMap::CAtlMap](#catlmap)。

##  <a name="rehash"></a>  CAtlMap::Rehash

调用此方法以 rehash`CAtlMap`对象。

```
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>参数

*nBins*<br/>
新的哈希表中使用的箱数。 请参阅[CAtlMap::CAtlMap](#catlmap)的说明。

### <a name="remarks"></a>备注

如果*nBins*为 0，`CAtlMap`计算合理数量根据映射和最佳的负载设置中的元素数。 通常情况下 rehashing 过程是自动的但是，如果[CAtlMap::DisableAutoRehash](#disableautorehash)已被调用，此方法将执行必要的调整大小。

##  <a name="removeall"></a>  CAtlMap::RemoveAll

调用此方法来删除中的所有元素`CAtlMap`对象。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>备注

清除`CAtlMap`对象，释放内存用于存储元素。

##  <a name="removeatpos"></a>  CAtlMap::RemoveAtPos

调用此方法来删除中的给定位置处的元素`CAtlMap`对象。

```
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>参数

*pos*<br/>
通过以前调用返回的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="remarks"></a>备注

删除存储在指定位置处的键/值对。 释放用于将元素存储的内存。 位置引用*pos*将变为无效，并在地图中的任何其他元素的位置保持有效，它们不一定是执行操作时保留相同的顺序。

##  <a name="removekey"></a>  CAtlMap::RemoveKey

调用此方法来删除从元素`CAtlMap`给定键的对象。

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>参数

*key*<br/>
你想要删除键相对应的元素对。

### <a name="return-value"></a>返回值

如果项是找到并移除，FALSE 失败，则返回 TRUE。

### <a name="example"></a>示例

有关示例，请参阅[CAtlMap::CAtlMap](#catlmap)。

##  <a name="setat"></a>  CAtlMap::SetAt

调用此方法要插入到映射的元素对。

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>参数

*key*<br/>
要添加到密钥值`CAtlMap`对象。

*值*<br/>
要添加到值`CAtlMap`对象。

### <a name="return-value"></a>返回值

返回的位置中的键/值元素对`CAtlMap`对象。

### <a name="remarks"></a>备注

`SetAt` 如果找到匹配项，将替换现有元素。 如果未找到该键，则创建新的键/值对。

##  <a name="setoptimalload"></a>  CAtlMap::SetOptimalLoad

调用此方法以设置的最佳的负载`CAtlMap`对象。

```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>参数

*fOptimalLoad*<br/>
最佳的负载之比。

*fLoThreshold*<br/>
负载比率的阈值下限。

*fHiThreshold*<br/>
负载比率的阈值上限。

*bRehashNow*<br/>
标志，用于指示是否应重新计算哈希表。

### <a name="remarks"></a>备注

此方法将重新定义的最佳的负载值`CAtlMap`对象。 请参阅[CAtlMap::CAtlMap](#catlmap)有关的各种参数的讨论。 如果*bRehashNow*为 true，并且元素的数目是外部的最小和最大值，则重新计算哈希表。

##  <a name="setvalueat"></a>  CAtlMap::SetValueAt

调用此方法来更改存储中给定位置处的值`CAtlMap`对象。

```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>参数

*pos*<br/>
通过以前调用返回的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。

*值*<br/>
要添加到值`CAtlMap`对象。

### <a name="remarks"></a>备注

更改存储中的指定位置的值元素`CAtlMap`对象。

##  <a name="vinargtype"></a>  CAtlMap::VINARGTYPE

将值传递作为输入参数时所使用的类型。

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CAtlMap::VOUTARGTYPE

作为输出参数传递一个值时所使用的类型。

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

##  <a name="m_key"></a>  CAtlMap::CPair::m_key

存储密钥的元素，该数据成员。

```
const K m_key;
```

### <a name="parameters"></a>参数

*K*<br/>
Key 元素类型。

##  <a name="m_value"></a>  CAtlMap::CPair::m_value

存储值元素，该数据成员。

```
V  m_value;
```

### <a name="parameters"></a>参数

*V*<br/>
值元素类型。

## <a name="see-also"></a>请参阅

[字幕示例](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV 示例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[类概述](../../atl/atl-class-overview.md)
