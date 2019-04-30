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
ms.openlocfilehash: 3fcba210d4018d22487d234b437acfee3634cec6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386130"
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
委托接口类型。

*TCallback*<br/>
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
[InvokeHelper::InvokeHelper](#invokehelper) | 初始化 `InvokeHelper` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                            | 描述
------------------------------- | -----------------------------------------------------------------------------------
[InvokeHelper::Invoke](#invoke) | 调用其签名包含指定的数量的参数的事件处理程序。

### <a name="public-data-members"></a>公共数据成员

名称                                 | 描述
------------------------------------ | ----------------------------------------------------------
[InvokeHelper::callback_](#callback) | 表示事件发生时要调用的事件处理程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

`InvokeHelper`

## <a name="requirements"></a>要求

**标头：** event.h

**命名空间：** Microsoft::WRL::Details

## <a name="callback"></a>Invokehelper:: Callback_

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
TCallback callback_;
```

### <a name="remarks"></a>备注

表示事件发生时要调用的事件处理程序。

`TCallback`模板参数指定的事件处理程序的类型。

## <a name="invoke"></a>InvokeHelper::Invoke

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

*arg2*<br/>
参数 2。

*arg3*<br/>
参数 3。

*arg4*<br/>
参数 4。

*arg5*<br/>
参数 5。

*arg6*<br/>
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

## <a name="invokehelper"></a>InvokeHelper::InvokeHelper

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>参数

*callback*<br/>
事件处理程序。

### <a name="remarks"></a>备注

初始化 `InvokeHelper` 类的新实例。

`TCallback`模板参数指定的事件处理程序的类型。
