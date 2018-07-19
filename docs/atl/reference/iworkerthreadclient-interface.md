---
title: IWorkerThreadClient 接口 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
dev_langs:
- C++
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86e35910469128ecaf38751d6db73094adf3422e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884719"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient 接口
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
|[执行](#execute)|实现此方法以执行代码时与此对象关联的句柄发出信号。|  
  
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
 *hHandle*  
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
 *dwParam*  
 User 参数中。  
  
 *hObject*  
 已收到信号的句柄。  
  
### <a name="return-value"></a>返回值  
 返回成功或失败时的错误 HRESULT，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 句柄和双字节/指针传递给此方法是以前通过调用与此对象关联[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>示例  
 下面的代码演示的简单实现`IWorkerThreadClient::Execute`。  
  
 [!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [类](../../atl/reference/atl-classes.md)   
 [CWorkerThread 类](../../atl/reference/cworkerthread-class.md)
