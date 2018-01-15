---
title: "CHandle 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
dev_langs: C++
helpviewer_keywords: CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cd58ba8ce15bb26b4e5b768baedbf8ddfe829f2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="chandle-class"></a>CHandle 类
此类提供用于创建和使用句柄对象的方法。  
  
## <a name="syntax"></a>语法  
  
```
class CHandle
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CHandle::CHandle](#chandle)|构造函数。|  
|[CHandle:: ~ CHandle](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CHandle::Attach](#attach)|调用此方法以将附加`CHandle`现有句柄到对象。|  
|[CHandle::Close](#close)|调用此方法来关闭`CHandle`对象。|  
|[CHandle::Detach](#detach)|调用此方法以分离从的句柄`CHandle`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CHandle::operator 句柄](#operator_handle)|返回存储的句柄的值。|  
|[CHandle::operator =](#operator_eq)|赋值运算符。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CHandle::m_h](#m_h)|存储句柄的成员变量。|  
  
## <a name="remarks"></a>备注  
 A`CHandle`需要句柄时，可以使用对象： 主要区别是，`CHandle`对象时将自动删除。  
  
> [!NOTE]
>  某些 API 函数将使用作为空或无效的句柄，NULL，而其他人使用 INVALID_HANDLE_VALUE。 `CHandle`仅使用 NULL，将为 INVALID_HANDLE_VALUE 视为实际句柄。 如果调用可返回 INVALID_HANDLE_VALUE API，则应检查该值之前调用[CHandle::Attach](#attach)或将其传递给`CHandle`构造函数，并改为将传递 NULL。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
##  <a name="attach"></a>CHandle::Attach  
 调用此方法以将附加`CHandle`现有句柄到对象。  
  
```
void Attach(HANDLE h) throw();
```  
  
### <a name="parameters"></a>参数  
 `h`  
 `CHandle`将句柄拥有`h`。  
  
### <a name="remarks"></a>备注  
 将分配`CHandle`对象传递给`h`处理。 在调试生成中 ATLASSERT 如果将会引发`h`为 NULL。 不其他句柄的有效性进行检查。  
  
##  <a name="chandle"></a>CHandle::CHandle  
 构造函数。  
  
```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```  
  
### <a name="parameters"></a>参数  
 `h`  
 现有句柄或`CHandle`。  
  
### <a name="remarks"></a>备注  
 创建一个新`CHandle`对象，可以选择使用现有句柄或`CHandle`对象。  
  
##  <a name="dtor"></a>CHandle:: ~ CHandle  
 析构函数。  
  
```
~CHandle() throw();
```  
  
### <a name="remarks"></a>备注  
 释放`CHandle`对象通过调用[CHandle::Close](#close)。  
  
##  <a name="close"></a>CHandle::Close  
 调用此方法来关闭`CHandle`对象。  
  
```
void Close() throw();
```  
  
### <a name="remarks"></a>备注  
 关闭打开的对象句柄。 如果句柄为 NULL，则为情况**关闭**已被调用，ATLASSERT 将会引发在调试生成中。  
  
##  <a name="detach"></a>CHandle::Detach  
 调用此方法以分离从的句柄`CHandle`对象。  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回要分离的句柄。  
  
### <a name="remarks"></a>备注  
 释放句柄的所有权。  
  
##  <a name="m_h"></a>CHandle::m_h  
 存储句柄的成员变量。  
  
```
HANDLE m_h;
```  
  
##  <a name="operator_eq"></a>CHandle::operator =  
 赋值运算符中。  
  
```
CHandle& operator=(CHandle& h) throw();
```  
  
### <a name="parameters"></a>参数  
 `h`  
 `CHandle`将句柄拥有`h`。  
  
### <a name="return-value"></a>返回值  
 返回对新的引用`CHandle`对象。  
  
### <a name="remarks"></a>备注  
 如果`CHandle`对象当前包含句柄，它将被关闭。 `CHandle`对象正在传递将具有其句柄引用设置为 NULL。 这样可确保两个`CHandle`对象永远不会将包含相同的 active 句柄。  
  
##  <a name="operator_handle"></a>CHandle::operator 句柄  
 返回存储的句柄的值。  
  
```  
operator HANDLE() const throw();
```  
  
### <a name="remarks"></a>备注  
 返回中存储的值[CHandle::m_h](#m_h)。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
