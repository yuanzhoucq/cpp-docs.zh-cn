---
title: "CAtlException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
dev_langs:
- C++
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 471ba42f25a4e237db03f2516288a7b33a0efd63
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="catlexception-class"></a>CAtlException 类
此类定义 ATL 异常。  
  
## <a name="syntax"></a>语法  
  
```
class CAtlException
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
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
  
## <a name="requirements"></a>要求  
 **标头︰** atlexcept.h  
  
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
  
## <a name="see-also"></a>另请参阅  
 [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)   
 [类概述](../../atl/atl-class-overview.md)

