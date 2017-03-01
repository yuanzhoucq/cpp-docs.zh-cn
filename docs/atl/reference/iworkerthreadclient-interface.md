---
title: "IWorkerThreadClient 界面 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IWorkerThreadClient
- ATL::IWorkerThreadClient
- IWorkerThreadClient
dev_langs:
- C++
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 2127d13dc11edb353ef27396f3457dd9abdc4a99
ms.lasthandoff: 02/24/2017

---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient 接口
`IWorkerThreadClient`是由客户端实现的接口[CWorkerThread](../../atl/reference/cworkerthread-class.md)类。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
__interface IWorkerThreadClient
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CloseHandle](#closehandle)|实现此方法以关闭与此对象关联的句柄。|  
|[执行](#execute)|实现此方法时要执行的代码与此对象关联的句柄将被发送信号。|  
  
## <a name="remarks"></a>备注  
 如果要在响应成为发出信号的句柄的工作线程上执行所需的代码，实现此接口。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlutil.h  
  
##  <a name="a-nameclosehandlea--iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::CloseHandle  
 实现此方法以关闭与此对象关联的句柄。  
  
```
HRESULT CloseHandle(HANDLE  hHandle);
```  
  
### <a name="parameters"></a>参数  
 *hHandle*  
 要关闭句柄。  
  
### <a name="return-value"></a>返回值  
 在成功或失败的错误 HRESULT 返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 传递给此方法的句柄是以前通过调用与此对象关联[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>示例  
 下面的代码演示的简单实现`IWorkerThreadClient::CloseHandle`。  
  
 [!code-cpp[NVC_ATL_Utilities #&135;](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]  
  
##  <a name="a-nameexecutea--iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Execute  
 实现此方法时要执行的代码与此对象关联的句柄将被发送信号。  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>参数  
 `dwParam`  
 对 user 参数。  
  
 `hObject`  
 已发送信号的句柄。  
  
### <a name="return-value"></a>返回值  
 在成功或失败的错误 HRESULT 返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 句柄和 DWORD/指针传递给此方法是以前通过调用与此对象关联[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>示例  
 下面的代码演示的简单实现`IWorkerThreadClient::Execute`。  
  
 [!code-cpp[NVC_ATL_Utilities #&136;](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [类](../../atl/reference/atl-classes.md)   
 [CWorkerThread 类](../../atl/reference/cworkerthread-class.md)

