---
title: unsupported_os 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- unsupported_os
- CONCRT/concurrency::unsupported_os
- CONCRT/concurrency::unsupported_os::unsupported_os
dev_langs:
- C++
helpviewer_keywords:
- unsupported_os class
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5298f7d8e6a998fb7841a6c3429a4240876c7cf1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016528"
---
# <a name="unsupportedos-class"></a>unsupported_os 类
此类描述使用不受支持的操作系统时引发的一种异常。  
  
## <a name="syntax"></a>语法  
  
```
class unsupported_os : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[unsupported_os](#ctor)|已重载。 构造 `unsupported_os` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `unsupported_os`  
  
## <a name="requirements"></a>要求  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a> unsupported_os 

 构造 `unsupported_os` 对象。  
  
```
explicit _CRTIMP unsupported_os(_In_z_ const char* _Message) throw();

unsupported_os() throw();
```  
  
### <a name="parameters"></a>参数  
*消息 （_m)*<br/>
错误的描述性消息。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
