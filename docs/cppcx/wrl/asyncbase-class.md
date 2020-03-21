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
ms.openlocfilehash: 09819c9e8dd924581ce8cd67233d273f7e8d62ca
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079900"
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

### <a name="parameters"></a>parameters

*TComplete*<br/>
异步操作完成时调用的事件处理程序。

*TProgress*<br/>
当正在运行的异步操作报告操作的当前进度时调用的事件处理程序。

*resultType*<br/>
[AsyncResultType](asyncresulttype-enumeration.md)枚举值之一。 默认为 `SingleResult`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                               | 说明
---------------------------------- | -------------------------------------------------
[AsyncBase：： AsyncBase](#asyncbase) | 初始化 `AsyncBase` 类的实例。

### <a name="public-methods"></a>公共方法

名称                                         | 说明
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase：： Cancel](#cancel)                 | 取消异步操作。
[AsyncBase：： Close](#close)                   | 关闭异步操作。
[AsyncBase：： FireCompletion](#firecompletion) | 调用完成事件处理程序，或重置内部进度委托。
[AsyncBase：： FireProgress](#fireprogress)     | 调用当前进度事件处理程序。
[AsyncBase：： get_ErrorCode](#get-errorcode)   | 检索当前异步操作的错误代码。
[AsyncBase：： get_Id](#get-id)                 | 检索异步操作的句柄。
[AsyncBase：： get_Status](#get-status)         | 检索一个值，该值指示异步操作的状态。
[AsyncBase：： GetOnComplete](#getoncomplete)   | 将当前完成事件处理程序的地址复制到指定的变量。
[AsyncBase：： GetOnProgress](#getonprogress)   | 将当前进度事件处理程序的地址复制到指定的变量。
[AsyncBase：:p ut_Id](#put-id)                 | 设置异步操作的句柄。
[AsyncBase：:P utOnComplete](#putoncomplete)   | 将完成事件处理程序的地址设置为指定值。
[AsyncBase：:P utOnProgress](#putonprogress)   | 将进度事件处理程序的地址设置为指定值。

### <a name="protected-methods"></a>受保护方法

名称                                                                         | 说明
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase：： CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | 测试是否可以在当前异步状态中修改委托属性。
[AsyncBase：： CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | 测试异步操作的结果是否可以在当前异步状态中收集。
[AsyncBase：： ContinueAsyncOperation](#continueasyncoperation)                 | 确定异步操作应继续处理还是应停止。
[AsyncBase：： CurrentStatus](#currentstatus)                                   | 检索当前异步操作的状态。
[AsyncBase：： ErrorCode](#errorcode)                                           | 检索当前异步操作的错误代码。
[AsyncBase：： OnCancel](#oncancel)                                             | 当在派生类中重写时，取消异步操作。
[AsyncBase：： OnClose](#onclose)                                               | 当在派生类中重写时，关闭异步操作。
[AsyncBase：： OnStart](#onstart)                                               | 当在派生类中重写时，启动异步操作。
[AsyncBase：： Start](#start)                                                   | 启动异步操作。
[AsyncBase：： TryTransitionToCompleted](#trytransitiontocompleted)             | 指示当前异步操作是否已完成。
[AsyncBase：： TryTransitionToError](#trytransitiontoerror)                     | 指示指定的错误代码是否可以修改内部错误状态。

## <a name="inheritance-hierarchy"></a>继承层次结构

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>要求

**标头：** async。h

**命名空间：** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>AsyncBase：： AsyncBase

初始化 `AsyncBase` 类的实例。

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>AsyncBase：： Cancel

取消异步操作。

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>返回值

默认情况下，始终返回 S_OK。

### <a name="remarks"></a>备注

`Cancel()` 是 `IAsyncInfo::Cancel`的默认实现，并且不执行任何实际工作。 若要实际取消异步操作，请重写 `OnCancel()` 纯虚方法。

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>AsyncBase：： CheckValidStateForDelegateCall

测试是否可以在当前异步状态中修改委托属性。

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>返回值

S_OK 如果可以修改委托属性，则为; 否则为。否则，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>AsyncBase：： CheckValidStateForResultsCall

测试异步操作的结果是否可以在当前异步状态中收集。

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>返回值

S_OK 是否可以收集结果;否则，E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseclose"></a><a name="close"></a>AsyncBase：： Close

关闭异步操作。

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>返回值

如果操作关闭或已关闭，则 S_OK;否则，E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>备注

`Close()` 是 `IAsyncInfo::Close`的默认实现，并且不执行任何实际工作。 若要实际关闭异步操作，请重写 `OnClose()` 纯虚方法。

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>AsyncBase：： ContinueAsyncOperation

确定异步操作应继续处理还是应停止。

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>返回值

如果异步操作的当前状态为 true，则**为 true** *，这*意味着操作应继续。 否则**为 false**，这意味着应停止操作。

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>AsyncBase：： CurrentStatus

检索当前异步操作的状态。

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>parameters

*status*<br/>
此操作存储当前状态的位置。

### <a name="remarks"></a>备注

此操作是线程安全的。

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>AsyncBase：： ErrorCode

检索当前异步操作的错误代码。

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>parameters

*error*<br/>
此操作存储当前错误代码的位置。

### <a name="remarks"></a>备注

此操作是线程安全的。

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>AsyncBase：： FireCompletion

调用完成事件处理程序，或重置内部进度委托。

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>备注

第一版 `FireCompletion()` 重置内部进度委托变量。 如果异步操作已完成，则第二个版本调用完成事件处理程序。

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>AsyncBase：： FireProgress

调用当前进度事件处理程序。

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>parameters

*arg*<br/>
要调用的事件处理程序方法。

### <a name="remarks"></a>备注

`ProgressTraits` 派生自[ArgTraitsHelper 结构](argtraitshelper-structure.md)。

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>AsyncBase：： get_ErrorCode

检索当前异步操作的错误代码。

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>parameters

*错误*<br/>
当前错误代码的存储位置。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，E_ILLEGAL_METHOD_CALL 是否关闭当前异步操作。

## <a name="asyncbaseget_id"></a><a name="get-id"></a>AsyncBase：： get_Id

检索异步操作的句柄。

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>parameters

*id*<br/>
要存储句柄的位置。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>备注

此方法实现 `IAsyncInfo::get_Id`。

## <a name="asyncbaseget_status"></a><a name="get-status"></a>AsyncBase：： get_Status

检索一个值，该值指示异步操作的状态。

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>parameters

*status*<br/>
要存储状态的位置。 有关详细信息，请参阅 `Windows::Foundation::AsyncStatus`。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>备注

此方法实现 `IAsyncInfo::get_Status`。

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>AsyncBase：： GetOnComplete

将当前完成事件处理程序的地址复制到指定的变量。

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>parameters

*completeHandler*<br/>
当前完成事件处理程序的地址的存储位置。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>AsyncBase：： GetOnProgress

将当前进度事件处理程序的地址复制到指定的变量。

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>parameters

*progressHandler*<br/>
当前进度事件处理程序的地址的存储位置。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>AsyncBase：： OnCancel

当在派生类中重写时，取消异步操作。

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>AsyncBase：： OnClose

当在派生类中重写时，关闭异步操作。

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>AsyncBase：： OnStart

当在派生类中重写时，启动异步操作。

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>AsyncBase：:p ut_Id

设置异步操作的句柄。

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>parameters

*id*<br/>
非零的句柄。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，E_INVALIDARG 或 E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>AsyncBase：:P utOnComplete

将完成事件处理程序的地址设置为指定值。

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>parameters

*completeHandler*<br/>
完成事件处理程序所设置到的地址。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>AsyncBase：:P utOnProgress

将进度事件处理程序的地址设置为指定值。

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>parameters

*progressHandler*<br/>
进度事件处理程序所设置到的地址。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasestart"></a><a name="start"></a>AsyncBase：： Start

启动异步操作。

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>返回值

如果操作已启动或已启动，则为 S_OK;否则，E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>备注

`Start()` 是在外部不可见的受保护方法，因为异步操作会在返回调用方之前 "热启动"。

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>AsyncBase：： TryTransitionToCompleted

指示当前异步操作是否已完成。

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>返回值

如果异步操作已完成，则为**true** ;否则**为 false**。

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>AsyncBase：： TryTransitionToError

指示指定的错误代码是否可以修改内部错误状态。

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>parameters

*error*<br/>
错误 HRESULT。

### <a name="return-value"></a>返回值

如果更改了内部错误状态，**则为 true** ;否则**为 false**。

### <a name="remarks"></a>备注

仅当错误状态已设置为 S_OK 时，此操作才会修改错误状态。 如果错误状态已是 "错误"、"已取消"、"已完成" 或 "已关闭"，则此操作无效。
