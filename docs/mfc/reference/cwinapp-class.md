---
title: CWinApp 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinApp
- AFXWIN/CWinApp
- AFXWIN/CWinApp::CWinApp
- AFXWIN/CWinApp::AddDocTemplate
- AFXWIN/CWinApp::AddToRecentFileList
- AFXWIN/CWinApp::ApplicationRecoveryCallback
- AFXWIN/CWinApp::CloseAllDocuments
- AFXWIN/CWinApp::CreatePrinterDC
- AFXWIN/CWinApp::DelRegTree
- AFXWIN/CWinApp::DoMessageBox
- AFXWIN/CWinApp::DoWaitCursor
- AFXWIN/CWinApp::EnableD2DSupport
- AFXWIN/CWinApp::EnableHtmlHelp
- AFXWIN/CWinApp::EnableTaskbarInteraction
- AFXWIN/CWinApp::ExitInstance
- AFXWIN/CWinApp::GetApplicationRecoveryParameter
- AFXWIN/CWinApp::GetApplicationRecoveryPingInterval
- AFXWIN/CWinApp::GetApplicationRestartFlags
- AFXWIN/CWinApp::GetAppRegistryKey
- AFXWIN/CWinApp::GetDataRecoveryHandler
- AFXWIN/CWinApp::GetFirstDocTemplatePosition
- AFXWIN/CWinApp::GetHelpMode
- AFXWIN/CWinApp::GetNextDocTemplate
- AFXWIN/CWinApp::GetPrinterDeviceDefaults
- AFXWIN/CWinApp::GetProfileBinary
- AFXWIN/CWinApp::GetProfileInt
- AFXWIN/CWinApp::GetProfileString
- AFXWIN/CWinApp::GetSectionKey
- AFXWIN/CWinApp::HideApplication
- AFXWIN/CWinApp::HtmlHelp
- AFXWIN/CWinApp::InitInstance
- AFXWIN/CWinApp::IsTaskbarInteractionEnabled
- AFXWIN/CWinApp::LoadCursor
- AFXWIN/CWinApp::LoadIcon
- AFXWIN/CWinApp::LoadOEMCursor
- AFXWIN/CWinApp::LoadOEMIcon
- AFXWIN/CWinApp::LoadStandardCursor
- AFXWIN/CWinApp::LoadStandardIcon
- AFXWIN/CWinApp::OnDDECommand
- AFXWIN/CWinApp::OnIdle
- AFXWIN/CWinApp::OpenDocumentFile
- AFXWIN/CWinApp::ParseCommandLine
- AFXWIN/CWinApp::PreTranslateMessage
- AFXWIN/CWinApp::ProcessMessageFilter
- AFXWIN/CWinApp::ProcessShellCommand
- AFXWIN/CWinApp::ProcessWndProcException
- AFXWIN/CWinApp::Register
- AFXWIN/CWinApp::RegisterWithRestartManager
- AFXWIN/CWinApp::ReopenPreviousFilesAtRestart
- AFXWIN/CWinApp::RestartInstance
- AFXWIN/CWinApp::RestoreAutosavedFilesAtRestart
- AFXWIN/CWinApp::Run
- AFXWIN/CWinApp::RunAutomated
- AFXWIN/CWinApp::RunEmbedded
- AFXWIN/CWinApp::SaveAllModified
- AFXWIN/CWinApp::SelectPrinter
- AFXWIN/CWinApp::SetHelpMode
- AFXWIN/CWinApp::SupportsApplicationRecovery
- AFXWIN/CWinApp::SupportsAutosaveAtInterval
- AFXWIN/CWinApp::SupportsAutosaveAtRestart
- AFXWIN/CWinApp::SupportsRestartManager
- AFXWIN/CWinApp::Unregister
- AFXWIN/CWinApp::WinHelp
- AFXWIN/CWinApp::WriteProfileBinary
- AFXWIN/CWinApp::WriteProfileInt
- AFXWIN/CWinApp::WriteProfileString
- AFXWIN/CWinApp::EnableShellOpen
- AFXWIN/CWinApp::LoadStdProfileSettings
- AFXWIN/CWinApp::OnContextHelp
- AFXWIN/CWinApp::OnFileNew
- AFXWIN/CWinApp::OnFileOpen
- AFXWIN/CWinApp::OnFilePrintSetup
- AFXWIN/CWinApp::OnHelp
- AFXWIN/CWinApp::OnHelpFinder
- AFXWIN/CWinApp::OnHelpIndex
- AFXWIN/CWinApp::OnHelpUsing
- AFXWIN/CWinApp::RegisterShellFileTypes
- AFXWIN/CWinApp::SetAppID
- AFXWIN/CWinApp::SetRegistryKey
- AFXWIN/CWinApp::UnregisterShellFileTypes
- AFXWIN/CWinApp::m_bHelpMode
- AFXWIN/CWinApp::m_eHelpType
- AFXWIN/CWinApp::m_hInstance
- AFXWIN/CWinApp::m_lpCmdLine
- AFXWIN/CWinApp::m_nCmdShow
- AFXWIN/CWinApp::m_pActiveWnd
- AFXWIN/CWinApp::m_pszAppID
- AFXWIN/CWinApp::m_pszAppName
- AFXWIN/CWinApp::m_pszExeName
- AFXWIN/CWinApp::m_pszHelpFilePath
- AFXWIN/CWinApp::m_pszProfileName
- AFXWIN/CWinApp::m_pszRegistryKey
- AFXWIN/CWinApp::m_dwRestartManagerSupportFlags
- AFXWIN/CWinApp::m_nAutosaveInterval
- AFXWIN/CWinApp::m_pDataRecoveryHandler
dev_langs:
- C++
helpviewer_keywords:
- CWinApp [MFC], CWinApp
- CWinApp [MFC], AddDocTemplate
- CWinApp [MFC], AddToRecentFileList
- CWinApp [MFC], ApplicationRecoveryCallback
- CWinApp [MFC], CloseAllDocuments
- CWinApp [MFC], CreatePrinterDC
- CWinApp [MFC], DelRegTree
- CWinApp [MFC], DoMessageBox
- CWinApp [MFC], DoWaitCursor
- CWinApp [MFC], EnableD2DSupport
- CWinApp [MFC], EnableHtmlHelp
- CWinApp [MFC], EnableTaskbarInteraction
- CWinApp [MFC], ExitInstance
- CWinApp [MFC], GetApplicationRecoveryParameter
- CWinApp [MFC], GetApplicationRecoveryPingInterval
- CWinApp [MFC], GetApplicationRestartFlags
- CWinApp [MFC], GetAppRegistryKey
- CWinApp [MFC], GetDataRecoveryHandler
- CWinApp [MFC], GetFirstDocTemplatePosition
- CWinApp [MFC], GetHelpMode
- CWinApp [MFC], GetNextDocTemplate
- CWinApp [MFC], GetPrinterDeviceDefaults
- CWinApp [MFC], GetProfileBinary
- CWinApp [MFC], GetProfileInt
- CWinApp [MFC], GetProfileString
- CWinApp [MFC], GetSectionKey
- CWinApp [MFC], HideApplication
- CWinApp [MFC], HtmlHelp
- CWinApp [MFC], InitInstance
- CWinApp [MFC], IsTaskbarInteractionEnabled
- CWinApp [MFC], LoadCursor
- CWinApp [MFC], LoadIcon
- CWinApp [MFC], LoadOEMCursor
- CWinApp [MFC], LoadOEMIcon
- CWinApp [MFC], LoadStandardCursor
- CWinApp [MFC], LoadStandardIcon
- CWinApp [MFC], OnDDECommand
- CWinApp [MFC], OnIdle
- CWinApp [MFC], OpenDocumentFile
- CWinApp [MFC], ParseCommandLine
- CWinApp [MFC], PreTranslateMessage
- CWinApp [MFC], ProcessMessageFilter
- CWinApp [MFC], ProcessShellCommand
- CWinApp [MFC], ProcessWndProcException
- CWinApp [MFC], Register
- CWinApp [MFC], RegisterWithRestartManager
- CWinApp [MFC], ReopenPreviousFilesAtRestart
- CWinApp [MFC], RestartInstance
- CWinApp [MFC], RestoreAutosavedFilesAtRestart
- CWinApp [MFC], Run
- CWinApp [MFC], RunAutomated
- CWinApp [MFC], RunEmbedded
- CWinApp [MFC], SaveAllModified
- CWinApp [MFC], SelectPrinter
- CWinApp [MFC], SetHelpMode
- CWinApp [MFC], SupportsApplicationRecovery
- CWinApp [MFC], SupportsAutosaveAtInterval
- CWinApp [MFC], SupportsAutosaveAtRestart
- CWinApp [MFC], SupportsRestartManager
- CWinApp [MFC], Unregister
- CWinApp [MFC], WinHelp
- CWinApp [MFC], WriteProfileBinary
- CWinApp [MFC], WriteProfileInt
- CWinApp [MFC], WriteProfileString
- CWinApp [MFC], EnableShellOpen
- CWinApp [MFC], LoadStdProfileSettings
- CWinApp [MFC], OnContextHelp
- CWinApp [MFC], OnFileNew
- CWinApp [MFC], OnFileOpen
- CWinApp [MFC], OnFilePrintSetup
- CWinApp [MFC], OnHelp
- CWinApp [MFC], OnHelpFinder
- CWinApp [MFC], OnHelpIndex
- CWinApp [MFC], OnHelpUsing
- CWinApp [MFC], RegisterShellFileTypes
- CWinApp [MFC], SetAppID
- CWinApp [MFC], SetRegistryKey
- CWinApp [MFC], UnregisterShellFileTypes
- CWinApp [MFC], m_bHelpMode
- CWinApp [MFC], m_eHelpType
- CWinApp [MFC], m_hInstance
- CWinApp [MFC], m_lpCmdLine
- CWinApp [MFC], m_nCmdShow
- CWinApp [MFC], m_pActiveWnd
- CWinApp [MFC], m_pszAppID
- CWinApp [MFC], m_pszAppName
- CWinApp [MFC], m_pszExeName
- CWinApp [MFC], m_pszHelpFilePath
- CWinApp [MFC], m_pszProfileName
- CWinApp [MFC], m_pszRegistryKey
- CWinApp [MFC], m_dwRestartManagerSupportFlags
- CWinApp [MFC], m_nAutosaveInterval
- CWinApp [MFC], m_pDataRecoveryHandler
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 037314c8c3a1449dff195052a2fb8a60fa72ff9f
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539588"
---
# <a name="cwinapp-class"></a>CWinApp 类
派生出 Windows 应用程序对象的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CWinApp : public CWinThread  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CWinApp::CWinApp](#cwinapp)|构造 `CWinApp` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWinApp::AddDocTemplate](#adddoctemplate)|将文档模板添加到可用的文档模板的应用程序的列表。|  
|[CWinApp::AddToRecentFileList](#addtorecentfilelist)|将文件名添加到最近使用 (过的 MRU) 文件列表。|  
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|应用程序意外退出时由框架调用。|  
|[CWinApp::CloseAllDocuments](#closealldocuments)|关闭所有打开的文档。|  
|[CWinApp::CreatePrinterDC](#createprinterdc)|创建打印机设备上下文。|  
|[CWinApp::DelRegTree](#delregtree)|删除指定的项及其所有子项。|  
|[CWinApp::DoMessageBox](#domessagebox)|实现[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)应用程序。|  
|[CWinApp::DoWaitCursor](#dowaitcursor)|打开和关闭将等待光标。|  
|[CWinApp::EnableD2DSupport](#enabled2dsupport)|启用应用程序 D2D 支持。 在初始化主窗口之前调用此方法。|  
|[CWinApp::EnableHtmlHelp](#enablehtmlhelp)|实现用于将应用程序，而不是 WinHelp HTMLHelp。|  
|[CWinApp::EnableTaskbarInteraction](#enabletaskbarinteraction)|启用任务栏交互。|  
|[CWinApp::ExitInstance](#exitinstance)|若要清理你的应用程序终止时的重写。|  
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|检索应用程序恢复方法的输入的参数。|  
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|返回有关恢复回调函数以返回等待重新启动管理器的时间长度。|  
|[CWinApp::GetApplicationRestartFlags](#getapplicationrestartflags)|重新启动管理器返回的标志。|  
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|返回键 HKEY_CURRENT_USER\\"简称软件"\RegistryKey\ProfileName。|  
|[CWinApp::GetDataRecoveryHandler](#getdatarecoveryhandler)|获取此实例的应用程序的数据恢复处理程序。|  
|[CWinApp::GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|检索的第一个文档模板的位置。|  
|[CWinApp::GetHelpMode](#gethelpmode)|检索帮助应用程序使用的类型。|  
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|检索文档模板的位置。 可以使用以递归方式。|  
|[CWinApp::GetPrinterDeviceDefaults](#getprinterdevicedefaults)|检索打印机设备默认值。|  
|[CWinApp::GetProfileBinary](#getprofilebinary)|从应用程序中的条目中检索二进制数据。INI 文件。|  
|[CWinApp::GetProfileInt](#getprofileint)|从应用程序中的条目中检索一个整数。INI 文件。|  
|[CWinApp::GetProfileString](#getprofilestring)|从应用程序中的条目中检索的字符串。INI 文件。|  
|[CWinApp::GetSectionKey](#getsectionkey)|返回键 HKEY_CURRENT_USER\\"简称软件"\RegistryKey\AppName\lpszSection。|  
|[CWinApp::HideApplication](#hideapplication)|隐藏应用程序，然后关闭所有文档。|  
|[CWinApp::HtmlHelp](#htmlhelp)|调用`HTMLHelp`Windows 函数。|  
|[Cwinapp:: Initinstance](#initinstance)|重写以执行 Windows 实例初始化，如创建窗口对象。|  
|[CWinApp::IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|指示是否启用了 Windows 7 任务栏交互。|  
|[CWinApp::LoadCursor](#loadcursor)|加载光标资源。|  
|[CWinApp::LoadIcon](#loadicon)|加载图标资源。|  
|[CWinApp::LoadOEMCursor](#loadoemcursor)|加载 Windows OEM 预定义的游标， **OCR_** 常量指定在 WINDOWS 中。H.|  
|[CWinApp::LoadOEMIcon](#loadoemicon)|加载 Windows OEM 预定义的图标， **OIC_** 常量指定在 WINDOWS 中。H.|  
|[CWinApp::LoadStandardCursor](#loadstandardcursor)|加载 Windows 预定义的游标， **IDC_** 常量指定在 WINDOWS 中。H.|  
|[CWinApp::LoadStandardIcon](#loadstandardicon)|加载 Windows 预定义的图标， **IDI_** 常量指定在 WINDOWS 中。H.|  
|[CWinApp::OnDDECommand](#onddecommand)|调用由框架响应动态数据交换 (DDE) 执行命令。|  
|[CWinApp::OnIdle](#onidle)|重写以执行特定于应用程序空闲时处理。|  
|[CWinApp::OpenDocumentFile](#opendocumentfile)|由框架调用以从文件打开文档。|  
|[CWinApp::ParseCommandLine](#parsecommandline)|分析每个参数和命令行中的标志。|  
|[CWinApp::PreTranslateMessage](#pretranslatemessage)|发送到 Windows 函数之前筛选消息[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)并[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)。|  
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|到达应用程序之前截获某些消息。|  
|[CWinApp::ProcessShellCommand](#processshellcommand)|处理命令行参数和标志。|  
|[CWinApp::ProcessWndProcException](#processwndprocexception)|截获由应用程序的消息和命令处理程序引发的所有未处理的异常。|  
|[CWinApp::Register](#register)|执行自定义的注册。|  
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|与重新启动管理器注册该应用程序。|  
|[CWinApp::ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|确定是否重新启动管理器重新打开该应用程序意外退出时，打开了文件。|  
|[CWinApp::RestartInstance](#restartinstance)|处理重新启动管理器启动应用程序重启。|  
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|确定是否重新启动管理器还原自动保存的文件，重新启动该应用程序时。|  
|[Cwinapp:: Run](#run)|运行默认消息循环。 重写自定义消息循环。|  
|[CWinApp::RunAutomated](#runautomated)|测试应用程序的命令行 **/Automation**选项。 已过时。 相反，使用中的值[CCommandLineInfo::m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated)后调用[ParseCommandLine](#parsecommandline)。|  
|[CWinApp::RunEmbedded](#runembedded)|测试应用程序的命令行 **/嵌入**选项。 已过时。 相反，使用中的值[CCommandLineInfo::m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded)后调用[ParseCommandLine](#parsecommandline)。|  
|[CWinApp::SaveAllModified](#saveallmodified)|提示用户保存所有已修改的文档。|  
|[CWinApp::SelectPrinter](#selectprinter)|选择打印机之前由用户完成一个打印对话框。|  
|[CWinApp::SetHelpMode](#sethelpmode)|设置和初始化的帮助应用程序使用的类型。|  
|[CWinApp::SupportsApplicationRecovery](#supportsapplicationrecovery)|确定是否重新启动管理器恢复的应用程序意外退出。|  
|[CWinApp::SupportsAutosaveAtInterval](#supportsautosaveatinterval)|确定是否重新启动管理器则自动保存在固定时间间隔打开文档。|  
|[CWinApp::SupportsAutosaveAtRestart](#supportsautosaveatrestart)|确定是否重新启动管理器则自动保存任何打开文档时应用程序重新启动。|  
|[CWinApp::SupportsRestartManager](#supportsrestartmanager)|确定应用程序是否支持重新启动管理器。|  
|[CWinApp::Unregister](#unregister)|注销的一切已知要注册的内容`CWinApp`对象。|  
|[CWinApp::WinHelp](#winhelp)|调用`WinHelp`Windows 函数。|  
|[CWinApp::WriteProfileBinary](#writeprofilebinary)|将二进制数据写入到应用程序中的条目。INI 文件。|  
|[Cwinapp:: Writeprofileint](#writeprofileint)|将整数写入到应用程序中的条目。INI 文件。|  
|[CWinApp::WriteProfileString](#writeprofilestring)|将字符串写入到应用程序中的条目。INI 文件。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWinApp::EnableShellOpen](#enableshellopen)|允许用户从 Windows 文件管理器中打开数据文件。|  
|[CWinApp::LoadStdProfileSettings](#loadstdprofilesettings)|加载标准。INI 文件设置和启用 MRU 文件列表功能。|  
|[CWinApp::OnContextHelp](#oncontexthelp)|处理应用程序中的 SHIFT + F1 帮助。|  
|[CWinApp::OnFileNew](#onfilenew)|实现 ID_FILE_NEW 命令。|  
|[CWinApp::OnFileOpen](#onfileopen)|实现 ID_FILE_OPEN 命令。|  
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|实现 ID_FILE_PRINT_SETUP 命令。|  
|[CWinApp::OnHelp](#onhelp)|处理应用程序中的 F1 帮助（使用当前上下文）。|  
|[CWinApp::OnHelpFinder](#onhelpfinder)|处理 ID_HELP_FINDER 和 ID_DEFAULT_HELP 命令。|  
|[CWinApp::OnHelpIndex](#onhelpindex)|处理 ID_HELP_INDEX 命令并提供默认帮助主题。|  
|[CWinApp::OnHelpUsing](#onhelpusing)|处理 ID_HELP_USING 命令。|  
|[对下列项自动](#registershellfiletypes)|注册应用程序的所有文档类型与 Windows 文件管理器。|  
|[CWinApp::SetAppID](#setappid)|显式设置为应用程序的应用程序用户模型 ID。 任何用户界面呈现给用户 （的最佳位置是应用程序构造函数） 之前，应调用此方法。|  
|[CWinApp::SetRegistryKey](#setregistrykey)|导致应用程序设置存储在注册表中而不是。INI 文件。|  
|[CWinApp::UnregisterShellFileTypes](#unregistershellfiletypes)|取消注册应用程序的所有文档类型与 Windows 文件管理器。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CWinApp::m_bHelpMode](#m_bhelpmode)|指示用户是否正在帮助上下文模式 （通常使用 SHIFT + F1 调用）。|  
|[CWinApp::m_eHelpType](#m_ehelptype)|指定的帮助应用程序使用的类型。|  
|[CWinApp::m_hInstance](#m_hinstance)|标识应用程序的当前实例。|  
|[CWinApp::m_lpCmdLine](#m_lpcmdline)|指向以 null 终止的字符串，指定应用程序的命令行。|  
|[CWinApp::m_nCmdShow](#m_ncmdshow)|指定窗口的初始显示方式。|  
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|指向 OLE 服务器处于就地活动状态时的容器应用程序的主窗口的指针。|  
|[CWinApp::m_pszAppID](#m_pszappid)|应用程序用户模型 id。|  
|[CWinApp::m_pszAppName](#m_pszappname)|指定应用程序的名称。|  
|[CWinApp::m_pszExeName](#m_pszexename)|应用程序的模块名称。|  
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|应用程序的帮助文件的路径。|  
|[CWinApp::m_pszProfileName](#m_pszprofilename)|应用程序的。INI 文件名。|  
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|用于确定用于存储应用程序配置文件设置的完整注册表项。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|确定重新启动管理器的行为方式的标志。|  
|[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)|以毫秒为单位，则自动保存之间的时间长度。|  
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|指向应用程序的数据恢复处理程序。|  
  
## <a name="remarks"></a>备注  
 应用程序对象用于初始化你的应用程序 （和它的每个实例） 以及用于运行应用程序提供成员函数。  
  
 使用 Microsoft 基础类每个应用程序只能包含一个对象派生自`CWinApp`。 此对象构造其他 c + + 的全局对象时，会构造并调用 Windows 时已提供`WinMain`函数，由 Microsoft 基础类库提供。 声明你派生`CWinApp`在全局级别的对象。  
  
 从应用程序类派生时`CWinApp`，重写[InitInstance](#initinstance)成员函数来创建应用程序的主窗口对象。  
  
 除了`CWinApp`成员函数，Microsoft 基础类库提供了以下全局函数，以访问您`CWinApp`对象和其他全局信息：  
  
- [AfxGetApp](application-information-and-management.md#afxgetapp)获取指向的`CWinApp`对象。  
  
- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)获取当前应用程序实例的句柄。  
  
- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle)获取应用程序的资源的句柄。  
  
- [AfxGetAppName](application-information-and-management.md#afxgetappname)获取指向包含应用程序的名称的字符串的指针。 或者，如果有一个指针指向`CWinApp`对象，请使用`m_pszExeName`若要获取应用程序的名称。  
  
 请参阅[CWinApp： 应用程序类](../../mfc/cwinapp-the-application-class.md)有关的详细信息`CWinApp`类，包括以下概述：  
  
- `CWinApp`-派生应用程序向导编写的代码。  
  
- `CWinApp`执行顺序的应用程序角色。  
  
- `CWinApp`默认成员函数实现。  
  
- `CWinApp`密钥可重写。  
  
 `m_hPrevInstance`数据成员不再存在。 有关检测的前一个实例的信息`CWinApp`，请参阅知识库文章"如何确定上一实例的应用程序"(KB106385) 网址[ http://support.microsoft.com/default.aspxscid=kb; en-我们; 106385](http://support.microsoft.com/default.aspxscid=kb;en-us;106385)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 `CWinApp`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="adddoctemplate"></a>  CWinApp::AddDocTemplate  
 调用此成员函数以将文档模板添加到该应用程序维护的可用文档模板的列表。  
  
```  
void AddDocTemplate(CDocTemplate* pTemplate);
```  
  
### <a name="parameters"></a>参数  
 *pTemplate*  
 一个指向`CDocTemplate`要添加。  
  
### <a name="remarks"></a>备注  
 应添加所有文档的应用程序的模板，然后再调用[RegisterShellFileTypes](#registershellfiletypes)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]  
  
##  <a name="addtorecentfilelist"></a>  CWinApp::AddToRecentFileList  
 调用此成员函数以添加*lpszPathName*到 MRU 文件列表。  
  
```  
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>参数  
 *lpszPathName*  
 文件的路径。  
  
### <a name="remarks"></a>备注  
 应调用[LoadStdProfileSettings](#loadstdprofilesettings)成员函数以加载当前的 MRU 文件列表，然后使用此成员函数。  
  
 在打开的文件或执行另存为命令，以使用新名称保存文件时，框架将调用此成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]  
  
##  <a name="applicationrecoverycallback"></a>  CWinApp::ApplicationRecoveryCallback  
 应用程序意外退出时由框架调用。  
  
```  
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```  
  
### <a name="parameters"></a>参数  
 [in]*lpvParam*  
 留待将来使用。  
  
### <a name="return-value"></a>返回值  
 如果成功，则此方法，则为 0如果发生错误，非零值。  
  
### <a name="remarks"></a>备注  
 如果你的应用程序支持重新启动管理器，框架将调用此函数，当你的应用程序意外退出。  
  
 默认实现`ApplicationRecoveryCallback`使用`CDataRecoveryHandler`将保存到注册表的当前打开的文档的列表。 此方法执行不自动保存的任何文件。  
  
 若要自定义行为，请重写此函数在派生[CWinApp 类](../../mfc/reference/cwinapp-class.md)或将您自己应用程序的恢复方法作为参数传递[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)。  
  
##  <a name="closealldocuments"></a>  CWinApp::CloseAllDocuments  
 调用此成员函数以在退出之前关闭所有打开的文档。  
  
```  
void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>参数  
 *bEndSession*  
 指定在正在结束 Windows 会话。 它，则会话正在结束; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 调用[HideApplication](#hideapplication)然后才能调用`CloseAllDocuments`。  
  
##  <a name="createprinterdc"></a>  CWinApp::CreatePrinterDC  
 调用此成员函数以创建从所选打印机的打印机设备上下文 (DC)。  
  
```  
BOOL CreatePrinterDC(CDC& dc);
```  
  
### <a name="parameters"></a>参数  
 *dc*  
 对打印机设备上下文的引用。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建打印机设备上下文，非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 `CreatePrinterDC` 初始化在通过引用传递，因此可以使用它来打印设备上下文。  
  
 如果函数成功，在完成打印时，您必须销毁设备上下文。 可以让的析构函数[CDC](../../mfc/reference/cdc-class.md)对象执行此操作，或通过调用，可以显式执行它[CDC::DeleteDC](../../mfc/reference/cdc-class.md#deletedc)。  
  
##  <a name="cwinapp"></a>  CWinApp::CWinApp  
 构造`CWinApp`对象并传递*lpszAppName*存储为应用程序名称。  
  
```  
CWinApp(LPCTSTR lpszAppName = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lpszAppName*  
 以 null 结尾的字符串，其中包含 Windows 使用的应用程序名称。 如果此参数未提供或为 NULL，`CWinApp`使用资源字符串 AFX_IDS_APP_TITLE 或可执行文件的文件名。  
  
### <a name="remarks"></a>备注  
 你应构造的一个全局对象在`CWinApp`-派生的类。 只能有一个`CWinApp`在应用程序中的对象。 构造函数存储一个指向`CWinApp`对象，以便`WinMain`可调用对象的成员函数来初始化和运行应用程序。  
  
##  <a name="delregtree"></a>  CWinApp::DelRegTree  
 删除特定的注册表项及其所有子项。  
  
```  
LONG DelRegTree(
    HKEY hParentKey,  
    const CString& strKeyName);

 
LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName,
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>参数  
 *hParentKey*  
 注册表项的句柄。  
  
 *strKeyName*  
 要删除的注册表项的名称。  
  
 *pTM*  
 指向 CAtlTransactionManager 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，返回值为 ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义一个非零错误代码。  
  
### <a name="remarks"></a>备注  
 调用此函数可删除指定的项及其子项。  
  
##  <a name="domessagebox"></a>  CWinApp::DoMessageBox  
 框架调用此成员函数以实现全局函数的消息框[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)。  
  
```  
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,  
    UINT nType,  
    UINT nIDPrompt);
```  
  
### <a name="parameters"></a>参数  
 *lpszPrompt*  
 在消息框文本的地址。  
  
 *n 类型*  
 消息框[样式](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)。  
  
 *nIDPrompt*  
 帮助上下文字符串的索引。  
  
### <a name="return-value"></a>返回值  
 返回与相同的值`AfxMessageBox`。  
  
### <a name="remarks"></a>备注  
 不调用此成员函数以打开一个消息框;使用`AfxMessageBox`相反。  
  
 重写此成员函数以自定义你的应用程序范围内处理的`AfxMessageBox`调用。  
  
##  <a name="dowaitcursor"></a>  CWinApp::DoWaitCursor  
 由框架来实现调用此成员函数[CWaitCursor](../../mfc/reference/cwaitcursor-class.md)， [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)， [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)，和[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。  
  
```  
virtual void DoWaitCursor(int nCode);
```  
  
### <a name="parameters"></a>参数  
 *nCode*  
 如果此参数为 1，将显示等待光标。 如果为 0，而无需递增引用计数还原将等待光标。 如果为-1，结束等待光标。  
  
### <a name="remarks"></a>备注  
 默认实现沙漏光标。 `DoWaitCursor` 维护引用计数。 在为正时, 将显示沙漏光标。  
  
 尽管您通常不会调用`DoWaitCursor`直接，可以重写此成员函数以更改将等待光标或执行附加的处理时显示等待光标。  
  
 有关的更简单、 更流畅地方法来实现等待光标，使用`CWaitCursor`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]  
  
##  <a name="enabled2dsupport"></a>  CWinApp::EnableD2DSupport  
 需要 Visual Studio 2010 SP1。  
  
 启用应用程序 D2D 支持。 在初始化主窗口之前调用此方法。  
  
```  
BOOL EnableD2DSupport(
D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>参数  
 *d2dFactoryType*  
 它创建 D2D 工厂和资源的线程模型。  
  
 *writeFactoryType*  
 一个值，指定是否将共享或隔离写工厂对象  
  
### <a name="return-value"></a>返回值  
 D2D 支持是否已启用，FALSE-否则将返回 TRUE  
  
##  <a name="enablehtmlhelp"></a>  CWinApp::EnableHtmlHelp  
 调用此成员函数的构造函数中你`CWinApp`的派生类 HTMLHelp 用于应用程序的帮助。  
  
```  
void EnableHtmlHelp();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="enableshellopen"></a>  CWinApp::EnableShellOpen  
 调用此函数中，通常从你`InitInstance`替代，用于启用应用程序的用户打开数据文件时它们双击在 Windows 文件管理器中的文件。  
  
```  
void EnableShellOpen();
```  
  
### <a name="remarks"></a>备注  
 调用`RegisterShellFileTypes`成员函数结合使用此函数，或提供。REG 文件，你的应用程序的文档类型的手动注册。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]  
  
##  <a name="enabletaskbarinteraction"></a>  CWinApp::EnableTaskbarInteraction  
 启用任务栏交互。  
  
```  
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bEnable*  
 指定与 Windows 7 任务栏交互 (TRUE)，应启用还是禁用 (FALSE)。  
  
### <a name="return-value"></a>返回值  
 如果任务栏交互可以启用或禁用，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 必须创建主窗口之前调用此方法，否则为它断言并返回 FALSE。  
  
##  <a name="exitinstance"></a>  CWinApp::ExitInstance  
 由框架调用内`Run`成员函数以退出应用程序的此实例。  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>返回值  
 应用程序的退出代码;0 表示没有错误，而大于 0 的值指示错误。 此值用作从返回的值`WinMain`。  
  
### <a name="remarks"></a>备注  
 不要调用此成员函数从任何位置之内`Run`成员函数。  
  
 此函数的默认实现将写入应用程序的框架选项。INI 文件。 重写此函数来清理您的应用程序终止时。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]  
  
##  <a name="getapplicationrecoveryparameter"></a>  CWinApp::GetApplicationRecoveryParameter  
 检索应用程序恢复方法的输入的参数。  
  
```  
virtual LPVOID GetApplicationRecoveryParameter();
```  
  
### <a name="return-value"></a>返回值  
 应用程序恢复方法的默认输入的参数。  
  
### <a name="remarks"></a>备注  
 此函数的默认行为，则返回 NULL。  
  
 有关详细信息，请参阅[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。  
  
##  <a name="getapplicationrecoverypinginterval"></a>  CWinApp::GetApplicationRecoveryPingInterval  
 返回有关恢复回调函数以返回等待重新启动管理器的时间长度。  
  
```  
virtual DWORD GetApplicationRecoveryPingInterval();
```  
  
### <a name="return-value"></a>返回值  
 以毫秒为单位的时间长度。  
  
### <a name="remarks"></a>备注  
 当使用重新启动管理器退出意外注册应用程序时、 应用程序尝试保存打开的文档，并调用恢复的回调函数。 默认恢复回调函数是[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。  
  
 有关恢复回调函数以返回框架等待的时间长度为 ping 时间间隔。 可以通过重写自定义的 ping 间隔`CWinApp::GetApplicationRecoveryPingInterval`或通过提供自定义值到`RegisterWithRestartManager`。  
  
##  <a name="getapplicationrestartflags"></a>  CWinApp::GetApplicationRestartFlags  
 重新启动管理器返回的标志。  
  
```  
virtual DWORD GetApplicationRestartFlags();
```  
  
### <a name="return-value"></a>返回值  
 重新启动管理器的标志。 默认实现将返回 0。  
  
### <a name="remarks"></a>备注  
 重新启动管理器的标志不会影响使用的默认实现。 它们提供以供将来使用。  
  
 与重新启动管理器中使用注册应用程序时设置的标志[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)。  
  
 重新启动管理器标志的可能值如下所示：  
  
- RESTART_NO_CRASH  
  
- RESTART_NO_HANG  
  
- RESTART_NO_PATCH  
  
- RESTART_NO_REBOOT  
  
##  <a name="getappregistrykey"></a>  CWinApp::GetAppRegistryKey  
 返回的键为 HKEY_CURRENT_USER\\"简称软件"\RegistryKey\ProfileName。  
  
```  
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pTM*  
 指向 `CAtlTransactionManager` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则应用程序密钥否则为，为 NULL。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getdatarecoveryhandler"></a>  CWinApp::GetDataRecoveryHandler  
 获取此实例的应用程序的数据恢复处理程序。  
  
```  
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```  
  
### <a name="return-value"></a>返回值  
 此实例的应用程序的数据恢复处理程序。  
  
### <a name="remarks"></a>备注  
 使用重新启动管理器每个应用程序必须具有的一个实例[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)。 此类负责监视打开的文档和自动保存文件。 行为`CDataRecoveryHandler`重新启动管理器的配置决定的。 有关详细信息，请参阅[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)。  
  
 此方法上的操作系统早于 Windows Vista 返回 NULL。 重新启动管理器不是支持的操作系统早于 Windows Vista。  
  
 如果应用程序当前不具有数据恢复处理程序，此方法将创建一个，并返回的指针。  
  
##  <a name="getfirstdoctemplateposition"></a>  CWinApp::GetFirstDocTemplatePosition  
 获取应用程序中的第一个文档模板的位置。  
  
```  
POSITION GetFirstDocTemplatePosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 可用于迭代或检索对象指针; 一个位置值如果列表为空，则为 NULL。  
  
### <a name="remarks"></a>备注  
 使用位置值对的调用中返回[GetNextDocTemplate](#getnextdoctemplate)若要获取第一个[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象。  
  
##  <a name="gethelpmode"></a>  CWinApp::GetHelpMode  
 检索帮助应用程序使用的类型。  
  
```  
AFX_HELP_TYPE GetHelpMode();
```  
  
### <a name="return-value"></a>返回值  
 使用应用程序的帮助类型。 请参阅[CWinApp::m_eHelpType](#m_ehelptype)有关详细信息。  
  
##  <a name="getnextdoctemplate"></a>  CWinApp::GetNextDocTemplate  
 获取由标识的文档模板*pos*，然后设置*pos*为位置值。  
  
```  
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 *pos*  
 对以前调用返回的位置值的引用`GetNextDocTemplate`或[GetFirstDocTemplatePosition](#getfirstdoctemplateposition)。 通过此调用到下一个位置更新的值。  
  
### <a name="return-value"></a>返回值  
 一个指向[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象。  
  
### <a name="remarks"></a>备注  
 可以使用`GetNextDocTemplate`如果建立调用一次的初始位置的向前迭代循环中`GetFirstDocTemplatePosition`。  
  
 您必须确保你的位置值有效。 如果无效，Microsoft 基础类库的调试版本断言。  
  
 如果检索到的文档模板是最后一个可用的新值然后*pos*设置为 NULL。  
  
##  <a name="getprinterdevicedefaults"></a>  CWinApp::GetPrinterDeviceDefaults  
 调用此成员函数以准备用于打印的打印机设备上下文。  
  
```  
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```  
  
### <a name="parameters"></a>参数  
 *pPrintDlg*  
 一个指向[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 从 Windows 中检索当前打印机默认值。INI 文件，必要时，或使用用户在打印设置中设置的最后一个打印机配置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]  
  
##  <a name="getprofilebinary"></a>  CWinApp::GetProfileBinary  
 调用此成员函数可从应用程序的注册表项的指定部分中的条目中检索二进制数据或。INI 文件。  
  
```  
BOOL GetProfileBinary(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPBYTE* ppData,  
    UINT* pBytes);
```  
  
### <a name="parameters"></a>参数  
 *lpszSection*  
 指向以 null 结尾的字符串，该字符串指定包含条目的部分。  
  
 *lpszEntry*  
 指向以 null 结尾的字符串，该字符串包含要检索其值的条目。  
  
 *ppData*  
 指向将接收的数据的地址的指针。  
  
 *pBytes*  
 指向将接收的大小 （以字节为单位） 的数据是 UINT。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数不区分大小写，因此中的字符串*lpszSection*并*lpszEntry*写可能不同的参数。  
  
> [!NOTE]
> `GetProfileBinary` 分配一个缓冲区，并返回其地址中的\* *ppData*。 调用方负责释放缓冲区使用**delete []**。  
  
> [!IMPORTANT]
>  此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]  
  
 有关其他示例，请参阅[CWinApp::WriteProfileBinary](#writeprofilebinary)。  
  
##  <a name="getprofileint"></a>  CWinApp::GetProfileInt  
 调用此成员函数以检索应用程序的注册表或 .INI 文件的指定部分中条目的整数的值。  
  
```  
UINT GetProfileInt(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    int nDefault);
```  
  
### <a name="parameters"></a>参数  
 *lpszSection*  
 指向以 null 结尾的字符串，该字符串指定包含条目的部分。  
  
 *lpszEntry*  
 指向以 null 结尾的字符串，该字符串包含要检索其值的条目。  
  
 *n 默认*  
 指定在框架找不到条目时要返回的默认值。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则为指定条目后面的字符串的整数值。 返回值为的值*n 默认*参数如果函数未找到该条目。 如果与指定条目对应的值不为整数，则返回值为 0。  
  
 在 .INI 文件中，此成员函数支持值的十六进制表示法。 当您检索有符号的整数时，您应将值强制转换到**int**。  
  
### <a name="remarks"></a>备注  
 此成员函数不区分大小写，因此中的字符串*lpszSection*并*lpszEntry*写可能不同的参数。  
  
> [!IMPORTANT]
>  此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]  
  
 有关其他示例，请参阅[cwinapp:: Writeprofileint](#writeprofileint)。  
  
##  <a name="getprofilestring"></a>  CWinApp::GetProfileString  
 调用此成员函数以检索应用程序的注册表中指定的节中的条目相关联的字符串或。INI 文件。  
  
```  
CString GetProfileString(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszDefault = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lpszSection*  
 指向以 null 结尾的字符串，该字符串指定包含条目的部分。  
  
 *lpszEntry*  
 指向包含其字符串是要检索的条目的以 null 结尾的字符串。 此值不能为 NULL。  
  
 *lpszDefault*  
 指向以给定的项目如果初始化文件中找不到该条目的默认字符串值。  
  
### <a name="return-value"></a>返回值  
 返回值是从应用程序的字符串。INI 文件或*lpszDefault*如果无法找到该字符串。 框架支持的最大字符串长度为 _MAX_PATH。 如果*lpszDefault*为 NULL，则返回值为空字符串。  
  
### <a name="remarks"></a>备注  
  
> [!IMPORTANT]
>  此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 有关其他示例，请参阅示例[CWinApp::GetProfileInt](#getprofileint)。  
  
##  <a name="getsectionkey"></a>  CWinApp::GetSectionKey  
 返回的键为 HKEY_CURRENT_USER\\"简称软件"\RegistryKey\AppName\lpszSection。  
  
```  
HKEY GetSectionKey(
LPCTSTR lpszSection,  
CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lpszSection*  
 要获取的键的名称。  
  
 *pTM*  
 指向 `CAtlTransactionManager` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则部分密钥否则为，为 NULL。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hideapplication"></a>  CWinApp::HideApplication  
 调用此成员函数可隐藏应用程序之前关闭打开的文档。  
  
```  
void HideApplication();
```  
  
##  <a name="htmlhelp"></a>  CWinApp::HtmlHelp  
 调用此成员函数以调用 HTMLHelp 应用程序。  
  
```  
virtual void HtmlHelp(
    DWORD_PTR dwData,  
    UINT nCmd = 0x000F);
```  
  
### <a name="parameters"></a>参数  
 *dwData*  
 指定其他数据。 使用的值取决于的值*nCmd*参数。  
  
 *nCmd*  
 指定请求的帮助的类型。 有关一系列可能的值以及它们如何影响*dwData*参数，请参阅*uCommand*有关 HTMLHelp API 函数 Windows SDK 中所述的参数。  
  
### <a name="remarks"></a>备注  
 该框架还会调用此函数可调用 HTMLHelp 应用程序。  
  
 当你的应用程序终止时，框架会自动关闭 HTMLHelp 应用程序。  
  
##  <a name="initinstance"></a>  Cwinapp:: Initinstance  
 Windows 允许要在同一时间运行的相同程序的多个副本。  
  
```  
virtual BOOL InitInstance();
```  
  
### <a name="return-value"></a>返回值  
 如果初始化成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 应用程序初始化从概念上讲划分为两个部分： 首先执行的一次性应用程序初始化时间运行的程序，并在每个运行的实例初始化的时间运行的程序，包括第一次的副本。 框架的实现`WinMain`调用此函数。  
  
 重写`InitInstance`初始化在 Windows 下运行的应用程序的每个新实例。 通常情况下，重写`InitInstance`来构造您的主窗口对象和设置`CWinThread::m_pMainWnd`数据成员，使其指向该窗口。 重写此成员函数的详细信息，请参阅[CWinApp： 应用程序类](../../mfc/cwinapp-the-application-class.md)。  
  
> [!NOTE]
>  MFC 应用程序必须初始化为单线程单元 (STA)。 如果您调用[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)在你`InitInstance`重写中，指定 COINIT_APARTMENTTHREADED （而非 COINIT_MULTITHREADED）。 有关详细信息，请参阅 PRB: MFC 应用程序停止响应时初始化为多线程单元 （828643） 在应用程序[ http://support.microsoft.com/default.aspxscid=kb; en-我们; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]  
  
##  <a name="istaskbarinteractionenabled"></a>  CWinApp::IsTaskbarInteractionEnabled  
 指示是否启用了 Windows 7 任务栏交互。  
  
```  
virtual BOOL IsTaskbarInteractionEnabled();
```  
  
### <a name="return-value"></a>返回值  
 返回 true; 否则`EnableTaskbarInteraction`已调用和操作系统是 Windows 7 或更高版本。  
  
### <a name="remarks"></a>备注  
 任务栏交互意味着 MDI 应用程序在鼠标指针位于应用程序的任务栏按钮时显示的单独选项卡式缩略图中显示 MDI 子窗体的内容。  
  
##  <a name="loadcursor"></a>  CWinApp::LoadCursor  
 加载由名为的光标资源*lpszResourceName*或者指定*nIDResource*从当前的可执行文件。  
  
```  
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpszResourceName*  
 指向包含游标资源的名称的以 null 结尾的字符串。 可以使用`CString`为此参数。  
  
 *nIDResource*  
 游标资源的 ID。 有关资源的列表，请参阅[LoadCursor](http://msdn.microsoft.com/library/windows/desktop/ms648391) Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 句柄游标，如果成功，则否则为，为 NULL。  
  
### <a name="remarks"></a>备注  
 `LoadCursor` 将光标加载到内存中，仅当它以前加载;否则，它将检索现有资源的句柄。  
  
 使用[LoadStandardCursor](#loadstandardcursor)或[LoadOEMCursor](#loadoemcursor)成员函数来访问预定义的 Windows 游标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]  
  
##  <a name="loadicon"></a>  CWinApp::LoadIcon  
 加载由名为的图标资源*lpszResourceName*或者指定*nIDResource*从可执行文件。  
  
```  
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpszResourceName*  
 指向包含图标资源的名称的以 null 结尾的字符串。 此外可以使用`CString`为此参数。  
  
 *nIDResource*  
 图标资源的 ID 号。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为图标的句柄否则为，为 NULL。  
  
### <a name="remarks"></a>备注  
 `LoadIcon` 仅当它以前加载; 加载的图标否则，它将检索现有资源的句柄。  
  
 可以使用[LoadStandardIcon](#loadstandardicon)或[LoadOEMIcon](#loadoemicon)成员函数来访问预定义的 Windows 图标。  
  
> [!NOTE]
>  此成员函数将调用 Win32 API 函数[LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072)，其中只能加载 SM_CXICON 和 SM_CYICON 系统指标值符合其大小的图标。  
  
##  <a name="loadoemcursor"></a>  CWinApp::LoadOEMCursor  
 加载 Windows 预定义的指定游标资源*nIDCursor*。  
  
```  
HCURSOR LoadOEMCursor(UINT nIDCursor) const;  
```  
  
### <a name="parameters"></a>参数  
 *nIDCursor*  
 **OCR_** 清单常量指定预定义的 Windows 光标的标识符。 您必须具有`#define OEMRESOURCE`之前`#include \<afxwin.h>`若要获取访问权限**OCR_** WINDOWS 中的常量。H.  
  
### <a name="return-value"></a>返回值  
 句柄游标，如果成功，则否则为，为 NULL。  
  
### <a name="remarks"></a>备注  
 使用`LoadOEMCursor`或[LoadStandardCursor](#loadstandardcursor)成员函数来访问预定义的 Windows 游标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]  
  
 [!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]  
  
##  <a name="loadoemicon"></a>  CWinApp::LoadOEMIcon  
 加载 Windows 预定义的指定图标资源*nIDIcon*。  
  
```  
HICON LoadOEMIcon(UINT nIDIcon) const;  
```  
  
### <a name="parameters"></a>参数  
 *nIDIcon*  
 **OIC_** 清单常量指定预定义的 Windows 图标的标识符。 您必须具有`#define OEMRESOURCE`之前`#include \<afxwin.h>`访问**OIC_** WINDOWS 中的常量。H.  
  
### <a name="return-value"></a>返回值  
 如果成功，则为图标的句柄否则为，为 NULL。  
  
### <a name="remarks"></a>备注  
 使用`LoadOEMIcon`或[LoadStandardIcon](#loadstandardicon)成员函数来访问预定义的 Windows 图标。  
  
##  <a name="loadstandardcursor"></a>  CWinApp::LoadStandardCursor  
 加载 Windows 预定义的游标资源的*lpszCursorName*指定。  
  
```  
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpszCursorName*  
 **IDC_** 清单常量指定预定义的 Windows 光标的标识符。 这些标识符是在 WINDOWS 中定义的。H. 以下列表显示了可能的预定义的值和含义*lpszCursorName*:  
  
- IDC_ARROW 标准箭头光标  
  
- IDC_IBEAM 标准文本插入光标  
  
- 使用 Windows 执行耗时任务时 IDC_WAIT 沙漏光标  
  
- 所选内容的 IDC_CROSS 十字线光标  
  
- 垂直向上 IDC_UPARROW 箭头  
  
- IDC_SIZE 过时和不受支持;使用 IDC_SIZEALL  
  
- IDC_SIZEALL 一个四指向箭头。 要用于调整窗口大小的光标。  
  
- IDC_ICON 过时和不受支持。 使用 IDC_ARROW。  
  
- 在左上角和右下方的端点为 IDC_SIZENWSE 的双向箭头  
  
- 使用较低和右左上为止 IDC_SIZENESW 的双向箭头  
  
- IDC_SIZEWE 水平双向箭头  
  
- IDC_SIZENS 垂直双向箭头  
  
### <a name="return-value"></a>返回值  
 句柄游标，如果成功，则否则为，为 NULL。  
  
### <a name="remarks"></a>备注  
 使用`LoadStandardCursor`或[LoadOEMCursor](#loadoemcursor)成员函数来访问预定义的 Windows 游标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]  
  
##  <a name="loadstandardicon"></a>  CWinApp::LoadStandardIcon  
 加载 Windows 预定义的图标资源的*lpszIconName*指定。  
  
```  
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpszIconName*  
 指定预定义的 Windows 图标清单常量标识符。 这些标识符是在 WINDOWS 中定义的。H. 预定义的可能值及其说明的列表，请参阅*lpIconName*中的参数[LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072) Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为图标的句柄否则为，为 NULL。  
  
### <a name="remarks"></a>备注  
 使用`LoadStandardIcon`或[LoadOEMIcon](#loadoemicon)成员函数来访问预定义的 Windows 图标。  
  
##  <a name="loadstdprofilesettings"></a>  CWinApp::LoadStdProfileSettings  
 在调用此成员函数[InitInstance](#initinstance)成员函数来启用和加载最近使用 (过的 MRU) 文件的列表和上一次预览状态。  
  
```  
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```  
  
### <a name="parameters"></a>参数  
 *nMaxMRU*  
 最近使用要跟踪的文件数。  
  
### <a name="remarks"></a>备注  
 如果*nMaxMRU*为 0，则没有 MRU 列表将保持不变。  
  
##  <a name="m_bhelpmode"></a>  CWinApp::m_bHelpMode  
 应用程序中的帮助上下文模式 （按传统方法调用使用了 SHIFT + F1）; 如果为 TRUE否则为 FALSE。  
  
```  
BOOL m_bHelpMode;  
```  
  
### <a name="remarks"></a>备注  
 在帮助上下文模式下，光标将变为一个问号和用户可以将其移动屏幕信息。 如果您想要实现特殊处理，在帮助模式时，请检查此标志。 `m_bHelpMode` BOOL 类型的公共变量。  
  
##  <a name="m_dwrestartmanagersupportflags"></a>  CWinApp::m_dwRestartManagerSupportFlags  
 确定重新启动管理器的行为方式的标志。  
  
```  
DWORD m_dwRestartManagerSupportFlags;  
```  
  
### <a name="remarks"></a>备注  
 若要重新启动管理器，设置`m_dwRestartManagerSupportFlags`到所需的行为。 下表显示了可用的标志。  
  
|||  
|-|-|  
|Flag|描述|  
|AFX_RESTART_MANAGER_SUPPORT_RESTART|使用注册应用程序[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)。 重新启动管理器负责重新启动应用程序，如果意外退出。|  
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY|重新启动管理器注册该应用程序，并且重新启动该应用程序时，重新启动管理器调用恢复的回调函数。 默认恢复回调函数是[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。|  
|-AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|启用了自动保存和重新启动管理器则自动保存任何打开文档时应用程序重新启动。|  
|-AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|启用了自动保存和重新启动管理器则自动保存任何打开文档的定期时间间隔。 通过定义间隔[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)。|  
|-AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|在重新启动从意外的退出应用程序后，重新启动管理器打开以前打开的文档。 [CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)处理存储的打开的文档列表并将它们还原。|  
|-AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|重新启动管理器会提示用户重新启动该应用程序后还原自动保存文件。 `CDataRecoveryHandler`类会询问用户。|  
|-AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|AFX_RESTART_MANAGER_SUPPORT_RESTART、 AFX_RESTART_MANAGER_SUPPORT_RECOVER 和 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 的并集。|  
|-AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE、 AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART、 AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL 和 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES 的联合。|  
|-AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_RESTART、 AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART、 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 和 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES 的联合。|  
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|联合 ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY、 AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL、 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 和 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES。|  
  
##  <a name="m_ehelptype"></a>  CWinApp::m_eHelpType  
 此数据成员的类型是枚举的类型 AFX_HELP_TYPE，在其中定义`CWinApp`类。  
  
```  
AFX_HELP_TYPE m_eHelpType;  
```  
  
### <a name="remarks"></a>备注  
 AFX_HELP_TYPE 枚举定义，如下所示：  
  
```  
enum AFX_HELP_TYPE {  
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };  
```  
  
-   若要设置到 HTML 帮助应用程序的帮助，请调用[SetHelpMode](#sethelpmode)并指定`afxHTMLHelp`。  
  
-   若要设置到 WinHelp 的应用程序的帮助，请调用`SetHelpMode`并指定`afxWinHelp`。  
  
##  <a name="m_hinstance"></a>  CWinApp::m_hInstance  
 对应于*hInstance*参数传递到 Windows `WinMain`。  
  
```  
HINSTANCE m_hInstance;  
```  
  
### <a name="remarks"></a>备注  
 `m_hInstance`数据成员是在 Windows 下运行的应用程序的当前实例的句柄。 这由全局函数返回[AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)。 `m_hInstance` 是类型 HINSTANCE 的公共变量。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]  
  
##  <a name="m_lpcmdline"></a>  CWinApp::m_lpCmdLine  
 对应于*lpCmdLine*参数传递到 Windows `WinMain`。  
  
```  
LPTSTR m_lpCmdLine;  
```  
  
### <a name="remarks"></a>备注  
 指向以 null 终止的字符串，指定应用程序的命令行。 使用`m_lpCmdLine`访问用户在应用程序启动时输入的任何命令行参数。 `m_lpCmdLine` 是公共类型的变量的 LPTSTR。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]  
  
##  <a name="m_nautosaveinterval"></a>  CWinApp::m_nAutosaveInterval  
 以毫秒为单位，则自动保存之间的时间长度。  
  
```  
int m_nAutosaveInterval;  
```  
  
### <a name="remarks"></a>备注  
 可以按设置的间隔配置为自动保存打开的文档的重新启动管理器。 如果你的应用程序不自动保存文件，则此参数无效。  
  
##  <a name="m_ncmdshow"></a>  CWinApp::m_nCmdShow  
 对应于*nCmdShow*参数传递到 Windows `WinMain`。  
  
```  
int m_nCmdShow;  
```  
  
### <a name="remarks"></a>备注  
 应传递`m_nCmdShow`作为参数调用时[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)的应用程序的主窗口。 `m_nCmdShow` 是类型的公共变量**int**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]  
  
##  <a name="m_pactivewnd"></a>  CWinApp::m_pActiveWnd  
 使用此数据成员来存储指向 OLE 容器应用程序在 OLE 服务器应用程序的就地激活的主窗口的指针。  
  
### <a name="remarks"></a>备注  
 如果此数据成员为 NULL，该应用程序不是处于就地活动状态。  
  
 就地激活的 OLE 容器应用程序框架窗口时，框架将设置此成员变量。  
  
##  <a name="m_pdatarecoveryhandler"></a>  CWinApp::m_pDataRecoveryHandler  
 指向应用程序的数据恢复处理程序。  
  
```  
CDataRecoveryHandler* m_pDataRecoveryHandler;  
```  
  
### <a name="remarks"></a>备注  
 数据恢复处理程序的应用程序监视打开的文档和则自动保存它们。 框架使用的数据恢复处理程序时意外退出后，重新启动应用程序还原自动保存文件。 有关详细信息，请参阅[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)。  
  
##  <a name="m_pszappname"></a>  CWinApp::m_pszAppName  
 指定应用程序的名称。  
  
```  
LPCTSTR m_pszAppName;  
```  
  
### <a name="remarks"></a>备注  
 应用程序名称可以来自参数传递给[CWinApp](#cwinapp)构造函数，或者，如果未指定，到使用 AFX_IDS_APP_TITLE ID 的资源字符串。 如果在资源中找不到应用程序名称，它将来自该程序。EXE 文件名。  
  
 全局函数返回[AfxGetAppName](application-information-and-management.md#afxgetappname)。 `m_pszAppName` 是类型的公共变量**const char\***。  
  
> [!NOTE]
>  如果你将值赋给`m_pszAppName`，它必须动态分配堆上。 `CWinApp`析构函数调用**免费**（与此指针)。 很多想要使用`_tcsdup`（） 运行时库函数来执行分配。 此外，释放分配新值之前将其与当前指针相关联的内存。 例如：  
  
 [!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]  
  
##  <a name="m_pszexename"></a>  CWinApp::m_pszExeName  
 包含不带扩展名的应用程序的可执行文件的名称。  
  
```  
LPCTSTR m_pszExeName;  
```  
  
### <a name="remarks"></a>备注  
 与不同[m_pszAppName](#m_pszappname)，此名称不能包含空格。 `m_pszExeName` 是类型的公共变量**const char\***。  
  
> [!NOTE]
>  如果你将值赋给`m_pszExeName`，它必须动态分配堆上。 `CWinApp`析构函数调用**免费**（与此指针)。 很多想要使用`_tcsdup`（） 运行时库函数来执行分配。 此外，释放分配新值之前将其与当前指针相关联的内存。 例如：  
  
 [!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]  
  
##  <a name="m_pszhelpfilepath"></a>  CWinApp::m_pszHelpFilePath  
 包含应用程序的帮助文件的路径。  
  
```  
LPCTSTR m_pszHelpFilePath;  
```  
  
### <a name="remarks"></a>备注  
 默认情况下，框架初始化`m_pszHelpFilePath`到与应用程序的名称"。HLP"追加。 若要更改的帮助文件的名称，设置`m_pszHelpFilePath`以指向包含所需的帮助文件的完整名称的字符串。 若要执行此操作方便位置是在应用程序的[InitInstance](#initinstance)函数。 `m_pszHelpFilePath` 是类型的公共变量**const char\***。  
  
> [!NOTE]
>  如果你将值赋给`m_pszHelpFilePath`，它必须动态分配堆上。 `CWinApp`析构函数调用**免费**（与此指针)。 很多想要使用`_tcsdup`（） 运行时库函数来执行分配。 此外，释放分配新值之前将其与当前指针相关联的内存。 例如：  
  
 [!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]  
  
##  <a name="m_pszprofilename"></a>  CWinApp::m_pszProfileName  
 包含在应用程序的名称。INI 文件。  
  
```  
LPCTSTR m_pszProfileName;  
```  
  
### <a name="remarks"></a>备注  
 `m_pszProfileName` 是类型的公共变量**const char\***。  
  
> [!NOTE]
>  如果你将值赋给`m_pszProfileName`，它必须动态分配堆上。 `CWinApp`析构函数调用**免费**（与此指针)。 很多想要使用`_tcsdup`（） 运行时库函数来执行分配。 此外，释放分配新值之前将其与当前指针相关联的内存。 例如：  
  
 [!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]  
  
##  <a name="m_pszregistrykey"></a>  CWinApp::m_pszRegistryKey  
 用于确定，在注册表或 INI 文件中，应用程序配置文件设置的存储位置。  
  
```  
LPCTSTR m_pszRegistryKey;  
```  
  
### <a name="remarks"></a>备注  
 通常情况下，此数据成员将被处理为只读的。  
  
-   值存储到注册表项。 应用程序配置文件设置的名称追加到以下注册表项： HKEY_CURRENT_USER/软件/LocalAppWizard 生成 /。  
  
 如果你将值赋给`m_pszRegistryKey`，它必须动态分配堆上。 `CWinApp`析构函数调用**免费**（与此指针)。 很多想要使用`_tcsdup`（） 运行时库函数来执行分配。 此外，释放分配新值之前将其与当前指针相关联的内存。 例如：  
  
 [!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]  
  
##  <a name="m_pszappid"></a>  CWinApp::m_pszAppID  
 应用程序用户模型 id。  
  
```  
LPCTSTR m_pszAppID;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="oncontexthelp"></a>  CWinApp::OnContextHelp  
 处理应用程序中的 SHIFT + F1 帮助。  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>备注  
 必须添加`ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )`语句在`CWinApp`类消息映射，还将添加快捷键对应表项，通常 SHIFT + F1，若要启用此成员函数。  
  
 `OnContextHelp` 将应用程序进入帮助模式。 然后，光标更改为一个箭头和问号，以及用户可以将鼠标指针移动，并按鼠标左键选择对话框、 窗口、 菜单或命令按钮。 此成员函数检索光标下的对象的帮助上下文，并调用 Windows 函数 WinHelp 与该帮助上下文。  
  
##  <a name="onddecommand"></a>  CWinApp::OnDDECommand  
 由框架调用，当主框架窗口收到 DDE 执行消息。  
  
```  
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```  
  
### <a name="parameters"></a>参数  
 *lpszCommand*  
 指向以对应用程序收到的 DDE 命令字符串。  
  
### <a name="return-value"></a>返回值  
 如果处理该命令; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现检查命令是否打开的文档的请求，是否是这样，将打开指定的文档。 当用户双击数据文件时，Windows 文件管理器通常将发送此类 DDE 命令字符串。 重写此函数以处理其他 DDE 执行命令，如要打印的命令。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]  
  
##  <a name="onfilenew"></a>  CWinApp::OnFileNew  
 实现 ID_FILE_NEW 命令。  
  
```  
afx_msg void OnFileNew();
```  
  
### <a name="remarks"></a>备注  
 必须添加`ON_COMMAND( ID_FILE_NEW, OnFileNew )`语句在`CWinApp`类消息映射，若要启用此成员函数。 如果启用，此函数将处理新文件的命令的执行。  
  
 请参阅[技术说明 22](../../mfc/tn022-standard-commands-implementation.md)有关默认行为，并指导如何重写此成员函数的信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="onfileopen"></a>  CWinApp::OnFileOpen  
 实现 ID_FILE_OPEN 命令。  
  
```  
afx_msg void OnFileOpen();
```  
  
### <a name="remarks"></a>备注  
 必须添加`ON_COMMAND( ID_FILE_OPEN, OnFileOpen )`语句在`CWinApp`类消息映射，若要启用此成员函数。 如果启用，此函数将处理的文件打开命令的执行。  
  
 默认行为的信息和如何重写此成员函数的指南，请参阅[技术说明 22](../../mfc/tn022-standard-commands-implementation.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="onfileprintsetup"></a>  CWinApp::OnFilePrintSetup  
 实现 ID_FILE_PRINT_SETUP 命令。  
  
```  
afx_msg void OnFilePrintSetup();
```  
  
### <a name="remarks"></a>备注  
 必须添加`ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )`语句在`CWinApp`类消息映射，若要启用此成员函数。 如果启用，此函数将处理文件打印命令的执行。  
  
 默认行为的信息和如何重写此成员函数的指南，请参阅[技术说明 22](../../mfc/tn022-standard-commands-implementation.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="onhelp"></a>  CWinApp::OnHelp  
 处理应用程序中的 F1 帮助（使用当前上下文）。  
  
```  
afx_msg void OnHelp();
```  
  
### <a name="remarks"></a>备注  
 通常，您还将添加 F1 键的加速键条目。 启用 F1 键是仅使用约定，不是要求。  
  
 必须添加`ON_COMMAND( ID_HELP, OnHelp )`语句在`CWinApp`类消息映射，若要启用此成员函数。 如果启用，，在用户按 F1 键时由框架调用。  
  
 此消息处理程序函数的默认实现确定对应于当前窗口、 对话框或菜单项，然后调用 WINHELP 的帮助上下文。EXE。 如果目前没有上下文，该函数将使用默认上下文。  
  
 重写此成员函数设置为窗口、 对话框、 菜单项或当前具有焦点的工具栏按钮以外的帮助上下文。 调用`WinHelp`与所需帮助上下文 id。  
  
##  <a name="onhelpfinder"></a>  CWinApp::OnHelpFinder  
 处理 ID_HELP_FINDER 和 ID_DEFAULT_HELP 命令。  
  
```  
afx_msg void OnHelpFinder();
```  
  
### <a name="remarks"></a>备注  
 必须添加`ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )`语句在`CWinApp`类消息映射，若要启用此成员函数。 如果启用，框架将调用此消息处理程序函数，当应用程序的用户选择要调用的帮助查找器命令`WinHelp`与标准**HELP_FINDER**主题。  
  
##  <a name="onhelpindex"></a>  CWinApp::OnHelpIndex  
 处理 ID_HELP_INDEX 命令并提供默认帮助主题。  
  
```  
afx_msg void OnHelpIndex();
```  
  
### <a name="remarks"></a>备注  
 必须添加`ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )`语句在`CWinApp`类消息映射，若要启用此成员函数。 如果启用，框架将调用此消息处理程序函数，当应用程序的用户选择要调用的帮助索引命令`WinHelp`与标准**HELP_INDEX**主题。  
  
##  <a name="onhelpusing"></a>  CWinApp::OnHelpUsing  
 处理 ID_HELP_USING 命令。  
  
```  
afx_msg void OnHelpUsing();
```  
  
### <a name="remarks"></a>备注  
 必须添加`ON_COMMAND( ID_HELP_USING, OnHelpUsing )`语句在`CWinApp`类消息映射，若要启用此成员函数。 你的应用程序在用户选择要调用的帮助使用命令时，框架将调用此消息处理程序函数`WinHelp`应用程序与标准**HELP_HELPONHELP**主题。  
  
##  <a name="onidle"></a>  CWinApp::OnIdle  
 重写此成员函数以执行空闲处理。  
  
```  
virtual BOOL OnIdle(LONG lCount);
```  
  
### <a name="parameters"></a>参数  
 *lCount*  
 每次增加计数器的数值`OnIdle`当应用程序的消息队列为空时调用。 每次处理新消息时，此计数是置为 0。 可以使用*lCount*参数，以确定的相对应用程序而不会处理一条消息处于空闲状态的时间长度。  
  
### <a name="return-value"></a>返回值  
 非零值，接收更多空闲处理时间;如果需要没有更多空闲时间为 0。  
  
### <a name="remarks"></a>备注  
 `OnIdle` 默认消息循环中应用程序的消息队列为空时调用。 使用重写调用您自己的背景空闲处理程序的任务。  
  
 `OnIdle` 应返回 0 以指示需要没有空闲的处理时间。 *LCount*参数会在每次递增`OnIdle`时消息队列为空，并且将重置为 0 每次处理新消息时调用。 您可以调用基于此计数将不同的空闲例程。  
  
 下面概述了空闲循环处理：  
  
1.  如果 Microsoft 基础类库中的消息循环检查消息队列，并找到不挂起消息，则会调用`OnIdle`应用程序对象和提供 0 作为*lCount*参数。  
  
2. `OnIdle` 执行一些处理，并返回一个非零值以指示它应再次调用，以执行进一步处理。  
  
3.  消息循环再次检查消息队列。 如果没有消息处于挂起状态，则会调用`OnIdle`同样，递增*lCount*参数。  
  
4.  最终，`OnIdle`完成处理其空闲状态的所有任务，并返回 0。 这将告知消息循环来停止调用`OnIdle`直到从消息队列接收到下一条消息，此时空闲周期会重新启动并将参数设置为 0。  
  
 不执行耗时较长的任务期间`OnIdle`因为您的应用程序无法处理用户输入，直到`OnIdle`返回。  
  
> [!NOTE]
>  默认实现`OnIdle`更新命令用户界面对象，如菜单项和工具栏按钮，它执行内部数据结构清理。 因此，如果重写`OnIdle`，必须调用`CWinApp::OnIdle`与`lCount`中重写版本。 首先调用所有基类空闲处理 (即，直到基类`OnIdle`返回 0)。 如果需要执行的工作，基类处理完成前，查看要选择适当的基类实现*lCount*来完成工作年限。  
  
 如果不希望`OnIdle`若要从消息队列检索消息时调用，可以重写[CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage)。 如果应用程序设置非常短的计时器，或系统将要发送 WM_SYSTIMER 消息，然后`OnIdle`将重复调用，会降低性能。  
  
### <a name="example"></a>示例  
 以下两个示例演示如何使用`OnIdle`。 第一个示例处理使用的两个空闲任务*lCount*自变量确定任务的优先顺序。 第一个任务是高优先级，这时应执行它只要有可能。 第二个任务是不太重要，只有在没有用户输入中的长时间暂停时应完成。 请注意到基类版本的调用`OnIdle`。 第二个示例管理一组具有不同优先级的空闲任务。  
  
 [!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]  
  
##  <a name="opendocumentfile"></a>  CWinApp::OpenDocumentFile  
 框架调用此方法打开的命名[CDocument](../../mfc/reference/cdocument-class.md)应用程序文件。  
  
```  
virtual CDocument* OpenDocumentFile(
LPCTSTR lpszFileName  
BOOL bAddToMRU = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*lpszFileName*  
 要打开的文件的名称。  
  
 [in]*bAddToMRU*  
 TRUE 表示的文档是一个最新的文件;FALSE 表示该文档不是最新的文件之一。  
  
### <a name="return-value"></a>返回值  
 一个指向`CDocument`如果成功，否则该值为 NULL。  
  
### <a name="remarks"></a>备注  
 如果具有该名称的文档已打开，包含该文档的第一个框架窗口将成为焦点。 如果应用程序支持多个文档模板，框架将使用的文件扩展名以查找相应的文档模板尝试加载该文档。 如果成功，文档模板然后创建框架窗口和文档的视图。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]  
  
##  <a name="parsecommandline"></a>  CWinApp::ParseCommandLine  
 调用此成员函数以分析命令行并为发送参数，一次一个地[CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)。  
  
```  
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```  
  
### <a name="parameters"></a>参数  
 *rCmdInfo*  
 对引用[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)对象。  
  
### <a name="remarks"></a>备注  
 当你启动新的 MFC 项目使用应用程序向导时，应用程序向导将创建的本地实例`CCommandLineInfo`，然后调用`ProcessShellCommand`并`ParseCommandLine`中[InitInstance](#initinstance)成员函数。 命令行如下所示如下所述的路由：  
  
1.  在创建后`InitInstance`，则`CCommandLineInfo`对象传递给`ParseCommandLine`。  
  
2. `ParseCommandLine` 然后，调用`CCommandLineInfo::ParseParam`重复一次针对每个参数。  
  
3. `ParseParam` 填充`CCommandLineInfo`对象，然后传递给[processshellcommand 之后发生](#processshellcommand)。  
  
4. `ProcessShellCommand` 处理命令行参数和标志。  
  
 请注意，可以调用`ParseCommandLine`直接根据需要。  
  
 有关命令行标志的说明，请参阅[CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)。  
  
##  <a name="pretranslatemessage"></a>  CWinApp::PreTranslateMessage  
 重写此函数可对筛选器窗口消息发送到 Windows 函数之前[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)并[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)默认实现将执行加速键转换，因此您必须调用`CWinApp::PreTranslateMessage`成员函数在重写版本。  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 *pMsg*  
 一个指向[MSG](../../mfc/reference/msg-structure1.md)结构，其中包含要处理的消息。  
  
### <a name="return-value"></a>返回值  
 如果消息已完全处理，在非零`PreTranslateMessage`，并且不应进一步处理。 如果应以正常方式处理消息，则为零。  
  
##  <a name="processmessagefilter"></a>  CWinApp::ProcessMessageFilter  
 框架的挂钩函数调用此成员函数来筛选和响应特定 Windows 消息。  
  
```  
virtual BOOL ProcessMessageFilter(
    int code,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>参数  
 *代码*  
 指定挂钩代码。 此成员函数使用代码来确定如何处理*lpMsg。*  
  
 *lpMsg*  
 指向 Windows [MSG](../../mfc/reference/msg-structure1.md)结构。  
  
### <a name="return-value"></a>返回值  
 如果处理了消息; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 挂钩函数处理事件发送到应用程序的正常消息之前处理。  
  
 如果重写此高级的功能，请务必调用基类版本，才能保持框架的挂钩处理。  
  
##  <a name="processshellcommand"></a>  CWinApp::ProcessShellCommand  
 调用此成员函数[InitInstance](#initinstance)以接受从传递的参数`CCommandLineInfo`标识的对象*rCmdInfo*，并执行指示的操作。  
  
```  
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```  
  
### <a name="parameters"></a>参数  
 *rCmdInfo*  
 对引用[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果已成功处理 shell 命令时，非零值。 如果 0，则返回从 FALSE [InitInstance](#initinstance)。  
  
### <a name="remarks"></a>备注  
 当你启动新的 MFC 项目使用应用程序向导时，应用程序向导将创建的本地实例`CCommandLineInfo`，然后调用`ProcessShellCommand`并[ParseCommandLine](#parsecommandline)中`InitInstance`成员函数。 命令行如下所示如下所述的路由：  
  
1.  在创建后`InitInstance`，则`CCommandLineInfo`对象传递给`ParseCommandLine`。  
  
2. `ParseCommandLine` 然后调用[CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)重复一次针对每个参数。  
  
3. `ParseParam` 填充`CCommandLineInfo`对象，然后传递给`ProcessShellCommand`。  
  
4. `ProcessShellCommand` 处理命令行参数和标志。  
  
 数据成员`CCommandLineInfo`标识的对象[CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)，将以下中定义的枚举类型的`CCommandLineInfo`类。  
  
```  
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };  
```
  
 每个值的简要说明，请参阅`CCommandLineInfo::m_nShellCommand`。  
  
##  <a name="processwndprocexception"></a>  CWinApp::ProcessWndProcException  
 框架调用此成员函数，每当该处理程序不会捕获在某个应用程序的消息或命令处理程序引发的异常。  
  
```  
virtual LRESULT ProcessWndProcException(
    CException* e,  
    const MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 *e*  
 一个指向未捕获的异常。  
  
 *pMsg*  
 一个[MSG](../../mfc/reference/msg-structure1.md)结构，它包含导致引发异常的 framework 的 windows 消息有关的信息。  
  
### <a name="return-value"></a>返回值  
 应返回到 Windows 的值。 通常这是 0 L 的 windows 消息，1 L (TRUE) 的命令消息。  
  
### <a name="remarks"></a>备注  
 请勿直接调用此成员函数。  
  
 此成员函数的默认实现将创建一个消息框。 如果未捕获的异常源自菜单、 工具栏或快捷键命令失败，消息框将显示"命令失败"消息;否则，会显示"内部应用程序错误"消息。  
  
 重写此成员函数以提供全局处理的异常。 如果你想要显示的消息框，只能调用的基本功能。  
  
##  <a name="register"></a>  CWinApp::Register  
 执行未由任何注册任务`RegisterShellFileTypes`。  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现只需返回 TRUE。 重写此函数可提供任何自定义的注册步骤。  
  
##  <a name="registershellfiletypes"></a>  对下列项自动  
 调用此成员函数以使用 Windows 文件管理器注册的所有应用程序的文档类型。  
  
```  
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bCompat*  
 TRUE 添加打印和打印到，允许用户直接从 shell 中，或通过将文件拖到打印机对象打印文件的 shell 命令的注册条目。 它还添加 DefaultIcon 密钥。 默认情况下，此参数为 FALSE 的向后兼容性。  
  
### <a name="remarks"></a>备注  
 这允许用户以打开通过文件管理器中双击从您的应用程序创建的数据文件。 调用`RegisterShellFileTypes`调用之后[AddDocTemplate](#adddoctemplate)为每个应用程序中的文档模板。 此外调用[EnableShellOpen](#enableshellopen)成员函数调用时`RegisterShellFileTypes`。  
  
 `RegisterShellFileTypes` 循环的列表[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)应用程序维护和，为每个文档模板，将项添加到注册数据库的 Windows 维护文件关联的对象。 文件管理器使用这些条目以打开数据文件，当用户双击它。 这消除了需要寄送。REG 文件，其应用程序。  
  
> [!NOTE]
> `RegisterShellFileTypes` 仅适用于用户具有管理员权限运行程序。 如果程序不具有管理员权限，它不能更改注册表项。  
  
 如果注册数据库已将给定的文件扩展名与另一种文件类型相关联，则会不创建任何新的关联。 请参阅`CDocTemplate`格式的字符串必须注册此信息的类。  
  
##  <a name="registerwithrestartmanager"></a>  CWinApp::RegisterWithRestartManager  
 与重新启动管理器注册该应用程序。  
  
```  
virtual HRESULT RegisterWithRestartManager(
BOOL bRegisterRecoveryCallback,  
const CString& strRestartIdentifier);

 
virtual HRESULT RegisterWithRestartManager(
LPCWSTR pwzCommandLineArgs,  
DWORD dwRestartFlags,  
APPLICATION_RECOVERY_CALLBACK pRecoveryCallback,  
LPVOID lpvParam,  
DWORD dwPingInterval,  
DWORD dwCallbackFlags);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*bRegisterRecoveryCallback*|TRUE 表示应用程序的此实例使用恢复回调函数;FALSE 表示它没有。 应用程序意外退出时，框架将调用恢复回调函数。 有关详细信息，请参阅[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。|  
|[in]*strRestartIdentifier*|用于标识此重新启动管理器实例的唯一字符串。 重新启动管理器标识符是唯一的应用程序的每个实例。|  
|[in]*pwzCommandLineArgs*|一个字符串，包含从命令行的任何额外参数。|  
|[in]*dwRestartFlags*|重新启动管理器的可选标志。 有关详细信息，请参阅“备注”部分。|  
|[in]*pRecoveryCallback*|恢复回调函数。 此函数必须采用 LPVOID 参数作为输入并返回一个 dword 值。 默认恢复回调函数是`CWinApp::ApplicationRecoveryCallback`。|  
|[in]*lpvParam*|恢复回调函数的输入的参数。 有关详细信息，请参阅[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。|  
|[in]*dwPingInterval*|有关恢复回调函数以返回等待重新启动管理器的时间长度。 此参数是以毫秒为单位。|  
|[in]*dwCallbackFlags*|标志传递给恢复回调函数。 留待将来使用。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
 如果应用程序使用的默认 MFC 实现自动保存文件，则应使用的简单版本`RegisterWithRestartManager`。 使用简单的版本`RegisterWithRestartManager`如果你想要自定义应用程序的自动保存行为。  
  
 如果调用此方法替换为空字符串*strRestartIdentifier*，`RegisterWithRestartManager`创建管理器的重新启动此实例的唯一标识符字符串。  
  
 当应用程序意外退出时，请重新启动管理器重新启动应用程序从命令行，并提供重新启动的唯一标识符作为可选参数。 在此方案中，框架将调用`RegisterWithRestartManager`两次。 第一个调用是来自[cwinapp:: Initinstance](#initinstance)用空字符串的字符串标识符。 然后，该方法[CWinApp::ProcessShellCommand](#processshellcommand)调用`RegisterWithRestartManager`具有唯一的重启标识符。  
  
 重新启动管理器中注册应用程序后，重新启动管理器监视应用程序。 如果应用程序意外退出，请重新启动管理器在关闭过程中调用恢复回调函数。 重新启动管理器等待*dwPingInterval*恢复回调函数的响应。 如果在此时间内未响应恢复回调函数，该应用程序退出时不执行恢复的回调函数。  
  
 默认情况下，dwRestartFlags 不受支持，但提供以供将来使用。 可能的值*dwRestartFlags*如下所示：  
  
- RESTART_NO_CRASH  
  
- RESTART_NO_HANG  
  
- RESTART_NO_PATCH  
  
- RESTART_NO_REBOOT  
  
##  <a name="reopenpreviousfilesatrestart"></a>  CWinApp::ReopenPreviousFilesAtRestart  
 确定是否重新启动管理器重新打开该应用程序意外退出时，打开了文件。  
  
```  
virtual BOOL ReopenPreviousFilesAtRestart() const;  
```  
  
### <a name="return-value"></a>返回值  
 TRUE 表示重新启动管理器重新打开以前打开的文件;FALSE 表示不重新启动管理器。  
  
##  <a name="restartinstance"></a>  CWinApp::RestartInstance  
 处理重新启动管理器启动应用程序重启。  
  
```  
virtual BOOL CWinApp::RestartInstance();
```  
  
### <a name="return-value"></a>返回值  
 数据恢复处理程序将打开以前打开的文档; 如果为 TRUE如果数据恢复处理程序中有错误，或者如果不有任何以前打开的文档，则为 FALSE。  
  
### <a name="remarks"></a>备注  
 重新启动管理器重新启动时应用程序，框架将调用此方法。 此方法将检索的数据恢复处理程序并还原自动保存文件。 此方法调用[CDataRecoveryHandler::RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments)来确定用户是否想要还原自动保存文件。  
  
 如果此方法返回 FALSE [CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md)确定没有任何打开的文档。 如果没有任何打开的文档，在应用程序通常启动。  
  
##  <a name="restoreautosavedfilesatrestart"></a>  CWinApp::RestoreAutosavedFilesAtRestart  
 确定是否重新启动管理器还原自动保存的文件，重新启动该应用程序时。  
  
```  
virtual BOOL RestoreAutosavedFilesAtRestart() const;  
```  
  
### <a name="return-value"></a>返回值  
 TRUE 表示重新启动管理器还原自动保存设置文件。FALSE 表示不重新启动管理器。  
  
##  <a name="run"></a>  Cwinapp:: Run  
 提供默认消息循环。  
  
```  
virtual int Run();
```  
  
### <a name="return-value"></a>返回值  
 **Int**由返回值`WinMain`。  
  
### <a name="remarks"></a>备注  
 `Run` 获取并将 Windows 消息调度之前应用程序收到取消 WM_QUIT 消息。 如果应用程序的消息队列当前不包含任何消息，`Run`调用[OnIdle](#onidle)来执行空闲处理。 传入消息转到[PreTranslateMessage](#pretranslatemessage)成员函数以进行特殊处理，然后对 Windows 函数`TranslateMessage`标准键盘翻译; 最后，`DispatchMessage`调用 Windows 函数。  
  
 `Run` 很少被重写，但您可以重写它以提供特殊行为。  
  
##  <a name="runautomated"></a>  CWinApp::RunAutomated  
 调用此函数可确定是否" **/Automation**" **-自动化**"选项是否存在，指示是否通过客户端应用程序启动服务器应用程序。  
  
```  
BOOL RunAutomated();
```  
  
### <a name="return-value"></a>返回值  
 如果选项; 如果未找到非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果存在，是从命令行删除的选项。 OLE 自动化的详细信息，请参阅文章[自动化服务器](../../mfc/automation-servers.md)。  
  
##  <a name="runembedded"></a>  CWinApp::RunEmbedded  
 调用此函数可确定是否" **/嵌入**" **-Embedding**"选项是否存在，指示是否通过客户端应用程序启动服务器应用程序。  
  
```  
BOOL RunEmbedded();
```  
  
### <a name="return-value"></a>返回值  
 如果选项; 如果未找到非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果存在，是从命令行删除的选项。 嵌入的详细信息，请参阅文章[服务器： 实现服务器](../../mfc/servers-implementing-a-server.md)。  
  
##  <a name="saveallmodified"></a>  CWinApp::SaveAllModified  
 调用由框架以保存所有文档时应用程序的主框架窗口将会关闭，或通过 WM_QUERYENDSESSION 消息。  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>返回值  
 如果可以安全地终止该应用程序; 非零值如果不安全，终止该应用程序为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数的默认实现调用[CDocument::SaveModified](../../mfc/reference/cdocument-class.md#savemodified)反过来的应用程序中的所有修改后文档的成员函数。  
  
##  <a name="selectprinter"></a>  CWinApp::SelectPrinter  
 调用此成员函数以选择特定打印机，然后释放以前在打印对话框中选定的打印机。  
  
```  
void SelectPrinter(
    HANDLE hDevNames,  
    HANDLE hDevMode,  
    BOOL bFreeOld = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *hDevNames*  
 句柄[DEVNAMES](../../mfc/reference/devnames-structure.md)标识驱动程序、 设备和特定打印机的输出端口名称的结构。  
  
 *hDevMode*  
 句柄[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)结构，它指定有关设备初始化和环境的打印机信息。  
  
 *bFreeOld*  
 释放以前选定的打印机。  
  
### <a name="remarks"></a>备注  
 如果这两个*hDevMode*并*hDevNames*均为 NULL，`SelectPrinter`使用当前的默认打印机。  
  
##  <a name="sethelpmode"></a>  CWinApp::SetHelpMode  
 设置应用程序的帮助类型。  
  
```  
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```  
  
### <a name="parameters"></a>参数  
 *eHelpType*  
 指定要使用帮助的类型。 请参阅[CWinApp::m_eHelpType](#m_ehelptype)有关详细信息。  
  
### <a name="remarks"></a>备注  
 设置应用程序的帮助类型。  
  
 若要将应用程序的帮助类型设置为 HTMLHelp，可以调用[EnableHTMLHelp](#enablehtmlhelp)。 一旦调用`EnableHTMLHelp`，应用程序必须使用 HTMLHelp 作为其帮助应用程序。 如果你想要改为使用 WinHelp，则可以调用`SetHelpMode`并设置*eHelpType*到`afxWinHelp`。  
  
##  <a name="setregistrykey"></a>  CWinApp::SetRegistryKey  
 导致应用程序设置存储在注册表中而不是 INI 文件。  
  
```  
void SetRegistryKey(LPCTSTR lpszRegistryKey);  
void SetRegistryKey(UINT nIDRegistryKey);
```  
  
### <a name="parameters"></a>参数  
 *lpszRegistryKey*  
 包含密钥的名称的字符串指针。  
  
 *nIDRegistryKey*  
 包含的注册表项名称的字符串资源的 ID。  
  
### <a name="remarks"></a>备注  
 此函数将*m_pszRegistryKey*，然后使用`GetProfileInt`， `GetProfileString`， `WriteProfileInt`，并且`WriteProfileString`的成员函数`CWinApp`。 如果已调用此函数，是也在注册表中存储的最近使用 (过的 MRU) 文件的列表。 注册表项通常是一家公司的名称。 它存储在以下形式的密钥： HKEY_CURRENT_USER\Software\\< 公司名称\>\\< 应用程序名称\>\\< 部分名称\>\\< 值名称\>。  
  
##  <a name="supportsapplicationrecovery"></a>  CWinApp::SupportsApplicationRecovery  
 确定是否重新启动管理器恢复的应用程序意外退出。  
  
```  
virtual BOOL SupportsApplicationRecovery() const;  
```  
  
### <a name="return-value"></a>返回值  
 TRUE 表示重新启动管理器将恢复该应用程序;FALSE 表示不重新启动管理器。  
  
##  <a name="supportsautosaveatinterval"></a>  CWinApp::SupportsAutosaveAtInterval  
 确定是否重新启动管理器则自动保存在固定时间间隔打开文档。  
  
```  
virtual BOOL SupportsAutosaveAtInterval() const;  
```  
  
### <a name="return-value"></a>返回值  
 TRUE 表示重新启动管理器则自动保存打开的文档;FALSE 表示不重新启动管理器。  
  
##  <a name="supportsautosaveatrestart"></a>  CWinApp::SupportsAutosaveAtRestart  
 确定是否重新启动管理器则自动保存任何打开文档时应用程序重新启动。  
  
```  
virtual BOOL SupportsAutosaveAtRestart() const;  
```  
  
### <a name="return-value"></a>返回值  
 TRUE 表示该应用程序重新启动; 时重新启动管理器则自动保存打开的文档FALSE 表示不重新启动管理器。  
  
##  <a name="supportsrestartmanager"></a>  CWinApp::SupportsRestartManager  
 确定应用程序是否支持重新启动管理器。  
  
```  
virtual BOOL SupportsRestartManager() const;  
```  
  
### <a name="return-value"></a>返回值  
 TRUE 表示该应用程序支持重新启动管理器;FALSE 表示应用程序不。  
  
##  <a name="unregister"></a>  CWinApp::Unregister  
 注销注册的应用程序对象的所有文件。  
  
```  
virtual BOOL Unregister();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 `Unregister`函数撤消注册执行的应用程序对象和[注册](#register)函数。 通常情况下，这两个函数由 MFC 隐式调用，并因此不会出现在你的代码。  
  
 重写此函数可执行的自定义注销步骤。  
  
##  <a name="unregistershellfiletypes"></a>  CWinApp::UnregisterShellFileTypes  
 调用此成员函数以取消注册的所有应用程序的文档类型与 Windows 文件管理器。  
  
```  
void UnregisterShellFileTypes();
```  
  
##  <a name="winhelp"></a>  CWinApp::WinHelp  
 调用此成员函数以调用 WinHelp 应用程序。  
  
```  
virtual void WinHelp(
    DWORD_PTR dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>参数  
 *dwData*  
 指定其他数据。 使用的值取决于的值*nCmd*参数。  
  
 *nCmd*  
 指定请求的帮助的类型。 有关一系列可能的值以及它们如何影响*dwData*参数，请参阅[WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267) Windows 函数。  
  
### <a name="remarks"></a>备注  
 该框架还会调用此函数以调用 WinHelp 应用程序。  
  
 当你的应用程序终止时，框架会自动关闭 WinHelp 应用程序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]  
  
##  <a name="writeprofilebinary"></a>  CWinApp::WriteProfileBinary  
 调用此成员函数可将二进制数据写入到应用程序的注册表项的指定部分或。INI 文件。  
  
```  
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPBYTE pData,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>参数  
 *lpszSection*  
 指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果该节不存在，则创建它。 节的名称是用例无关;字符串可以是任何组合的大写和小写字母。  
  
 *lpszEntry*  
 指向包含到其中的值是要写入的条目的以 null 结尾的字符串。 如果该条目不存在指定的节中，将创建它。  
  
 *pData*  
 指向要写入的数据。  
  
 *nBytes*  
 包含要写入的字节数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 此示例使用`CWinApp* pApp = AfxGetApp();`CWinApp 类演示一种方法获取，`WriteProfileBinary`和`GetProfileBinary`可以从 MFC 应用程序中的任何函数使用。  
  
 [!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]  
  
 有关其他示例，请参阅示例[CWinApp::GetProfileBinary](#getprofilebinary)。  
  
##  <a name="writeprofileint"></a>  Cwinapp:: Writeprofileint  
 调用此成员函数可将指定的值写入到应用程序的注册表项的指定部分或。INI 文件。  
  
```  
BOOL WriteProfileInt(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    int nValue);
```  
  
### <a name="parameters"></a>参数  
 *lpszSection*  
 指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果该节不存在，则创建它。 节的名称是用例无关;字符串可以是任何组合的大写和小写字母。  
  
 *lpszEntry*  
 指向包含到其中的值是要写入的条目的以 null 结尾的字符串。 如果该条目不存在指定的节中，将创建它。  
  
 *n 值*  
 包含要写入的值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 此示例使用`CWinApp* pApp = AfxGetApp();`CWinApp 类演示一种方法获取， `WriteProfileString`， `WriteProfileInt`， `GetProfileString`，和`GetProfileInt`可以从 MFC 应用程序中的任何函数使用。  
  
 [!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 有关其他示例，请参阅示例[CWinApp::GetProfileInt](#getprofileint)。  
  
##  <a name="writeprofilestring"></a>  CWinApp::WriteProfileString  
 调用此成员函数可将指定的字符串写入到应用程序的注册表项的指定部分或。INI 文件。  
  
```  
BOOL WriteProfileString(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>参数  
 *lpszSection*  
 指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果该节不存在，则创建它。 节的名称是用例无关;字符串可以是任何组合的大写和小写字母。  
  
 *lpszEntry*  
 指向包含到其中的值是要写入的条目的以 null 结尾的字符串。 如果该条目不存在指定的节中，将创建它。 如果此参数为 NULL，部分中指定的*lpszSection*被删除。  
  
 *lpszValue*  
 指向要写入的字符串。 如果此参数为 NULL，由指定的项*lpszEntry*删除参数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 有关其他示例，请参阅示例[CWinApp::GetProfileInt](#getprofileint)。  
  
##  <a name="setappid"></a>  CWinApp::SetAppID  
 显式设置为应用程序的应用程序用户模型 ID。 任何用户界面显示给用户 （的最佳位置是应用程序构造函数） 之前，应调用此方法。  
  
```  
void SetAppID(LPCTSTR lpcszAppID);
```  
  
### <a name="parameters"></a>参数  
 *lpcszAppID*  
 指定应用程序用户模型 id。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [CWinThread 类](../../mfc/reference/cwinthread-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [如何：添加重启管理器支持](../../mfc/how-to-add-restart-manager-support.md)



