---
title: "invalid_oversubscribe_operation 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::invalid_oversubscribe_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
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
ms.openlocfilehash: becb02cfd6a052a019ee73e182804c63a286403e
ms.lasthandoff: 02/24/2017

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
|[invalid_oversubscribe_operation 构造函数](#ctor)|已重载。 构造 `invalid_oversubscribe_operation` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `invalid_oversubscribe_operation`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namectora-invalidoversubscribeoperation"></a><a name="ctor"></a>invalid_oversubscribe_operation 

 构造 `invalid_oversubscribe_operation` 对象。  
  
```  
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

 
invalid_oversubscribe_operation() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

