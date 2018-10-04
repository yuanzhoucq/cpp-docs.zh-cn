---
title: InvokeHelper 结构 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 46cd067e41fcc9ac0d8d3dd9fe50c9edd23532c3
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789106"
---
# <a name="invokehelper-structure"></a>InvokeHelper 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<typename TDelegateInterface, typename TCallback, unsigned int argCount>
struct InvokeHelper;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 0> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 1> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 2> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 3> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 4> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 5> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 6> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 7> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 8> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 9> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;
```

### <a name="parameters"></a>参数

*TDelegateInterface*<br/>
*TCallback*  
事件处理程序函数的类型。

*argCount*<br/>
中的参数数目`InvokeHelper`专用化。

## <a name="remarks"></a>备注

提供的实现`Invoke()`方法基于指定的数目和参数的类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称     | 描述
-------- | -----------------------------------------------------------------------------
`Traits` | 类定义的每个事件处理程序自变量的类型的同义词。

### <a name="public-constructors"></a>公共构造函数

名称                                        | 描述
------------------------------------------- | -------------------------------------------------------
[Invokehelper:: Invokehelper](#invokehelper) | 初始化 `InvokeHelper` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                            | 描述
------------------------------- | -----------------------------------------------------------------------------------
[Invokehelper:: Invoke](#invoke) | 调用其签名包含指定的数量的参数的事件处理程序。

### <a name="public-data-members"></a>公共数据成员

名称                                 | 描述
------------------------------------ | ----------------------------------------------------------
[Invokehelper:: Callback_](#callback) | 表示事件发生时要调用的事件处理程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

`InvokeHelper`

## <a name="requirements"></a>要求

**标头：** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="callback"></a>Invokehelper:: Callback_

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
TCallback callback_;
```

### <a name="remarks"></a>备注

表示事件发生时要调用的事件处理程序。

`TCallback`模板参数指定的事件处理程序的类型。

## <a name="invoke"></a>Invokehelper:: Invoke

支持 WRL 基础结构，不应在代码中直接使用。

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

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为描述错误的 HRESULT。

### <a name="remarks"></a>备注

调用其签名包含指定的数量的参数的事件处理程序。

## <a name="invokehelper"></a>Invokehelper:: Invokehelper

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>参数

*回调*<br/>
事件处理程序。

### <a name="remarks"></a>备注

初始化 `InvokeHelper` 类的新实例。

`TCallback`模板参数指定的事件处理程序的类型。
