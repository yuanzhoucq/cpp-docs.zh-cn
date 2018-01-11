---
title: "operation_timed_out 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- operation_timed_out
- CONCRT/concurrency::operation_timed_out
- CONCRT/concurrency::operation_timed_out::operation_timed_out
dev_langs: C++
helpviewer_keywords: operation_timed_out class
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3c4f211248fd46abb5276f4108268f1dc5a56acd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="requirements"></a>惠?  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a>operation_timed_out 

 构造 `operation_timed_out` 对象。  
  
```
explicit _CRTIMP operation_timed_out(_In_z_ const char* _Message) throw();

operation_timed_out() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
