---
title: "scheduler_resource_allocation_error 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::scheduler_resource_allocation_error
dev_langs:
- C++
helpviewer_keywords:
- scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 52233a99e1d1a715fc7d52599ffeff18a3c2c34b
ms.lasthandoff: 02/24/2017

---
# <a name="schedulerresourceallocationerror-class"></a>scheduler_resource_allocation_error 类
此类描述因未能在并发运行时中获取关键资源而引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class scheduler_resource_allocation_error : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[scheduler_resource_allocation_error 构造函数](#ctor)|已重载。 构造 `scheduler_resource_allocation_error` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[get_error_code 方法](#get_error_code)|返回导致异常的错误代码。|  
  
## <a name="remarks"></a>备注  
 对从并发运行时中的操作系统调用失败时，通常将引发此异常。 通常从调用 Win32 方法 `GetLastError` 返回的错误代码将转换为类型 `HRESULT` 的值，并且可以使用 `get_error_code` 方法检索。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `scheduler_resource_allocation_error`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namegeterrorcodea-geterrorcode"></a><a name="get_error_code"></a>get_error_code 

 返回导致异常的错误代码。  
  
```
HRESULT get_error_code() const throw();
```  
  
### <a name="return-value"></a>返回值  
 `HRESULT`导致异常的错误值。  
  
##  <a name="a-namectora-schedulerresourceallocationerror"></a><a name="ctor"></a>scheduler_resource_allocation_error 

 构造 `scheduler_resource_allocation_error` 对象。  
  
```
scheduler_resource_allocation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_resource_allocation_error(
    HRESULT _Hresult) throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
 `_Hresult`  
 `HRESULT`导致异常的错误值。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

