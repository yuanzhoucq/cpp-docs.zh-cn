---
title: CAtlServiceModuleT 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2d059a990b9b01cdfc959284d9fe20f3dfd12af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT 类
此类实现服务。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, UINT nServiceNameID>  
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类派生自`CAtlServiceModuleT`。  
  
 *nServiceNameID*  
 服务资源标识符。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlServiceModuleT::Handler](#handler)|有关服务该处理程序例程。|  
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|提供默认值为服务的安全设置。|  
|[CAtlServiceModuleT::Install](#install)|安装并创建服务。|  
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|确认已安装了服务。|  
|[CAtlServiceModuleT::LogEvent](#logevent)|将写入事件日志。|  
|[CAtlServiceModuleT::OnContinue](#oncontinue)|重写此方法继续使用服务。|  
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|重写此方法以询问该服务。|  
|[CAtlServiceModuleT::OnPause](#onpause)|重写此方法以暂停服务。|  
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|重写此方法，以关闭服务|  
|[CAtlServiceModuleT::OnStop](#onstop)|重写此方法以停止服务|  
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|重写此方法以处理未知的服务请求|  
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|分析命令行，并根据需要执行注册。|  
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|输入消息循环之前调用此方法。|  
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|在注册表中注册服务。|  
|[CAtlServiceModuleT::Run](#run)|运行服务。|  
|[CAtlServiceModuleT::ServiceMain](#servicemain)|调用服务控制管理器的方法。|  
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|更新服务状态。|  
|[CAtlServiceModuleT::Start](#start)|由调用`CAtlServiceModuleT::WinMain`服务启动时。|  
|[CAtlServiceModuleT::Uninstall](#uninstall)|停止并删除该服务。|  
|[CAtlServiceModuleT::Unlock](#unlock)|递减服务的锁计数。|  
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|从注册表中删除服务。|  
|[CAtlServiceModuleT::WinMain](#winmain)|此方法实现运行服务所需的代码。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlServiceModuleT::m_bService](#m_bservice)|该标志指明作为服务运行程序。|  
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|存储的线程标识符的成员变量。|  
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|成员变量存储当前服务的状态信息结构的句柄。|  
|[CAtlServiceModuleT::m_status](#m_status)|存储当前服务的状态信息结构的成员变量。|  
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|要注册服务的名称。|  
  
## <a name="remarks"></a>备注  
 `CAtlServiceModuleT`派生自[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)，实现 ATL 服务模块。 `CAtlServiceModuleT`提供用于命令行处理、 安装、 注册和删除方法。 如果需要额外功能，则可以覆盖这些和其他方法。  
  
 此类替换已过时[CComModule 类](../../atl/reference/ccommodule-class.md)的 atl。 早期版本中使用 请参阅[ATL Module 类](../../atl/atl-module-classes.md)有关详细信息。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)  
  
 `CAtlServiceModuleT`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
##  <a name="catlservicemodulet"></a>CAtlServiceModuleT::CAtlServiceModuleT  
 构造函数。  
  
```
CAtlServiceModuleT() throw();
```  
  
### <a name="remarks"></a>备注  
 初始化数据成员并设置的初始服务状态。  
  
##  <a name="handler"></a>CAtlServiceModuleT::Handler  
 有关服务该处理程序例程。  
  
```
void Handler(DWORD dwOpcode) throw();
```  
  
### <a name="parameters"></a>参数  
 *dwOpcode*  
 一台交换机定义处理程序操作。 有关详细信息，请参阅备注。  
  
### <a name="remarks"></a>备注  
 这是服务控制管理器 (SCM) 调用以检索的服务和问题的说明，例如停止的状态或暂停的代码。 SCM 传递操作代码中，为下面所示`Handler`以指示服务应执行的操作。  
  
|操作代码|含义|  
|--------------------|-------------|  
|SERVICE_CONTROL_STOP|停止服务。 重写方法[CAtlServiceModuleT::OnStop](#onstop)中 atlbase.h 更改的行为。|  
|SERVICE_CONTROL_PAUSE|实现的用户。 重写空方法[CAtlServiceModuleT::OnPause](#onpause) atlbase.h 暂停该服务中。|  
|SERVICE_CONTROL_CONTINUE|实现的用户。 重写空方法[CAtlServiceModuleT::OnContinue](#oncontinue) atlbase.h 继续使用服务中。|  
|SERVICE_CONTROL_INTERROGATE|实现的用户。 重写空方法[CAtlServiceModuleT::OnInterrogate](#oninterrogate) atlbase.h 以便询问服务中。|  
|SERVICE_CONTROL_SHUTDOWN|实现的用户。 重写空方法[CAtlServiceModuleT::OnShutdown](#onshutdown)中 atlbase.h 到关闭服务。|  
  
 如果操作代码未被识别，该方法[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)调用。  
  
 一个默认 ATL 生成服务仅处理停止指令。 如果 SCM 通过停止指令，则服务将通知 SCM 程序即将停止。 然后，服务调用`PostThreadMessage`发布到其自身发出退出的消息。 这将终止消息循环并将最终关闭服务。  
  
##  <a name="initializesecurity"></a>CAtlServiceModuleT::InitializeSecurity  
 提供默认值为服务的安全设置。  
  
```
HRESULT InitializeSecurity() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 在 Visual Studio.NET 2003 中，在基类中不实现此方法。 Visual Studio 项目向导在生成的代码中，包含此方法，但如果使用 ATL 7.1 编译 Visual c + + 的早期版本中创建的项目，将产生编译错误。 任何派生自的类`CAtlServiceModuleT`必须在派生类中实现此方法。  
  
 对的调用中使用 PKT 级身份验证、 RPC_C_IMP_LEVEL_IDENTIFY 的模拟级别和相应的非 null 安全描述符**CoInitializeSecurity**。  
  
 对于向导生成非属性化的服务项目，这将是在  
  
 [!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]  
  
 对于特性化的服务项目，这将是在  
  
 [!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]  
  
##  <a name="install"></a>CAtlServiceModuleT::Install  
 安装并创建服务。  
  
```
BOOL Install() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 安装服务到服务控制管理器 (SCM) 数据库，然后创建服务对象。 如果无法创建该服务，则显示一个消息框，并且该方法返回 FALSE。  
  
##  <a name="isinstalled"></a>CAtlServiceModuleT::IsInstalled  
 确认已安装了服务。  
  
```
BOOL IsInstalled() throw();
```  
  
### <a name="return-value"></a>返回值  
 服务是否已安装，则为 FALSE 否则，则返回 TRUE。  
  
##  <a name="logevent"></a>CAtlServiceModuleT::LogEvent  
 将写入事件日志。  
  
```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszFormat`  
 要写入事件日志的字符串。  
  
 ...  
 可选的额外字符串写入到事件日志。  
  
### <a name="remarks"></a>备注  
 此方法写出到事件日志，使用函数的详细信息[ReportEvent](http://msdn.microsoft.com/library/windows/desktop/aa363679)。 如果任何服务正在不运行，则将字符串发送到控制台。  
  
##  <a name="m_bservice"></a>CAtlServiceModuleT::m_bService  
 该标志指明作为服务运行程序。  
  
```
BOOL m_bService;
```  
  
### <a name="remarks"></a>备注  
 用于将服务 EXE 与应用程序 EXE 区分开来。  
  
##  <a name="m_dwthreadid"></a>CAtlServiceModuleT::m_dwThreadID  
 存储服务的线程标识符的成员变量。  
  
```
DWORD m_dwThreadID;
```  
  
### <a name="remarks"></a>备注  
 此变量存储当前线程的线程标识符。  
  
##  <a name="m_hservicestatus"></a>CAtlServiceModuleT::m_hServiceStatus  
 成员变量存储当前服务的状态信息结构的句柄。  
  
```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```  
  
### <a name="remarks"></a>备注  
 [SERVICE_STATUS](http://msdn.microsoft.com/library/windows/desktop/ms685996)结构包含有关服务的信息。  
  
##  <a name="m_status"></a>CAtlServiceModuleT::m_status  
 存储当前服务的状态信息结构的成员变量。  
  
```
SERVICE_STATUS m_status;
```  
  
### <a name="remarks"></a>备注  
 [SERVICE_STATUS](http://msdn.microsoft.com/library/windows/desktop/ms685996)结构包含有关服务的信息。  
  
##  <a name="m_szservicename"></a>CAtlServiceModuleT::m_szServiceName  
 要注册服务的名称。  
  
```
TCHAR [256] m_szServiceName;
```  
  
### <a name="remarks"></a>备注  
 以 null 结尾的字符串，它存储在服务的名称。  
  
##  <a name="oncontinue"></a>CAtlServiceModuleT::OnContinue  
 重写此方法继续使用服务。  
  
```
void OnContinue() throw();
```  
  
##  <a name="oninterrogate"></a>CAtlServiceModuleT::OnInterrogate  
 重写此方法以询问该服务。  
  
```
void OnInterrogate() throw();
```  
  
##  <a name="onpause"></a>CAtlServiceModuleT::OnPause  
 重写此方法以暂停服务。  
  
```
void OnPause() throw();
```  
  
##  <a name="onshutdown"></a>CAtlServiceModuleT::OnShutdown  
 重写此方法，以关闭服务。  
  
```
void OnShutdown() throw();
```  
  
##  <a name="onstop"></a>CAtlServiceModuleT::OnStop  
 重写此方法以停止服务。  
  
```
void OnStop() throw();
```  
  
##  <a name="onunknownrequest"></a>CAtlServiceModuleT::OnUnknownRequest  
 重写此方法以处理未知的服务请求。  
  
```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```  
  
### <a name="parameters"></a>参数  
 */\*dwOpcode\*/*  
 保留。  
  
##  <a name="parsecommandline"></a>CAtlServiceModuleT::ParseCommandLine  
 分析命令行，并根据需要执行注册。  
  
```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpCmdLine`  
 命令行。  
  
 `pnRetCode`  
 （如果发生） 到注册相对应的 HRESULT。  
  
### <a name="return-value"></a>返回值  
 成功，则无法注册命令行中提供的 rgs 否则为 false 则返回 true。  
  
### <a name="remarks"></a>备注  
 分析命令行和注册或注销提供的 RGS 文件，如有必要。 此方法调用[CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline)检查**/RegServer**和**/UnregServer**。 与参数相加**-/ 服务**将注册该服务。  
  
##  <a name="premessageloop"></a>CAtlServiceModuleT::PreMessageLoop  
 输入消息循环之前调用此方法。  
  
```
HRESULT PreMessageLoop(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>参数  
 `nShowCmd`  
 此参数传递给[CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop)。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 重写此方法可为服务中添加自定义的初始化代码。  
  
##  <a name="registerappid"></a>CAtlServiceModuleT::RegisterAppId  
 在注册表中注册服务。  
  
```
inline HRESULT RegisterAppId(bool bService = false) throw();
```  
  
### <a name="parameters"></a>参数  
 *bService*  
 必须为 true，则作为服务注册。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="run"></a>CAtlServiceModuleT::Run  
 运行服务。  
  
```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```  
  
### <a name="parameters"></a>参数  
 `nShowCmd`  
 指定如何显示窗口。 此参数可以为所述的值之一[WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559)部分。 默认值为 SW_HIDE。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 后调用，**运行**调用[CAtlServiceModuleT::PreMessageLoop](#premessageloop)， [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)，和[CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop)。  
  
##  <a name="servicemain"></a>CAtlServiceModuleT::ServiceMain  
 调用此方法由服务控制管理器。  
  
```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```  
  
### <a name="parameters"></a>参数  
 *dwArgc*  
 Argc 自变量。  
  
 *lpszArgv*  
 Argv 自变量。  
  
### <a name="remarks"></a>备注  
 服务控制管理器 (SCM) 调用`ServiceMain`时在控制面板中打开服务应用程序，请选择该服务，并单击开始。  
  
 SCM 后调用`ServiceMain`，服务必须为 SCM 指定处理程序函数。 此函数可获取服务的状态并传递特定的指令 （如暂停或停止） 的 SCM。 随后， [CAtlServiceModuleT::Run](#run)调用以执行服务的主要工作。 **运行**继续执行，直到该服务已停止。  
  
##  <a name="setservicestatus"></a>CAtlServiceModuleT::SetServiceStatus  
 此方法更新服务状态。  
  
```
void SetServiceStatus(DWORD dwState) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwState`  
 新的状态。 请参阅[SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241)有关可能的值。  
  
### <a name="remarks"></a>备注  
 更新服务的服务控制管理器的状态信息。 它由[CAtlServiceModuleT::Run](#run)， [CAtlServiceModuleT::ServiceMain](#servicemain)和其他处理程序方法。 状态也存储在成员变量[CAtlServiceModuleT::m_status](#m_status)。  
  
##  <a name="start"></a>CAtlServiceModuleT::Start  
 由调用`CAtlServiceModuleT::WinMain`服务启动时。  
  
```
HRESULT Start(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>参数  
 `nShowCmd`  
 指定如何显示窗口。 此参数可以为所述的值之一[WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559)部分。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 [CAtlServiceModuleT::WinMain](#winmain)方法处理注册和安装，以及任务涉及在正在删除注册表项和卸载该模块。 当运行时服务时，`WinMain`调用**启动**。  
  
##  <a name="uninstall"></a>CAtlServiceModuleT::Uninstall  
 停止并删除该服务。  
  
```
BOOL Uninstall() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 停止运行中的服务并将其从服务控制管理器数据库中删除。  
  
##  <a name="unlock"></a>CAtlServiceModuleT::Unlock  
 递减服务的锁计数。  
  
```
LONG Unlock() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的锁计数，这可能是用于诊断和调试。  
  
##  <a name="unregisterappid"></a>CAtlServiceModuleT::UnregisterAppId  
 从注册表中删除服务。  
  
```
HRESULT UnregisterAppId() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="winmain"></a>CAtlServiceModuleT::WinMain  
 此方法实现所需启动服务的代码。  
  
```
int WinMain(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>参数  
 `nShowCmd`  
 指定如何显示窗口。 此参数可以为所述的值之一[WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559)部分。  
  
### <a name="return-value"></a>返回值  
 返回服务的返回值。  
  
### <a name="remarks"></a>备注  
 此方法可处理命令行 (使用[CAtlServiceModuleT::ParseCommandLine](#parsecommandline))，然后启动服务 (使用[CAtlServiceModuleT::Start](#start))。  
  
## <a name="see-also"></a>请参阅  
 [CAtlExeModuleT 类](../../atl/reference/catlexemodulet-class.md)   
 [类概述](../../atl/atl-class-overview.md)
