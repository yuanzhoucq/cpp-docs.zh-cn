---
title: "invalid_compute_domain 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
dev_langs: C++
helpviewer_keywords: invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a6b41017563a7bd3c6e5ebfd3fc3752ea1e97c3a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="invalidcomputedomain-class"></a>invalid_compute_domain 类
当运行时无法通过使用在指定的计算域启动内核时引发的异常[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)调用站点。  

  
## <a name="syntax"></a>语法  
  
```  
class invalid_compute_domain : public runtime_exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[invalid_compute_domain 构造函数](#ctor)|初始化 `invalid_compute_domain` 类的新实例。|  

  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
 `invalid_compute_domain`  
  
## <a name="requirements"></a>要求  
 **标头：** amprt.h  
  
 **命名空间：** 并发  

## <a name="ctor"></a>invalid_compute_domain 

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
 实例`invalid_compute_domain`类  
    
## <a name="see-also"></a>另请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
