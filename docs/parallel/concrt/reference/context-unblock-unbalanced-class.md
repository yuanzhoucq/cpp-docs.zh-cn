---
title: "context_unblock_unbalanced 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
dev_langs: C++
helpviewer_keywords: context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44130ba1991a9e14340e44427e0bb80c5bac0a47
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="contextunblockunbalanced-class"></a>context_unblock_unbalanced 类
此类描述对 `Context` 对象的 `Block` 和 `Unblock` 方法的调用未恰当配对时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```  
class context_unblock_unbalanced : public std::exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[context_unblock_unbalanced](#ctor)|已重载。 构造 `context_unblock_unbalanced` 对象。|  
  
## <a name="remarks"></a>备注  
 调用`Block`和`Unblock`方法`Context`对象必须始终正确配对。 并发运行时允许按任意顺序发生操作。 例如，调用 `Block` 后可以调用 `Unblock`，反之亦然。 如果，例如，两次调用将引发此异常`Unblock`方法所做在行中，`Context`未被阻止的对象。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `context_unblock_unbalanced`  
  
## <a name="requirements"></a>惠?  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a>context_unblock_unbalanced 

 构造 `context_unblock_unbalanced` 对象。  
  
```  
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

 
context_unblock_unbalanced() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
