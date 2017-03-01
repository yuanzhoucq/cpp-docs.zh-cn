---
title: "invalid_compute_domain 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amprt/Concurrency::invalid_compute_domain
dev_langs:
- C++
helpviewer_keywords:
- invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: e37012f62a40649876d043c3a0e89a1655c40455
ms.lasthandoff: 02/24/2017

---
# <a name="invalidcomputedomain-class"></a>invalid_compute_domain 类
在运行时无法通过使用在指定的计算域启动内核时引发的异常[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)调用站点。  

  
## <a name="syntax"></a>语法  
  
```  
class invalid_compute_domain : public runtime_exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[invalid_compute_domain 构造函数](#ctor)|初始化 `invalid_compute_domain` 类的新实例。|  

  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
 `invalid_compute_domain`  
  
## <a name="requirements"></a>要求  
 **标头︰** amprt.h  
  
 **命名空间：** 并发  

## <a name="a-namectora-invalidcomputedomain"></a><a name="ctor"></a>invalid_compute_domain 

初始化类的新实例。  
  
## <a name="syntax"></a>语法  
  
```  
explicit invalid_compute_domain(  
    const char * _Message ) throw();  
  
invalid_compute_domain() throw();  
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误说明。  
  
### <a name="return-value"></a>返回值  
 一个实例`invalid_compute_domain`类  
    
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)

