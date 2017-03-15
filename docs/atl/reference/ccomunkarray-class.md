---
title: "CComUnkArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComUnkArray
- ATL.CComUnkArray<nMaxSize>
- ATL::CComUnkArray<nMaxSize>
- ATL::CComUnkArray
- CComUnkArray
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
caps.latest.revision: 17
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 94f1062ff3808f527874a8890eca95c9b655b1bf
ms.lasthandoff: 02/24/2017

---
# <a name="ccomunkarray-class"></a>CComUnkArray 类
此类存储**IUnknown**指针，它旨在以参数形式向使用[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类。  
  
## <a name="syntax"></a>语法  
  
```
template<unsigned int nMaxSize>
class CComUnkArray
```  
  
#### <a name="parameters"></a>参数  
 *nMaxSize*  
 最大数**IUnknown**可以包含在静态数组的指针。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComUnkArray::CComUnkArray](#ccomunkarray)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComUnkArray::Add](#add)|调用此方法可添加**IUnknown**指向数组的指针。|  
|[CComUnkArray::begin](#begin)|将指针返回到第一个**IUnknown**集合中的指针。|  
|[CComUnkArray::end](#end)|将指针返回到上一次之后一个**IUnknown**集合中的指针。|  
|[CComUnkArray::GetCookie](#getcookie)|调用此方法以获取与关联的 cookie 给定**IUnknown**指针。|  
|[CComUnkArray::GetUnknown](#getunknown)|调用此方法以获取**IUnknown**给定 cookie 与相关联的指针。|  
|[CComUnkArray::Remove](#remove)|调用此方法来删除**IUnknown**从数组的指针。|  
  
## <a name="remarks"></a>备注  
 **CComUnkArray**保存固定的数量的**IUnknown**指针，每个连接上的某个接口的点。 **CComUnkArray**可以使用以参数形式向[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类。 **CComUnkArray\<1&1;>**是模板专用化**CComUnkArray** ，经过优化的一个连接点。  
  
 **CComUnkArray**方法[开始](#begin)和[结束](#end)可用于循环访问所有连接点 （例如，激发的事件时）。  
  
 请参阅[添加到对象的连接点](../../atl/adding-connection-points-to-an-object.md)点代理服务器的自动创建连接的详细信息。  
  
> [!NOTE]
> **请注意**类[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)由**添加类**向导创建一个具有连接点的控件时。 如果你想要手动指定连接点的数量，将更改从引用**CComDynamicUnkArray**到`CComUnkArray<` *n* `>`，其中*n*是所需的连接点的数目。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-nameadda--ccomunkarrayadd"></a><a name="add"></a>CComUnkArray::Add  
 调用此方法可添加**IUnknown**指向数组的指针。  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 调用此方法可添加**IUnknown**指向数组的指针。  
  
### <a name="return-value"></a>返回值  
 返回与新添加的指针，则为 0，如果数组是不足够大以包含新的指针的 cookie。  
  
##  <a name="a-namebegina--ccomunkarraybegin"></a><a name="begin"></a>CComUnkArray::begin  
 将指针返回到的集合的开头**IUnknown**接口指针。  
  
```
IUnknown**
    begin();
```     
  
### <a name="return-value"></a>返回值  
 一个指向**IUnknown**接口指针。  
  
### <a name="remarks"></a>备注  
 该集合包含为本地存储的接口指针**IUnknown**。 您在将每个转换**IUnknown**接口为实际的接口类型，然后调用通过它。 不需要的接口第一次查询。  
  
 在使用之前**IUnknown**接口，您应检查不是**NULL**。  
  
##  <a name="a-nameccomunkarraya--ccomunkarrayccomunkarray"></a><a name="ccomunkarray"></a>CComUnkArray::CComUnkArray  
 构造函数。  
  
```
CComUnkArray();
```  
  
### <a name="remarks"></a>备注  
 设置的集合来保存`nMaxSize` **IUnknown**指针，并初始化指向**NULL**。  
  
##  <a name="a-nameenda--ccomunkarrayend"></a><a name="end"></a>CComUnkArray::end  
 将指针返回到上一次之后一个**IUnknown**集合中的指针。  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>返回值  
 一个指向**IUnknown**接口指针。  
  
### <a name="remarks"></a>备注  
 `CComUnkArray`方法**开始**和**结束**可用于遍历所有连接点，例如，激发的事件时。  
  
 [!code-cpp[NVC_ATL_COM&#44;](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]  
  
##  <a name="a-namegetcookiea--ccomunkarraygetcookie"></a><a name="getcookie"></a>CComUnkArray::GetCookie  
 调用此方法以获取与关联的 cookie 给定**IUnknown**指针。  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>参数  
 `ppFind`  
 **IUnknown**关联的 cookie 为所需的指针。  
  
### <a name="return-value"></a>返回值  
 返回与关联的 cookie **IUnknown**指针或如果没有匹配的 0 **IUnknown**找到指针。  
  
### <a name="remarks"></a>备注  
 如果没有相同的多个实例**IUnknown**指针，此函数将返回第一个 cookie。  
  
##  <a name="a-namegetunknowna--ccomunkarraygetunknown"></a><a name="getunknown"></a>CComUnkArray::GetUnknown  
 调用此方法以获取**IUnknown**给定 cookie 与相关联的指针。  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>参数  
 `dwCookie`  
 为其 cookie 关联**IUnknown**指针是必需的。  
  
### <a name="return-value"></a>返回值  
 返回**IUnknown**指针，则为 NULL，如果不找到任何匹配的 cookie。  
  
##  <a name="a-nameremovea--ccomunkarrayremove"></a><a name="remove"></a>CComUnkArray::Remove  
 调用此方法来删除**IUnknown**从数组的指针。  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>参数  
 `dwCookie`  
 Cookie 引用**IUnknown**指针，用以从数组中删除。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果删除指针，则**FALSE**否则为。  
  
## <a name="see-also"></a>另请参阅  
 [CComDynamicUnkArray 类](../../atl/reference/ccomdynamicunkarray-class.md)   
 [类概述](../../atl/atl-class-overview.md)

