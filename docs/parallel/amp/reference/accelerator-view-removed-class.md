---
title: accelerator_view_removed 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0426dd44cfcb8f655f3981802dfe23adcd436a0d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688149"
---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed 类
基础 DirectX 调用因 Windows 超时检测和恢复机制而失败时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```  
class accelerator_view_removed : public runtime_exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
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
 **标头：** amprt.h  
  
 **命名空间：** 并发  

## <a name="ctor"></a> accelerator_view_removed 

初始化的新实例[accelerator_view_removed](accelerator-view-removed-class.md)类。  
  
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
  
## <a name="get_view_removed_reason_method"></a> get_view_removed_reason 

返回一个 HRESULT 错误代码，指示移除 `accelerator_view` 对象的原因。  
  
### <a name="syntax"></a>语法  
  
```  
HRESULT get_view_removed_reason() const throw();  
```  
  
 
## <a name="see-also"></a>请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
