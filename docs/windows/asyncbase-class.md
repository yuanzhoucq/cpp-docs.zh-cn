---
title: AsyncBase 类 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
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
- async/Microsoft::WRL::AsyncBase::Start
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs:
- C++
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
- Microsoft::WRL::AsyncBase::Start method
- Microsoft::WRL::AsyncBase::TryTransitionToCompleted method
- Microsoft::WRL::AsyncBase::TryTransitionToError method
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6538d06c291bccc8764403b26f5c8d88f4afd781
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788794"
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

*TComplete*<br/>
异步操作完成时调用事件处理程序。

*TProgress*<br/>
当正在运行的异步操作报告当前操作的进度时调用事件处理程序。

*resultType*<br/>
之一[AsyncResultType](../windows/asyncresulttype-enumeration.md)枚举值。 默认情况下， `SingleResult`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                               | 描述
---------------------------------- | -------------------------------------------------
[Asyncbase:: Asyncbase](#asyncbase) | 初始化 `AsyncBase` 类的实例。

### <a name="public-methods"></a>公共方法

名称                                         | 描述
-------------------------------------------- | -------------------------------------------------------------------------------------
[Asyncbase:: Cancel](#cancel)                 | 取消异步操作。
[Asyncbase:: Close](#close)                   | 关闭的异步操作。
[Asyncbase:: Firecompletion](#firecompletion) | 调用完成事件处理程序，或重置内部进行委托。
[Asyncbase:: Fireprogress](#fireprogress)     | 调用当前正在进行事件处理程序。
[Asyncbase:: Get_errorcode](#get-errorcode)   | 检索当前的异步操作的错误代码。
[Asyncbase:: Get_id](#get-id)                 | 检索异步操作的句柄。
[Asyncbase:: Get_status](#get-status)         | 检索一个值，该值指示异步操作的状态。
[Asyncbase:: Getoncomplete](#getoncomplete)   | 将当前的完成事件处理程序的地址复制到指定的变量。
[Asyncbase:: Getonprogress](#getonprogress)   | 将当前进度事件处理程序的地址复制到指定的变量。
[Asyncbase:: Put_id](#put-id)                 | 设置异步操作的句的柄。
[Asyncbase:: Putoncomplete](#putoncomplete)   | 为指定的值设置完成事件处理程序的地址。
[Asyncbase:: Putonprogress](#putonprogress)   | 为指定的值设置的进度事件处理程序的地址。
[Asyncbase:: Start](#start)                   | 启动异步操作。

### <a name="protected-methods"></a>受保护的方法

名称                                                                         | 描述
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[Asyncbase:: Checkvalidstatefordelegatecall](#checkvalidstatefordelegatecall) | 测试是否可以在当前的异步状态中修改委托属性。
[Asyncbase:: Checkvalidstateforresultscall](#checkvalidstateforresultscall)   | 测试是否可以在当前的异步状态中收集的异步操作结果。
[Asyncbase:: Continueasyncoperation](#continueasyncoperation)                 | 确定异步操作是否会继续进行处理，或者应该中止。
[Asyncbase:: Currentstatus](#currentstatus)                                   | 检索当前的异步操作的状态。
[Asyncbase:: Errorcode](#errorcode)                                           | 检索当前的异步操作的错误代码。
[Asyncbase:: Oncancel](#oncancel)                                             | 当在派生类中重写时取消异步操作。
[Asyncbase:: Onclose](#onclose)                                               | 当在派生类中重写，会关闭一个异步操作。
[Asyncbase:: Onstart](#onstart)                                               | 当在派生类中重写时启动的异步操作。
[Asyncbase:: Trytransitiontocompleted](#trytransitiontocompleted)             | 指示当前的异步操作是否已完成。
[Asyncbase:: Trytransitiontoerror](#trytransitiontoerror)                     | 指示指定的错误代码是否可以修改的内部错误状态。

## <a name="inheritance-hierarchy"></a>继承层次结构

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="asyncbase"></a>Asyncbase:: Asyncbase

初始化 `AsyncBase` 类的实例。

```cpp
AsyncBase();
```

## <a name="cancel"></a>Asyncbase:: Cancel

取消异步操作。

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>返回值

默认情况下，始终返回 S_OK。

### <a name="remarks"></a>备注

`Cancel()` 是的默认实现`IAsyncInfo::Cancel`，并不执行任何实际工作。 若要实际取消异步操作，请重写`OnCancel()`纯虚方法。

## <a name="checkvalidstatefordelegatecall"></a>Asyncbase:: Checkvalidstatefordelegatecall

测试是否可以在当前的异步状态中修改委托属性。

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>返回值

如果可以修改委托属性; 则为 S_OK否则为 E_ILLEGAL_METHOD_CALL。

## <a name="checkvalidstateforresultscall"></a>Asyncbase:: Checkvalidstateforresultscall

测试是否可以在当前的异步状态中收集的异步操作结果。

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>返回值

如果可以收集结果; 则为 S_OK否则为 E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL。

## <a name="close"></a>Asyncbase:: Close

关闭的异步操作。

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>返回值

如果该操作将关闭，或者已经为 S_OK 关闭;否则为 E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>备注

`Close()` 是的默认实现`IAsyncInfo::Close`，并不执行任何实际工作。 若要实际关闭异步操作，请重写`OnClose()`纯虚方法。

## <a name="continueasyncoperation"></a>Asyncbase:: Continueasyncoperation

确定异步操作是否会继续进行处理，或者应该中止。

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>返回值

`true` 如果异步操作的当前状态是*启动*，这意味着该操作应继续。 否则为`false`，这意味着该操作应该中止。

## <a name="currentstatus"></a>Asyncbase:: Currentstatus

检索当前的异步操作的状态。

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>参数

*status*<br/>
此操作存储的当前状态的位置。

### <a name="remarks"></a>备注

此操作是线程安全的。

## <a name="errorcode"></a>Asyncbase:: Errorcode

检索当前的异步操作的错误代码。

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>参数

*error*<br/>
此操作存储当前的错误代码的位置。

### <a name="remarks"></a>备注

此操作是线程安全的。

## <a name="firecompletion"></a>Asyncbase:: Firecompletion

调用完成事件处理程序，或重置内部进行委托。

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>备注

第一个版本`FireCompletion()`重置内部进度委托变量。 如果异步操作已完成，第二个版本调用完成事件处理程序。

## <a name="fireprogress"></a>Asyncbase:: Fireprogress

调用当前正在进行事件处理程序。

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>参数

*arg*<br/>
要调用的事件处理程序方法。

### <a name="remarks"></a>备注

`ProgressTraits` 派生自[ArgTraitsHelper 结构](../windows/argtraitshelper-structure.md)。

## <a name="get-errorcode"></a>Asyncbase:: Get_errorcode

检索当前的异步操作的错误代码。

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>参数

*错误代码*<br/>
存储当前的错误代码的位置。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_ILLEGAL_METHOD_CALL 如果关闭当前的异步操作。

## <a name="get-id"></a>Asyncbase:: Get_id

检索异步操作的句柄。

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>参数

*id*<br/>
句柄所在存储的位置。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>备注

此方法实现 `IAsyncInfo::get_Id`。

## <a name="get-status"></a>Asyncbase:: Get_status

检索一个值，该值指示异步操作的状态。

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>参数

*status*<br/>
状态所在存储的位置。 有关详细信息，请参阅 `Windows::Foundation::AsyncStatus`。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>备注

此方法实现 `IAsyncInfo::get_Status`。

## <a name="getoncomplete"></a>Asyncbase:: Getoncomplete

将当前的完成事件处理程序的地址复制到指定的变量。

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>参数

*completeHandler*<br/>
存储当前完成事件处理程序的地址的位置。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_ILLEGAL_METHOD_CALL。

## <a name="getonprogress"></a>Asyncbase:: Getonprogress

将当前进度事件处理程序的地址复制到指定的变量。

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>参数

*progressHandler*<br/>
存储当前进度事件处理程序的地址的位置。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_ILLEGAL_METHOD_CALL。

## <a name="oncancel"></a>Asyncbase:: Oncancel

当在派生类中重写时取消异步操作。

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="onclose"></a>Asyncbase:: Onclose

当在派生类中重写，会关闭一个异步操作。

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="onstart"></a>Asyncbase:: Onstart

当在派生类中重写时启动的异步操作。

```cpp
virtual void OnStart(
   void
) = 0;
```

## <a name="put-id"></a>Asyncbase:: Put_id

设置异步操作的句的柄。

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>参数

*id*<br/>
非零值的句柄。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_INVALIDARG 或 E_ILLEGAL_METHOD_CALL。

## <a name="putoncomplete"></a>Asyncbase:: Putoncomplete

为指定的值设置完成事件处理程序的地址。

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>参数

*completeHandler*<br/>
为设置完成事件处理程序地址。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_ILLEGAL_METHOD_CALL。

## <a name="putonprogress"></a>Asyncbase:: Putonprogress

为指定的值设置的进度事件处理程序的地址。

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>参数

*progressHandler*<br/>
进度事件处理程序设置为地址。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_ILLEGAL_METHOD_CALL。

## <a name="start"></a>Asyncbase:: Start

启动异步操作。

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>返回值

如果该操作启动或已，启动，则为 S_OK;否则为 E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>备注

`Start()` 是的默认实现`IAsyncInfo::Start`，并不执行任何实际工作。 若要实际启动异步操作，重写`OnStart()`纯虚方法。

## <a name="trytransitiontocompleted"></a>Asyncbase:: Trytransitiontocompleted

指示当前的异步操作是否已完成。

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>返回值

`true` 如果异步操作已完成;否则为`false`。

## <a name="trytransitiontoerror"></a>Asyncbase:: Trytransitiontoerror

指示指定的错误代码是否可以修改的内部错误状态。

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>参数

*error*<br/>
错误的 HRESULT。

### <a name="return-value"></a>返回值

`true` 如果内部错误状态发生了更改;否则为`false`。

### <a name="remarks"></a>备注

仅当错误状态已设置为，则为 S_OK，则此操作修改的错误状态。 如果错误状态已经是错误，已取消、 已完成，或已关闭，则此操作无效。
