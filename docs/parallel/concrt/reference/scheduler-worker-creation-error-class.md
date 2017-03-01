---
title: "scheduler_worker_creation_error 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::scheduler_worker_creation_error
dev_langs:
- C++
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
caps.latest.revision: 9
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
ms.openlocfilehash: c880ed65ef9e01c7eebdd2de45598a41763da57c
ms.lasthandoff: 02/24/2017

---
# <a name="schedulerworkercreationerror-class"></a>scheduler_worker_creation_error 类
此类描述因未能在并发运行时中创建辅助执行上下文而引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[scheduler_worker_creation_error 构造函数](#ctor)|已重载。 构造 `scheduler_worker_creation_error` 对象。|  
  
## <a name="remarks"></a>备注  
 该异常通常是在调用并发运行时内创建执行上下文的操作系统失败时引发。 执行上下文是在并发运行时中执行任务的线程。 通常通过调用 Win32 方法 `GetLastError` 返回的错误代码将转换为类型 `HRESULT` 的一个值，并且可以使用基类方法 `get_error_code` 检索。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)  
  
 `scheduler_worker_creation_error`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namectora-schedulerworkercreationerror"></a><a name="ctor"></a>scheduler_worker_creation_error 

 构造 `scheduler_worker_creation_error` 对象。  
  
```
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
 `_Hresult`  
 `HRESULT`导致异常的错误值。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

