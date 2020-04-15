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
ms.openlocfilehash: 5d87eada997d0bbfe44cd07a819f6b012a7a3a20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321341"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT 类

此类实现服务。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
来自 的类`CAtlServiceModuleT`派生自 。

*n服务名称ID*<br/>
服务的资源标识符。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtl服务模块T：CAtl服务模块T](#catlservicemodulet)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlServiceModuleT：：处理程序](#handler)|服务的处理程序例程。|
|[CAtlServiceModuleT：初始化安全性](#initializesecurity)|提供服务的默认安全设置。|
|[CAtlService 模块T：安装](#install)|安装并创建服务。|
|[CAtlServiceModuleT：已安装](#isinstalled)|确认已安装该服务。|
|[CAtlServiceModuleT：：日志事件](#logevent)|写入事件日志。|
|[CatlService 模块T：：继续](#oncontinue)|重写此方法以继续服务。|
|[CAtlServiceModuleT：：上查询](#oninterrogate)|重写此方法以询问服务。|
|[CatlServiceModuleT：：打开暂停](#onpause)|重写此方法以暂停服务。|
|[CatlServiceModuleT：：关闭时间](#onshutdown)|重写此方法以关闭服务|
|[CatlServiceModuleT：：打开](#onstop)|重写此方法以停止服务|
|[CatlServiceModuleT：关于未知请求](#onunknownrequest)|重写此方法以处理对服务的未知请求|
|[CAtlServiceModuleT：:Parse命令热线](#parsecommandline)|分析命令行并在必要时执行注册。|
|[CAtl服务模块T：:P重新消息循环](#premessageloop)|在输入消息循环之前立即调用此方法。|
|[CAtlServiceModuleT：：注册应用程序](#registerappid)|在注册表中注册服务。|
|[CAtlService 模块T：：运行](#run)|运行服务。|
|[CAtlServiceModuleT：服务主](#servicemain)|服务控制管理器调用的方法。|
|[CAtl服务模块T：设置服务状态](#setservicestatus)|更新服务状态。|
|[CAtlService 模块T：：开始](#start)|服务启动`CAtlServiceModuleT::WinMain`时调用。|
|[CAtlServiceModuleT：：卸载](#uninstall)|停止并删除服务。|
|[CAtlService 模块T：解锁](#unlock)|撤销服务的锁计数。|
|[CAtlServiceModuleT：：未注册AppId](#unregisterappid)|从注册表中删除服务。|
|[CAtlServiceModuleT：：赢曼](#winmain)|此方法实现运行服务所需的代码。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CAtlServiceModuleT：m_bService](#m_bservice)|指示程序作为服务运行的标志。|
|[CAtlServiceModuleT：m_dwThreadID](#m_dwthreadid)|存储线程标识符的成员变量。|
|[CAtlServiceModuleT：m_hServiceStatus](#m_hservicestatus)|存储当前服务状态信息结构句柄的成员变量。|
|[CAtlService 模块T：m_status](#m_status)|存储当前服务的状态信息结构的成员变量。|
|[CAtlServiceModuleT：m_szServiceName](#m_szservicename)|正在注册的服务的名称。|

## <a name="remarks"></a>备注

`CAtlServiceModuleT`，派生自[CAtlExeModuleT，](../../atl/reference/catlexemodulet-class.md)实现 ATL 服务模块。 `CAtlServiceModuleT`提供了命令行处理、安装、注册和删除的方法。 如果需要额外的功能，可以重写这些方法和其他方法。

此类将替换早期版本的 ATL 中使用的过时的[CComModule 类](../../atl/reference/ccommodule-class.md)。 有关详细信息，请参阅[ATL 模块课程](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="catlservicemoduletcatlservicemodulet"></a><a name="catlservicemodulet"></a>CAtl服务模块T：CAtl服务模块T

构造函数。

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>备注

初始化数据成员并设置初始服务状态。

## <a name="catlservicemodulethandler"></a><a name="handler"></a>CAtlServiceModuleT：：处理程序

服务的处理程序例程。

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>参数

*dwOpcode*<br/>
定义处理程序操作的开关。 有关详细信息，请参阅注释。

### <a name="remarks"></a>备注

这是服务控制管理器 （SCM） 调用的代码来检索服务的状态并发出停止或暂停等指令。 SCM 传递操作代码（如下所示）以`Handler`指示服务应执行哪些操作。

|操作代码|含义|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|停止服务。 重写方法[CAtlServiceModuleT：atlbase.h](#onstop)中的 OnStop 以更改行为。|
|SERVICE_CONTROL_PAUSE|用户实现。 重写空方法[CAtlServiceModuleT：atlbase.h 中的"OnPause"](#onpause)以暂停服务。|
|SERVICE_CONTROL_CONTINUE|用户实现。 重写空方法[CAtlServiceModuleT：：在](#oncontinue)atlbase.h 中继续继续继续服务。|
|SERVICE_CONTROL_INTERROGATE|用户实现。 重写空方法[CAtlServiceModuleT：atlbase.h 中的"OnInterrogate"](#oninterrogate)以询问服务。|
|SERVICE_CONTROL_SHUTDOWN|用户实现。 重写空方法[CAtlServiceModuleT：在](#onshutdown)atlbase.h 中关闭以关闭服务。|

如果无法识别操作代码，则调用方法[CAtlServiceModuleT：on 未知请求](#onunknownrequest)。

默认 ATL 生成的服务仅处理停止指令。 如果 SCM 通过停止指令，服务会告诉 SCM 程序即将停止。 然后，服务调用`PostThreadMessage`将退出消息发布到自身。 这将终止消息循环，服务最终将关闭。

## <a name="catlservicemoduletinitializesecurity"></a><a name="initializesecurity"></a>CAtlServiceModuleT：初始化安全性

提供服务的默认安全设置。

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

派生的任何`CAtlServiceModuleT`类都必须在派生类中实现此方法。

在调用 中使用 PKT 级身份验证、RPC_C_IMP_LEVEL_IDENTIFY的模拟级别以及调用`CoInitializeSecurity`中适当的非空安全描述符。

对于向导生成的非属性化服务项目，这将在

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

对于属性化服务项目，这将在

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

## <a name="catlservicemoduletinstall"></a><a name="install"></a>CAtlService 模块T：安装

安装并创建服务。

```
BOOL Install() throw();
```

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

将服务安装到服务控制管理器 （SCM） 数据库中，然后创建服务对象。 如果无法创建服务，将显示一个消息框，该方法将返回 FALSE。

## <a name="catlservicemoduletisinstalled"></a><a name="isinstalled"></a>CAtlServiceModuleT：已安装

确认已安装该服务。

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>返回值

如果安装了服务，则返回 TRUE，否则返回 FALSE。

## <a name="catlservicemoduletlogevent"></a><a name="logevent"></a>CAtlServiceModuleT：：日志事件

写入事件日志。

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>参数

*psz格式*<br/>
要写入事件日志的字符串。

*...*<br/>
要写入事件日志的可选额外字符串。

### <a name="remarks"></a>备注

此方法使用函数[ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw)将详细信息写入事件日志。 如果没有服务运行，则字符串将发送到控制台。

## <a name="catlservicemoduletm_bservice"></a><a name="m_bservice"></a>CAtlServiceModuleT：m_bService

指示程序作为服务运行的标志。

```
BOOL m_bService;
```

### <a name="remarks"></a>备注

用于区分服务 EXE 和应用程序 EXE。

## <a name="catlservicemoduletm_dwthreadid"></a><a name="m_dwthreadid"></a>CAtlServiceModuleT：m_dwThreadID

存储服务线程标识符的成员变量。

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>备注

此变量存储当前线程的线程标识符。

## <a name="catlservicemoduletm_hservicestatus"></a><a name="m_hservicestatus"></a>CAtlServiceModuleT：m_hServiceStatus

存储当前服务状态信息结构句柄的成员变量。

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>备注

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status)结构包含有关服务的信息。

## <a name="catlservicemoduletm_status"></a><a name="m_status"></a>CAtlService 模块T：m_status

存储当前服务的状态信息结构的成员变量。

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>备注

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status)结构包含有关服务的信息。

## <a name="catlservicemoduletm_szservicename"></a><a name="m_szservicename"></a>CAtlServiceModuleT：m_szServiceName

正在注册的服务的名称。

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>备注

存储服务名称的 null 终止字符串。

## <a name="catlservicemoduletoncontinue"></a><a name="oncontinue"></a>CatlService 模块T：：继续

重写此方法以继续服务。

```
void OnContinue() throw();
```

## <a name="catlservicemoduletoninterrogate"></a><a name="oninterrogate"></a>CAtlServiceModuleT：：上查询

重写此方法以询问服务。

```
void OnInterrogate() throw();
```

## <a name="catlservicemoduletonpause"></a><a name="onpause"></a>CatlServiceModuleT：：打开暂停

重写此方法以暂停服务。

```
void OnPause() throw();
```

## <a name="catlservicemoduletonshutdown"></a><a name="onshutdown"></a>CatlServiceModuleT：：关闭时间

重写此方法以关闭服务。

```
void OnShutdown() throw();
```

## <a name="catlservicemoduletonstop"></a><a name="onstop"></a>CatlServiceModuleT：：打开

重写此方法以停止服务。

```
void OnStop() throw();
```

## <a name="catlservicemoduletonunknownrequest"></a><a name="onunknownrequest"></a>CatlServiceModuleT：关于未知请求

重写此方法以处理对服务的未知请求。

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>参数

*dwOpcode*<br/>
保留。

## <a name="catlservicemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlServiceModuleT：:Parse命令热线

分析命令行并在必要时执行注册。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>参数

*lpCmdline*<br/>
命令行。

*pnRet代码*<br/>
与注册对应的 HRESULT（如果发生）。

### <a name="return-value"></a>返回值

如果无法注册命令行中提供的 RGS 文件，则在成功时返回 true，或 false。

### <a name="remarks"></a>备注

如有必要，分析命令行并注册或取消注册提供的 RGS 文件。 此方法调用[CAtlExeModuleT：:Parse命令线](../../atl/reference/catlexemodulet-class.md#parsecommandline)来检查 **/RegServer**和 **/unregServer**。 添加参数 **-/服务**将注册服务。

## <a name="catlservicemoduletpremessageloop"></a><a name="premessageloop"></a>CAtl服务模块T：:P重新消息循环

在输入消息循环之前立即调用此方法。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
此参数传递给[CAtlExeModuleT：:PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop)。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

重写此方法以添加服务的自定义初始化代码。

## <a name="catlservicemoduletregisterappid"></a><a name="registerappid"></a>CAtlServiceModuleT：：注册应用程序

在注册表中注册服务。

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>参数

*b服务*<br/>
注册为服务必须为 true。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catlservicemoduletrun"></a><a name="run"></a>CAtlService 模块T：：运行

运行服务。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)部分中讨论的值之一。 默认值为SW_HIDE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

被调用后，`Run`调用 CAtlServiceModuleT：:PreMessageLoop，CAtlExeModuleT：：RunMessageLoop，cAtlExeModuleT：:PostMessageLoop 。 [CAtlServiceModuleT::PreMessageLoop](#premessageloop) [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop) [CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop)

## <a name="catlservicemoduletservicemain"></a><a name="servicemain"></a>CAtlServiceModuleT：服务主

此方法由服务控制管理器调用。

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>参数

*德阿格克*<br/>
argc 参数。

*lpszArgv*<br/>
argv 参数。

### <a name="remarks"></a>备注

在"控制面板"中打开服务应用程序`ServiceMain`时，服务控制管理器 （SCM） 会调用，选择服务，然后单击"开始"。

SCM 调用`ServiceMain`后，服务必须为 SCM 提供处理程序功能。 此功能允许 SCM 获取服务状态并传递特定指令（如暂停或停止）。 随后[，CAtlServiceModuleT：](#run)调用 Run 来执行服务的主要工作。 `Run`继续执行，直到服务停止。

## <a name="catlservicemoduletsetservicestatus"></a><a name="setservicestatus"></a>CAtl服务模块T：设置服务状态

此方法更新服务状态。

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>参数

*德沃州*<br/>
新状态。 有关可能的值，请参阅[设置服务状态](/windows/win32/api/winsvc/nf-winsvc-setservicestatus)。

### <a name="remarks"></a>备注

更新服务控制管理器的服务状态信息。 它由[CAtlServiceModuleT 调用：：运行](#run)[，CAtlServiceModuleT：：服务Main](#servicemain)和其他处理程序方法。 状态也存储在成员变量[CAtlServiceModuleT：：m_status](#m_status)。

## <a name="catlservicemoduletstart"></a><a name="start"></a>CAtlService 模块T：：开始

服务启动`CAtlServiceModuleT::WinMain`时调用。

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)部分中讨论的值之一。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

[CAtlServiceModuleT：WinMain](#winmain)方法既处理注册和安装，也处理删除注册表项和卸载模块所涉及的任务。 运行服务时，`WinMain`调用`Start`。

## <a name="catlservicemoduletuninstall"></a><a name="uninstall"></a>CAtlServiceModuleT：：卸载

停止并删除服务。

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

停止服务运行，并将其从服务控制管理器数据库中删除。

## <a name="catlservicemoduletunlock"></a><a name="unlock"></a>CAtlService 模块T：解锁

撤销服务的锁计数。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>返回值

返回锁计数，这可能可用于诊断和调试。

## <a name="catlservicemoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlServiceModuleT：：未注册AppId

从注册表中删除服务。

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catlservicemoduletwinmain"></a><a name="winmain"></a>CAtlServiceModuleT：：赢曼

此方法实现启动服务所需的代码。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>参数

*nShowCmd*<br/>
指定窗口的显示方式。 此参数可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)部分中讨论的值之一。

### <a name="return-value"></a>返回值

返回服务的返回值。

### <a name="remarks"></a>备注

此方法处理命令行（使用[CAtlServiceModuleT：:Parse命令线](#parsecommandline)），然后启动服务（使用[CAtlServiceModuleT：：开始](#start)）。

## <a name="see-also"></a>另请参阅

[CAtlExeModuleT 类](../../atl/reference/catlexemodulet-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
