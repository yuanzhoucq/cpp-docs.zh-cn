---
title: "CAtlMap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 3730827a56c47497db2fd8324f54c7ba88a584d6
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

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
 用于复制或移动关键元素的代码。 请参阅[CElementTraits 类](../../atl/reference/celementtraits-class.md)的更多详细信息。  
  
 `VTraits`  
 用于复制或移动值元素的代码。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlMap::KINARGTYPE](#kinargtype)|作为输入参数传递某个键时使用的类型|  
|[CAtlMap::KOUTARGTYPE](#koutargtype)|作为输出参数返回一个密钥时所使用的类型。|  
|[CAtlMap::VINARGTYPE](#vinargtype)|将值传递作为输入参数时所使用的类型。|  
|[CAtlMap::VOUTARGTYPE](#voutargtype)|作为输出参数传递一个值时所使用的类型。|  
  
### <a name="public-classes"></a>公共类  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlMap::CPair 类](#cpair_class)|一个包含键和值的元素的类。|  

  
### <a name="cpair-data-members"></a>CPair 数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CPair::m_key](#m_key)|数据成员将存储的关键元素。|  
|[CPair::m_value](#m_value)|存储的值元素，该数据成员。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlMap::CAtlMap](#catlmap)|构造函数。|  
|[CAtlMap:: ~ CAtlMap](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlMap::AssertValid](#assertvalid)|调用此方法以引发断言，如果`CAtlMap`无效。|  
|[CAtlMap::DisableAutoRehash](#disableautorehash)|调用此方法来禁用自动重复的讨论`CAtlMap`对象。|  
|[CAtlMap::EnableAutoRehash](#enableautorehash)|调用此方法以启用自动重复的讨论`CAtlMap`对象。|  
|[CAtlMap::GetAt](#getat)|调用此方法以返回映射中的指定位置处的元素。|  
|[CAtlMap::GetCount](#getcount)|调用此方法以检索该映射中的元素数。|  
|[CAtlMap::GetHashTableSize](#gethashtablesize)|调用此方法以确定映射的哈希表中的箱数。|  
|[CAtlMap::GetKeyAt](#getkeyat)|调用此方法以检索存储的指定位置中的键`CAtlMap`对象。|  
|[CAtlMap::GetNext](#getnext)|调用此方法以获取对存储中的下一个元素的指针`CAtlMap`对象。|  
|[CAtlMap::GetNextAssoc](#getnextassoc)|获取用于循环的下一个元素。|  
|[CAtlMap::GetNextKey](#getnextkey)|调用此方法以检索中的下一步键`CAtlMap`对象。|  
|[CAtlMap::GetNextValue](#getnextvalue)|调用此方法以获取下一个值从`CAtlMap`对象。|  
|[CAtlMap::GetStartPosition](#getstartposition)|调用此方法以开始映射迭代。|  
|[CAtlMap::GetValueAt](#getvalueat)|调用此方法以检索存储的给定位置的值`CAtlMap`对象。|  
|[CAtlMap::InitHashTable](#inithashtable)|调用此方法以初始化哈希表。|  
|[CAtlMap::IsEmpty](#isempty)|调用此方法以测试空映射对象。|  
|[CAtlMap::Lookup](#lookup)|调用此方法来查找键或值的`CAtlMap`对象。|  
|[CAtlMap::Rehash](#rehash)|调用此方法以 rehash`CAtlMap`对象。|  
|[CAtlMap::RemoveAll](#removeall)|调用此方法来删除中的所有元素`CAtlMap`对象。|  
|[CAtlMap::RemoveAtPos](#removeatpos)|调用此方法来删除中的指定位置处的元素`CAtlMap`对象。|  
|[CAtlMap::RemoveKey](#removekey)|调用此方法来删除从元素`CAtlMap`给定键的对象。|  
|[CAtlMap::SetAt](#setat)|调用此方法来插入到映射的元素对。|  
|[CAtlMap::SetOptimalLoad](#setoptimalload)|调用此方法可设置的最佳负载`CAtlMap`对象。|  
|[CAtlMap::SetValueAt](#setvalueat)|调用此方法以更改存储中的给定位置的值`CAtlMap`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|替换或添加到一个新元素`CAtlMap`。|  

  
## <a name="remarks"></a>备注  
 `CAtlMap`为管理无序的键的元素和相关联的值数组任何给定类型的映射数组提供支持。 使用哈希算法，从而允许大量的数据来有效地存储和检索存储元素 （包含一个键和值）。  
  
 `KTraits`和`VTraits`参数是包含复制或移动元素所需的任何补充代码的特征类。  
  
 一种替代方法`CAtlMap`提供的[CRBMap](../../atl/reference/crbmap-class.md)类。 `CRBMap`此外存储键/值对，但表现出不同的性能特性。 插入一项所花费的时间查找密钥，或删除的密钥`CRBMap`对象是订单的*log(n)*，其中*n*是元素的数目。 有关`CAtlMap`，所有这些操作通常很耗时常量，尽管最坏情况可能是订单的*n*。 因此，在典型的情况下，`CAtlMap`速度更快。  
  
 之间的其他差异`CRBMap`和`CAtlMap`变得显而易见，当循环访问存储的元素。 在`CRBMap`，按排序顺序访问元素。 在`CAtlMap`、 未排序元素，并可以推断出任何顺序。  
  
 当需要存储的元素数量少时，请考虑使用[CSimpleMap](../../atl/reference/csimplemap-class.md)类。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
##  <a name="assertvalid"></a>CAtlMap::AssertValid  
 调用此方法以引发断言，如果`CAtlMap`对象无效。  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果该方法将导致断言`CAtlMap`对象无效。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="catlmap"></a>CAtlMap::CAtlMap  
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
 提供对存储的元素的指针的箱数。 请参阅有关的箱中的说明本主题后面的备注。  
  
 `fOptimalLoad`  
 最佳的负载比。  
  
 `fLoThreshold`  
 对于负载比率的阈值下限。  
  
 `fHiThreshold`  
 对于负载比率的阈值上限。  
  
 `nBlockSize`  
 块大小。  
  
### <a name="remarks"></a>备注  
 `CAtlMap`引用所有其存储的元素的方法是首先创建索引的键使用哈希算法。 此索引引用了"bin"其中包含指向存储元素。 如果正在使用中，将创建一个链接列表来访问后续元素。 遍历列表是比直接访问正确的元素要慢，因此 map 结构需要权衡的要求存储和性能。 默认参数已经已选择在大多数情况下提供较好的结果。  
  
 负载比率是 map 对象中存储的元素数目的箱数的比率。 Map 结构被重新计算，时更新*fOptimalLoad*将使用参数值来计算所需的箱数。 此值可以更改使用[CAtlMap::SetOptimalLoad](#setoptimalload)方法。  
  
 `fLoThreshold`参数是较低的值之前可以达到的负载比`CAtlMap`将重新计算该映射的最佳大小。  
  
 `fHiThreshold`参数是较大的负载比联系方式为之前的值`CAtlMap`对象进行重新计算该映射的最佳大小。  
  
 默认情况下启用此重新计算过程 （称为重复讨论）。 如果你想要禁用此过程中，可能是输入包含大量数据一次调用时[CAtlMap::DisableAutoRehash](#disableautorehash)方法。 将其与重新激活[CAtlMap::EnableAutoRehash](#enableautorehash)方法。  
  
 `nBlockSize`参数是分配一个新元素时所需的内存量的度量值。 更大的块大小减少对内存分配例程的调用，但使用更多的资源。  
  
 可以存储任何数据之前，有必要初始化哈希表，通过调用[CAtlMap::InitHashTable](#inithashtable)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&72;](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlMap:: ~ CAtlMap  
 析构函数。  
  
```
~CAtlMap() throw();
```  
  
### <a name="remarks"></a>备注  
 释放任何已分配的资源。  
  
##  <a name="cpair_class"></a>CAtlMap::CPair 类  
 一个包含键和值的元素的类。  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>备注  
 方法使用此类[CAtlMap::GetNext](#getnext)和[CAtlMap::Lookup](#lookup)访问存储在映射结构的键和值元素。  
  
##  <a name="disableautorehash"></a>CAtlMap::DisableAutoRehash  
 调用此方法来禁用自动重复的讨论`CAtlMap`对象。  
  
```
void DisableAutoRehash() throw();
```  
  
### <a name="remarks"></a>备注  
 启用自动重复讨论后 （即它默认情况下），在哈希表的箱数将自动重新计算如果负载值 （存储在数组中的元素数目的箱数的比率） 超出了创建代码图的时间在指定的最大值或最小值。  
  
 `DisableAutoRehash`当大量的元素将上一次添加到映射，则将最为有用。 而不是触发 rehashing 进程，每次超出限制时，它会更有效调用`DisableAutoRehash`，添加元素，并最后调用[CAtlMap::EnableAutoRehash](#enableautorehash)。  
  
##  <a name="enableautorehash"></a>CAtlMap::EnableAutoRehash  
 调用此方法以启用自动重复的讨论`CAtlMap`对象。  
  
```
void EnableAutoRehash() throw();
```  
  
### <a name="remarks"></a>备注  
 启用自动重复讨论后 （即它默认情况下），在哈希表的箱数将自动重新计算如果负载值 （存储在数组中的元素数目的箱数的比率） 超出了在创建映射时指定的最大值或最小值。  
  
 **EnableAutoRefresh**最常用于在调用后[CAtlMap::DisableAutoRehash](#disableautorehash)。  
  
##  <a name="getat"></a>CAtlMap::GetAt  
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
  
 *值*  
 指定的映射值的类型的模板参数。  
  
### <a name="return-value"></a>返回值  
 返回指向当前对存储在映射的键/值元素的指针。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果发生断言错误`pos`是否等同于 NULL。  
  
##  <a name="getcount"></a>CAtlMap::GetCount  
 调用此方法以检索该映射中的元素数。  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 Map 对象中返回元素的数。 单个元素是一个键/值对。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="gethashtablesize"></a>CAtlMap::GetHashTableSize  
 调用此方法以确定映射的哈希表中的箱数。  
  
```
UINT GetHashTableSize() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回哈希表中的箱数。 请参阅[CAtlMap::CAtlMap](#catlmap)的说明。  
  
##  <a name="getkeyat"></a>CAtlMap::GetKeyAt  
 调用此方法以检索存储的指定位置中的键`CAtlMap`对象。  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>返回值  
 返回位于给定位置中存储的密钥对`CAtlMap`对象。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getnext"></a>CAtlMap::GetNext  
 调用此方法以获取对存储中的下一个元素的指针`CAtlMap`对象。  
  
```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>返回值  
 返回指向下一步对存储在映射的键/值元素的指针。 `pos`位置计数器在每次调用后被更新。 如果检索的元素是在映射中，最后一个`pos`设置为 NULL。  
  
##  <a name="getnextassoc"></a>CAtlMap::GetNextAssoc  
 获取用于循环的下一个元素。  
  
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
  
 *值*  
 指定的映射值的类型的模板参数。  
  
### <a name="remarks"></a>备注  
 `pos`位置计数器在每次调用后被更新。 如果检索的元素是在映射中，最后一个`pos`设置为 NULL。  
  
##  <a name="getnextkey"></a>CAtlMap::GetNextKey  
 调用此方法以检索中的下一步键`CAtlMap`对象。  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>返回值  
 返回映射中的下一步的键的引用。  
  
### <a name="remarks"></a>备注  
 更新当前的位置计数器， `pos`。 如果在映射中有更多的项，则会将位置计数器设置为 NULL。  
  
##  <a name="getnextvalue"></a>CAtlMap::GetNextValue  
 调用此方法以获取下一个值从`CAtlMap`对象。  
  
```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>返回值  
 返回映射中的下一步的值的引用。  
  
### <a name="remarks"></a>备注  
 更新当前的位置计数器， `pos`。 如果在映射中有更多的项，则会将位置计数器设置为 NULL。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getstartposition"></a>CAtlMap::GetStartPosition  
 调用此方法以开始映射迭代。  
  
```
POSITION GetStartPosition() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回如果映射为空，则返回起始位置，则为 NULL。  
  
### <a name="remarks"></a>备注  
 调用此方法以开始映射迭代通过返回**位置**值，可以传递给`GetNextAssoc`方法。  
  
> [!NOTE]
>  没有可预测的迭代顺序  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getvalueat"></a>CAtlMap::GetValueAt  
 调用此方法以检索存储的给定位置的值`CAtlMap`对象。  
  
```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>返回值  
 返回位于给定位置中存储的值的引用`CAtlMap`对象。  
  
##  <a name="inithashtable"></a>CAtlMap::InitHashTable  
 调用此方法以初始化哈希表。  
  
```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```  
  
### <a name="parameters"></a>参数  
 `nBins`  
 哈希表使用的箱数。 请参阅[CAtlMap::CAtlMap](#catlmap)的说明。  
  
 `bAllocNow`  
 标志指示应分配内存时。  
  
### <a name="return-value"></a>返回值  
 返回**true**上成功初始化**false**失败。  
  
### <a name="remarks"></a>备注  
 `InitHashTable`必须在调用之前存储在哈希表中的任何元素。  如果不显式调用此方法，它将自动调用第一次添加元素，则使用由指定的容器计数**CAtlMap**构造函数。  否则，该映射将使用初始化由指定的新容器计数`nBins`参数。  
  
 如果`bAllocNow`参数为 false 时，直到第一次是必需，将不会分配所需的哈希表的内存。 这可以是不确定，如果将使用该映射的情况下很有用。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="isempty"></a>CAtlMap::IsEmpty  
 调用此方法以测试空映射对象。  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回**true**如果映射为空， **false**否则为。  
  
##  <a name="kinargtype"></a>CAtlMap::KINARGTYPE  
 作为输入参数传递某个键时所使用的类型。  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="koutargtype"></a>CAtlMap::KOUTARGTYPE  
 作为输出参数返回一个密钥时所使用的类型。  
  
```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```  
  
##  <a name="lookup"></a>CAtlMap::Lookup  
 调用此方法来查找键或值的`CAtlMap`对象。  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 指定用于标识要查找的元素的键。  
  
 *值*  
 接收查阅到值的变量。  
  
### <a name="return-value"></a>返回值  
 该方法的第一种形式返回如果找到了项，否则为 false，则返回 true。 第二个和第三个窗体返回一个指向[CPair](#cpair_class)它可以作为位置使用，以便调用[CAtlMap::GetNext](#getnext) ，依此类推。  
  
### <a name="remarks"></a>备注  
 `Lookup`使用哈希算法来快速找到包含与给定的密钥参数完全匹配的键的地图元素。  
  
##  <a name="operator_at"></a>CAtlMap::operator\[\]  
 替换或添加到一个新元素`CAtlMap`。  
  
```
V& operator[](kinargtype key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要添加或替换的元素的键。  
  
### <a name="return-value"></a>返回值  
 返回与给定的键关联的值的引用。  
  
### <a name="example"></a>示例  
 如果键已存在，该元素将被替换。 如果该键不存在，添加一个新的元素。 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="rehash"></a>CAtlMap::Rehash  
 调用此方法以 rehash`CAtlMap`对象。  
  
```
void Rehash(UINT nBins = 0);
```  
  
### <a name="parameters"></a>参数  
 `nBins`  
 新的使用哈希表中的箱数。 请参阅[CAtlMap::CAtlMap](#catlmap)的说明。  
  
### <a name="remarks"></a>备注  
 如果`nBins`为 0，`CAtlMap`计算合理数量根据在映射和最佳负载设置中的元素的数目。 通常情况下 rehashing 过程是自动的但是，如果[CAtlMap::DisableAutoRehash](#disableautorehash)已被调用，此方法将执行必要的调整大小。  
  
##  <a name="removeall"></a>CAtlMap::RemoveAll  
 调用此方法来删除中的所有元素`CAtlMap`对象。  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>备注  
 将清除`CAtlMap`对象，并释放内存用来存储元素。  
  
##  <a name="removeatpos"></a>CAtlMap::RemoveAtPos  
 调用此方法来删除中的指定位置处的元素`CAtlMap`对象。  
  
```
void RemoveAtPos(POSITION pos) throw();
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="remarks"></a>备注  
 删除存储在指定位置处的键/值对。 在用来存储该元素将释放内存。 由位置引用`pos`将变为无效，并在地图中的任何其他元素的位置保持有效，它们不一定是执行时保留相同的顺序。  
  
##  <a name="removekey"></a>CAtlMap::RemoveKey  
 调用此方法来删除从元素`CAtlMap`给定键的对象。  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 你想要删除键相对应的元素对。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果找到该键并将其删除， **false**失败。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="setat"></a>CAtlMap::SetAt  
 调用此方法来插入到映射的元素对。  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要添加到密钥值`CAtlMap`对象。  
  
 *值*  
 要添加到值`CAtlMap`对象。  
  
### <a name="return-value"></a>返回值  
 返回的位置中的键/值元素对`CAtlMap`对象。  
  
### <a name="remarks"></a>备注  
 `SetAt`如果找到匹配项，将替换现有元素。 如果未找到该键，则创建新的键/值对。  
  
##  <a name="setoptimalload"></a>CAtlMap::SetOptimalLoad  
 调用此方法可设置的最佳负载`CAtlMap`对象。  
  
```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```  
  
### <a name="parameters"></a>参数  
 `fOptimalLoad`  
 最佳的负载比。  
  
 `fLoThreshold`  
 对于负载比率的阈值下限。  
  
 `fHiThreshold`  
 对于负载比率的阈值上限。  
  
 `bRehashNow`  
 该标志指明如果应计算哈希表。  
  
### <a name="remarks"></a>备注  
 此方法将重新定义的最佳负载值`CAtlMap`对象。 请参阅[CAtlMap::CAtlMap](#catlmap)有关的各个参数的讨论。 如果`bRehashNow`为 true，并且元素的数目超出最小和最大值，重新计算哈希表。  
  
##  <a name="setvalueat"></a>CAtlMap::SetValueAt  
 调用此方法以更改存储中的给定位置的值`CAtlMap`对象。  
  
```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 返回上次调用的位置计数器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
 *值*  
 要添加到值`CAtlMap`对象。  
  
### <a name="remarks"></a>备注  
 更改存储中的指定位置的值元素`CAtlMap`对象。  
  
##  <a name="vinargtype"></a>CAtlMap::VINARGTYPE  
 将值传递作为输入参数时所使用的类型。  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="voutargtype"></a>CAtlMap::VOUTARGTYPE  
 作为输出参数传递一个值时所使用的类型。  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
##  <a name="m_key"></a>CAtlMap::CPair::m_key  
 数据成员将存储的关键元素。  
  
```
const K m_key;
```    
  
### <a name="parameters"></a>参数  
 `K`  
 键的元素类型。  
  
##  <a name="m_value"></a>CAtlMap::CPair::m_value  
 存储的值元素，该数据成员。  
  
```
V  m_value;
```    
  
### <a name="parameters"></a>参数  
 *V*  
 值的元素类型。  
  
## <a name="see-also"></a>另请参阅  
 [字幕示例](../../visual-cpp-samples.md)   
 [UpdatePV 示例](../../visual-cpp-samples.md)   
 [类概述](../../atl/atl-class-overview.md)

