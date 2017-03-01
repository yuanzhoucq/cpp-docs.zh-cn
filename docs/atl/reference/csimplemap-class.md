---
title: "CSimpleMap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CSimpleMap
- ATL.CSimpleMap
- CSimpleMap
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: c02ef1d9d3fafebf38abaaa55d77511f4476a02f
ms.lasthandoff: 02/24/2017

---
# <a name="csimplemap-class"></a>CSimpleMap 类
此类简单映射阵列提供支持。  
  
## <a name="syntax"></a>语法  
  
```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>  
class CSimpleMap
```  
  
#### <a name="parameters"></a>参数  
 `TKey`  
 键的元素类型。  
  
 `TVal`  
 值的元素类型。  
  
 `TEqual`  
 特征对象，用于定义类型的元素相等性测试`T`。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|对于值类型的 Typedef。|  
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|对键类型的 Typedef。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CSimpleMap::CSimpleMap](#csimplemap)|构造函数。|  
|[CSimpleMap:: ~ CSimpleMap](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSimpleMap::Add](#add)|映射阵列中添加的键和相关联的值。|  
|[CSimpleMap::FindKey](#findkey)|查找特定键。|  
|[CSimpleMap::FindVal](#findval)|查找特定值。|  
|[CSimpleMap::GetKeyAt](#getkeyat)|检索指定的键。|  
|[CSimpleMap::GetSize](#getsize)|映射阵列中返回的项数。|  
|[CSimpleMap::GetValueAt](#getvalueat)|检索指定的值。|  
|[CSimpleMap::Lookup](#lookup)|返回与给定的键关联的值。|  
|[CSimpleMap::Remove](#remove)|删除密钥和匹配的值。|  
|[CSimpleMap::RemoveAll](#removeall)|删除所有键和值。|  
|[CSimpleMap::RemoveAt](#removeat)|删除特定的键和匹配的值。|  
|[CSimpleMap::ReverseLookup](#reverselookup)|返回与给定的值相关联的密钥。|  
|[CSimpleMap::SetAt](#setat)|设置与给定的键相关联的值。|  
|[CSimpleMap::SetAtIndex](#setatindex)|设置特定的键和值。|  
  
## <a name="remarks"></a>备注  
 `CSimpleMap`提供对任何给定的类型的简单映射数组的支持`T`，管理无序的键的元素和相关联的值数组。  
  
 该参数`TEqual`提供了一种定义类型的两个元素相等性比较函数`T`。 通过创建一个类类似于[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)，就可能会更改任何给定数组相等性测试的行为。 例如，当处理的指针的数组，它可能有必要定义为根据指针引用的值的相等性。 默认实现使用**operator==()**。  
  
 同时`CSimpleMap`和[CSimpleArray](../../atl/reference/csimplearray-class.md)为释放与以前的 ATL 的兼容性，并由提供更完整且有效的集合实现提供[CAtlArray](../../atl/reference/catlarray-class.md)和[CAtlMap](../../atl/reference/catlmap-class.md)。  
  
 与不同的是 ATL 和 MFC 中的其他映射集合，此类实现与一个简单的数组，并查找搜索需要的线性搜索。 `CAtlMap`在该数组包含的元素数量大时，应使用。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsimpcoll.h  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&91;](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]  
  
##  <a name="a-nameadda--csimplemapadd"></a><a name="add"></a>CSimpleMap::Add  
 映射阵列中添加的键和相关联的值。  
  
```
BOOL Add(const TKey& key, const TVal& val);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 键。  
  
 *val*  
 关联的值。  
  
### <a name="return-value"></a>返回值  
 键和值是否已成功添加，则返回 FALSE 否则，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 每个键 / 值对添加映射数组内存释放和重新分配，从而确保每个数据始终连续存储的原因。 也就是说，第二个关键元素始终紧随在内存中的第一个关键元素，依此类推。  
  
##  <a name="a-namearrayelementtypea--csimplemaparrayelementtype"></a><a name="_arrayelementtype"></a>CSimpleMap::_ArrayElementType  
 密钥类型的 typedef。  
  
```
typedef TVal _ArrayElementType;
```  
  
##  <a name="a-namearraykeytypea--csimplemaparraykeytype"></a><a name="_arraykeytype"></a>CSimpleMap::_ArrayKeyType  
 值类型的 typedef。  
  
```
typedef TKey _ArrayKeyType;
```  
  
##  <a name="a-namecsimplemapa--csimplemapcsimplemap"></a><a name="csimplemap"></a>CSimpleMap::CSimpleMap  
 构造函数。  
  
```
CSimpleMap();
```  
  
### <a name="remarks"></a>备注  
 数据成员初始化。  
  
##  <a name="a-namedtora--csimplemapcsimplemap"></a><a name="dtor"></a>CSimpleMap:: ~ CSimpleMap  
 析构函数。  
  
```
~CSimpleMap();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="a-namefindkeya--csimplemapfindkey"></a><a name="findkey"></a>CSimpleMap::FindKey  
 查找特定键。  
  
```
int FindKey(const TKey& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要搜索的键。  
  
### <a name="return-value"></a>返回值  
 返回找到的密钥 if 索引，否则返回-1。  
  
##  <a name="a-namefindvala--csimplemapfindval"></a><a name="findval"></a>CSimpleMap::FindVal  
 查找特定值。  
  
```
int FindVal(const TVal& val) const;
```  
  
### <a name="parameters"></a>参数  
 *val*  
 要搜索值。  
  
### <a name="return-value"></a>返回值  
 返回值的索引如果找到，否则返回-1。  
  
##  <a name="a-namegetkeyata--csimplemapgetkeyat"></a><a name="getkeyat"></a>CSimpleMap::GetKeyAt  
 检索位于指定索引处的密钥。  
  
```
TKey& GetKeyAt(int nIndex) const;
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要返回的键的索引。  
  
### <a name="return-value"></a>返回值  
 返回引用的键`nIndex`。  
  
### <a name="remarks"></a>备注  
 通过传递的索引`nIndex`必须是有效的有意义的返回值。  
  
##  <a name="a-namegetsizea--csimplemapgetsize"></a><a name="getsize"></a>CSimpleMap::GetSize  
 映射阵列中返回的项数。  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>返回值  
 映射阵列中返回的项数 （键和值是一项）。  
  
##  <a name="a-namegetvalueata--csimplemapgetvalueat"></a><a name="getvalueat"></a>CSimpleMap::GetValueAt  
 检索位于特定索引处的值。  
  
```
TVal& GetValueAt(int nIndex) const;
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要返回的值的索引。  
  
### <a name="return-value"></a>返回值  
 返回由引用的值`nIndex`。  
  
### <a name="remarks"></a>备注  
 通过传递的索引`nIndex`必须是有效的有意义的返回值。  
  
##  <a name="a-namelookupa--csimplemaplookup"></a><a name="lookup"></a>CSimpleMap::Lookup  
 返回与给定的键关联的值。  
  
```
TVal Lookup(const TKey& key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 键。  
  
### <a name="return-value"></a>返回值  
 返回关联的值。 如果没有匹配的键是找到为 NULL 则返回。  
  
##  <a name="a-nameremovea--csimplemapremove"></a><a name="remove"></a>CSimpleMap::Remove  
 删除密钥和匹配的值。  
  
```
BOOL Remove(const TKey& key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 键。  
  
### <a name="return-value"></a>返回值  
 键和匹配的值是否已成功删除，则返回 FALSE 否则，则返回 TRUE。  
  
##  <a name="a-nameremovealla--csimplemapremoveall"></a><a name="removeall"></a>CSimpleMap::RemoveAll  
 删除所有键和值。  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 删除映射数组对象中的所有键和值。  
  
##  <a name="a-nameremoveata--csimplemapremoveat"></a><a name="removeat"></a>CSimpleMap::RemoveAt  
 删除密钥和关联的指定索引处的值。  
  
```
BOOL RemoveAt(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 密钥和要删除的关联的值的索引。  
  
### <a name="return-value"></a>返回值  
 如果，返回 TRUE 成功时，FALSE 指定的索引是无效的索引。  
  
##  <a name="a-namereverselookupa--csimplemapreverselookup"></a><a name="reverselookup"></a>CSimpleMap::ReverseLookup  
 返回与给定的值相关联的密钥。  
  
```
TKey ReverseLookup(const TVal& val) const;
```  
  
### <a name="parameters"></a>参数  
 *val*  
 值。  
  
### <a name="return-value"></a>返回值  
 返回关联的键。 如果没有匹配的键是找到为 NULL 则返回。  
  
##  <a name="a-namesetata--csimplemapsetat"></a><a name="setat"></a>CSimpleMap::SetAt  
 设置与给定的键相关联的值。  
  
```
BOOL SetAt(const TKey& key, const TVal& val);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 键。  
  
 *val*  
 要分配的新值。  
  
### <a name="return-value"></a>返回值  
 如果找到该键，而的值已成功更改，则返回 FALSE 否则，返回 TRUE。  
  
##  <a name="a-namesetatindexa--csimplemapsetatindex"></a><a name="setatindex"></a>CSimpleMap::SetAtIndex  
 设置指定索引处的键和值。  
  
```
BOOL SetAtIndex(  
    int nIndex,
    const TKey& key,
    const TVal& val);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 引用的键和值对来更改索引。  
  
 `key`  
 新的密钥。  
  
 *val*  
 新值。  
  
### <a name="return-value"></a>返回值  
 如果，返回 TRUE 成功，则 FALSE 如果索引无效。  
  
### <a name="remarks"></a>备注  
 更新的键和值指向的`nIndex`。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

