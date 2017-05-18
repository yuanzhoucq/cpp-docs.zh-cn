---
title: "CHandle 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
caps.latest.revision: 19
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: bbc0703ae5eaab01c0819be7e378509c7dc579ef
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="chandle-class"></a>CHandle 类
此类提供用于创建和使用句柄对象的方法。  
  
## <a name="syntax"></a>语法  
  
```
class CHandle
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CHandle::CHandle](#chandle)|构造函数。|  
|[CHandle:: ~ CHandle](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CHandle::Attach](#attach)|调用此方法可将附加`CHandle`对象传递给现有的句柄。|  
|[CHandle::Close](#close)|调用此方法来关闭`CHandle`对象。|  
|[CHandle::Detach](#detach)|调用此方法以分离的句柄从`CHandle`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CHandle::operator 句柄](#operator_handle)|返回存储句柄的值。|  
|[CHandle::operator =](#operator_eq)|赋值运算符。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CHandle::m_h](#m_h)|成员变量，用于存储句柄。|  
  
## <a name="remarks"></a>备注  
 一个`CHandle`需要一个句柄时，可以使用对象︰ 主要区别在于`CHandle`自动删除的对象。  
  
> [!NOTE]
>  某些 API 函数将使用空值为空或无效的句柄，而其他人使用 INVALID_HANDLE_VALUE。 `CHandle`仅使用 NULL 并将它们 INVALID_HANDLE_VALUE 视为实际句柄。 如果调用可返回 INVALID_HANDLE_VALUE 的 API，则应检查此值之前，先调用[CHandle::Attach](#attach)或将其传递给`CHandle`构造函数中，而是传递 NULL。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="attach"></a>CHandle::Attach  
 调用此方法可将附加`CHandle`对象传递给现有的句柄。  
  
```
void Attach(HANDLE h) throw();
```  
  
### <a name="parameters"></a>参数  
 `h`  
 `CHandle`将获得句柄所有权`h`。  
  
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
 现有的句柄或`CHandle`。  
  
### <a name="remarks"></a>备注  
 创建一个新`CHandle`对象时，可以选择使用现有句柄或`CHandle`对象。  
  
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
 关闭打开的对象句柄。 如果句柄为 NULL，这将是如果**关闭**并且尚未调用，ATLASSERT 将会引发在调试生成中。  
  
##  <a name="detach"></a>CHandle::Detach  
 调用此方法以分离的句柄从`CHandle`对象。  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回要分离的句柄。  
  
### <a name="remarks"></a>备注  
 释放该句柄的所有权。  
  
##  <a name="m_h"></a>CHandle::m_h  
 成员变量，用于存储句柄。  
  
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
 `CHandle`将获得句柄所有权`h`。  
  
### <a name="return-value"></a>返回值  
 返回对新的引用`CHandle`对象。  
  
### <a name="remarks"></a>备注  
 如果`CHandle`对象当前包含一个句柄，它将被关闭。 `CHandle`对象中传递将具有其句柄引用设置为 NULL。 这样可确保两个`CHandle`对象永远不会将包含相同的活动句柄。  
  
##  <a name="operator_handle"></a>CHandle::operator 句柄  
 返回存储句柄的值。  
  
```  
operator HANDLE() const throw();
```  
  
### <a name="remarks"></a>备注  
 返回的值存储在[CHandle::m_h](#m_h)。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

