---
title: "context_unblock_unbalanced 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::context_unblock_unbalanced"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "context_unblock_unbalanced 类"
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# context_unblock_unbalanced 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

此类描述对 `Context` 对象的 `Block` 和 `Unblock` 方法的调用未恰当配对时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```  
class context_unblock_unbalanced : public std::exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[context_unblock_unbalanced:: context_unblock_unbalanced 构造函数](#context_unblock_unbalanced__context_unblock_unbalanced_constructor)|已重载。 构造 `context_unblock_unbalanced` 对象。|  
  
## <a name="remarks"></a>备注  
 调用 `Block` 和 `Unblock` 方法 `Context` 对象必须始终正确配对。 并发运行时允许执行操作以按任意顺序发生。 例如，调用 `Block` 后可以调用 `Unblock`，反之亦然。 如果，例如，两次调用将引发此异常 `Unblock` 方法上所做某行中， `Context` 不阻止的对象。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `context_unblock_unbalanced`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namecontextunblockunbalancedcontextunblockunbalancedconstructora-contextunblockunbalancedcontextunblockunbalanced-constructor"></a><a name="context_unblock_unbalanced__context_unblock_unbalanced_constructor"></a>  context_unblock_unbalanced:: context_unblock_unbalanced 构造函数  
 构造 `context_unblock_unbalanced` 对象。  
  
```  
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

 
context_unblock_unbalanced() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](../../../parallel/concrt/reference/concurrency-namespace.md)
