---
title: missing_wait 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
dev_langs:
- C++
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2a44cbdb5abeed7d5dbd7be7dfaba37ba1d0145
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024934"
---
# <a name="missingwait-class"></a>missing_wait 类
此类描述执行对象的析构函数时仍有计划到 `task_group` 或 `structured_task_group` 对象的任务时引发的异常。 如果因为堆栈展开为异常的结果而到达析构函数的调用条件，则永远不会引发此异常。  
  
## <a name="syntax"></a>语法  
  
```
class missing_wait : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[missing_wait](#ctor)|已重载。 构造 `missing_wait` 对象。|  
  
## <a name="remarks"></a>备注  
 不存在异常流，您应负责调用`wait`或`run_and_wait`方法`task_group`或`structured_task_group`之前允许来析构该对象的对象。 在运行时引发此异常，忘记调用指示`wait`或`run_and_wait`方法。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `missing_wait`  
  
## <a name="requirements"></a>要求  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a> missing_wait 

 构造 `missing_wait` 对象。  
  
```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```  
  
### <a name="parameters"></a>参数  
*消息 （_m)*<br/>
错误的描述性消息。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [task_group 类](task-group-class.md)   
 [等待](task-group-class.md)   
 [run_and_wait](task-group-class.md)   
 [structured_task_group 类](structured-task-group-class.md)
