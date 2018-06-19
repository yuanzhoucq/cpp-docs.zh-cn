---
title: CAtlMap 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c0a90ad7ce9d515331f817ef9ef5ee40d2d25b2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366285"
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
 `K`  
 键的元素类型。  
  
 V  
 值的元素类型。  
  
 `KTraits`  
 用于复制或移动关键元素的代码。 请参阅[CElementTraits 类](../../atl/reference/celementtraits-class.md)有关详细信息。  
  
 `VTraits`  
 用于复制或移动值元素的代码。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlMap::KINARGTYPE](#kinargtype)|作为输入参数传递一个键时使用的类型|  
|[CAtlMap::KOUTARGTYPE](#koutargtype)|作为输出参数返回一个密钥时所用的类型。|  
|[CAtlMap::VINARGTYPE](#vinargtype)|作为输入参数传递一个值时所用的类型。|  
|[CAtlMap::VOUTARGTYPE](#voutargtype)|作为输出参数传递一个值时所用的类型。|  
  
### <a name="public-classes"></a>公共类  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlMap::CPair 类](#cpair_class)|包含的键和值的元素的类。|  

  
### <a name="cpair-data-members"></a>CPair 数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CPair::m_key](#m_key)|存储密钥的元素数据成员。|  
|[CPair::m_value](#m_value)|存储值元素，该数据成员。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlMap::CAtlMap](#catlmap)|构造函数。|  
|[CAtlMap:: ~ CAtlMap](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlMap::AssertValid](#assertvalid)|调用此方法，从而导致出现一个断言，如果`CAtlMap`无效。|  
|[CAtlMap::DisableAutoRehash](#disableautorehash)|调用此方法以禁用的自动 rehashing`CAtlMap`对象。|  
|[CAtlMap::EnableAutoRehash](#enableautorehash)|调用此方法以启用的自动 rehashing`CAtlMap`对象。|  
|[CAtlMap::GetAt](#getat)|调用此方法以返回映射中的指定位置处的元素。|  
|[CAtlMap::GetCount](#getcount)|调用此方法以检索在映射中的元素的数目。|  
|[CAtlMap::GetHashTableSize](#gethashtablesize)|调用此方法以确定映射的哈希表中的箱数。|  
|[CAtlMap::GetKeyAt](#getkeyat)|调用此方法以检索位于给定位置中存储的密钥`CAtlMap`对象。|  
|[CAtlMap::GetNext](#getnext)|调用此方法以获取指向对存储中的下一个元素的`CAtlMap`对象。|  
|[CAtlMap::GetNextAssoc](#getnextassoc)|获取循环的下一个元素。|  
|[CAtlMap::GetNextKey](#getnextkey)|调用此方法以检索从的下一个键`CAtlMap`对象。|  
|[CAtlMap::GetNextValue](#getnextvalue)|调用此方法以获取下一步值`CAtlMap`对象。|  
|[CAtlMap::GetStartPosition](#getstartposition)|调用此方法以启动映射迭代。|  
|[CAtlMap::GetValueAt](#getvalueat)|调用此方法以检索存储中给定位置处的值`CAtlMap`对象。|  
|[CAtlMap::InitHashTable](#inithashtable)|调用此方法以初始化哈希表。|  
|[CAtlMap::IsEmpty](#isempty)|调用此方法可为空映射对象测试。|  
|[CAtlMap::Lookup](#lookup)|调用此方法以查找密钥或中的值`CAtlMap`对象。|  
|[CAtlMap::Rehash](#rehash)|调用此方法以 rehash`CAtlMap`对象。|  
|[CAtlMap::RemoveAll](#removeall)|调用此方法以删除中的所有元素`CAtlMap`对象。|  
|[CAtlMap::RemoveAtPos](#removeatpos)|调用此方法以删除中的给定位置处的元素`CAtlMap`对象。|  
|[CAtlMap::RemoveKey](#removekey)|调用此方法以删除从元素`CAtlMap`给定键的对象。|  
|[CAtlMap::SetAt](#setat)|调用此方法以插入到映射的元素对。|  
|[CAtlMap::SetOptimalLoad](#setoptimalload)|调用此方法以设置的最佳负载`CAtlMap`对象。|  
|[CAtlMap::SetValueAt](#setvalueat)|调用此方法可以更改存储中给定位置处的值`CAtlMap`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|替换或添加到一个新元素`CAtlMap`。|  

  
## <a name="remarks"></a>备注  
 `CAtlMap` 为管理数组未排序键的元素及其关联的任何的值给定类型的映射数组提供支持。 使用哈希算法，允许大量的数据来高效地存储和检索存储元素 （包含的键和值）。  
  
 `KTraits`和`VTraits`参数是包含复制或移动元素所需的任何补充代码的特征类。  
  
 一种替代方法`CAtlMap`所提供的[CRBMap](../../atl/reference/crbmap-class.md)类。 `CRBMap` 此外存储键/值对，但表现出不同的性能特征。 插入一项所花的时间查找一个键，或删除的密钥`CRBMap`对象的顺序是*log(n)*，其中*n*是元素的数目。 有关`CAtlMap`，所有这些操作通常采用固定的时间，尽管的顺序可能是最坏情况*n*。 因此，在一种典型情况，`CAtlMap`速度更快。  
  
 之间的其他差异`CRBMap`和`CAtlMap`会了然-当循环访问存储的元素。 在`CRBMap`，按排序顺序访问元素。 在`CAtlMap`、 未排序元素，并且可以推断没有顺序。  
  
 当需要存储的元素的数量少时，请考虑使用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcoll.h  
  
##  <a name="assertvalid"></a>  CAtlMap::AssertValid  
 调用此方法，从而导致出现一个断言，如果`CAtlMap`对象无效。  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果该方法将导致断言`CAtlMap`对象无效。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
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
 `nBins`  
 提供指向存储的元素的指针的箱数。 请参阅有关的箱说明本主题后面的备注。  
  
 `fOptimalLoad`  
 最佳的负载比中。  
  
 `fLoThreshold`  
 负载比率的阈值下限。  
  
 `fHiThreshold`  
 该阈值上限的负载比率。  
  
 `nBlockSize`  
 块大小。  
  
### <a name="remarks"></a>备注  
 `CAtlMap` 通过先创建索引的键使用哈希算法中引用所有其存储的元素。 此索引引用"bin"其中包含指向存储元素。 如果 bin 已在使用中，将创建一个链接列表来访问后续元素。 遍历列表是比直接访问正确的元素中，要慢，因此站点地图结构需要对性能的存储要求相平衡。 默认参数已经已选择在大多数情况下提供较好的效果。  
  
 负载比率是 map 对象中存储的元素数目的箱数的比率。 站点地图结构被重新计算，时更新*fOptimalLoad*参数值将用于计算所需的箱数。 可以使用更改此值[CAtlMap::SetOptimalLoad](#setoptimalload)方法。  
  
 `fLoThreshold`参数是负载比率可以访问之前的较低值`CAtlMap`将重新计算地图的最佳大小。  
  
 `fHiThreshold`参数是较大的值的负载比能够到达之前`CAtlMap`对象将重新计算地图的最佳大小。  
  
 默认情况下启用 （称为 rehashing） 此重新计算进程。 如果你想要禁用此过程中，可能是输入大量数据一次调用时[CAtlMap::DisableAutoRehash](#disableautorehash)方法。 重新激活它与[CAtlMap::EnableAutoRehash](#enableautorehash)方法。  
  
 `nBlockSize`参数是分配需要一个新的元素时的内存量的度量值。 更大的块大小减少到内存分配例程的调用，但使用更多资源。  
  
 可以存储任何数据之前，务必初始化通过调用哈希表[CAtlMap::InitHashTable](#inithashtable)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]  
  
##  <a name="dtor"></a>  CAtlMap:: ~ CAtlMap  
 析构函数。  
  
```
~CAtlMap() throw();
```  
  
### <a name="remarks"></a>备注  
 释放任何已分配的资源。  
  
##  <a name="cpair_class"></a>  CAtlMap::CPair 类  
 包含的键和值的元素的类。  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>备注  
 此类由方法[CAtlMap::GetNext](#getnext)和[CAtlMap::Lookup](#lookup)访问存储在映射结构的键和值的元素。  
  
##  <a name="disableautorehash"></a>  CAtlMap::DisableAutoRehash  
 调用此方法以禁用的自动 rehashing`CAtlMap`对象。  
  
```
void DisableAutoRehash() throw();
```  
  
### <a name="remarks"></a>备注  
 启用自动 rehashing 后 （这它是默认情况下），在哈希表的箱数将自动重新计算如果负载值 （存储在数组中的元素数目的箱数的比率） 超过最大或最小值指定在创建代码图的时间。  
  
 `DisableAutoRehash` 当大量的元素将添加到映射一次，则将最为有用。 而不是每次超过限制时，则触发 rehashing 过程，它会更加高效调用`DisableAutoRehash`，添加元素，最后调用[CAtlMap::EnableAutoRehash](#enableautorehash)。  
  
##  <a name="enableautorehash"></a>  CAtlMap::EnableAutoRehash  
 调用此方法以启用的自动 rehashing`CAtlMap`对象。  
  
```
void EnableAutoRehash() throw();
```  
  
### <a name="remarks"></a>备注  
 启用自动 rehashing 后 （这它是默认情况下），在哈希表的箱数将自动重新计算如果负载值 （存储在数组中的元素数目的箱数的比率） 超过最大或最小值指定在创建代码图的时间。  
  
 **EnableAutoRefresh**之后调用最常使用[CAtlMap::DisableAutoRehash](#disableautorehash)。  
  
##  <a name="getat"></a>  CAtlMap::GetAt  
 调用此方法以返回映射中的指定位置处的元素。  
  
```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
 `key`  
 指定地图的键的类型的模板参数。  
  
 *value*  
 指定地图的值的类型的模板参数。  
  
### <a name="return-value"></a>返回值  
 返回指向当前对存储在映射中的键/值元素的指针。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果出现断言错误`pos`等于为 NULL。  
  
##  <a name="getcount"></a>  CAtlMap::GetCount  
 调用此方法以检索在映射中的元素的数目。  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 Map 对象中返回元素的数。 单个元素是一个键/值对。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="gethashtablesize"></a>  CAtlMap::GetHashTableSize  
 调用此方法以确定映射的哈希表中的箱数。  
  
```
UINT GetHashTableSize() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回哈希表中的箱数。 请参阅[CAtlMap::CAtlMap](#catlmap)有关说明。  
  
##  <a name="getkeyat"></a>  CAtlMap::GetKeyAt  
 调用此方法以检索位于给定位置中存储的密钥`CAtlMap`对象。  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>返回值  
 返回位于给定位置中存储的密钥的引用`CAtlMap`对象。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getnext"></a>  CAtlMap::GetNext  
 调用此方法以获取指向对存储中的下一个元素的`CAtlMap`对象。  
  
```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>返回值  
 返回指向下一步对存储在映射中的键/值元素的指针。 `pos`位置计数器在每次调用后被更新。 如果检索的元素为在映射中，最后一个`pos`设置为 NULL。  
  
##  <a name="getnextassoc"></a>  CAtlMap::GetNextAssoc  
 获取循环的下一个元素。  
  
```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
 `key`  
 指定地图的键的类型的模板参数。  
  
 *value*  
 指定地图的值的类型的模板参数。  
  
### <a name="remarks"></a>备注  
 `pos`位置计数器在每次调用后被更新。 如果检索的元素为在映射中，最后一个`pos`设置为 NULL。  
  
##  <a name="getnextkey"></a>  CAtlMap::GetNextKey  
 调用此方法以检索从的下一个键`CAtlMap`对象。  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>返回值  
 返回映射中的下一个键对的引用。  
  
### <a name="remarks"></a>备注  
 更新当前的位置计数器， `pos`。 如果映射中不存在多个项，则会将位置计数器设置为 NULL。  
  
##  <a name="getnextvalue"></a>  CAtlMap::GetNextValue  
 调用此方法以获取下一步值`CAtlMap`对象。  
  
```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>返回值  
 返回映射中的下一个值对的引用。  
  
### <a name="remarks"></a>备注  
 更新当前的位置计数器， `pos`。 如果映射中不存在多个项，则会将位置计数器设置为 NULL。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getstartposition"></a>  CAtlMap::GetStartPosition  
 调用此方法以启动映射迭代。  
  
```
POSITION GetStartPosition() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回如果映射为空，则返回的起始位置或为 NULL。  
  
### <a name="remarks"></a>备注  
 调用此方法以通过返回启动映射迭代**位置**值，可以传递给`GetNextAssoc`方法。  
  
> [!NOTE]
>  迭代序列不是可预测  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getvalueat"></a>  CAtlMap::GetValueAt  
 调用此方法以检索存储中给定位置处的值`CAtlMap`对象。  
  
```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>返回值  
 返回位于给定位置中存储的值的引用`CAtlMap`对象。  
  
##  <a name="inithashtable"></a>  CAtlMap::InitHashTable  
 调用此方法以初始化哈希表。  
  
```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```  
  
### <a name="parameters"></a>参数  
 `nBins`  
 使用哈希表的箱数。 请参阅[CAtlMap::CAtlMap](#catlmap)有关说明。  
  
 `bAllocNow`  
 标志指示应分配内存时。  
  
### <a name="return-value"></a>返回值  
 返回**true**上成功初始化**false**失败。  
  
### <a name="remarks"></a>备注  
 `InitHashTable` 必须在调用之前的任何元素存储在哈希表。  如果不显式调用此方法，它将调用自动使用指定的容器计数添加的元素的第一个时间**CAtlMap**构造函数。  否则，该映射将初始化使用指定的新容器计数`nBins`参数。  
  
 如果`bAllocNow`参数为 false 时，直到它首先需要，将不会分配所需的哈希表的内存。 这很有用，如果它是不确定，如果将使用该映射。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="isempty"></a>  CAtlMap::IsEmpty  
 调用此方法可为空映射对象测试。  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回**true**如果映射为空， **false**否则为。  
  
##  <a name="kinargtype"></a>  CAtlMap::KINARGTYPE  
 作为输入参数传递一个键时所用的类型。  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="koutargtype"></a>  CAtlMap::KOUTARGTYPE  
 作为输出参数返回一个密钥时所用的类型。  
  
```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```  
  
##  <a name="lookup"></a>  CAtlMap::Lookup  
 调用此方法以查找密钥或中的值`CAtlMap`对象。  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 指定标识要查找的元素的键。  
  
 *value*  
 接收的查阅到值的变量。  
  
### <a name="return-value"></a>返回值  
 第一种形式的方法返回 true，如果找到项，否则为 false。 第二个和第三个窗体返回一个指向[CPair](#cpair_class)它可以作为位置使用，以便调用[CAtlMap::GetNext](#getnext) ，依此类推。  
  
### <a name="remarks"></a>备注  
 `Lookup` 使用哈希算法来快速查找包含与给定的密钥参数完全匹配的键的地图元素。  
  
##  <a name="operator_at"></a>  CAtlMap::operator \[\]  
 替换或添加到一个新元素`CAtlMap`。  
  
```
V& operator[](kinargtype key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要添加或替换的元素键。  
  
### <a name="return-value"></a>返回值  
 返回与给定的键关联的值的引用。  
  
### <a name="example"></a>示例  
 如果键已存在，将被替换元素。 如果不存在该键，添加一个新的元素。 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="rehash"></a>  CAtlMap::Rehash  
 调用此方法以 rehash`CAtlMap`对象。  
  
```
void Rehash(UINT nBins = 0);
```  
  
### <a name="parameters"></a>参数  
 `nBins`  
 若要使用哈希表中的箱中新的数。 请参阅[CAtlMap::CAtlMap](#catlmap)有关说明。  
  
### <a name="remarks"></a>备注  
 如果`nBins`为 0，`CAtlMap`计算合理数目基于将地图和最佳负载设置中的元素数。 通常情况下 rehashing 过程是自动进行的但是，如果[CAtlMap::DisableAutoRehash](#disableautorehash)已被调用，此方法将执行必要的调整大小。  
  
##  <a name="removeall"></a>  CAtlMap::RemoveAll  
 调用此方法以删除中的所有元素`CAtlMap`对象。  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>备注  
 清除`CAtlMap`对象，并释放内存用于存储元素。  
  
##  <a name="removeatpos"></a>  CAtlMap::RemoveAtPos  
 调用此方法以删除中的给定位置处的元素`CAtlMap`对象。  
  
```
void RemoveAtPos(POSITION pos) throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="remarks"></a>备注  
 删除存储在指定位置处的键/值对。 释放内存用于存储元素。 位置引用的`pos`将变为无效，并在映射中的任何其他元素的位置就保持有效，它们不一定实现时保留相同的顺序。  
  
##  <a name="removekey"></a>  CAtlMap::RemoveKey  
 调用此方法以删除从元素`CAtlMap`给定键的对象。  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 你想要删除的元素对相应的密钥。  
  
### <a name="return-value"></a>返回值  
 返回**true**找到密钥并将其删除，如果**false**失败。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="setat"></a>  CAtlMap::SetAt  
 调用此方法以插入到映射的元素对。  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 密钥的值将添加到`CAtlMap`对象。  
  
 *value*  
 要添加到值`CAtlMap`对象。  
  
### <a name="return-value"></a>返回值  
 返回的位置中的键/值元素对`CAtlMap`对象。  
  
### <a name="remarks"></a>备注  
 `SetAt` 如果找到匹配的键，将替换现有元素。 如果未找到项，都要创建新的键/值对。  
  
##  <a name="setoptimalload"></a>  CAtlMap::SetOptimalLoad  
 调用此方法以设置的最佳负载`CAtlMap`对象。  
  
```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```  
  
### <a name="parameters"></a>参数  
 `fOptimalLoad`  
 最佳的负载比中。  
  
 `fLoThreshold`  
 负载比率的阈值下限。  
  
 `fHiThreshold`  
 该阈值上限的负载比率。  
  
 `bRehashNow`  
 标志指示是否应重新计算哈希表。  
  
### <a name="remarks"></a>备注  
 此方法重新定义的最佳负载值`CAtlMap`对象。 请参阅[CAtlMap::CAtlMap](#catlmap)有关的各种参数的讨论。 如果`bRehashNow`为 true，并且元素的数目超出最小和最大值，重新计算哈希表。  
  
##  <a name="setvalueat"></a>  CAtlMap::SetValueAt  
 调用此方法可以更改存储中给定位置处的值`CAtlMap`对象。  
  
```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
 *value*  
 要添加到值`CAtlMap`对象。  
  
### <a name="remarks"></a>备注  
 更改存储中给定位置处的值元素`CAtlMap`对象。  
  
##  <a name="vinargtype"></a>  CAtlMap::VINARGTYPE  
 作为输入参数传递一个值时所用的类型。  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="voutargtype"></a>  CAtlMap::VOUTARGTYPE  
 作为输出参数传递一个值时所用的类型。  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
##  <a name="m_key"></a>  CAtlMap::CPair::m_key  
 存储密钥的元素数据成员。  
  
```
const K m_key;
```    
  
### <a name="parameters"></a>参数  
 `K`  
 键的元素类型。  
  
##  <a name="m_value"></a>  CAtlMap::CPair::m_value  
 存储值元素，该数据成员。  
  
```
V  m_value;
```    
  
### <a name="parameters"></a>参数  
 *V*  
 值的元素类型。  
  
## <a name="see-also"></a>请参阅  
 [选框示例](../../visual-cpp-samples.md)   
 [UpdatePV 示例](../../visual-cpp-samples.md)   
 [类概述](../../atl/atl-class-overview.md)
