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
ms.openlocfilehash: 621d32a14618327873e6e0cce856c5792e1f8c46
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327113"
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
|[C调试报告钩：：C调试报告钩](#cdebugreporthook)|调用[设置管道名称](#setpipename)、[设置超时](#settimeout)和设置[Hook](#sethook)。|
|[C调试报告钩：*C调试报告钩](#dtor)|调用[CDebug 报告钩：：删除胡克](#removehook)。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C调试报告钩：：C调试报告胡克](#cdebugreporthookproc)|（静态）挂接到 C 运行时调试报告流程的自定义报告函数。|
|[CDebug报告钩：：删除胡克](#removehook)|调用此方法停止向命名管道发送调试报告并还原上一个报表挂钩。|
|[CDebug报告钩：：设置胡克](#sethook)|调用此方法开始向命名管道发送调试报告。|
|[CDebug 报告钩：：设置管道名称](#setpipename)|调用此方法以设置将调试报告发送到的管道的计算机和名称。|
|[CDebug 报告钩：设置超时](#settimeout)|调用此方法以设置此类将等待命名管道变为可用的时间（以毫秒为单位）。|

## <a name="remarks"></a>备注

在服务或应用程序的调试版本中创建此类的实例，以将调试报告发送到命名管道。 调试报告是通过调用[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)或使用包装器来生成此函数（如[ATLTRACE](debugging-and-error-reporting-macros.md#atltrace)和[ATLASSERT](debugging-and-error-reporting-macros.md#atlassert)宏）。

使用此类允许您以交互方式调试在非交互式[窗口站](/windows/win32/winstation/window-stations)中运行的组件。

请注意，调试报告是使用线程的基础安全上下文发送的。 临时禁用模拟，以便在正在模拟低特权用户的情况下（如 Web 应用程序中）查看调试报告。

## <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="cdebugreporthookcdebugreporthook"></a><a name="cdebugreporthook"></a>C调试报告钩：：C调试报告钩

调用[设置管道名称](#setpipename)、[设置超时](#settimeout)和设置[Hook](#sethook)。

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>参数

*szMachine名称*<br/>
应向其发送调试输出的计算机的名称。 默认值为本地计算机。

*szPipe名称*<br/>
应向其发送调试输出的命名管道的名称。

*dwTimeout*<br/>
此类将等待命名管道变为可用的时间（以毫秒为单位）。

## <a name="cdebugreporthookcdebugreporthook"></a><a name="dtor"></a>C调试报告钩：*C调试报告钩

调用[CDebug 报告钩：：删除胡克](#removehook)。

```
~CDebugReportHook() throw();
```

## <a name="cdebugreporthookcdebugreporthookproc"></a><a name="cdebugreporthookproc"></a>C调试报告钩：：C调试报告胡克

挂接到 C 运行时调试报告流程的自定义报告函数。

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>参数

*报表类型*<br/>
报表的类型（_CRT_WARN、_CRT_ERROR 或_CRT_ASSERT）。

*消息*<br/>
message 字符串。

*返回值*<br/>
应由[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)返回的值。

### <a name="return-value"></a>返回值

如果挂钩完全处理有问题的消息，则返回 FALSE，以便无需进一步报告。 返回 TRUE，如果`_CrtDbgReport`要以正常方式报告消息。

### <a name="remarks"></a>备注

报告函数尝试打开命名管道，并在另一端与进程通信。 如果管道繁忙，报告功能将等待管道空闲或超时过期。 超时可以由构造函数设置，也可以由[CDebug 报告Hook 的调用设置：设置超时](#settimeout)。

此函数中的代码在调用线程的基础安全上下文中执行，也就是说，在此函数的持续时间内禁用模拟。

## <a name="cdebugreporthookremovehook"></a><a name="removehook"></a>CDebug报告钩：：删除胡克

调用此方法停止向命名管道发送调试报告并还原上一个报表挂钩。

```
void RemoveHook() throw();
```

### <a name="remarks"></a>备注

调用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)以还原上一个报表挂钩。

## <a name="cdebugreporthooksethook"></a><a name="sethook"></a>CDebug报告钩：：设置胡克

调用此方法开始向命名管道发送调试报告。

```
void SetHook() throw();
```

### <a name="remarks"></a>备注

调用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)通过[CDebugReportHookProc](#cdebugreporthookproc)路由调试报告到命名管道。 此类跟踪上一个报表挂钩，以便在调用[RemoveHook](#removehook)时还原它。

## <a name="cdebugreporthooksetpipename"></a><a name="setpipename"></a>CDebug 报告钩：：设置管道名称

调用此方法以设置将调试报告发送到的管道的计算机和名称。

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>参数

*szMachine名称*<br/>
应向其发送调试输出的计算机的名称。

*szPipe名称*<br/>
应向其发送调试输出的命名管道的名称。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="cdebugreporthooksettimeout"></a><a name="settimeout"></a>CDebug 报告钩：设置超时

调用此方法以设置此类将等待命名管道变为可用的时间（以毫秒为单位）。

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>参数

*dwTimeout*<br/>
此类将等待命名管道变为可用的时间（以毫秒为单位）。

## <a name="see-also"></a>另请参阅

[类](../../atl/reference/atl-classes.md)
