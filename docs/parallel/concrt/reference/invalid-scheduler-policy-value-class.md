---
title: "invalid_scheduler_policy_value 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
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
ms.openlocfilehash: 85396192c7384cbe7379b675f4a38e5deb322235
ms.lasthandoff: 03/17/2017

---
# <a name="invalidschedulerpolicyvalue-class"></a>invalid_scheduler_policy_value 类
此类描述 `SchedulerPolicy` 对象的策略键设置为对于该键无效的值时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class invalid_scheduler_policy_value : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[invalid_scheduler_policy_value](invalid-scheduler-policy-thread-specification-class.md#ctor|已重载。 构造 `invalid_scheduler_policy_value` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
    
##  <a name="ctor"></a>invalid_scheduler_policy_value 

 构造 `invalid_scheduler_policy_value` 对象。  
  
```
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  

## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [SchedulerPolicy 类](schedulerpolicy-class.md)

