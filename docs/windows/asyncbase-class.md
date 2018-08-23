---
title: AsyncBase 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
dev_langs:
- C++
helpviewer_keywords:
- AsyncBase class
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cba5aaaec3303d9cd3534ff86cb677219c9c81c7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586779"
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

template <
   typename TComplete,
   AsyncResultType resultType
>
class AsyncBase<TComplete, Details::Nil, resultType> : public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>参数

*TComplete*  
异步操作完成时调用事件处理程序。

*TProgress*  
当正在运行的异步操作报告当前操作的进度时调用事件处理程序。

*resultType*  
之一[AsyncResultType](../windows/asyncresulttype-enumeration.md)枚举值。 默认情况下， `SingleResult`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[AsyncBase::AsyncBase 构造函数](../windows/asyncbase-asyncbase-constructor.md)|初始化的实例**AsyncBase**类。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[AsyncBase::Cancel 方法](../windows/asyncbase-cancel-method.md)|取消异步操作。|
|[AsyncBase::Close 方法](../windows/asyncbase-close-method.md)|关闭的异步操作。|
|[AsyncBase::FireCompletion 方法](../windows/asyncbase-firecompletion-method.md)|调用完成事件处理程序，或重置内部进行委托。|
|[AsyncBase::FireProgress 方法](../windows/asyncbase-fireprogress-method.md)|调用当前正在进行事件处理程序。|
|[AsyncBase::get_ErrorCode 方法](../windows/asyncbase-get-errorcode-method.md)|检索当前的异步操作的错误代码。|
|[AsyncBase::get_Id 方法](../windows/asyncbase-get-id-method.md)|检索异步操作的句柄。|
|[AsyncBase::get_Status 方法](../windows/asyncbase-get-status-method.md)|检索一个值，该值指示异步操作的状态。|
|[AsyncBase::GetOnComplete 方法](../windows/asyncbase-getoncomplete-method.md)|将当前的完成事件处理程序的地址复制到指定的变量。|
|[AsyncBase::GetOnProgress 方法](../windows/asyncbase-getonprogress-method.md)|将当前进度事件处理程序的地址复制到指定的变量。|
|[AsyncBase::put_Id 方法](../windows/asyncbase-put-id-method.md)|设置异步操作的句的柄。|
|[AsyncBase::PutOnComplete 方法](../windows/asyncbase-putoncomplete-method.md)|为指定的值设置完成事件处理程序的地址。|
|[AsyncBase::PutOnProgress 方法](../windows/asyncbase-putonprogress-method.md)|为指定的值设置的进度事件处理程序的地址。|
|[AsyncBase::Start 方法](../windows/asyncbase-start-method.md)|启动异步操作。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[AsyncBase::CheckValidStateForDelegateCall 方法](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|测试是否可以在当前的异步状态中修改委托属性。|
|[AsyncBase::CheckValidStateForResultsCall 方法](../windows/asyncbase-checkvalidstateforresultscall-method.md)|测试是否可以在当前的异步状态中收集的异步操作结果。|
|[AsyncBase::ContinueAsyncOperation 方法](../windows/asyncbase-continueasyncoperation-method.md)|确定异步操作是否会继续进行处理，或者应该中止。|
|[AsyncBase::CurrentStatus 方法](../windows/asyncbase-currentstatus-method.md)|检索当前的异步操作的状态。|
|[AsyncBase::ErrorCode 方法](../windows/asyncbase-errorcode-method.md)|检索当前的异步操作的错误代码。|
|[AsyncBase::OnCancel 方法](../windows/asyncbase-oncancel-method.md)|当在派生类中重写时取消异步操作。|
|[AsyncBase::OnClose 方法](../windows/asyncbase-onclose-method.md)|当在派生类中重写，会关闭一个异步操作。|
|[AsyncBase::OnStart 方法](../windows/asyncbase-onstart-method.md)|当在派生类中重写时启动的异步操作。|
|[AsyncBase::TryTransitionToCompleted 方法](../windows/asyncbase-trytransitiontocompleted-method.md)|指示当前的异步操作是否已完成。|
|[AsyncBase::TryTransitionToError 方法](../windows/asyncbase-trytransitiontoerror-method.md)|指示指定的错误代码是否可以修改的内部错误状态。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)