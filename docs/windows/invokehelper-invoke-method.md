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
ms.openlocfilehash: 7d1addd96456a33b30259182e4490df70335d0d3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408357"
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

*arg1*<br/>
参数 1。

*Arg2*<br/>
参数 2。

*arg3*<br/>
参数 3。

*了 arg4*<br/>
参数 4。

*arg5*<br/>
参数 5。

*了 arg6*<br/>
自变量 6。

*arg7*<br/>
参数 7。

*arg8*<br/>
参数 8。

*arg9*<br/>
参数 9。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为描述错误的 HRESULT。

## <a name="remarks"></a>备注

调用其签名包含指定的数量的参数的事件处理程序。

## <a name="requirements"></a>要求

**标头：** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[InvokeHelper 结构](../windows/invokehelper-structure.md)<br/>
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)