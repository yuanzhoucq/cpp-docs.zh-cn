---
title: "accelerator_view_removed 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:get_view_removed_reason
dev_langs:
- C++
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
caps.latest.revision: 6
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: c45eb8192266999c8771f6788de16859fe7a12c8
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed 类
基础 DirectX 调用因 Windows 超时检测和恢复机制而失败时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```  
class accelerator_view_removed : public runtime_exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[accelerator_view_removed 构造函数](#ctor)|初始化 `accelerator_view_removed` 类的新实例。|  

### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[get_view_removed_reason](#get_view_removed_reason)|返回一个 HRESULT 错误代码，指示移除 `accelerator_view` 对象的原因。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>要求  
 **标头︰** amprt.h  
  
 **命名空间：** 并发  

## <a name="ctor"></a>accelerator_view_removed 

新实例初始化[accelerator_view_removed](accelerator-view-removed-class.md)类。  
  
### <a name="syntax"></a>语法  
  
```  
explicit accelerator_view_removed(  
    const char * _Message,  
    HRESULT _View_removed_reason ) throw();  
  
explicit accelerator_view_removed(  
    HRESULT _View_removed_reason ) throw();  
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误说明。  
  
 `_View_removed_reason`  
 指示 `accelerator_view` 对象移除原因的 HRESULT 错误代码。  
  
### <a name="return-value"></a>返回值  
 Accelerator_view_removed 类的新实例。  
  
## <a name="get_view_removed_reason_method"></a>get_view_removed_reason 

返回一个 HRESULT 错误代码，指示移除 `accelerator_view` 对象的原因。  
  
### <a name="syntax"></a>语法  
  
```  
HRESULT get_view_removed_reason() const throw();  
```  
  
 
## <a name="see-also"></a>另请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

