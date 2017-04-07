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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 1de883341e0a53a1520fa44d99e7907ee1fe10b6
ms.lasthandoff: 03/31/2017

---
# <a name="cdebugreporthook-class"></a>CDebugReportHook 类
使用此类将调试报告发送到命名管道。  
  
## <a name="syntax"></a>语法  
  
```
class CDebugReportHook
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|调用[SetPipeName](#setpipename)， [SetTimeout](#settimeout)，和[SetHook](#sethook)。|  
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|调用[CDebugReportHook::RemoveHook](#removehook)。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|（静态）挂钩到 C 运行时自定义报告函数调试报告过程。|  
|[CDebugReportHook::RemoveHook](#removehook)|调用此方法来停止调试报告发送给命名管道和还原以前的报告挂钩。|  
|[CDebugReportHook::SetHook](#sethook)|调用此方法来启动调试报告发送给命名管道。|  
|[CDebugReportHook::SetPipeName](#setpipename)|调用此方法以设置的计算机和调试报表将发送到管道名称。|  
|[CDebugReportHook::SetTimeout](#settimeout)|调用此方法以设置中此类将等待可用的命名管道的毫秒的时间。|  
  
## <a name="remarks"></a>备注  
 在你的服务或应用程序将调试报告发送到命名管道的调试版本中创建此类的实例。 调试报告生成通过调用[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)或使用此函数包装，如[ATLTRACE](debugging-and-error-reporting-macros.md#atltrace)和[ATLASSERT](debugging-and-error-reporting-macros.md#atlassert)宏。  
  
 使用此类允许你以交互方式调试运行非交互的组件[窗口工作站](http://msdn.microsoft.com/library/windows/desktop/ms687096)。  
  
 请注意调试报告发送使用线程的基础安全上下文。 模拟暂时被禁用，这样在低权限用户的模拟发生，如在 web 应用程序的情况下，可以查看调试报告。  
  
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
 应该发送调试输出的命名管道的名称。  
  
 `dwTimeout`  
 时间 （毫秒） 此类将等待可用的命名管道。  
  
##  <a name="dtor"></a>CDebugReportHook:: ~ CDebugReportHook  
 调用[CDebugReportHook::RemoveHook](#removehook)。  
  
```
~CDebugReportHook() throw();
```  
  
##  <a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc  
 挂钩到 C 运行时自定义报告函数调试报告过程。  
  
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
 应通过返回的值[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)。  
  
### <a name="return-value"></a>返回值  
 如果挂钩完全处理了所涉及的消息以便不执行进一步的报告要求，则返回 FALSE。 如果返回 TRUE`_CrtDbgReport`应以正常方式报告消息。  
  
### <a name="remarks"></a>备注  
 报告函数尝试打开的命名的管道并与另一端进程通信。 如果管道正忙，报告的函数将等待，直到管道可用或在超时到期。 可以通过构造函数或调用设置超时[CDebugReportHook::SetTimeout](#settimeout)。  
  
 在调用线程的基础安全上下文中执行此函数中的代码，即，模拟如何根据此函数的持续时间处于禁用状态。  
  
##  <a name="removehook"></a>CDebugReportHook::RemoveHook  
 调用此方法来停止调试报告发送给命名管道和还原以前的报告挂钩。  
  
```
void RemoveHook() throw();
```  
  
### <a name="remarks"></a>备注  
 调用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)还原以前的报告挂钩。  
  
##  <a name="sethook"></a>CDebugReportHook::SetHook  
 调用此方法来启动调试报告发送给命名管道。  
  
```
void SetHook() throw();
```  
  
### <a name="remarks"></a>备注  
 调用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)得到调试报告通过路由[CDebugReportHookProc](#cdebugreporthookproc)到命名管道。 此类用于跟踪的以前的报告挂钩，以便它可以是还原时[RemoveHook](#removehook)调用。  
  
##  <a name="setpipename"></a>CDebugReportHook::SetPipeName  
 调用此方法以设置的计算机和调试报表将发送到管道名称。  
  
```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```  
  
### <a name="parameters"></a>参数  
 `szMachineName`  
 调试输出应发送到计算机的名称。  
  
 `szPipeName`  
 应该发送调试输出的命名管道的名称。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
##  <a name="settimeout"></a>CDebugReportHook::SetTimeout  
 调用此方法以设置中此类将等待可用的命名管道的毫秒的时间。  
  
```
void SetTimeout(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>参数  
 `dwTimeout`  
 时间 （毫秒） 此类将等待可用的命名管道。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../atl/reference/atl-classes.md)

