---
title: unsupported_feature 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
dev_langs:
- C++
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7472e8fa8932983569ad9e2a9c1fe6cdfc9318b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059675"
---
# <a name="unsupportedfeature-class"></a>unsupported_feature 类
使用不支持的功能时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```  
class unsupported_feature : public runtime_exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[unsupported_feature 构造函数](#ctor)|构造的新实例`unsupported_feature`异常。|  

  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
 `unsupported_feature`  
  
## <a name="unsupported_feature__ctor"></a> unsupported_feature 

  构造的功能异常的新实例。  
  
### <a name="syntax"></a>语法  
  
```  
explicit unsupported_feature(  
    const char * _Message ) throw();  
  
unsupported_feature() throw();  
```  
  
### <a name="parameters"></a>参数  
*消息 （_m)*<br/>
错误说明。  
  
### <a name="return-value"></a>返回值  
 `unsupported_feature` 对象。  
  
## <a name="requirements"></a>要求  
 **标头：** amprt.h  
  
 **命名空间：** 并发  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
