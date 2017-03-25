---
title: "nested_scheduler_missing_detach 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
dev_langs:
- C++
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
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
ms.openlocfilehash: 7ab8dc3761c6f11529b70ec4d71bbaebdfea0493
ms.lasthandoff: 03/17/2017

---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach 类
此类描述并发运行时检测到你没有在通过 `Scheduler` 对象的 `Attach` 方法附加到第二个计划程序的上下文中调用 `CurrentScheduler::Detach` 方法时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class nested_scheduler_missing_detach : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[nested_scheduler_missing_detach](#ctor)|已重载。 构造 `nested_scheduler_missing_detach` 对象。|  
  
## <a name="remarks"></a>备注  
 仅当在另一个计划程序中嵌套计划程序，方法为在已由另一计划程序拥有或连接至另一计划程序的上下文中调用 `Attach` 对象的 `Scheduler` 方法时，才会引发该异常。 并发运行时引发此异常时它可以检测方案，以帮助找到问题所在。 不是每个实例忘记调用`CurrentScheduler::Detach`方法肯定会引发此异常。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a>nested_scheduler_missing_detach 

 构造 `nested_scheduler_missing_detach` 对象。  
  
```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [Scheduler 类](scheduler-class.md)

