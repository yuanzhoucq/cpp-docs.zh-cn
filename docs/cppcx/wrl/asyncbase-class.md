---
title: AsyncBase 类
ms.date: 10/08/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
- async/Microsoft::WRL::AsyncBase::AsyncBase
- async/Microsoft::WRL::AsyncBase::Cancel
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
- async/Microsoft::WRL::AsyncBase::Close
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
- async/Microsoft::WRL::AsyncBase::CurrentStatus
- async/Microsoft::WRL::AsyncBase::ErrorCode
- async/Microsoft::WRL::AsyncBase::FireCompletion
- async/Microsoft::WRL::AsyncBase::FireProgress
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
- async/Microsoft::WRL::AsyncBase::get_Id
- async/Microsoft::WRL::AsyncBase::get_Status
- async/Microsoft::WRL::AsyncBase::GetOnComplete
- async/Microsoft::WRL::AsyncBase::GetOnProgress
- async/Microsoft::WRL::AsyncBase::OnCancel
- async/Microsoft::WRL::AsyncBase::OnClose
- async/Microsoft::WRL::AsyncBase::OnStart
- async/Microsoft::WRL::AsyncBase::put_Id
- async/Microsoft::WRL::AsyncBase::PutOnComplete
- async/Microsoft::WRL::AsyncBase::PutOnProgress
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
helpviewer_keywords:
- Microsoft::WRL::AsyncBase class
- Microsoft::WRL::AsyncBase::AsyncBase, constructor
- Microsoft::WRL::AsyncBase::Cancel method
- Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall method
- Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall method
- Microsoft::WRL::AsyncBase::Close method
- Microsoft::WRL::AsyncBase::ContinueAsyncOperation method
- Microsoft::WRL::AsyncBase::CurrentStatus method
- Microsoft::WRL::AsyncBase::ErrorCode method
- Microsoft::WRL::AsyncBase::FireCompletion method
- Microsoft::WRL::AsyncBase::FireProgress method
- Microsoft::WRL::AsyncBase::get_ErrorCode method
- Microsoft::WRL::AsyncBase::get_Id method
- Microsoft::WRL::AsyncBase::get_Status method
- Microsoft::WRL::AsyncBase::GetOnComplete method
- Microsoft::WRL::AsyncBase::GetOnProgress method
- Microsoft::WRL::AsyncBase::OnCancel method
- Microsoft::WRL::AsyncBase::OnClose method
- Microsoft::WRL::AsyncBase::OnStart method
- Microsoft::WRL::AsyncBase::put_Id method
- Microsoft::WRL::AsyncBase::PutOnComplete method
- Microsoft::WRL::AsyncBase::PutOnProgress method
- Microsoft::WRL::AsyncBase::TryTransitionToCompleted method
- Microsoft::WRL::AsyncBase::TryTransitionToError method
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
ms.openlocfilehash: 0254aa4dc243eeffa43850c437a833a6530c01e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371860"
---
# <a name="asyncbase-class"></a>AsyncBase 类

实现 Windows 运行时异步状态机。

## <a name="syntax"></a>语法

```cpp
template <
    typename TComplete,
    typename TProgress = Details::Nil,
    AsyncResultType resultType = SingleResult
>
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;

template <typename TComplete, AsyncResultType resultType>
class AsyncBase<TComplete, Details::Nil, resultType> :
    public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>参数

*完成*<br/>
异步操作完成后调用的事件处理程序。

*T进展*<br/>
运行异步操作报告操作的当前进度时调用的事件处理程序。

*结果类型*<br/>
[AsyncResult 类型](asyncresulttype-enumeration.md)枚举值之一。 默认为 `SingleResult`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                               | 说明
---------------------------------- | -------------------------------------------------
[异步基础：：异步基础](#asyncbase) | 初始化 `AsyncBase` 类的实例。

### <a name="public-methods"></a>公共方法

名称                                         | 说明
-------------------------------------------- | -------------------------------------------------------------------------------------
[异步基础：：取消](#cancel)                 | 取消异步操作。
[异步基础：关闭](#close)                   | 关闭异步操作。
[异步基础：：火完成](#firecompletion) | 调用完成事件处理程序，或重置内部进度委托。
[异步基础：：火进度](#fireprogress)     | 调用当前进度事件处理程序。
[异步基础：：get_ErrorCode](#get-errorcode)   | 检索当前异步操作的错误代码。
[异步基础：：get_Id](#get-id)                 | 检索异步操作的句柄。
[异步基础：：get_Status](#get-status)         | 检索指示异步操作状态的值。
[异步基础：：完成](#getoncomplete)   | 将当前完成事件处理程序的地址复制到指定的变量。
[异步基础：：获取进度](#getonprogress)   | 将当前进度事件处理程序的地址复制到指定的变量。
[异步基础：:put_Id](#put-id)                 | 设置异步操作的句柄。
[异步基础：:PutOnComplete](#putoncomplete)   | 将完成事件处理程序的地址设置为指定值。
[异步基础：:P](#putonprogress)   | 将进度事件处理程序的地址设置为指定值。

### <a name="protected-methods"></a>受保护的方法

名称                                                                         | 说明
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[异步基础：：检查有效状态的委托呼叫](#checkvalidstatefordelegatecall) | 测试是否可以在当前异步状态下修改委托属性。
[异步基础：：检查有效状态结果调用](#checkvalidstateforresultscall)   | 测试异步操作的结果是否可以在当前异步状态下收集。
[异步基础：继续同步操作](#continueasyncoperation)                 | 确定异步操作是继续处理还是应停止。
[异步基础：：当前状态](#currentstatus)                                   | 检索当前异步操作的状态。
[异步基础：：错误代码](#errorcode)                                           | 检索当前异步操作的错误代码。
[异步基础：：打开取消](#oncancel)                                             | 在派生类中重写时，将取消异步操作。
[异步基础：：关闭](#onclose)                                               | 在派生类中重写时，将关闭异步操作。
[异步基础：：开始](#onstart)                                               | 在派生类中重写时，启动异步操作。
[异步基础：：开始](#start)                                                   | 启动异步操作。
[异步基础：：尝试过渡完成](#trytransitiontocompleted)             | 指示当前异步操作是否已完成。
[异步基础：：尝试转换到错误](#trytransitiontoerror)                     | 指示指定的错误代码是否可以修改内部错误状态。

## <a name="inheritance-hierarchy"></a>继承层次结构

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>要求

**标题：** 异步.h

**命名空间：** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>异步基础：：异步基础

初始化 `AsyncBase` 类的实例。

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>异步基础：：取消

取消异步操作。

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>返回值

默认情况下，始终返回S_OK。

### <a name="remarks"></a>备注

`Cancel()`是 的`IAsyncInfo::Cancel`默认实现，不执行实际工作。 要实际取消异步操作，请重写`OnCancel()`纯虚拟方法。

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>异步基础：：检查有效状态的委托呼叫

测试是否可以在当前异步状态下修改委托属性。

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>返回值

S_OK是否可以修改委托属性;如果可以修改委托属性，则否则，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>异步基础：：检查有效状态结果调用

测试异步操作的结果是否可以在当前异步状态下收集。

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>返回值

S_OK是否可以收集结果;否则，E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseclose"></a><a name="close"></a>异步基础：关闭

关闭异步操作。

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>返回值

如果操作关闭或已关闭，S_OK;否则，E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>备注

`Close()`是 的`IAsyncInfo::Close`默认实现，不执行实际工作。 要实际关闭异步操作，重写`OnClose()`纯虚拟方法。

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>异步基础：继续同步操作

确定异步操作是继续处理还是应停止。

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>返回值

如果异步操作的当前状态*已启动*，则**为 true，** 这意味着该操作应继续。 否则 **，false**，这意味着操作应停止。

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>异步基础：：当前状态

检索当前异步操作的状态。

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>参数

*状态*<br/>
此操作存储当前状态的位置。

### <a name="remarks"></a>备注

此操作是线程安全的。

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>异步基础：：错误代码

检索当前异步操作的错误代码。

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>参数

*错误*<br/>
此操作存储当前错误代码的位置。

### <a name="remarks"></a>备注

此操作是线程安全的。

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>异步基础：：火完成

调用完成事件处理程序，或重置内部进度委托。

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>备注

第一个版本`FireCompletion()`重置内部进度委托变量。 如果异步操作完成，第二个版本将调用完成事件处理程序。

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>异步基础：：火进度

调用当前进度事件处理程序。

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>参数

*精 氨 酸*<br/>
要调用的事件处理程序方法。

### <a name="remarks"></a>备注

`ProgressTraits`派生自[阿格格瑟斯帮助器结构](argtraitshelper-structure.md)。

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>异步基础：：get_ErrorCode

检索当前异步操作的错误代码。

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>参数

*errorCode*<br/>
存储当前错误代码的位置。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，如果关闭当前异步操作，则E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseget_id"></a><a name="get-id"></a>异步基础：：get_Id

检索异步操作的句柄。

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>参数

*id*<br/>
要存储句柄的位置。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>备注

此方法实现 `IAsyncInfo::get_Id`。

## <a name="asyncbaseget_status"></a><a name="get-status"></a>异步基础：：get_Status

检索指示异步操作状态的值。

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>参数

*状态*<br/>
要存储状态的位置。 有关详细信息，请参阅 `Windows::Foundation::AsyncStatus`。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>备注

此方法实现 `IAsyncInfo::get_Status`。

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>异步基础：：完成

将当前完成事件处理程序的地址复制到指定的变量。

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>参数

*完成汉德勒*<br/>
存储当前完成事件处理程序地址的位置。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>异步基础：：获取进度

将当前进度事件处理程序的地址复制到指定的变量。

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>参数

*进度处理程序*<br/>
存储当前进度事件处理程序地址的位置。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>异步基础：：打开取消

在派生类中重写时，将取消异步操作。

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>异步基础：：关闭

在派生类中重写时，将关闭异步操作。

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>异步基础：：开始

在派生类中重写时，启动异步操作。

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>异步基础：:put_Id

设置异步操作的句柄。

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>参数

*id*<br/>
非零句柄。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，E_INVALIDARG或E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>异步基础：:PutOnComplete

将完成事件处理程序的地址设置为指定值。

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>参数

*完成汉德勒*<br/>
将完成事件处理程序设置为的地址。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>异步基础：:P

将进度事件处理程序的地址设置为指定值。

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>参数

*进度处理程序*<br/>
将进度事件处理程序设置为的地址。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasestart"></a><a name="start"></a>异步基础：：开始

启动异步操作。

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>返回值

S_OK操作是否启动或已启动;如果操作已启动，则否则，E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>备注

`Start()`是一种不受外部可见的受保护方法，因为异步操作在返回到调用方之前"热启动"。

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>异步基础：：尝试过渡完成

指示当前异步操作是否已完成。

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>返回值

如果异步操作已完成，**则为 true;** 否则，**假**。

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>异步基础：：尝试转换到错误

指示指定的错误代码是否可以修改内部错误状态。

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>参数

*错误*<br/>
错误 HRESULT。

### <a name="return-value"></a>返回值

如果内部错误状态已更改，为 true;如果内部错误状态已更改，**则为 true。** 否则，**假**。

### <a name="remarks"></a>备注

仅当错误状态已设置为S_OK时，此操作才会修改错误状态。 如果错误状态已出错、已取消、已完成或关闭，则此操作无效。
