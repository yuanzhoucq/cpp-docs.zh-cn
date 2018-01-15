---
title: "CAtlException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
dev_langs: C++
helpviewer_keywords: CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0af7fa5a0bc78043e0eac204255f30ab1b9672c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="catlexception-class"></a>CAtlException 类
此类定义 ATL 异常。  
  
## <a name="syntax"></a>语法  
  
```
class CAtlException
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlException::CAtlException](#catlexception)|构造函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlException::operator HRESULT](#operator_hresult)|强制转换为 HRESULT 值的当前对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlException::m_hr](#m_hr)|类型的变量 HRESULT 由对象和创建用于存储的错误条件。|  
  
## <a name="remarks"></a>备注  
 A`CAtlException`对象表示与 ATL 操作相关的异常条件。 `CAtlException`类包括存储原因异常和转换运算符，您可以将异常，就像它是一个 HRESULT，该值指示的状态代码的公共数据成员。  
  
 一般情况下，将调用`AtlThrow`而不是创建`CAtlException`直接对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlexcept.h  
  
##  <a name="catlexception"></a>CAtlException::CAtlException  
 构造函数。  
  
```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```  
  
### <a name="parameters"></a>参数  
 `hr`  
 `HRESULT`错误代码。  
  
##  <a name="operator_hresult"></a>CAtlException::operator HRESULT 
 强制转换为 HRESULT 值的当前对象。  
  
```  
operator HRESULT() const throw ();
```  
  
##  <a name="m_hr"></a>CAtlException::m_hr  
 `HRESULT`数据成员。  
  
```
HRESULT m_hr;
```  
  
### <a name="remarks"></a>备注  
 数据成员的存储的错误条件。 HRESULT 值由构造函数中，设置[CAtlException::CAtlException](#catlexception)。  
  
## <a name="see-also"></a>请参阅  
 [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)   
 [类概述](../../atl/atl-class-overview.md)
