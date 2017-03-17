---
title: "CComDynamicUnkArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 69fc2c9dbb86f88c85461e765182fd88050521e9
ms.lasthandoff: 02/24/2017

---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray 类
此类存储的数组**IUnknown**指针。  
  
## <a name="syntax"></a>语法  
  
```
class CComDynamicUnkArray
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|构造函数。 初始化集合的值为**NULL**和集合大小为零。|  
|[CComDynamicUnkArray:: ~ CComDynamicUnkArray](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComDynamicUnkArray::Add](#add)|调用此方法可添加`IUnknown`指向数组的指针。|  
|[CComDynamicUnkArray::begin](#begin)|将指针返回到第一个`IUnknown`集合中的指针。|  
|[CComDynamicUnkArray::clear](#clear)|清空该数组。|  
|[CComDynamicUnkArray::end](#end)|将指针返回到上一次之后一个**IUnknown**集合中的指针。|  
|[CComDynamicUnkArray::GetAt](#getat)|检索位于指定索引处的元素。|  
|[CComDynamicUnkArray::GetCookie](#getcookie)|调用此方法以获取与关联的 cookie 给定**IUnknown**指针。|  
|[CComDynamicUnkArray::GetSize](#getsize)|返回一个数组的长度。|  
|[CComDynamicUnkArray::GetUnknown](#getunknown)|调用此方法以获取**IUnknown**给定 cookie 与相关联的指针。|  
|[CComDynamicUnkArray::Remove](#remove)|调用此方法来删除**IUnknown**从数组的指针。|  
  
## <a name="remarks"></a>备注  
 **CComDynamicUnkArray**保存动态分配的数组**IUnknown**指针，每个连接上的某个接口的点。 **CComDynamicUnkArray**可以使用以参数形式向[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类。  
  
 **CComDynamicUnkArray**方法[开始](#begin)和[结束](#end)可用于循环访问所有连接点 （例如，激发的事件时）。  
  
 请参阅[添加到对象的连接点](../../atl/adding-connection-points-to-an-object.md)点代理服务器的自动创建连接的详细信息。  
  
> [!NOTE]
> **请注意**类**CComDynamicUnkArray**由**添加类**向导创建一个具有连接点的控件时。 如果你想要手动指定连接点的数量，将更改从引用**CComDynamicUnkArray**到`CComUnkArray<` *n* `>`，其中*n*是所需的连接点的数目。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="add"></a>CComDynamicUnkArray::Add  
 调用此方法可添加**IUnknown**指向数组的指针。  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 **IUnknown**若要添加到数组的指针。  
  
### <a name="return-value"></a>返回值  
 返回新添加的指针与关联的 cookie。  
  
##  <a name="begin"></a>CComDynamicUnkArray::begin  
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
  
##  <a name="clear"></a>CComDynamicUnkArray::clear  
 清空该数组。  
  
```
void clear();
```  
  
##  <a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray  
 构造函数。  
  
```
CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>备注  
 将集合大小设置为零并初始化这些值与**NULL**。 析构函数释放该集合，如有必要。  
  
##  <a name="dtor"></a>CComDynamicUnkArray:: ~ CComDynamicUnkArray  
 析构函数。  
  
```
~CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>备注  
 释放由类构造函数分配的资源。  
  
##  <a name="end"></a>CComDynamicUnkArray::end  
 将指针返回到上一次之后一个**IUnknown**集合中的指针。  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>返回值  
 一个指向**IUnknown**接口指针。  
  
##  <a name="getat"></a>CComDynamicUnkArray::GetAt  
 检索位于指定索引处的元素。  
  
```
IUnknown* GetAt(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要检索的元素的索引。  
  
### <a name="return-value"></a>返回值  
 一个指向[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)接口。  
  
##  <a name="getcookie"></a>CComDynamicUnkArray::GetCookie  
 调用此方法以获取与关联的 cookie 给定**IUnknown**指针。  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>参数  
 `ppFind`  
 **IUnknown**关联的 cookie 为所需的指针。  
  
### <a name="return-value"></a>返回值  
 返回与关联的 cookie **IUnknown**指针或如果没有匹配的零**IUnknown**找到指针。  
  
### <a name="remarks"></a>备注  
 如果没有相同的多个实例**IUnknown**指针，此函数将返回第一个 cookie。  
  
##  <a name="getsize"></a>CComDynamicUnkArray::GetSize  
 返回一个数组的长度。  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>返回值  
 数组的长度。  
  
##  <a name="getunknown"></a>CComDynamicUnkArray::GetUnknown  
 调用此方法以获取**IUnknown**给定 cookie 与相关联的指针。  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>参数  
 `dwCookie`  
 为其 cookie 关联**IUnknown**指针是必需的。  
  
### <a name="return-value"></a>返回值  
 返回**IUnknown**指针，则为 NULL，如果不找到任何匹配的 cookie。  
  
##  <a name="remove"></a>CComDynamicUnkArray::Remove  
 调用此方法来删除**IUnknown**从数组的指针。  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>参数  
 `dwCookie`  
 Cookie 引用**IUnknown**指针，用以从数组中删除。  
  
### <a name="return-value"></a>返回值  
 如果该指针被删除; 将返回 TRUE否则为 FALSE。  
  
## <a name="see-also"></a>另请参阅  
 [CComUnkArray 类](../../atl/reference/ccomunkarray-class.md)   
 [类概述](../../atl/atl-class-overview.md)

