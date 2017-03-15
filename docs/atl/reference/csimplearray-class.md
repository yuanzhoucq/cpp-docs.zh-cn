---
title: "CSimpleArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CSimpleArray
- ATL::CSimpleArray
- CSimpleArray
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
caps.latest.revision: 20
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: e261f95a375a2edda1d543a36b605d23fc718b99
ms.lasthandoff: 02/24/2017

---
# <a name="csimplearray-class"></a>CSimpleArray 类
此类提供用于管理一个简单的数组的方法。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>  
class CSimpleArray
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在数组中的数据类型。  
  
 `TEqual`  
 特征对象，用于定义类型的元素相等性测试`T`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CSimpleArray::CSimpleArray](#csimplearray)|简单数组的构造函数。|  
|[CSimpleArray:: ~ CSimpleArray](#dtor)|简单数组的析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleArray::Add](#add)|将新元素添加到数组。|  
|[CSimpleArray::Find](#find)|数组中查找的元素。|  
|[CSimpleArray::GetData](#getdata)|返回指向数组中存储的数据的指针。|  
|[CSimpleArray::GetSize](#getsize)|返回存储在数组中的元素数量。|  
|[CSimpleArray::Remove](#remove)|从数组中移除给定的元素。|  
|[CSimpleArray::RemoveAll](#removeall)|从数组中移除所有元素。|  
|[CSimpleArray::RemoveAt](#removeat)|从数组中移除指定的元素。|  
|[CSimpleArray::SetAtIndex](#setatindex)|设置数组中指定的元素。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CSimpleArray::operator\[\]](#operator_at)|从数组中检索元素。|  
|[CSimpleArray::operator =](#operator_eq)|赋值运算符。|  

  
## <a name="remarks"></a>备注  
 `CSimpleArray`提供用于创建和管理任何给定的类型的简单数组的方法`T`。  
  
 该参数`TEqual`提供了一种定义类型的两个元素相等性比较函数`T`。 通过创建一个类类似于[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)，就可能会更改任何给定数组相等性测试的行为。 例如，当处理的指针的数组，它可能有必要定义为根据指针引用的值的相等性。 默认实现使用**operator=()**。  
  
 同时`CSimpleArray`和[CSimpleMap](../../atl/reference/csimplemap-class.md)旨在用于少量元素。 [CAtlArray](../../atl/reference/catlarray-class.md)和[CAtlMap](../../atl/reference/catlmap-class.md)该数组包含的元素数量大时，应使用。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsimpcoll.h  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&86;](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]  
  
##  <a name="a-nameadda--csimplearrayadd"></a><a name="add"></a>CSimpleArray::Add  
 将新元素添加到数组。  
  
```
BOOL Add(const T& t);
```  
  
### <a name="parameters"></a>参数  
 *t*  
 要添加到数组的元素。  
  
### <a name="return-value"></a>返回值  
 如果该元素已成功添加到 FALSE 的数组，否则，则返回 TRUE。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&87;](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]  
  
##  <a name="a-namecsimplearraya--csimplearraycsimplearray"></a><a name="csimplearray"></a>CSimpleArray::CSimpleArray  
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
  
##  <a name="a-namedtora--csimplearraycsimplearray"></a><a name="dtor"></a>CSimpleArray:: ~ CSimpleArray  
 析构函数。  
  
```
~CSimpleArray();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="a-namefinda--csimplearrayfind"></a><a name="find"></a>CSimpleArray::Find  
 数组中查找的元素。  
  
```
int Find(const T& t) const;
```  
  
### <a name="parameters"></a>参数  
 *t*  
 为要搜索的元素。  
  
### <a name="return-value"></a>返回值  
 如果未找到的元素，则返回找到的元素，则为-1 的索引。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&88;](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]  
  
##  <a name="a-namegetdataa--csimplearraygetdata"></a><a name="getdata"></a>CSimpleArray::GetData  
 返回指向数组中存储的数据的指针。  
  
```
T* GetData() const;
```  
  
### <a name="return-value"></a>返回值  
 返回指向数组中的数据的指针。  
  
##  <a name="a-namegetsizea--csimplearraygetsize"></a><a name="getsize"></a>CSimpleArray::GetSize  
 返回存储在数组中的元素数量。  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>返回值  
 返回存储在数组中的元素数量。  
  
##  <a name="a-nameoperatorata--csimplearrayoperator-"></a><a name="operator_at"></a>CSimpleArray::operator\[\]  
 从数组中检索元素。  
  
```
T& operator[](int nindex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 元素的索引。  
  
### <a name="return-value"></a>返回值  
 返回所引用的数组的元素`nIndex`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&89;](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]  
  
##  <a name="a-nameoperatoreqa--csimplearrayoperator-"></a><a name="operator_eq"></a>CSimpleArray::operator =  
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
 返回一个指向已更新`CSimpleArray`对象。  
  
### <a name="remarks"></a>备注  
 将复制中的所有元素`CSimpleArray`所引用对象*src*到当前数组对象替换所有现有的数据。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&90;](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]  
  
##  <a name="a-nameremovea--csimplearrayremove"></a><a name="remove"></a>CSimpleArray::Remove  
 从数组中移除给定的元素。  
  
```
BOOL Remove(const T& t);
```  
  
### <a name="parameters"></a>参数  
 *t*  
 要从数组中移除的元素。  
  
### <a name="return-value"></a>返回值  
 如果该元素是找到并移除，则 FALSE 否则，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 在删除某个元素后，该数组中的其余元素会重新编号来填充空白区域。  
  
##  <a name="a-nameremovealla--csimplearrayremoveall"></a><a name="removeall"></a>CSimpleArray::RemoveAll  
 从数组中移除所有元素。  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 移除当前存储在数组中的所有元素。  
  
##  <a name="a-nameremoveata--csimplearrayremoveat"></a><a name="removeat"></a>CSimpleArray::RemoveAt  
 从数组中移除指定的元素。  
  
```
BOOL RemoveAtint nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指向要移除的元素的索引。  
  
### <a name="return-value"></a>返回值  
 此元素是已删除，如果索引无效，则返回 FALSE，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 在删除某个元素后，该数组中的其余元素会重新编号来填充空白区域。  
  
##  <a name="a-namesetatindexa--csimplearraysetatindex"></a><a name="setatindex"></a>CSimpleArray::SetAtIndex  
 将指定的元素设置数组中。  
  
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
 如果，返回 TRUE 成功，则 FALSE 如果索引无效。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

