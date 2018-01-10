---
title: "Win32ThreadTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
dev_langs: C++
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf4fd3ffaf2fc4a035fdecf679ab507ebb557f38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits 类
此类提供了 Windows 线程创建函数。 如果线程将不会使用 CRT 函数，请使用此类。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class Win32ThreadTraits
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Win32ThreadTraits::CreateThread](#createthread)|（静态）调用此函数可创建一个不应使用 CRT 函数的线程。|  
  
## <a name="remarks"></a>备注  
 线程特征是线程的为特定类型提供创建函数的类。 创建函数将具有与 Windows 相同的签名和语义[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)函数。  
  
 由以下类使用线程特征：  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 线程要使用 CRT 函数，如果使用[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)相反。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
##  <a name="createthread"></a>Win32ThreadTraits::CreateThread  
 调用此函数可创建一个不应使用 CRT 函数的线程。  
  
```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpsa`  
 新线程的安全属性。  
  
 `dwStackSize`  
 新线程堆栈大小。  
  
 `pfnThreadProc`  
 新线程的线程的过程。  
  
 `pvParam`  
 要传递给了线程过程的参数。  
  
 `dwCreationFlags`  
 创建标志 （0 个或 CREATE_SUSPENDED）。  
  
 `pdwThreadId`  
 [out]成功时，接收新创建的线程的线程 ID 的 DWORD 变量的地址。  
  
### <a name="return-value"></a>返回值  
 失败时返回的新创建的线程或为 NULL 的句柄。 调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)若要获得扩展的错误信息。  
  
### <a name="remarks"></a>备注  
 请参阅[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)有关对此函数的参数的详细信息。  
  
 此函数将调用`CreateThread`创建的线程。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
