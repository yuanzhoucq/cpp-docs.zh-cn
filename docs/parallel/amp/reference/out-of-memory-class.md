---
title: "out_of_memory 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
dev_langs:
- C++
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
caps.latest.revision: 11
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
ms.openlocfilehash: b593f8f85d4e36496f2ec2fc7bbadf8f2bfd742e
ms.lasthandoff: 02/24/2017

---
# <a name="outofmemory-class"></a>out_of_memory 类
一种方法将因系统或设备的内存不足而失败时，将引发异常。  
  
## <a name="syntax"></a>语法  
  
```  
class out_of_memory : public runtime_exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[out_of_memory 构造函数](#ctor)|初始化 `out_of_memory` 类的新实例。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>要求  
 **标头︰** amprt.h  
  
 **命名空间：** 并发  
## <a name="ctor"></a>out_of_memory 

 初始化类的新实例。  
  
### <a name="syntax"></a>语法  
  
```  
explicit out_of_memory(  
    const char * _Message ) throw();  
  
out_of_memory () throw();  
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误说明。  
  
### <a name="return-value"></a>返回值  
 `out_of_memory` 类的新实例。  
  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)

