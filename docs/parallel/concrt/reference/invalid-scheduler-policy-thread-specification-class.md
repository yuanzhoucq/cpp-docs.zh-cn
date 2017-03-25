---
title: "invalid_scheduler_policy_thread_specification 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
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
ms.openlocfilehash: d9b49f65d8b862a7b85cdf3e09137f326fa8a1fa
ms.lasthandoff: 03/17/2017

---
# <a name="invalidschedulerpolicythreadspecification-class"></a>invalid_scheduler_policy_thread_specification 类
此类描述尝试设置 `SchedulerPolicy` 对象的并发限制，以便 `MinConcurrency` 键的值小于 `MaxConcurrency` 键的值时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class invalid_scheduler_policy_thread_specification : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[invalid_scheduler_policy_thread_specification](无效的计划程序的策略的值-class.md #ctor|已重载。 构造 `invalid_scheduler_policy_value` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `invalid_scheduler_policy_thread_specification`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
##  <a name="ctor"></a>invalid_scheduler_policy_thread_specification 

 构造 `invalid_scheduler_policy_value` 对象。  
  
```
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  

## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [SchedulerPolicy 类](schedulerpolicy-class.md)

