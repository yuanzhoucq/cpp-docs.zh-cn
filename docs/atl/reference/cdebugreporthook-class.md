---
title: "CDebugReportHook 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
caps.latest.revision: 22
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
ms.openlocfilehash: 632167d4f78ef930673450d6d087f32e91b6541f
ms.lasthandoff: 02/24/2017

---
# <a name="cdebugreporthook-class"></a>CDebugReportHook 类
使用此类将调试报告发送到命名管道。  
  
## <a name="syntax"></a>语法  
  
```
class CDebugReportHook
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|调用[SetPipeName](#setpipename)， [SetTimeout](#settimeout)，和[SetHook](#sethook)。|  
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|调用[CDebugReportHook::RemoveHook](#removehook)。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|（静态）挂接到 C 运行时调试报告过程自定义报告函数。|  
|[CDebugReportHook::RemoveHook](#removehook)|调用此方法来停止调试报告发送给命名管道和还原以前的报告挂钩。|  
|[CDebugReportHook::SetHook](#sethook)|调用此方法中开始调试报告发送到命名管道。|  
|[CDebugReportHook::SetPipeName](#setpipename)|调用此方法来设置计算机和调试报告将发送到管道名称。|  
|[CDebugReportHook::SetTimeout](#settimeout)|调用此方法可设置的时间以毫秒为单位的此类将等待变得可用的命名管道。|  
  
## <a name="remarks"></a>备注  
 在您的服务或应用程序将调试报告发送到命名管道的调试版本中创建此类的实例。 调试报告都由调用[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)或如使用此函数的包装器[ATLTRACE](http://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e)和[ATLASSERT](http://msdn.microsoft.com/library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3)宏。  
  
 使用此类允许您以交互方式调试运行非交互的组件[窗口站](http://msdn.microsoft.com/library/windows/desktop/ms687096)。  
  
 请注意，使用该线程的基础安全上下文发送调试报告。 模拟被暂时禁用，以便可以在其中的低特权用户的模拟正在进行，如在 web 应用程序的情况下查看调试报告。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlutil.h  
  
##  <a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook  
 调用[SetPipeName](#setpipename)， [SetTimeout](#settimeout)，和[SetHook](#sethook)。  
  
```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```  
  
### <a name="parameters"></a>参数  
 `szMachineName`  
 调试输出应发送到计算机的名称。 默认值为本地计算机。  
  
 `szPipeName`  
 调试输出应发送到的命名管道的名称。  
  
 `dwTimeout`  
 时间 （毫秒） 此类将等待变得可用的命名管道。  
  
##  <a name="dtor"></a>CDebugReportHook:: ~ CDebugReportHook  
 调用[CDebugReportHook::RemoveHook](#removehook)。  
  
```
~CDebugReportHook() throw();
```  
  
##  <a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc  
 挂接到 C 运行时调试报告过程自定义报告函数。  
  
```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```  
  
### <a name="parameters"></a>参数  
 `reportType`  
 报表 （_CRT_WARN、 _CRT_ERROR 或 _CRT_ASSERT） 的类型。  
  
 `message`  
 消息字符串中。  
  
 *returnValue*  
 应由返回的值[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)。  
  
### <a name="return-value"></a>返回值  
 如果挂钩完全处理了所讨论的消息，以便不执行进一步的报告是必需，则返回 FALSE。 如果返回 TRUE`_CrtDbgReport`应以正常方式报告消息。  
  
### <a name="remarks"></a>备注  
 报告函数尝试打开命名的管道，并与另一端进程进行通信。 如果管道繁忙，管道可用，或在超时到期之前将等待报告函数。 可以通过构造函数或调用设置超时[CDebugReportHook::SetTimeout](#settimeout)。  
  
 调用线程的基础安全上下文中执行此函数中的代码，也就是说，此函数的持续时间内禁用模拟。  
  
##  <a name="removehook"></a>CDebugReportHook::RemoveHook  
 调用此方法来停止调试报告发送给命名管道和还原以前的报告挂钩。  
  
```
void RemoveHook() throw();
```  
  
### <a name="remarks"></a>备注  
 调用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)若要还原以前的报告挂钩。  
  
##  <a name="sethook"></a>CDebugReportHook::SetHook  
 调用此方法中开始调试报告发送到命名管道。  
  
```
void SetHook() throw();
```  
  
### <a name="remarks"></a>备注  
 调用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)将调试报告通过路由[CDebugReportHookProc](#cdebugreporthookproc)到命名管道。 此类跟踪的以前的报告挂钩，因此它可以是还原时[RemoveHook](#removehook)调用。  
  
##  <a name="setpipename"></a>CDebugReportHook::SetPipeName  
 调用此方法来设置计算机和调试报告将发送到管道名称。  
  
```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```  
  
### <a name="parameters"></a>参数  
 `szMachineName`  
 调试输出应发送到计算机的名称。  
  
 `szPipeName`  
 调试输出应发送到的命名管道的名称。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
##  <a name="settimeout"></a>CDebugReportHook::SetTimeout  
 调用此方法可设置的时间以毫秒为单位的此类将等待变得可用的命名管道。  
  
```
void SetTimeout(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>参数  
 `dwTimeout`  
 时间 （毫秒） 此类将等待变得可用的命名管道。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../atl/reference/atl-classes.md)

