---
title: CSimpleArray 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 187dee79cd09e366fb56d9cd0e71395589476a69
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364255"
---
# <a name="csimplearray-class"></a>CSimpleArray 类
此类提供用于管理简单数组的方法。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>  
class CSimpleArray
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在数组中的数据类型。  
  
 `TEqual`  
 定义类型的元素相等性测试的特征对象`T`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleArray::CSimpleArray](#csimplearray)|简单数组构造函数。|  
|[CSimpleArray:: ~ CSimpleArray](#dtor)|简单数组的析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleArray::Add](#add)|将新元素添加到数组。|  
|[CSimpleArray::Find](#find)|数组中查找的元素。|  
|[CSimpleArray::GetData](#getdata)|返回一个指向数组中存储的数据。|  
|[CSimpleArray::GetSize](#getsize)|返回存储在数组中元素的数目。|  
|[CSimpleArray::Remove](#remove)|从数组中移除给定的元素。|  
|[CSimpleArray::RemoveAll](#removeall)|从数组中移除所有元素。|  
|[CSimpleArray::RemoveAt](#removeat)|从数组中移除指定的元素。|  
|[CSimpleArray::SetAtIndex](#setatindex)|设置数组中指定的元素。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleArray::operator\[\]](#operator_at)|从数组中检索元素。|  
|[CSimpleArray::operator =](#operator_eq)|赋值运算符。|  

  
## <a name="remarks"></a>备注  
 `CSimpleArray` 提供用于创建和管理一个简单的数组，任何给定的类型的方法`T`。  
  
 参数`TEqual`提供了一种定义的类型的两个元素相等性比较函数`T`。 通过创建一个类类似于[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)，可以改变的相等性测试的任何给定的数组的行为。 例如，在处理一个指针数组，它可能会有用定义为相等性，具体取决于指针引用的值。 默认实现利用**operator=()**。  
  
 同时`CSimpleArray`和[CSimpleMap](../../atl/reference/csimplemap-class.md)旨在用于少量的元素。 [CAtlArray](../../atl/reference/catlarray-class.md)和[CAtlMap](../../atl/reference/catlmap-class.md)数组包含大量元素时，应使用。  
  
## <a name="requirements"></a>要求  
 **标头：** atlsimpcoll.h  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]  
  
##  <a name="add"></a>  CSimpleArray::Add  
 将新元素添加到数组。  
  
```
BOOL Add(const T& t);
```  
  
### <a name="parameters"></a>参数  
 *t*  
 要添加到数组的元素。  
  
### <a name="return-value"></a>返回值  
 如果该元素已成功添加到数组中，FALSE 否则，则返回 TRUE。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]  
  
##  <a name="csimplearray"></a>  CSimpleArray::CSimpleArray  
 数组对象的构造函数。  
  
```
CSimpleArray(const CSimpleArray<T, TEqual>& src);  
CSimpleArray();
```     
  
### <a name="parameters"></a>参数  
 *src*  
 一个现有的 `CSimpleArray` 对象。  
  
### <a name="remarks"></a>备注  
 初始化数据成员，创建新的空`CSimpleArray`对象或现有的副本`CSimpleArray`对象。  
  
##  <a name="dtor"></a>  CSimpleArray:: ~ CSimpleArray  
 析构函数。  
  
```
~CSimpleArray();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="find"></a>  CSimpleArray::Find  
 数组中查找的元素。  
  
```
int Find(const T& t) const;
```  
  
### <a name="parameters"></a>参数  
 *t*  
 要搜索元素。  
  
### <a name="return-value"></a>返回值  
 如果未找到的元素，则返回找到的元素，则为-1 的索引。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]  
  
##  <a name="getdata"></a>  CSimpleArray::GetData  
 返回一个指向数组中存储的数据。  
  
```
T* GetData() const;
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向数组中的数据。  
  
##  <a name="getsize"></a>  CSimpleArray::GetSize  
 返回存储在数组中元素的数目。  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>返回值  
 返回存储在数组中元素的数目。  
  
##  <a name="operator_at"></a>  CSimpleArray::operator \[\]  
 从数组中检索元素。  
  
```
T& operator[](int nindex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 元素索引中。  
  
### <a name="return-value"></a>返回值  
 返回所引用的数组的元素`nIndex`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]  
  
##  <a name="operator_eq"></a>  CSimpleArray::operator =  
 赋值运算符。  
  
```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```  
  
### <a name="parameters"></a>参数  
 *src*  
 要复制的数组。  
  
### <a name="return-value"></a>返回值  
 将指针返回到更新`CSimpleArray`对象。  
  
### <a name="remarks"></a>备注  
 将从所有元素都复制`CSimpleArray`所引用对象*src*到当前数组对象中，替换现有的所有数据。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]  
  
##  <a name="remove"></a>  CSimpleArray::Remove  
 从数组中移除给定的元素。  
  
```
BOOL Remove(const T& t);
```  
  
### <a name="parameters"></a>参数  
 *t*  
 要从数组中移除的元素。  
  
### <a name="return-value"></a>返回值  
 如果该元素是找到并移除，FALSE 否则，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 元素中删除时，会重新编号数组中的剩余元素来填充空白区域。  
  
##  <a name="removeall"></a>  CSimpleArray::RemoveAll  
 从数组中移除所有元素。  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 移除当前存储在数组中的所有元素。  
  
##  <a name="removeat"></a>  CSimpleArray::RemoveAt  
 从数组中移除指定的元素。  
  
```
BOOL RemoveAtint nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指向要移除的元素的索引。  
  
### <a name="return-value"></a>返回值  
 如果此元素是已删除，如果索引无效，则返回 FALSE，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 元素中删除时，会重新编号数组中的剩余元素来填充空白区域。  
  
##  <a name="setatindex"></a>  CSimpleArray::SetAtIndex  
 设置数组中指定的元素。  
  
```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要更改的元素的索引。  
  
 *t*  
 要分配给指定元素的值。  
  
### <a name="return-value"></a>返回值  
 如果，返回 TRUE 成功，则为 FALSE 如果索引无效。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
