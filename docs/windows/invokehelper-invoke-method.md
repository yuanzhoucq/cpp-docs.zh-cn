---
title: 'Invokehelper:: Invoke 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
dev_langs:
- C++
helpviewer_keywords:
- Invoke method
ms.assetid: 98618815-c30e-4699-b3dd-203c91b1bf3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 56f7f77284d855a2d9a737c8694efdd357d0a6fb
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011495"
---
# <a name="invokehelperinvoke-method"></a>InvokeHelper::Invoke 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
STDMETHOD(  
   Invoke  
)();  
STDMETHOD(  
   Invoke  
)(typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
```  
  
### <a name="parameters"></a>参数  
 *arg1*  
 参数 1。  
  
 *Arg2*  
 参数 2。  
  
 *arg3*  
 参数 3。  
  
 *了 arg4*  
 参数 4。  
  
 *arg5*  
 参数 5。  
  
 *了 arg6*  
 自变量 6。  
  
 *arg7*  
 参数 7。  
  
 *arg8*  
 参数 8。  
  
 *arg9*  
 参数 9。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为描述错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 调用其签名包含指定的数量的参数的事件处理程序。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [InvokeHelper 结构](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)