---
title: "message_not_found 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- message_not_found
- CONCRT/concurrency::message_not_found
- CONCRT/concurrency::message_not_found::message_not_found
dev_langs:
- C++
helpviewer_keywords:
- message_not_found class
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
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
ms.openlocfilehash: 4dc29ff5a9836aa784efa15313efbf60569142d4
ms.lasthandoff: 03/17/2017

---
# <a name="messagenotfound-class"></a>message_not_found 类
此类描述消息块找不到请求的消息时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class message_not_found : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[message_not_found](#ctor)|已重载。 构造 `message_not_found` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `message_not_found`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a>message_not_found 

 构造 `message_not_found` 对象。  
  
```
explicit _CRTIMP message_not_found(_In_z_ const char* _Message) throw();

message_not_found() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)




