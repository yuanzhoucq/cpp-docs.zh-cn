---
title: "context_self_unblock 类 | Microsoft Docs"
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
  - "concrt/concurrency::context_self_unblock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "context_self_unblock 类"
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# context_self_unblock 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

此类描述从同一上下文调用 `Context` 对象的 `Unblock` 方法时引发的异常。 这将指示给定上下文解除阻止自身的尝试。  
  
## <a name="syntax"></a>语法  
  
```  
class context_self_unblock : public std::exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[context_self_unblock:: context_self_unblock 构造函数](#context_self_unblock__context_self_unblock_constructor)|已重载。 构造 `context_self_unblock` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `context_self_unblock`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namecontextselfunblockcontextselfunblockconstructora-contextselfunblockcontextselfunblock-constructor"></a><a name="context_self_unblock__context_self_unblock_constructor"></a>  context_self_unblock:: context_self_unblock 构造函数  
 构造 `context_self_unblock` 对象。  
  
```  
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

 
context_self_unblock() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](../../../parallel/concrt/reference/concurrency-namespace.md)
