---
title: operation_timed_out 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- operation_timed_out
- CONCRT/concurrency::operation_timed_out
- CONCRT/concurrency::operation_timed_out::operation_timed_out
dev_langs:
- C++
helpviewer_keywords:
- operation_timed_out class
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af30dd9d7ff6ac64d6c0659520a6e7a15f2d0d93
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116630"
---
# <a name="operationtimedout-class"></a>operation_timed_out 类
此类描述操作超时时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class operation_timed_out : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[operation_timed_out](#ctor)|已重载。 构造 `operation_timed_out` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `operation_timed_out`  
  
## <a name="requirements"></a>要求  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a> operation_timed_out 

 构造 `operation_timed_out` 对象。  
  
```
explicit _CRTIMP operation_timed_out(_In_z_ const char* _Message) throw();

operation_timed_out() throw();
```  
  
### <a name="parameters"></a>参数  
*消息 （_m)*<br/>
错误的描述性消息。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
