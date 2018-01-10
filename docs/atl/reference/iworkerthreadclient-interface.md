---
title: "IWorkerThreadClient 接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
dev_langs: C++
helpviewer_keywords: IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86b0578b3fbe16d21a12edf2ac5eb91528419e83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient 接口
`IWorkerThreadClient`是的客户端实现的接口[CWorkerThread](../../atl/reference/cworkerthread-class.md)类。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
__interface IWorkerThreadClient
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CloseHandle](#closehandle)|实现此方法来关闭与此对象关联的句柄。|  
|[执行](#execute)|实现此方法可执行代码时与此对象关联的句柄将被发送信号。|  
  
## <a name="remarks"></a>备注  
 当你有需要在响应变得有信号状态的句柄的工作线程上执行的代码，则实现此接口。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlutil.h  
  
##  <a name="closehandle"></a>IWorkerThreadClient::CloseHandle  
 实现此方法来关闭与此对象关联的句柄。  
  
```
HRESULT CloseHandle(HANDLE  hHandle);
```  
  
### <a name="parameters"></a>参数  
 *hHandle*  
 要关闭的句柄。  
  
### <a name="return-value"></a>返回值  
 返回成功，则失败的错误 HRESULT，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 传递给此方法的句柄已以前通过调用与此对象关联[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>示例  
 下面的代码演示的简单实现`IWorkerThreadClient::CloseHandle`。  
  
 [!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]  
  
##  <a name="execute"></a>IWorkerThreadClient::Execute  
 实现此方法可执行代码时与此对象关联的句柄将被发送信号。  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>参数  
 `dwParam`  
 用户参数中。  
  
 `hObject`  
 变为终止状态句柄。  
  
### <a name="return-value"></a>返回值  
 返回成功，则失败的错误 HRESULT，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 以前通过调用与此对象关联的句柄和 DWORD/指针传递给此方法了[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>示例  
 下面的代码演示的简单实现`IWorkerThreadClient::Execute`。  
  
 [!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [类](../../atl/reference/atl-classes.md)   
 [CWorkerThread 类](../../atl/reference/cworkerthread-class.md)
