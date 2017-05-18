---
title: "bad_target 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
dev_langs:
- C++
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 145aa17b4589fb572f3b6594360ec69db5e15287
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

---
# <a name="badtarget-class"></a>bad_target 类
此类描述消息块被给予指向目标的指针，但该目标对于正在执行的操作无效时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class bad_target : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[bad_target](#ctor)|已重载。 构造 `bad_target` 对象。|  
  
## <a name="remarks"></a>备注  
 由于尝试使用一条消息而保留为不同目标或释放它所持有的保留的目标的原因通常引发此异常。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `bad_target`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a>bad_target 

 构造 `bad_target` 对象。  
  
```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)




