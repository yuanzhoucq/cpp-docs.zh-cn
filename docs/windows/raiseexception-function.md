---
title: "RaiseException 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::RaiseException
dev_langs: C++
helpviewer_keywords: RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 380e3792c5b2b9504bec841965e70bd47ec619d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="raiseexception-function"></a>RaiseException 函数
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
inline void __declspec(noreturn)   RaiseException(  
      HRESULT hr,   
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);  
```  
  
#### <a name="parameters"></a>参数  
 `hr`  
 异常引发; 异常代码也就是说，操作失败的 HRESULT。  
  
 `dwExceptionFlags`  
 一个标志，指示 （标志值为零） 的持续性异常或 noncontinuable 异常 （标志值为非零）。 默认情况下，异常是不可继续。  
  
## <a name="remarks"></a>备注  
 引发调用的线程中出现异常。  
  
 有关详细信息，请参阅 Windows **RaiseException**函数。  
  
## <a name="requirements"></a>惠?  
 **标头：** internal.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)