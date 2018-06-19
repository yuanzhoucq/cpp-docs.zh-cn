---
title: CRTThreadTraits 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
dev_langs:
- C++
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f08f0d6ea57aa5a153d190b357785911e64d6f09
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358161"
---
# <a name="crtthreadtraits-class"></a>CRTThreadTraits 类
此类提供了 CRT 线程创建函数。 如果线程将使用的 CRT 函数，请使用此类。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CRTThreadTraits
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRTThreadTraits::CreateThread](#createthread)|（静态）调用此函数可创建一个可以使用的 CRT 函数的线程。|  
  
## <a name="remarks"></a>备注  
 线程特征是线程的为特定类型提供创建函数的类。 创建函数将具有与 Windows 相同的签名和语义[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)函数。  
  
 由以下类使用线程特征：  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 如果未将使用线程的 CRT 函数，使用[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)相反。  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
##  <a name="createthread"></a>  CRTThreadTraits::CreateThread  
 调用此函数可创建一个可以使用的 CRT 函数的线程。  
  
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
  
 此函数将调用[_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)创建的线程。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
