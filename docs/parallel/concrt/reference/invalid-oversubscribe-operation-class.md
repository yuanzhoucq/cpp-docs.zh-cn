---
title: invalid_oversubscribe_operation 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 612a5658e0ef678253ec493f23b71cc564288904
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689511"
---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation 类
此类描述在先前没有对 `Context::Oversubscribe` 方法进行调用（`_BeginOversubscription` 参数设置为 `true`）的情况下，调用 `Context::Oversubscribe` 方法（`_BeginOversubscription` 参数设置为 `false`）时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```  
class invalid_oversubscribe_operation : public std::exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[invalid_oversubscribe_operation](#ctor)|已重载。 构造 `invalid_oversubscribe_operation` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `invalid_oversubscribe_operation`  
  
## <a name="requirements"></a>要求  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a> invalid_oversubscribe_operation 

 构造 `invalid_oversubscribe_operation` 对象。  
  
```  
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

 
invalid_oversubscribe_operation() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
