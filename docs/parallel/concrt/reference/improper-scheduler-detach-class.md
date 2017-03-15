---
title: "improper_scheduler_detach 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::improper_scheduler_detach
dev_langs:
- C++
helpviewer_keywords:
- improper_scheduler_detach class
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
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
ms.openlocfilehash: 6a4bb4be90966f3abed8792bfbef086e7b399922
ms.lasthandoff: 02/24/2017

---
# <a name="improperschedulerdetach-class"></a>improper_scheduler_detach 类
此类描述在尚未附加到任何使用 `Scheduler` 对象的 `Attach` 方法的计划程序的上下文中调用 `CurrentScheduler::Detach` 方法时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class improper_scheduler_detach : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[improper_scheduler_detach 构造函数](#ctor)|已重载。 构造 `improper_scheduler_detach` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `improper_scheduler_detach`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namectora-improperschedulerdetach"></a><a name="ctor"></a>improper_scheduler_detach 

 构造 `improper_scheduler_detach` 对象。  
  
```
explicit _CRTIMP improper_scheduler_detach(_In_z_ const char* _Message) throw();

improper_scheduler_detach() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [Scheduler 类](scheduler-class.md)

