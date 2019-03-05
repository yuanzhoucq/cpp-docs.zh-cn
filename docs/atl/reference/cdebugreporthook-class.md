---
title: CDebugReportHook 类
ms.date: 11/04/2016
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
ms.openlocfilehash: a7c5993d1b96daaa73e7fc9509c93e66daed77f3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262449"
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
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|调用[SetPipeName](#setpipename)， [SetTimeout](#settimeout)，并[SetHook](#sethook)。|
|[CDebugReportHook::~CDebugReportHook](#dtor)|调用[CDebugReportHook::RemoveHook](#removehook)。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|（静态）挂钩到 C 运行时调试报告过程自定义报告函数。|
|[CDebugReportHook::RemoveHook](#removehook)|调用此方法以停止调试报告发送给命名管道和还原以前的报告挂钩。|
|[CDebugReportHook::SetHook](#sethook)|调用此方法来启动调试报告发送给命名管道。|
|[CDebugReportHook::SetPipeName](#setpipename)|调用此方法来设置计算机和调试报表将发送到管道的名称。|
|[CDebugReportHook::SetTimeout](#settimeout)|调用此方法可设置的时间以毫秒为单位，此类将等待可用的命名管道。|

## <a name="remarks"></a>备注

在你的服务或应用程序将调试报告发送到命名管道的调试版本中创建此类的实例。 通过调用生成调试报告[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)或使用此函数的包装器，如[ATLTRACE](debugging-and-error-reporting-macros.md#atltrace)并[ATLASSERT](debugging-and-error-reporting-macros.md#atlassert)宏。

使用此类允许您以交互方式调试组件运行非交互式[窗口站](/windows/desktop/winstation/window-stations)。

请注意调试报告发送使用的线程的基础安全上下文。 模拟暂时禁用状态，以便可以在其中的低特权用户的模拟正在进行，如在 web 应用程序的情况下查看调试报告。

## <a name="requirements"></a>要求

**标头：** atlutil.h

##  <a name="cdebugreporthook"></a>  CDebugReportHook::CDebugReportHook

调用[SetPipeName](#setpipename)， [SetTimeout](#settimeout)，并[SetHook](#sethook)。

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>参数

*szMachineName*<br/>
调试输出应发送到计算机的名称。 默认值为本地计算机。

*szPipeName*<br/>
调试输出应发送到的命名管道的名称。

*dwTimeout*<br/>
以毫秒为单位，此类将变得可用的命名管道等待时间。

##  <a name="dtor"></a>  CDebugReportHook:: ~ CDebugReportHook

调用[CDebugReportHook::RemoveHook](#removehook)。

```
~CDebugReportHook() throw();
```

##  <a name="cdebugreporthookproc"></a>  CDebugReportHook::CDebugReportHookProc

挂钩到 C 运行时调试报告过程自定义报告函数。

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>参数

*reportType*<br/>
报表 （_CRT_WARN、 _CRT_ERROR 或 _CRT_ASSERT） 的类型。

*message*<br/>
消息字符串中。

*returnValue*<br/>
应由返回的值[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)。

### <a name="return-value"></a>返回值

如果挂钩完全处理了所涉及的消息，以便无报告是必需，则返回 FALSE。 返回 true; 否则`_CrtDbgReport`应以正常方式报告消息。

### <a name="remarks"></a>备注

报表函数尝试打开命名的管道，并与另一端进程进行通信。 如果管道繁忙，报告的函数将等待，直到管道可用或在超时过期。 可以通过构造函数或调用设置超时[CDebugReportHook::SetTimeout](#settimeout)。

调用线程的基础安全上下文中执行此函数中的代码，也就是说，此函数的持续时间内禁用模拟。

##  <a name="removehook"></a>  CDebugReportHook::RemoveHook

调用此方法以停止调试报告发送给命名管道和还原以前的报告挂钩。

```
void RemoveHook() throw();
```

### <a name="remarks"></a>备注

调用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)还原以前的报告挂钩。

##  <a name="sethook"></a>  CDebugReportHook::SetHook

调用此方法来启动调试报告发送给命名管道。

```
void SetHook() throw();
```

### <a name="remarks"></a>备注

调用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)能够调试报表通过路由[CDebugReportHookProc](#cdebugreporthookproc)到命名管道。 此类跟踪的以前的报告挂钩，以便它可以还原何时[RemoveHook](#removehook)调用。

##  <a name="setpipename"></a>  CDebugReportHook::SetPipeName

调用此方法来设置计算机和调试报表将发送到管道的名称。

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>参数

*szMachineName*<br/>
调试输出应发送到计算机的名称。

*szPipeName*<br/>
调试输出应发送到的命名管道的名称。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

##  <a name="settimeout"></a>  CDebugReportHook::SetTimeout

调用此方法可设置的时间以毫秒为单位，此类将等待可用的命名管道。

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>参数

*dwTimeout*<br/>
以毫秒为单位，此类将变得可用的命名管道等待时间。

## <a name="see-also"></a>请参阅

[类](../../atl/reference/atl-classes.md)
