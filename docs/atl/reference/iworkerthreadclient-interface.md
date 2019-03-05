---
title: IWorkerThreadClient Interface
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: 1fa8a5e42d002260076f737d3d33cfa191ff297a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295274"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient Interface

`IWorkerThreadClient` 是的客户端实现的接口[CWorkerThread](../../atl/reference/cworkerthread-class.md)类。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
__interface IWorkerThreadClient
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CloseHandle](#closehandle)|实现此方法以关闭与此对象关联的句柄。|
|[Execute](#execute)|实现此方法以执行代码时与此对象关联的句柄发出信号。|

## <a name="remarks"></a>备注

在您将需要成为发出信号的句柄的响应的工作线程上执行的代码实现此接口。

## <a name="requirements"></a>要求

**标头：** atlutil.h

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

实现此方法以关闭与此对象关联的句柄。

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>参数

*hHandle*<br/>
要关闭句柄。

### <a name="return-value"></a>返回值

返回成功或失败时的错误 HRESULT，则为 S_OK。

### <a name="remarks"></a>备注

传递给此方法的句柄是以前通过调用与此对象关联[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。

### <a name="example"></a>示例

下面的代码演示的简单实现`IWorkerThreadClient::CloseHandle`。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

实现此方法以执行代码时与此对象关联的句柄发出信号。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>参数

*dwParam*<br/>
User 参数中。

*hObject*<br/>
已收到信号的句柄。

### <a name="return-value"></a>返回值

返回成功或失败时的错误 HRESULT，则为 S_OK。

### <a name="remarks"></a>备注

句柄和双字节/指针传递给此方法是以前通过调用与此对象关联[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。

### <a name="example"></a>示例

下面的代码演示的简单实现`IWorkerThreadClient::Execute`。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>请参阅

[类](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread 类](../../atl/reference/cworkerthread-class.md)
