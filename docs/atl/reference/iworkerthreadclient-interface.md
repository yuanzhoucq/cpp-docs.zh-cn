---
title: IWorkerThreadClient 接口
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: 6a68f25f153a0ad2cf42ebfaa374ff63c5746fcd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326302"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient 接口

`IWorkerThreadClient`是[CWorkerThread](../../atl/reference/cworkerthread-class.md)类的客户端实现的接口。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
__interface IWorkerThreadClient
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[关闭手柄](#closehandle)|实现此方法以关闭与此对象关联的句柄。|
|[执行](#execute)|实现此方法，当与此对象关联的句柄发出信号时执行代码。|

## <a name="remarks"></a>备注

当您有代码需要在工作线程上执行以响应变为信号的句柄时，实现此接口。

## <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThread客户端：：关闭句柄

实现此方法以关闭与此对象关联的句柄。

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>参数

*hHandle*<br/>
要关闭的句柄。

### <a name="return-value"></a>返回值

返回成功时S_OK，或失败时出现错误 HRESULT。

### <a name="remarks"></a>备注

传递给此方法的句柄以前通过调用[CWorkerThread：：addHandle](../../atl/reference/cworkerthread-class.md#addhandle)与此对象相关联。

### <a name="example"></a>示例

以下代码显示了`IWorkerThreadClient::CloseHandle`的简单实现。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThread客户端：执行

实现此方法，当与此对象关联的句柄发出信号时执行代码。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>参数

*德帕拉姆*<br/>
用户参数。

*hObject*<br/>
已发出信号的句柄。

### <a name="return-value"></a>返回值

返回成功时S_OK，或失败时出现错误 HRESULT。

### <a name="remarks"></a>备注

传递给此方法的句柄和 DWORD/指针以前通过调用[CWorkerThread：：addHandle](../../atl/reference/cworkerthread-class.md#addhandle)与此对象相关联。

### <a name="example"></a>示例

以下代码显示了`IWorkerThreadClient::Execute`的简单实现。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>另请参阅

[类](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread 类](../../atl/reference/cworkerthread-class.md)
