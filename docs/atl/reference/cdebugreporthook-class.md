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
ms.openlocfilehash: 7187448b2ba2c9d3ab0399aa3e75ce8d757bfec1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496773"
---
# <a name="cdebugreporthook-class"></a>CDebugReportHook 类

使用此类可将调试报告发送到命名管道。

## <a name="syntax"></a>语法

```
class CDebugReportHook
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|调用[SetPipeName](#setpipename)、 [SetTimeout](#settimeout)和[SetHook](#sethook)。|
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|调用[CDebugReportHook:: RemoveHook](#removehook)。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|静止挂接到 C 运行时调试报告过程中的自定义报告函数。|
|[CDebugReportHook::RemoveHook](#removehook)|调用此方法以停止将调试报告发送到命名管道并还原上一个报表挂钩。|
|[CDebugReportHook::SetHook](#sethook)|调用此方法可开始将调试报告发送到命名管道。|
|[CDebugReportHook::SetPipeName](#setpipename)|调用此方法可设置要将调试报告发送到的管道的计算机和名称。|
|[CDebugReportHook::SetTimeout](#settimeout)|调用此方法可设置此类等待命名管道变为可用的时间 (以毫秒为单位)。|

## <a name="remarks"></a>备注

在服务或应用程序的调试版本中创建此类的实例, 以将调试报告发送到命名管道。 调试报表是通过调用[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)或为此函数使用包装 (如[ATLTRACE](debugging-and-error-reporting-macros.md#atltrace)和[ATLASSERT](debugging-and-error-reporting-macros.md#atlassert)宏) 生成的。

使用此类可以以交互方式调试在非交互式[窗口工作站](/windows/win32/winstation/window-stations)中运行的组件。

请注意, 调试报表是使用线程的基础安全上下文发送的。 暂时禁用模拟, 以便在模拟低特权用户发生的情况下 (例如在 web 应用程序中) 查看调试报告。

## <a name="requirements"></a>要求

**标头:** atlutil

##  <a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook

调用[SetPipeName](#setpipename)、 [SetTimeout](#settimeout)和[SetHook](#sethook)。

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>参数

*szMachineName*<br/>
调试输出应发送到的计算机的名称。 默认为本地计算机。

*szPipeName*<br/>
调试输出应发送到的命名管道的名称。

*dwTimeout*<br/>
此类等待命名管道变为可用的时间 (以毫秒为单位)。

##  <a name="dtor"></a>CDebugReportHook:: ~ CDebugReportHook

调用[CDebugReportHook:: RemoveHook](#removehook)。

```
~CDebugReportHook() throw();
```

##  <a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc

挂接到 C 运行时调试报告过程中的自定义报告函数。

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>参数

*reportType*<br/>
报表的类型 (_CRT_WARN、_CRT_ERROR 或 _CRT_ASSERT)。

*message*<br/>
消息字符串。

*returnValue*<br/>
应由[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)返回的值。

### <a name="return-value"></a>返回值

如果挂钩完全处理所涉及的消息, 以便不需要进一步报告, 则返回 FALSE。 如果`_CrtDbgReport`应以正常方式报告消息, 则返回 TRUE。

### <a name="remarks"></a>备注

报表函数尝试打开命名管道, 并与另一端的进程进行通信。 如果管道处于繁忙状态, 则报告函数将等待, 直到管道空闲或超时过期。 可以通过构造函数或对[CDebugReportHook:: SetTimeout](#settimeout)的调用来设置超时。

此函数中的代码在调用线程的基础安全上下文中执行, 也就是说, 在此函数的持续时间内禁用模拟。

##  <a name="removehook"></a>CDebugReportHook::RemoveHook

调用此方法以停止将调试报告发送到命名管道并还原上一个报表挂钩。

```
void RemoveHook() throw();
```

### <a name="remarks"></a>备注

调用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)来还原以前的报表挂钩。

##  <a name="sethook"></a>CDebugReportHook::SetHook

调用此方法可开始将调试报告发送到命名管道。

```
void SetHook() throw();
```

### <a name="remarks"></a>备注

调用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) , 将调试报表通过[CDebugReportHookProc](#cdebugreporthookproc)路由到命名管道。 此类跟踪上一报表挂钩, 以便可以在调用[RemoveHook](#removehook)时还原。

##  <a name="setpipename"></a>CDebugReportHook::SetPipeName

调用此方法可设置要将调试报告发送到的管道的计算机和名称。

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>参数

*szMachineName*<br/>
调试输出应发送到的计算机的名称。

*szPipeName*<br/>
调试输出应发送到的命名管道的名称。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

##  <a name="settimeout"></a>CDebugReportHook:: SetTimeout

调用此方法可设置此类等待命名管道变为可用的时间 (以毫秒为单位)。

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>参数

*dwTimeout*<br/>
此类等待命名管道变为可用的时间 (以毫秒为单位)。

## <a name="see-also"></a>请参阅

[类](../../atl/reference/atl-classes.md)
