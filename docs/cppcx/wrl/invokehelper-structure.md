---
title: InvokeHelper 结构
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
ms.openlocfilehash: 9cb4e166628a6b5e7671494446d467e73c9f8cc3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371388"
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

*T委托接口*<br/>
委托接口类型。

*回拨*<br/>
事件处理程序函数的类型。

*argCount*<br/>
`InvokeHelper`专门化中的参数数。

## <a name="remarks"></a>备注

根据指定的参数数和`Invoke()`类型提供方法的实现。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称     | 说明
-------- | -----------------------------------------------------------------------------
`Traits` | 定义每个事件处理程序参数类型的类的同义词。

### <a name="public-constructors"></a>公共构造函数

名称                                        | 说明
------------------------------------------- | -------------------------------------------------------
[调用帮助者：：调用帮助程序](#invokehelper) | 初始化 `InvokeHelper` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                            | 说明
------------------------------- | -----------------------------------------------------------------------------------
[调用帮助器：：调用](#invoke) | 调用其签名包含指定参数数的事件处理程序。

### <a name="public-data-members"></a>公共数据成员

名称                                 | 说明
------------------------------------ | ----------------------------------------------------------
[调用帮助者：：callback_](#callback) | 表示事件发生时要调用的事件处理程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

`InvokeHelper`

## <a name="requirements"></a>要求

**标题：** 事件.h

**命名空间：** 微软：：WRL：:D

## <a name="invokehelpercallback_"></a><a name="callback"></a>调用帮助者：：callback_

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
TCallback callback_;
```

### <a name="remarks"></a>备注

表示事件发生时要调用的事件处理程序。

模板`TCallback`参数指定事件处理程序的类型。

## <a name="invokehelperinvoke"></a><a name="invoke"></a>调用帮助器：：调用

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
参数 1.

*arg2*<br/>
参数 2.

*arg3*<br/>
参数 3.

*arg4*<br/>
参数 4.

*arg5*<br/>
参数 5.

*arg6*<br/>
参数 6.

*arg7*<br/>
参数 7.

*arg8*<br/>
参数 8.

*arg9*<br/>
参数 9.

### <a name="return-value"></a>返回值

S_OK如果成功;否则，描述错误的 HRESULT。

### <a name="remarks"></a>备注

调用其签名包含指定参数数的事件处理程序。

## <a name="invokehelperinvokehelper"></a><a name="invokehelper"></a>调用帮助者：：调用帮助程序

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>参数

*回调 (callback)*<br/>
事件处理程序。

### <a name="remarks"></a>备注

初始化 `InvokeHelper` 类的新实例。

模板`TCallback`参数指定事件处理程序的类型。
