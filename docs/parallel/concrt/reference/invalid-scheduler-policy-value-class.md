---
title: "invalid_scheduler_policy_value 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: concrt/concurrency::invalid_scheduler_policy_value
dev_langs: C++
helpviewer_keywords: invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dc8d6a06d578169cb60bc757c1719b7028e12b06
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
 **标头：** concrt.h  
  
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
