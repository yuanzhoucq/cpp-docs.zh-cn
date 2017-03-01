---
title: "improper_scheduler_attach 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::improper_scheduler_attach
dev_langs:
- C++
helpviewer_keywords:
- improper_scheduler_attach class
ms.assetid: 5a76da0a-091b-4748-8f62-b3a28f674f9e
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
ms.openlocfilehash: 57649ddf3662a4610561ec0e109e795985450b9d
ms.lasthandoff: 02/24/2017

---
# <a name="improperschedulerattach-class"></a>improper_scheduler_attach 类
此类描述在已附加到当前上下文的 `Scheduler` 对象上调用 `Attach` 方法时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class improper_scheduler_attach : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[improper_scheduler_attach 构造函数](#ctor)|已重载。 构造 `improper_scheduler_attach` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `improper_scheduler_attach`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namectora-improperschedulerattach"></a><a name="ctor"></a>improper_scheduler_attach 

 构造 `improper_scheduler_attach` 对象。  
  
```
explicit _CRTIMP improper_scheduler_attach(_In_z_ const char* _Message) throw();

improper_scheduler_attach() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [Scheduler 类](scheduler-class.md)

