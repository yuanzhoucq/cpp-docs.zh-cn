---
title: "invalid_operation 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::invalid_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
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
ms.openlocfilehash: 0484e149409b2515f60b2e9aa34a85d5381e05a5
ms.lasthandoff: 02/24/2017

---
# <a name="invalidoperation-class"></a>invalid_operation 类
此类描述执行无效操作时引发的异常，由并发运行时引发的其他异常类型不会对此异常进行更为准确的描述。  
  
## <a name="syntax"></a>语法  
  
```
class invalid_operation : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[invalid_operation 构造函数](#ctor)|已重载。 构造 `invalid_operation` 对象。|  
  
## <a name="remarks"></a>备注  
 引发此异常的各种方法通常会记录它们将引发此异常的环境。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `invalid_operation`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namectora-invalidoperation"></a><a name="ctor"></a>invalid_operation 

 构造 `invalid_operation` 对象。  
  
```
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

