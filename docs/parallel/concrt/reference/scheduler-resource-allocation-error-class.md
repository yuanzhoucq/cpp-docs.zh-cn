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
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 84f32bb6192057c9d5872147cc8ef0bd2c13b349
ms.lasthandoff: 03/17/2017

---
# <a name="schedulerresourceallocationerror-class"></a>scheduler_resource_allocation_error 类
此类描述因未能在并发运行时中获取关键资源而引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class scheduler_resource_allocation_error : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[scheduler_resource_allocation_error](#ctor)|已重载。 构造 `scheduler_resource_allocation_error` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[get_error_code](#get_error_code)|返回导致异常的错误代码。|  
  
## <a name="remarks"></a>备注  
 对从并发运行时中的操作系统调用失败时，通常将引发此异常。 通常从调用 Win32 方法 `GetLastError` 返回的错误代码将转换为类型 `HRESULT` 的值，并且可以使用 `get_error_code` 方法检索。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `scheduler_resource_allocation_error`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="get_error_code"></a>get_error_code 

 返回导致异常的错误代码。  
  
```
HRESULT get_error_code() const throw();
```  
  
### <a name="return-value"></a>返回值  
 `HRESULT`导致异常的错误值。  
  
##  <a name="ctor"></a>scheduler_resource_allocation_error 

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
 [并发命名空间](concurrency-namespace.md)

