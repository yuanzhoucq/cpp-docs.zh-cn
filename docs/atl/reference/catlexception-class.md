---
title: "CAtlException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlException
- ATL::CAtlException
- ATL.CAtlException
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 30c9235f16581c86ab5612522909dc366b1ce17e
ms.lasthandoff: 02/24/2017

---
# <a name="catlexception-class"></a>CAtlException 类
此类定义了一个 ATL 异常。  
  
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
|[CAtlException::operator HRESULT](#operator_hresult)|将强制转换为 HRESULT 值的当前对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlException::m_hr](#m_hr)|类型的变量 HRESULT 由对象和创建用于存储错误条件。|  
  
## <a name="remarks"></a>备注  
 一个`CAtlException`对象都表示对 ATL 操作相关的异常条件。 `CAtlException`类包括一个将存储，该值指示该异常和转换运算符，您可以像它是一个 HRESULT，它将处理该异常的原因的状态代码的公共数据成员。  
  
 一般情况下，将调用`AtlThrow`而不是创建`CAtlException`直接对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlexcept.h  
  
##  <a name="a-namecatlexceptiona--catlexceptioncatlexception"></a><a name="catlexception"></a>CAtlException::CAtlException  
 构造函数。  
  
```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```  
  
### <a name="parameters"></a>参数  
 `hr`  
 `HRESULT`错误代码。  
  
##  <a name="a-nameoperatorhresulta--catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException::operator HRESULT 
 将强制转换为 HRESULT 值的当前对象。  
  
```  
operator HRESULT() const throw ();
```  
  
##  <a name="a-namemhra--catlexceptionmhr"></a><a name="m_hr"></a>CAtlException::m_hr  
 `HRESULT`数据成员。  
  
```
HRESULT m_hr;
```  
  
### <a name="remarks"></a>备注  
 数据成员的存储错误条件。 HRESULT 值由构造函数中，设置[CAtlException::CAtlException](#catlexception)。  
  
## <a name="see-also"></a>另请参阅  
 [AtlThrow](http://msdn.microsoft.com/library/2bd111da-8170-488d-914a-c9bf6b6765f7)   
 [类概述](../../atl/atl-class-overview.md)

