---
title: CAtlServiceModuleT 类
ms.date: 05/06/2019
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
ms.openlocfilehash: 2854d0902700b268383eca094bed35843ea73272
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497735"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT 类

此类实现服务。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`CAtlServiceModuleT`的类。

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
|[CAtlServiceModuleT::Handler](#handler)|服务的处理程序例程。|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|提供服务的默认安全设置。|
|[CAtlServiceModuleT::Install](#install)|安装和创建服务。|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|确认已安装该服务。|
|[CAtlServiceModuleT::LogEvent](#logevent)|写入事件日志。|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|重写此方法以继续服务。|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|重写此方法以询问服务。|
|[CAtlServiceModuleT::OnPause](#onpause)|重写此方法可以暂停服务。|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|重写此方法以关闭服务|
|[CAtlServiceModuleT::OnStop](#onstop)|重写此方法以停止服务|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|重写此方法以处理对服务的未知请求|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|分析命令行并在必要时执行注册。|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|此方法将在进入消息循环前立即调用。|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|在注册表中注册该服务。|
|[CAtlServiceModuleT::Run](#run)|运行该服务。|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|服务控制管理器调用的方法。|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|更新服务状态。|
|[CAtlServiceModuleT::Start](#start)|`CAtlServiceModuleT::WinMain`当服务启动时调用。|
|[CAtlServiceModuleT::Uninstall](#uninstall)|停止并删除服务。|
|[CAtlServiceModuleT::Unlock](#unlock)|减少服务的锁计数。|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|从注册表中删除服务。|
|[CAtlServiceModuleT::WinMain](#winmain)|此方法实现运行服务所需的代码。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|指示程序作为服务运行的标志。|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|存储线程标识符的成员变量。|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|存储当前服务的状态信息结构的句柄的成员变量。|
|[CAtlServiceModuleT::m_status](#m_status)|存储当前服务的状态信息结构的成员变量。|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|正在注册的服务的名称。|

## <a name="remarks"></a>备注

`CAtlServiceModuleT`派生自[catlexemodulet 用作](../../atl/reference/catlexemodulet-class.md)的实现 ATL 服务模块。 `CAtlServiceModuleT`提供用于命令行处理、安装、注册和删除操作的方法。 如果需要额外的功能, 则可以重写这些方法和其他方法。

此类替换在早期版本的 ATL 中使用的过时[CComModule 类](../../atl/reference/ccommodule-class.md)。 有关更多详细信息, 请参阅[ATL Module 类](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>要求

**标头:** atlbase。h

##  <a name="catlservicemodulet"></a>CAtlServiceModuleT:: CAtlServiceModuleT

构造函数。

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>备注

初始化数据成员并设置初始服务状态。

##  <a name="handler"></a>CAtlServiceModuleT:: Handler

服务的处理程序例程。

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>参数

*dwOpcode*<br/>
一个定义处理程序操作的开关。 有关详细信息, 请参阅 "备注"。

### <a name="remarks"></a>备注

这是服务控制管理器 (SCM) 为检索服务的状态而调用的代码, 并发出停止或暂停等说明。 SCM 将操作代码 (如下所示) `Handler`传递给, 以指示服务应执行的操作。

|操作代码|含义|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|停止服务。 重写 atlbase.h 中的方法[CAtlServiceModuleT:: OnStop](#onstop)以更改行为。|
|SERVICE_CONTROL_PAUSE|用户已实现。 覆盖 atlbase.h 中的空方法[CAtlServiceModuleT:: OnPause](#onpause)以暂停该服务。|
|SERVICE_CONTROL_CONTINUE|用户已实现。 覆盖 atlbase.h 中的空方法[CAtlServiceModuleT:: OnContinue](#oncontinue)以继续服务。|
|SERVICE_CONTROL_INTERROGATE|用户已实现。 覆盖 atlbase.h 中的空方法[CAtlServiceModuleT:: OnInterrogate](#oninterrogate)来询问服务。|
|SERVICE_CONTROL_SHUTDOWN|用户已实现。 覆盖 atlbase.h 中的空方法[CAtlServiceModuleT:: OnShutdown](#onshutdown)以关闭服务。|

如果无法识别操作代码, 则调用方法[CAtlServiceModuleT:: OnUnknownRequest](#onunknownrequest) 。

默认的 ATL 生成的服务仅处理停止指令。 如果 SCM 传递了 stop 指令, 则该服务会告诉 SCM, 程序即将停止。 然后, 服务会`PostThreadMessage`调用向其自身发送 quit 消息。 这将终止消息循环, 并最终关闭服务。

##  <a name="initializesecurity"></a>  CAtlServiceModuleT::InitializeSecurity

提供服务的默认安全设置。

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

派生自`CAtlServiceModuleT`的任何类必须在派生类中实现此方法。

在对的调用`CoInitializeSecurity`中使用 PKT 级别的身份验证、RPC_C_IMP_LEVEL_IDENTIFY 的模拟级别和适当的非 null 安全描述符。

对于向导生成的非特性化服务项目, 该项目将处于

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

对于特性化服务项目, 该项目将位于

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>CAtlServiceModuleT:: Install

安装和创建服务。

```
BOOL Install() throw();
```

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

将服务安装到服务控制管理器 (SCM) 数据库中, 然后创建服务对象。 如果无法创建该服务, 则会显示一个消息框, 并且该方法将返回 FALSE。

##  <a name="isinstalled"></a>CAtlServiceModuleT:: IsInstalled

确认已安装该服务。

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>返回值

如果安装了服务, 则返回 TRUE, 否则返回 FALSE。

##  <a name="logevent"></a>  CAtlServiceModuleT::LogEvent

写入事件日志。

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>参数

*pszFormat*<br/>
要写入事件日志的字符串。

*...*<br/>
要写入事件日志的可选的额外字符串。

### <a name="remarks"></a>备注

此方法使用函数[ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw)将详细信息写入事件日志。 如果没有正在运行的服务, 则会将字符串发送到控制台。

##  <a name="m_bservice"></a>  CAtlServiceModuleT::m_bService

指示程序作为服务运行的标志。

```
BOOL m_bService;
```

### <a name="remarks"></a>备注

用于将服务 EXE 与应用程序 EXE 区分开来。

##  <a name="m_dwthreadid"></a>CAtlServiceModuleT:: m_dwThreadID

存储服务的线程标识符的成员变量。

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>备注

此变量存储当前线程的线程标识符。

##  <a name="m_hservicestatus"></a>CAtlServiceModuleT:: m_hServiceStatus

存储当前服务的状态信息结构的句柄的成员变量。

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>备注

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status)结构包含有关服务的信息。

##  <a name="m_status"></a>CAtlServiceModuleT:: m_status

存储当前服务的状态信息结构的成员变量。

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>备注

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status)结构包含有关服务的信息。

##  <a name="m_szservicename"></a>  CAtlServiceModuleT::m_szServiceName

正在注册的服务的名称。

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>备注

以 null 结尾的字符串, 用于存储服务的名称。

##  <a name="oncontinue"></a>CAtlServiceModuleT:: OnContinue

重写此方法以继续服务。

```
void OnContinue() throw();
```

##  <a name="oninterrogate"></a>  CAtlServiceModuleT::OnInterrogate

重写此方法以询问服务。

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>  CAtlServiceModuleT::OnPause

重写此方法可以暂停服务。

```
void OnPause() throw();
```

##  <a name="onshutdown"></a>CAtlServiceModuleT:: OnShutdown

重写此方法以关闭服务。

```
void OnShutdown() throw();
```

##  <a name="onstop"></a>CAtlServiceModuleT:: OnStop

重写此方法以停止服务。

```
void OnStop() throw();
```

##  <a name="onunknownrequest"></a>CAtlServiceModuleT:: OnUnknownRequest

重写此方法以处理对服务的未知请求。

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>参数

*dwOpcode*<br/>
保留。

##  <a name="parsecommandline"></a>  CAtlServiceModuleT::ParseCommandLine

分析命令行并在必要时执行注册。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>参数

*lpCmdLine*<br/>
命令行。

*pnRetCode*<br/>
与注册相对应的 HRESULT (如果已发生)。

### <a name="return-value"></a>返回值

如果成功, 则返回 true; 如果无法注册命令行中提供的 RGS 文件, 则返回 false。

### <a name="remarks"></a>备注

如果需要, 分析命令行并注册或取消注册所提供的 RGS 文件。 此方法调用[catlexemodulet 用作::P arsecommandline](../../atl/reference/catlexemodulet-class.md#parsecommandline)来检查 **/RegServer**和 **/UnregServer**。 添加参数 **-/Service**将注册该服务。

##  <a name="premessageloop"></a>  CAtlServiceModuleT::PreMessageLoop

此方法将在进入消息循环前立即调用。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
此参数传递给[catlexemodulet 用作::P remessageloop](../../atl/reference/catlexemodulet-class.md#premessageloop)。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

重写此方法以添加服务的自定义初始化代码。

##  <a name="registerappid"></a>  CAtlServiceModuleT::RegisterAppId

在注册表中注册该服务。

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>参数

*bService*<br/>
注册为服务时必须为 true。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

##  <a name="run"></a>CAtlServiceModuleT:: Run

运行该服务。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)节中讨论的值之一。 默认值为 SW_HIDE。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用后`Run` , 调用[CAtlServiceModuleT::P remessageloop](#premessageloop)、 [catlexemodulet 用作:: RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)和[catlexemodulet 用作::P ostmessageloop](../../atl/reference/catlexemodulet-class.md#postmessageloop)。

##  <a name="servicemain"></a>CAtlServiceModuleT:: ServiceMain

此方法由服务控制管理器调用。

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>参数

*dwArgc*<br/>
Argc 参数。

*lpszArgv*<br/>
Argv 参数。

### <a name="remarks"></a>备注

在控制面板中打开 "服务" 应用`ServiceMain`程序时, 服务控制管理器 (SCM) 会调用, 请选择该服务, 然后单击 "启动"。

在 SCM 调用`ServiceMain`后, 服务必须为 SCM 指定处理程序函数。 此函数允许 SCM 获取服务的状态并传递特定说明 (如暂停或停止)。 随后, 将调用[CAtlServiceModuleT:: Run](#run)来执行服务的主要工作。 `Run`继续执行, 直到服务停止。

##  <a name="setservicestatus"></a>  CAtlServiceModuleT::SetServiceStatus

此方法更新服务状态。

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>参数

*dwState*<br/>
新状态。 有关可能的值, 请参阅[SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) 。

### <a name="remarks"></a>备注

更新服务的服务控制管理器的状态信息。 它由[CAtlServiceModuleT:: Run](#run)、 [CAtlServiceModuleT:: ServiceMain](#servicemain)和其他处理程序方法调用。 状态还存储在成员变量[CAtlServiceModuleT:: m_status](#m_status)中。

##  <a name="start"></a>CAtlServiceModuleT:: Start

`CAtlServiceModuleT::WinMain`当服务启动时调用。

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)节中讨论的值之一。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

[CAtlServiceModuleT:: WinMain](#winmain)方法既处理注册和安装, 还处理删除注册表项和卸载模块所涉及的任务。 当服务运行时, `WinMain`调用。 `Start`

##  <a name="uninstall"></a>CAtlServiceModuleT:: Uninstall

停止并删除服务。

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

停止运行服务并将其从服务控制管理器数据库中删除。

##  <a name="unlock"></a>  CAtlServiceModuleT::Unlock

减少服务的锁计数。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>返回值

返回锁计数, 这可能对诊断和调试非常有用。

##  <a name="unregisterappid"></a>  CAtlServiceModuleT::UnregisterAppId

从注册表中删除服务。

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

##  <a name="winmain"></a>CAtlServiceModuleT:: WinMain

此方法实现启动服务所需的代码。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)节中讨论的值之一。

### <a name="return-value"></a>返回值

返回服务的返回值。

### <a name="remarks"></a>备注

此方法处理命令行 (使用[CAtlServiceModuleT::P arsecommandline](#parsecommandline)), 然后启动服务 (使用[CAtlServiceModuleT:: Start](#start))。

## <a name="see-also"></a>请参阅

[CAtlExeModuleT 类](../../atl/reference/catlexemodulet-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
