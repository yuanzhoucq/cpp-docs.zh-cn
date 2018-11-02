---
title: CAtlServiceModuleT 类
ms.date: 11/04/2016
f1_keywords:
- CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::Handler
- ATLBASE/ATL::CAtlServiceModuleT::InitializeSecurity
- ATLBASE/ATL::CAtlServiceModuleT::Install
- ATLBASE/ATL::CAtlServiceModuleT::IsInstalled
- ATLBASE/ATL::CAtlServiceModuleT::LogEvent
- ATLBASE/ATL::CAtlServiceModuleT::OnContinue
- ATLBASE/ATL::CAtlServiceModuleT::OnInterrogate
- ATLBASE/ATL::CAtlServiceModuleT::OnPause
- ATLBASE/ATL::CAtlServiceModuleT::OnShutdown
- ATLBASE/ATL::CAtlServiceModuleT::OnStop
- ATLBASE/ATL::CAtlServiceModuleT::OnUnknownRequest
- ATLBASE/ATL::CAtlServiceModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlServiceModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlServiceModuleT::RegisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::Run
- ATLBASE/ATL::CAtlServiceModuleT::ServiceMain
- ATLBASE/ATL::CAtlServiceModuleT::SetServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::Start
- ATLBASE/ATL::CAtlServiceModuleT::Uninstall
- ATLBASE/ATL::CAtlServiceModuleT::Unlock
- ATLBASE/ATL::CAtlServiceModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::WinMain
- ATLBASE/ATL::CAtlServiceModuleT::m_bService
- ATLBASE/ATL::CAtlServiceModuleT::m_dwThreadID
- ATLBASE/ATL::CAtlServiceModuleT::m_hServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::m_status
- ATLBASE/ATL::CAtlServiceModuleT::m_szServiceName
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
ms.openlocfilehash: b577ee002e34fa051b6e1dd5ffca71f935d93433
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619136"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT 类

此类实现一种服务。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类派生自`CAtlServiceModuleT`。

*nServiceNameID*<br/>
服务的资源标识符。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[Catlservicemodulet:: Handler](#handler)|该服务处理程序例程。|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|提供了默认的服务的安全设置。|
|[CAtlServiceModuleT::Install](#install)|安装和创建服务。|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|确认已安装了服务。|
|[CAtlServiceModuleT::LogEvent](#logevent)|写入事件日志。|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|重写此方法以继续该服务。|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|重写此方法以询问该服务。|
|[CAtlServiceModuleT::OnPause](#onpause)|重写此方法可以暂停服务。|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|重写此方法以关闭服务|
|[CAtlServiceModuleT::OnStop](#onstop)|重写此方法以停止服务|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|重写此方法以处理未知的服务请求|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|分析命令行，并根据需要执行注册。|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|输入消息循环之前调用此方法。|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|在注册表中注册该服务。|
|[Catlservicemodulet:: Run](#run)|运行服务。|
|[Catlservicemodulet:: Servicemain](#servicemain)|调用服务控制管理器的方法。|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|更新服务状态。|
|[Catlservicemodulet:: Start](#start)|由调用`CAtlServiceModuleT::WinMain`服务启动时。|
|[CAtlServiceModuleT::Uninstall](#uninstall)|停止并删除该服务。|
|[CAtlServiceModuleT::Unlock](#unlock)|服务的锁计数递减。|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|从注册表中删除该服务。|
|[CAtlServiceModuleT::WinMain](#winmain)|此方法实现来运行服务所需的代码。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|指示作为服务运行该程序的标记。|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|成员变量存储线程标识符。|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|存储的句柄当前服务的状态信息结构的成员变量。|
|[CAtlServiceModuleT::m_status](#m_status)|存储当前服务的状态信息结构的成员变量。|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|正在注册的服务的名称。|

## <a name="remarks"></a>备注

`CAtlServiceModuleT`派生自[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)，实现 ATL 服务模块。 `CAtlServiceModuleT` 提供用于命令行处理、 安装、 注册和删除方法。 如果需要额外的功能，可以重写这些方法和其他方法。

此类替换已过时[CComModule 类](../../atl/reference/ccommodule-class.md)使用在早期版本的 atl。 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="catlservicemodulet"></a>  CAtlServiceModuleT::CAtlServiceModuleT

构造函数。

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>备注

初始化数据成员并设置初始服务状态。

##  <a name="handler"></a>  Catlservicemodulet:: Handler

该服务处理程序例程。

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>参数

*dwOpcode*<br/>
可定义处理程序操作的开关。 有关详细信息，请参阅备注。

### <a name="remarks"></a>备注

这是服务控制管理器 (SCM) 调用来检索状态的服务和问题的说明，例如停止或暂停的代码。 SCM 将传递一个操作代码，如下所示，为`Handler`以指示服务应执行的操作。

|操作代码|含义|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|停止服务。 重写方法[CAtlServiceModuleT::OnStop](#onstop)中 atlbase.h 更改的行为。|
|SERVICE_CONTROL_PAUSE|实现的用户。 重写空方法[CAtlServiceModuleT::OnPause](#onpause) atlbase.h 暂停该服务中。|
|SERVICE_CONTROL_CONTINUE|实现的用户。 重写空方法[CAtlServiceModuleT::OnContinue](#oncontinue) atlbase.h 来继续该服务中。|
|SERVICE_CONTROL_INTERROGATE|实现的用户。 重写空方法[CAtlServiceModuleT::OnInterrogate](#oninterrogate) atlbase.h 以便询问服务中。|
|SERVICE_CONTROL_SHUTDOWN|实现的用户。 重写空方法[CAtlServiceModuleT::OnShutdown](#onshutdown)中 atlbase.h 到关闭服务。|

如果无法识别操作代码，该方法[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)调用。

默认 ATL 生成服务仅处理停止指令。 如果 SCM 通过 stop 指令，则服务将通知 SCM 程序即将停止。 然后，该服务调用`PostThreadMessage`来发送退出的消息到其自身。 这将终止消息循环，并最终将关闭该服务。

##  <a name="initializesecurity"></a>  CAtlServiceModuleT::InitializeSecurity

提供了默认的服务的安全设置。

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

在 Visual Studio.NET 2003 中，此方法未实现基类中。 Visual Studio 项目向导生成的代码中包括此方法，但如果使用 ATL 7.1 编译 Visual c + + 的早期版本中创建的项目将出现编译错误。 从派生的任何类`CAtlServiceModuleT`必须在派生类中实现此方法。

在调用中使用 PKT 级别身份验证、 RPC_C_IMP_LEVEL_IDENTIFY 的模拟级别和相应的非 null 安全描述符`CoInitializeSecurity`。

对于向导生成非属性化的服务项目，这将是在

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

对于特性化的服务项目，这将是在

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>  CAtlServiceModuleT::Install

安装和创建服务。

```
BOOL Install() throw();
```

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

安装服务到服务控制管理器 (SCM) 数据库，并创建服务对象。 如果无法创建该服务，显示一个消息框，该方法返回 FALSE。

##  <a name="isinstalled"></a>  CAtlServiceModuleT::IsInstalled

确认已安装了服务。

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>返回值

如果该服务不安装，则为 FALSE，则返回 TRUE。

##  <a name="logevent"></a>  CAtlServiceModuleT::LogEvent

写入事件日志。

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>参数

*pszFormat*<br/>
要写入事件日志的字符串。

*...*<br/>
可选的额外字符串写入到事件日志。

### <a name="remarks"></a>备注

此方法写出到事件日志，使用该函数的详细信息[ReportEvent](/windows/desktop/api/winbase/nf-winbase-reporteventa)。 如果没有服务正在运行，则将字符串发送到控制台。

##  <a name="m_bservice"></a>  CAtlServiceModuleT::m_bService

指示作为服务运行该程序的标记。

```
BOOL m_bService;
```

### <a name="remarks"></a>备注

用于从应用程序 EXE 区分服务 EXE。

##  <a name="m_dwthreadid"></a>  CAtlServiceModuleT::m_dwThreadID

存储服务的线程标识符的成员变量。

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>备注

此变量存储当前线程的线程标识符。

##  <a name="m_hservicestatus"></a>  CAtlServiceModuleT::m_hServiceStatus

存储的句柄当前服务的状态信息结构的成员变量。

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>备注

[SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status)结构包含有关服务的信息。

##  <a name="m_status"></a>  CAtlServiceModuleT::m_status

存储当前服务的状态信息结构的成员变量。

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>备注

[SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status)结构包含有关服务的信息。

##  <a name="m_szservicename"></a>  CAtlServiceModuleT::m_szServiceName

正在注册的服务的名称。

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>备注

以 null 结尾的字符串将存储服务的名称。

##  <a name="oncontinue"></a>  CAtlServiceModuleT::OnContinue

重写此方法以继续该服务。

```
void OnContinue() throw();
```

##  <a name="oninterrogate"></a>  CAtlServiceModuleT::OnInterrogate

重写此方法以询问该服务。

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>  CAtlServiceModuleT::OnPause

重写此方法可以暂停服务。

```
void OnPause() throw();
```

##  <a name="onshutdown"></a>  CAtlServiceModuleT::OnShutdown

重写此方法以关闭服务。

```
void OnShutdown() throw();
```

##  <a name="onstop"></a>  CAtlServiceModuleT::OnStop

重写此方法以停止服务。

```
void OnStop() throw();
```

##  <a name="onunknownrequest"></a>  CAtlServiceModuleT::OnUnknownRequest

重写此方法以处理未知的服务请求。

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>参数

*dwOpcode*<br/>
保留。

##  <a name="parsecommandline"></a>  CAtlServiceModuleT::ParseCommandLine

分析命令行，并根据需要执行注册。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>参数

*lpCmdLine*<br/>
命令行。

*pnRetCode*<br/>
（如果发生） 与注册相对应的 HRESULT。

### <a name="return-value"></a>返回值

成功，则无法注册命令行中提供的 RGS 文件否则，false 则返回 true。

### <a name="remarks"></a>备注

分析命令行和注册或注销提供的 RGS 文件，如有必要。 此方法调用[CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline)检查 **/RegServer**并 **/UnregServer**。 与参数相加 **-/ 服务**将注册该服务。

##  <a name="premessageloop"></a>  CAtlServiceModuleT::PreMessageLoop

输入消息循环之前调用此方法。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
此参数传递给[CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop)。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

重写此方法可为服务添加自定义初始化代码。

##  <a name="registerappid"></a>  CAtlServiceModuleT::RegisterAppId

在注册表中注册该服务。

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>参数

*bService*<br/>
必须为 true，则注册为服务。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="run"></a>  Catlservicemodulet:: Run

运行服务。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是讨论中的值之一[WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559)部分。 默认值为 SW_HIDE。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

被调用后`Run`调用[CAtlServiceModuleT::PreMessageLoop](#premessageloop)， [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)，并[CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

##  <a name="servicemain"></a>  Catlservicemodulet:: Servicemain

此方法称为服务控制管理器。

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>参数

*dwArgc*<br/>
Argc 自变量。

*lpszArgv*<br/>
Argv 自变量。

### <a name="remarks"></a>备注

服务控制管理器 (SCM) 调用`ServiceMain`时在控制面板中打开服务应用程序，请选择该服务，并单击开始。

SCM 后，将调用`ServiceMain`，服务必须为 SCM 提供处理程序函数。 此函数允许 SCM 获得服务的状态并传递 （例如暂停或停止） 的具体说明。 随后， [catlservicemodulet:: Run](#run)调用来执行该服务的主要工作。 `Run` 继续执行，直到该服务已停止。

##  <a name="setservicestatus"></a>  CAtlServiceModuleT::SetServiceStatus

此方法更新服务状态。

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>参数

*dwState*<br/>
新的状态。 请参阅[SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)有关可能的值。

### <a name="remarks"></a>备注

更新服务的服务控制管理器的状态信息。 调用[catlservicemodulet:: Run](#run)， [catlservicemodulet:: Servicemain](#servicemain)和其他处理程序方法。 状态也存储在成员变量[CAtlServiceModuleT::m_status](#m_status)。

##  <a name="start"></a>  Catlservicemodulet:: Start

由调用`CAtlServiceModuleT::WinMain`服务启动时。

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是讨论中的值之一[WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559)部分。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

[CAtlServiceModuleT::WinMain](#winmain)方法处理注册和安装，以及任务涉及删除注册表项和卸载模块。 当运行该服务时，`WinMain`调用`Start`。

##  <a name="uninstall"></a>  CAtlServiceModuleT::Uninstall

停止并删除该服务。

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

停止运行服务，并从服务控制管理器数据库中删除它。

##  <a name="unlock"></a>  CAtlServiceModuleT::Unlock

服务的锁计数递减。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>返回值

返回的锁计数，这可能是有用的诊断和调试。

##  <a name="unregisterappid"></a>  CAtlServiceModuleT::UnregisterAppId

从注册表中删除该服务。

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="winmain"></a>  CAtlServiceModuleT::WinMain

此方法实现所需启动该服务的代码。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是讨论中的值之一[WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559)部分。

### <a name="return-value"></a>返回值

返回服务的返回值。

### <a name="remarks"></a>备注

此方法处理命令行 (与[CAtlServiceModuleT::ParseCommandLine](#parsecommandline))，然后启动该服务 (使用[catlservicemodulet:: Start](#start))。

## <a name="see-also"></a>请参阅

[CAtlExeModuleT 类](../../atl/reference/catlexemodulet-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
