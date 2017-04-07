---
title: "uninitialized_object 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
dev_langs:
- C++
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
caps.latest.revision: 10
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
ms.openlocfilehash: 1ff7840ec3ff4ab00b7e13d647c329a892dade42
ms.lasthandoff: 02/24/2017

---
# <a name="uninitializedobject-class"></a>uninitialized_object 类
使用未初始化的对象时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```  
class uninitialized_object : public runtime_exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[uninitialized_object 构造函数](#ctor)|初始化 `uninitialized_object` 类的新实例。|  

  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
 `uninitialized_object`  
  
## <a name="requirements"></a>要求  
 **标头︰** amprt.h  
  
 **命名空间：** 并发  
## <a name="uninitialized_object__ctor"></a>unsupported_feature 

构造 unsupported_feature 异常的新实例。  
  
### <a name="syntax"></a>语法  
  
```  
explicit unsupported_feature(  
    const char * _Message ) throw();  
  
unsupported_feature() throw();  
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误说明。  
  
### <a name="return-value"></a>返回值  
 `unsupported_feature` 对象。 

## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)

