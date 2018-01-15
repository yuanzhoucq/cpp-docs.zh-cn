---
title: "missing_wait 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
dev_langs: C++
helpviewer_keywords: missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 952a2b88ebb91449341085a923e06d389aa10fe4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
 缺少异常流，你将负责调用`wait`或`run_and_wait`方法`task_group`或`structured_task_group`之前允许销毁该对象的对象。 则运行时会引发此异常你忘记调用用于指示`wait`或`run_and_wait`方法。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `missing_wait`  
  
## <a name="requirements"></a>惠?  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a>missing_wait 

 构造 `missing_wait` 对象。  
  
```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [task_group 类](task-group-class.md)   
 [等待](task-group-class.md)   
 [run_and_wait](task-group-class.md)   
 [structured_task_group 类](structured-task-group-class.md)
