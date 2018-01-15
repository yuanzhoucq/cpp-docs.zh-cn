---
title: "CComUnkArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
dev_langs: C++
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ca462648a43869b11984e4582c8eb2c3dfaece7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomunkarray-class"></a>CComUnkArray 类
此类存储**IUnknown**指针，而是使用作为参数传递给[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类。  
  
## <a name="syntax"></a>语法  
  
```
template<unsigned int nMaxSize>
class CComUnkArray
```  
  
#### <a name="parameters"></a>参数  
 *nMaxSize*  
 最大数**IUnknown**可以保存在静态数组的指针。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComUnkArray::CComUnkArray](#ccomunkarray)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComUnkArray::Add](#add)|调用此方法可添加**IUnknown**到数组的指针。|  
|[CComUnkArray::begin](#begin)|将指针返回到第一个**IUnknown**集合中的指针。|  
|[CComUnkArray::end](#end)|将指针返回到一个过去的最后一个**IUnknown**集合中的指针。|  
|[CComUnkArray::GetCookie](#getcookie)|调用此方法以获取与关联的 cookie 给定**IUnknown**指针。|  
|[CComUnkArray::GetUnknown](#getunknown)|调用此方法以获取**IUnknown**给定 cookie 与关联的指针。|  
|[CComUnkArray::Remove](#remove)|调用此方法以删除**IUnknown**从数组的指针。|  
  
## <a name="remarks"></a>备注  
 **CComUnkArray**保存固定的数量的**IUnknown**指针，每个点的连接上的接口。 **CComUnkArray**可作为参数传递给[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类。 **CComUnkArray\<1 >**模板专用化**CComUnkArray** ，经过优化的一个连接点。  
  
 **CComUnkArray**方法[开始](#begin)和[结束](#end)可用于循环访问所有连接点 （例如，激发事件时）。  
  
 请参阅[添加到的对象的连接点](../../atl/adding-connection-points-to-an-object.md)有关详细信息自动创建的连接点代理服务器。  
  
> [!NOTE]
> **请注意**类[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)由**添加类**向导创建控件具有连接点时。 如果你想要手动指定连接点的数目，更改从引用**CComDynamicUnkArray**到`CComUnkArray<`  *n*  `>`，其中*n* 是所需的连接点数目。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcom.h  
  
##  <a name="add"></a>CComUnkArray::Add  
 调用此方法可添加**IUnknown**到数组的指针。  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 调用此方法可添加**IUnknown**到数组的指针。  
  
### <a name="return-value"></a>返回值  
 返回数组是否不足够大以包含新指针与新添加的指针或 0 相关联的 cookie。  
  
##  <a name="begin"></a>CComUnkArray::begin  
 将指针返回到的集合的开头**IUnknown**接口指针。  
  
```
IUnknown**
    begin();
```     
  
### <a name="return-value"></a>返回值  
 指向的指针**IUnknown**接口指针。  
  
### <a name="remarks"></a>备注  
 该集合包含指向本地存储为接口**IUnknown**。 强制每个转换**IUnknown**接口为实际的接口类型，然后调用通过它。 不需要首先查询的接口。  
  
 在使用之前**IUnknown**接口，应检查它不是**NULL**。  
  
##  <a name="ccomunkarray"></a>CComUnkArray::CComUnkArray  
 构造函数。  
  
```
CComUnkArray();
```  
  
### <a name="remarks"></a>备注  
 设置要保存的集合`nMaxSize` **IUnknown**指针，并初始化指向**NULL**。  
  
##  <a name="end"></a>CComUnkArray::end  
 将指针返回到一个过去的最后一个**IUnknown**集合中的指针。  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>返回值  
 指向的指针**IUnknown**接口指针。  
  
### <a name="remarks"></a>备注  
 `CComUnkArray`方法**开始**和**结束**可用于循环访问所有连接点，例如，激发事件时。  
  
 [!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]  
  
##  <a name="getcookie"></a>CComUnkArray::GetCookie  
 调用此方法以获取与关联的 cookie 给定**IUnknown**指针。  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>参数  
 `ppFind`  
 **IUnknown**需要关联的 cookie 的指针。  
  
### <a name="return-value"></a>返回值  
 返回与关联的 cookie **IUnknown**指针或如果没有任何匹配 0 **IUnknown**找到指针。  
  
### <a name="remarks"></a>备注  
 是否有多个实例的相同**IUnknown**指针，此函数将返回针对第一个 cookie。  
  
##  <a name="getunknown"></a>CComUnkArray::GetUnknown  
 调用此方法以获取**IUnknown**给定 cookie 与关联的指针。  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>参数  
 `dwCookie`  
 为其 cookie 关联**IUnknown**指针是必需的。  
  
### <a name="return-value"></a>返回值  
 返回**IUnknown**指针或 NULL 如果不找到任何匹配的 cookie。  
  
##  <a name="remove"></a>CComUnkArray::Remove  
 调用此方法以删除**IUnknown**从数组的指针。  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>参数  
 `dwCookie`  
 Cookie 引用**IUnknown**指针从数组中移除。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果删除指针，则**FALSE**否则为。  
  
## <a name="see-also"></a>请参阅  
 [CComDynamicUnkArray 类](../../atl/reference/ccomdynamicunkarray-class.md)   
 [类概述](../../atl/atl-class-overview.md)
