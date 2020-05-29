---
title: CWinApp 类
ms.date: 07/15/2019
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
ms.openlocfilehash: 4bb1ade4182424cbdcbf0d7ba69af88bbb88abe6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750670"
---
# <a name="cwinapp-class"></a>CWinApp 类

派生出 Windows 应用程序对象的基类。

## <a name="syntax"></a>语法

```
class CWinApp : public CWinThread
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CWinApp：CWinApp](#cwinapp)|构造 `CWinApp` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWinApp：：添加DocTemplate](#adddoctemplate)|将文档模板添加到应用程序的可用文档模板列表中。|
|[CWinApp：：添加到最新文件列表](#addtorecentfilelist)|将文件名添加到最近使用的 （MRU） 文件列表中。|
|[CWinApp：：应用程序恢复回电](#applicationrecoverycallback)|当应用程序意外退出时，由框架调用。|
|[CWinApp：关闭所有文档](#closealldocuments)|关闭所有打开的文档。|
|[CWinApp：：创建打印机DC](#createprinterdc)|创建打印机设备上下文。|
|[CWinApp：:DelRegTree](#delregtree)|删除指定的密钥及其所有子键。|
|[CWinApp：:DoMessageBox](#domessagebox)|为应用程序实现[AfxMessageBox。](cstring-formatting-and-message-box-display.md#afxmessagebox)|
|[CWinApp：:Do等待光标](#dowaitcursor)|打开和关闭等待光标。|
|[CWinApp：启用D2D支持](#enabled2dsupport)|支持应用程序 D2D 支持。 在初始化主窗口之前调用此方法。|
|[CWinApp：：启用Html帮助](#enablehtmlhelp)|实现应用程序的 HTML 帮助，而不是 WinHelp。|
|[CWinApp：：启用任务栏交互](#enabletaskbarinteraction)|启用任务栏交互。|
|[CWinApp：退出实例](#exitinstance)|覆盖以在应用程序终止时清理。|
|[CWinApp：获取应用程序恢复参数](#getapplicationrecoveryparameter)|检索应用程序恢复方法的输入参数。|
|[CWinApp：获取应用程序恢复间隔](#getapplicationrecoverypinginterval)|返回重新启动管理器等待恢复回调函数返回的时间长度。|
|[CWinApp：：获取应用程序重启标志](#getapplicationrestartflags)|返回重新启动管理器的标志。|
|[CWinApp：：获取应用注册密钥](#getappregistrykey)|返回HKEY_CURRENT_USER"\\软件"的密钥\注册表项\配置文件名称。|
|[CWinApp：获取数据恢复处理程序](#getdatarecoveryhandler)|获取应用程序此实例的数据恢复处理程序。|
|[CWinApp：获取第一文档模板位置](#getfirstdoctemplateposition)|检索第一个文档模板的位置。|
|[CWinApp：获取帮助模式](#gethelpmode)|检索应用程序使用的帮助类型。|
|[CWinApp：：获取NextDocTemplate](#getnextdoctemplate)|检索文档模板的位置。 可递归使用。|
|[CWinApp：：获取打印机设备默认值](#getprinterdevicedefaults)|检索打印机设备默认值。|
|[CWinApp：获取配置文件二进制](#getprofilebinary)|从应用程序中的条目检索二进制数据。INI 文件。|
|[CWinApp：获取配置文件](#getprofileint)|从应用程序中的条目中检索整数。INI 文件。|
|[CWinApp：获取配置文件字符串](#getprofilestring)|从应用程序中的条目中检索字符串。INI 文件。|
|[CWinApp：获取节键](#getsectionkey)|返回HKEY_CURRENT_USER"\\软件"的键\注册表项\AppName_lpszSection。|
|[CWinApp：隐藏应用程序](#hideapplication)|在关闭所有文档之前隐藏应用程序。|
|[CWinApp：html帮助](#htmlhelp)|调用`HTMLHelp`Windows 函数。|
|[CWinApp：ininininininininininininininininininininInin](#initinstance)|覆盖以执行 Windows 实例初始化，例如创建窗口对象。|
|[CWinApp：是任务栏交互启用](#istaskbarinteractionenabled)|告诉是否启用了 Windows 7 任务栏交互。|
|[CWinApp：：加载光标](#loadcursor)|加载游标资源。|
|[CWinApp：：加载图标](#loadicon)|加载图标资源。|
|[CWinApp：：加载OEM光标](#loadoemcursor)|加载**OCR_** 常量在 WINDOWS 中指定的 Windows OEM 预定义游标。H。|
|[CWinApp：：加载OEMIcon](#loadoemicon)|加载**OIC_** 常量在 WINDOWS 中指定的 Windows OEM 预定义图标。H。|
|[CWinApp：：加载标准光标](#loadstandardcursor)|加载**IDC_** 常量在 WINDOWS 中指定的 Windows 预定义游标。H。|
|[CWinApp：：加载标准图标](#loadstandardicon)|加载**IDI_** 常量在 WINDOWS 中指定的 Windows 预定义图标。H。|
|[CWinApp：OnDDE命令](#onddecommand)|框架调用以响应动态数据交换 （DDE） 执行命令。|
|[CWinApp：：上](#onidle)|覆盖以执行特定于应用程序的空闲时间处理。|
|[CWinApp：：打开文件文件](#opendocumentfile)|由框架调用以从文件打开文档。|
|[CWinApp：:P](#parsecommandline)|分析命令行中的单个参数和标志。|
|[CWinApp：:P重新翻译消息](#pretranslatemessage)|在邮件发送到 Windows 函数["翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)"和["调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)"之前对其进行筛选。|
|[CWinApp：:Process消息过滤器](#processmessagefilter)|在某些消息到达应用程序之前拦截它们。|
|[CWinApp：:P罗塞斯舍尔命令](#processshellcommand)|处理命令行参数和标志。|
|[CWinApp：:P罗塞斯·温德普罗奇例外](#processwndprocexception)|拦截应用程序的消息和命令处理程序引发的所有未处理异常。|
|[CWinApp：注册](#register)|执行自定义注册。|
|[CWinApp：：注册与重新启动管理器](#registerwithrestartmanager)|向重新启动管理器注册应用程序。|
|[CWinApp：：重新打开以前的文件在重新启动](#reopenpreviousfilesatrestart)|确定重新启动管理器是否重新打开应用程序意外退出时打开的文件。|
|[CWinApp：重新启动实例](#restartinstance)|处理重新启动管理器启动的应用程序重新启动。|
|[CWinApp：：恢复自动保存的文件在重新启动](#restoreautosavedfilesatrestart)|确定重新启动管理器在重新启动应用程序时是否还原自动保存的文件。|
|[CWinApp：：运行](#run)|运行默认消息循环。 重写以自定义消息循环。|
|[CWinApp：：运行自动](#runautomated)|测试应用程序的命令行为 **/自动化**选项。 已过时。 而是在调用[ParseCommandLine](#parsecommandline)后，使用[CCommandLineInfo：：m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated)中的值。|
|[CWinApp：：运行嵌入式](#runembedded)|测试应用程序的命令行/**嵌入**选项。 已过时。 而是在调用[ParseCommandLine](#parsecommandline)后，使用[CCommandLineInfo：：m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded)中的值。|
|[CWinApp：：保存所有修改](#saveallmodified)|提示用户保存所有修改的文档。|
|[CWinApp：：选择打印机](#selectprinter)|通过打印对话框选择以前由用户指示的打印机。|
|[CWinApp：：设置帮助模式](#sethelpmode)|设置和初始化应用程序使用的帮助类型。|
|[CWinApp：：支持应用程序恢复](#supportsapplicationrecovery)|确定重新启动管理器是否恢复意外退出的应用程序。|
|[CWinApp：：支持自动保存At间隔](#supportsautosaveatinterval)|确定重新启动管理器是否以常规间隔自动保存打开的文档。|
|[CWinApp：：支持自动保存Atrestart](#supportsautosaveatrestart)|确定重新启动管理器在应用程序重新启动时是否自动保存任何打开的文档。|
|[CWinApp：：支持重新启动管理器](#supportsrestartmanager)|确定应用程序是否支持重新启动管理器。|
|[CWinApp：：取消注册](#unregister)|取消注册`CWinApp`对象注册的所有内容。|
|[CWinApp：：赢帮助](#winhelp)|调用`WinHelp`Windows 函数。|
|[CWinApp：：写配置文件二进制](#writeprofilebinary)|将二进制数据写入应用程序的条目。INI 文件。|
|[CWinApp：：写配置文件](#writeprofileint)|将整数写入应用程序的条目。INI 文件。|
|[CWinApp：：写配置文件字符串](#writeprofilestring)|将字符串写入应用程序中的条目。INI 文件。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CWinApp：：启用ShellOpen](#enableshellopen)|允许用户从 Windows 文件管理器打开数据文件。|
|[CWinApp：：加载Std配置文件设置](#loadstdprofilesettings)|负载标准 。INI 文件设置并启用 MRU 文件列表功能。|
|[CWinApp：在上下文帮助](#oncontexthelp)|在应用程序中处理 SHIFT_F1 帮助。|
|[CWinApp：在文件新](#onfilenew)|实现ID_FILE_NEW命令。|
|[CWinApp：在文件打开](#onfileopen)|实现ID_FILE_OPEN命令。|
|[CWinApp：：在文件打印设置](#onfileprintsetup)|实现ID_FILE_PRINT_SETUP命令。|
|[CWinApp：：上帮助](#onhelp)|处理应用程序中的 F1 帮助（使用当前上下文）。|
|[CWinApp：：在帮助查找器上](#onhelpfinder)|处理ID_HELP_FINDER和ID_DEFAULT_HELP命令。|
|[CWinApp：：在帮助索引](#onhelpindex)|处理ID_HELP_INDEX命令并提供默认帮助主题。|
|[CWinApp：：在帮助使用](#onhelpusing)|处理ID_HELP_USING命令。|
|[CWinApp：：注册外壳文件类型](#registershellfiletypes)|向 Windows 文件管理器注册应用程序的所有文档类型。|
|[CWinApp：：SetAppID](#setappid)|显式设置应用程序的应用程序用户模型 ID。 在向用户显示任何用户界面之前，应调用此方法（最佳位置是应用程序构造函数）。|
|[CWinApp：：设置注册密钥](#setregistrykey)|导致应用程序设置存储在注册表中而不是 。INI 文件。|
|[CWinApp：：取消注册ShellFile类型](#unregistershellfiletypes)|向 Windows 文件管理器取消注册应用程序的所有文档类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CWinApp：m_bHelpMode](#m_bhelpmode)|指示用户是否处于帮助上下文模式（通常使用 SHIFT_F1 调用）。|
|[CWinApp：m_eHelpType](#m_ehelptype)|指定应用程序使用的帮助类型。|
|[CWinApp：m_hInstance](#m_hinstance)|标识应用程序的当前实例。|
|[CWinApp：m_lpCmdLine](#m_lpcmdline)|指向指定应用程序的命令行的 null 端接字符串。|
|[CWinApp：m_nCmdShow](#m_ncmdshow)|指定最初显示窗口的方式。|
|[CWinApp：m_pActiveWnd](#m_pactivewnd)|当 OLE 服务器就地处于活动状态时，指向容器应用程序的主窗口。|
|[CWinApp：m_pszAppID](#m_pszappid)|应用程序用户型号 ID。|
|[CWinApp：m_pszAppName](#m_pszappname)|指定应用程序的名称。|
|[CWinApp：m_pszExeName](#m_pszexename)|应用程序的模块名称。|
|[CWinApp：m_pszHelpFilePath](#m_pszhelpfilepath)|应用程序的帮助文件的路径。|
|[CWinApp：m_pszProfileName](#m_pszprofilename)|应用程序的 。INI 文件名。|
|[CWinApp：m_pszRegistryKey](#m_pszregistrykey)|用于确定用于存储应用程序配置文件设置的完整注册表项。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CWinApp：m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|确定重新启动管理器如何执行的标志。|
|[CWinApp：m_nAutosaveInterval](#m_nautosaveinterval)|自动保存之间的时间长度（以毫秒为单位）。|
|[CWinApp：m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|指向应用程序的数据恢复处理程序的指针。|

## <a name="remarks"></a>备注

应用程序对象提供成员函数，用于初始化应用程序（及其每个实例）和运行应用程序。

使用 Microsoft 基础类的每个应用程序只能包含派生自 的`CWinApp`一个对象。 此对象是在构造其他C++全局对象时构造的，并且在 Windows 调用由`WinMain`Microsoft 基础类库提供的函数时已经可用。 在全局级别`CWinApp`声明派生对象。

从 派生应用程序类时`CWinApp`，将重写[InitInstance](#initinstance)成员函数以创建应用程序的主窗口对象。

除了`CWinApp`成员函数之外，Microsoft 基础类库还提供以下全局函数来访问对象`CWinApp`和其他全局信息：

- [AfxGetApp](application-information-and-management.md#afxgetapp)获取指向对象的`CWinApp`指针。

- [AfxGetinstanceHandle](application-information-and-management.md#afxgetinstancehandle)获取当前应用程序实例的句柄。

- [AfxGet资源手柄](application-information-and-management.md#afxgetresourcehandle)获取应用程序的资源的句柄。

- [AfxGetApp名称](application-information-and-management.md#afxgetappname)获取指向包含应用程序名称的字符串的指针。 或者，如果您有指向对象的指针，`CWinApp`请使用`m_pszExeName`来获取应用程序的名称。

有关`CWinApp`该类的详细信息，请参阅[CWinApp：应用程序类](../../mfc/cwinapp-the-application-class.md)，包括以下概述：

- `CWinApp`-由应用程序向导编写的派生代码。

- `CWinApp`在应用程序的执行序列中的角色。

- `CWinApp`的默认成员函数实现。

- `CWinApp`关键超易。

数据`m_hPrevInstance`成员不再存在。 要确定应用程序的另一个实例是否正在运行，请使用命名的互斥体。 如果打开互斥体失败，则应用程序没有其他实例运行。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cwinappadddoctemplate"></a><a name="adddoctemplate"></a>CWinApp：：添加DocTemplate

调用此成员函数将文档模板添加到应用程序维护的可用文档模板列表中。

```cpp
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>参数

*pTemplate*<br/>
要添加 的`CDocTemplate`指针。

### <a name="remarks"></a>备注

在调用[注册ShellFileType](#registershellfiletypes)之前，应将所有文档模板添加到应用程序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

## <a name="cwinappaddtorecentfilelist"></a><a name="addtorecentfilelist"></a>CWinApp：：添加到最新文件列表

调用此成员函数将*lpszPathName*添加到 MRU 文件列表中。

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>参数

*lpszPath名称*<br/>
文件的路径。

### <a name="remarks"></a>备注

在使用此成员函数之前，应调用[LoadStdProfile设置](#loadstdprofilesettings)成员函数来加载当前 MRU 文件列表。

当框架打开文件或执行"保存为"命令以保存具有新名称的文件时，将调用此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

## <a name="cwinappapplicationrecoverycallback"></a><a name="applicationrecoverycallback"></a>CWinApp：：应用程序恢复回电

当应用程序意外退出时，由框架调用。

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>参数

*lpvParam*<br/>
[在]保留以供将来使用。

### <a name="return-value"></a>返回值

如果此方法成功，为 0;如果发生错误，则非零。

### <a name="remarks"></a>备注

如果应用程序支持重新启动管理器，则当应用程序意外退出时，框架将调用此函数。

的`ApplicationRecoveryCallback`默认实现使用`CDataRecoveryHandler`将当前打开的文档的列表保存到注册表。 此方法不自动保存任何文件。

要自定义行为，请在派生[的 CWinApp 类](../../mfc/reference/cwinapp-class.md)中重写此函数，或将您自己的应用程序恢复方法作为参数传递给[CWinApp：：注册与RestartManager](#registerwithrestartmanager)。

## <a name="cwinappclosealldocuments"></a><a name="closealldocuments"></a>CWinApp：关闭所有文档

在退出之前调用此成员函数关闭所有打开的文档。

```cpp
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>参数

*bEndSession*<br/>
指定是否终止 Windows 会话。 如果会话正在结束，则为 TRUE;如果会话已结束，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

在调用`CloseAllDocuments`之前调用[隐藏应用程序](#hideapplication)。

## <a name="cwinappcreateprinterdc"></a><a name="createprinterdc"></a>CWinApp：：创建打印机DC

调用此成员函数从所选打印机创建打印机设备上下文 （DC）。

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>参数

*直流*<br/>
对打印机设备上下文的引用。

### <a name="return-value"></a>返回值

如果成功创建打印机设备上下文，则非零;否则 0。

### <a name="remarks"></a>备注

`CreatePrinterDC`初始化通过引用传递的设备上下文，以便可以使用它进行打印。

如果函数成功，则在完成打印后，必须销毁设备上下文。 您可以让[CDC](../../mfc/reference/cdc-class.md)对象的析构函数执行此操作，也可以通过调用[CDC：:DeleteDC](../../mfc/reference/cdc-class.md#deletedc)来显式执行此操作。

## <a name="cwinappcwinapp"></a><a name="cwinapp"></a>CWinApp：CWinApp

构造`CWinApp`对象并传递*lpszAppName*以存储为应用程序名称。

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>参数

*lpszApp名称*<br/>
包含 Windows 使用的应用程序名称的 null 终止字符串。 如果未提供此参数或为 NULL，`CWinApp`则使用资源字符串AFX_IDS_APP_TITLE或可执行文件的文件名。

### <a name="remarks"></a>备注

应构造`CWinApp`派生类的一个全局对象。 应用程序中只能有一个`CWinApp`对象。 构造函数存储指向对象的指针，`CWinApp``WinMain`以便调用对象的成员函数来初始化和运行应用程序。

## <a name="cwinappdelregtree"></a><a name="delregtree"></a>CWinApp：:DelRegTree

删除特定的注册表项及其所有子密钥。

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

*h父键*<br/>
句柄到注册表项。

*斯特基名称*<br/>
要删除的注册表项的名称。

*pTM*<br/>
指向 CAtl 事务管理器对象的指针。

### <a name="return-value"></a>返回值

如果函数成功，则返回值ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义的非零错误代码。

### <a name="remarks"></a>备注

调用此函数以删除指定的密钥及其子键。

## <a name="cwinappdomessagebox"></a><a name="domessagebox"></a>CWinApp：:DoMessageBox

该框架调用此成员函数来实现全局函数[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)的消息框。

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>参数

*lpszPrompt*<br/>
消息框中的文本地址。

nType**<br/>
消息框[样式](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)。

*nID提示*<br/>
帮助上下文字符串的索引。

### <a name="return-value"></a>返回值

返回与`AfxMessageBox`的值相同的值。

### <a name="remarks"></a>备注

不要调用此成员函数打开消息框;改`AfxMessageBox`用。

重写此成员函数以自定义应用程序范围的`AfxMessageBox`呼叫处理。

## <a name="cwinappdowaitcursor"></a><a name="dowaitcursor"></a>CWinApp：:Do等待光标

此成员函数由框架调用，以实现[CWaitCursor、CCmdTarget：：开始等待光标](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)[、CCmdTarget：：结束等待光标](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)和[CmdTarget：：还原等待光标](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。 [CWaitCursor](../../mfc/reference/cwaitcursor-class.md)

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>参数

*n代码*<br/>
如果此参数为 1，则将显示等待光标。 如果为 0，则无需增加引用计数即可还原等待光标。 如果 -1，则等待光标结束。

### <a name="remarks"></a>备注

默认值实现沙漏光标。 `DoWaitCursor`维护引用计数。 为正时，将显示沙漏光标。

虽然通常不会直接调用`DoWaitCursor`，但可以重写此成员函数以更改等待光标或在显示等待光标时执行其他处理。

要获得更简单、更简化的方法来实现等待光标，请使用`CWaitCursor`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

## <a name="cwinappenabled2dsupport"></a><a name="enabled2dsupport"></a>CWinApp：启用D2D支持

需要 Visual Studio 2010 SP1。

支持应用程序 D2D 支持。 在初始化主窗口之前调用此方法。

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>参数

*d2d工厂类型*<br/>
D2D 工厂的线程模型及其创建的资源。

*写入工厂类型*<br/>
指定写入工厂对象是共享还是隔离的值

### <a name="return-value"></a>返回值

如果启用了 D2D 支持，则返回 TRUE，否则

## <a name="cwinappenablehtmlhelp"></a><a name="enablehtmlhelp"></a>CWinApp：：启用Html帮助

从`CWinApp`派生类的构造函数中调用此成员函数，以便使用 HTMLHelp 来帮助应用程序。

```cpp
void EnableHtmlHelp();
```

### <a name="remarks"></a>备注

## <a name="cwinappenableshellopen"></a><a name="enableshellopen"></a>CWinApp：：启用ShellOpen

调用此函数（通常从`InitInstance`重写）以使应用程序的用户在从 Windows 文件管理器中双击文件时打开数据文件。

```cpp
void EnableShellOpen();
```

### <a name="remarks"></a>备注

将`RegisterShellFileTypes`成员函数与此函数结合使用，或提供 。注册文件与您的应用程序手动注册文档类型。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

## <a name="cwinappenabletaskbarinteraction"></a><a name="enabletaskbarinteraction"></a>CWinApp：：启用任务栏交互

启用任务栏交互。

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
指定是启用与 Windows 7 任务栏的交互（TRUE），还是禁用 （FALSE）。

### <a name="return-value"></a>返回值

如果可以启用或禁用任务栏交互，则返回 TRUE。

### <a name="remarks"></a>备注

在创建主窗口之前，必须调用此方法，否则它断言并返回 FALSE。

## <a name="cwinappexitinstance"></a><a name="exitinstance"></a>CWinApp：退出实例

由框架从`Run`成员函数中调用以退出应用程序的此实例。

```
virtual int ExitInstance();
```

### <a name="return-value"></a>返回值

应用程序的退出代码;0 表示没有错误，大于 0 的值表示错误。 此值用作 中的`WinMain`返回值。

### <a name="remarks"></a>备注

不要从任何位置调用此成员函数，`Run`但不得在成员函数内调用。

此函数的默认实现将框架选项写入应用程序的 。INI 文件。 重写此函数以在应用程序终止时清理。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

## <a name="cwinappgetapplicationrecoveryparameter"></a><a name="getapplicationrecoveryparameter"></a>CWinApp：获取应用程序恢复参数

检索应用程序恢复方法的输入参数。

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>返回值

应用程序恢复方法的默认输入参数。

### <a name="remarks"></a>备注

此函数的默认行为返回 NULL。

有关详细信息，请参阅[CWinApp：应用程序恢复回电](#applicationrecoverycallback)。

## <a name="cwinappgetapplicationrecoverypinginterval"></a><a name="getapplicationrecoverypinginterval"></a>CWinApp：获取应用程序恢复间隔

返回重新启动管理器等待恢复回调函数返回的时间长度。

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>返回值

时间长度（以毫秒为单位）。

### <a name="remarks"></a>备注

当注册为重新启动管理器的应用程序意外退出时，应用程序将尝试保存打开的文档并调用恢复回调功能。 默认恢复回调函数是[CWinApp：：应用程序恢复回调](#applicationrecoverycallback)。

框架等待恢复回调函数返回的时间长度是 ping 间隔。 您可以通过重写`CWinApp::GetApplicationRecoveryPingInterval`或向 提供自定义值来自定义 ping 间隔`RegisterWithRestartManager`。

## <a name="cwinappgetapplicationrestartflags"></a><a name="getapplicationrestartflags"></a>CWinApp：：获取应用程序重启标志

返回重新启动管理器的标志。

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>返回值

重新启动管理器的标志。 默认实现返回 0。

### <a name="remarks"></a>备注

重新启动管理器的标志对默认实现不起作用。 它们供将来使用。

使用[CWinApp：：注册与RestartManager](#registerwithrestartmanager)注册应用程序时，您可以设置标志。

重新启动管理器标志的可能值如下所示：

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappgetappregistrykey"></a><a name="getappregistrykey"></a>CWinApp：：获取应用注册密钥

返回HKEY_CURRENT_USER"\\软件"\注册表项\配置文件名称的密钥。

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*pTM*<br/>
指向 `CAtlTransactionManager` 对象的指针。

### <a name="return-value"></a>返回值

如果函数成功，则应用程序密钥;否则 NULL。

### <a name="remarks"></a>备注

## <a name="cwinappgetdatarecoveryhandler"></a><a name="getdatarecoveryhandler"></a>CWinApp：获取数据恢复处理程序

获取应用程序此实例的数据恢复处理程序。

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>返回值

应用程序此实例的数据恢复处理程序。

### <a name="remarks"></a>备注

使用重新启动管理器的每个应用程序必须具有[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)的一个实例。 此类负责监视打开的文档和自动保存文件。 的行为`CDataRecoveryHandler`取决于重新启动管理器的配置。 有关详细信息，请参阅[CData 恢复处理程序类](../../mfc/reference/cdatarecoveryhandler-class.md)。

此方法在操作系统上返回 NULL 早于 Windows Vista。 重新启动管理器在操作系统上不受 Windows Vista 的支持。

如果应用程序当前没有数据恢复处理程序，此方法将创建一个并返回指向它的指针。

## <a name="cwinappgetfirstdoctemplateposition"></a><a name="getfirstdoctemplateposition"></a>CWinApp：获取第一文档模板位置

获取应用程序中第一个文档模板的位置。

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的定位值;如果列表为空，则为 NULL。

### <a name="remarks"></a>备注

使用调用[GetNextDocTemplate](#getnextdoctemplate)中返回的"位置"值获取第一个[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象。

## <a name="cwinappgethelpmode"></a><a name="gethelpmode"></a>CWinApp：获取帮助模式

检索应用程序使用的帮助类型。

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>返回值

应用程序使用的帮助类型。 有关详细信息，请参阅[CWinApp：：m_eHelpType。](#m_ehelptype)

## <a name="cwinappgetnextdoctemplate"></a><a name="getnextdoctemplate"></a>CWinApp：：获取NextDocTemplate

获取*pos*标识的文档模板，然后将*位置*设置到"位置"值。

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>参数

*Pos*<br/>
对前一个调用`GetNextDocTemplate`或[GetFirstDocTemplate位置](#getfirstdoctemplateposition)返回的定位值的引用。 此调用将该值更新为下一个位置。

### <a name="return-value"></a>返回值

指向[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象的指针。

### <a name="remarks"></a>备注

如果使用`GetNextDocTemplate`调用`GetFirstDocTemplatePosition`建立初始位置，则可以在转发迭代循环中使用。

您必须确保您的"位置"值有效。 如果无效，则 Microsoft 基础类库的调试版本断言。

如果检索到的文档模板是最后可用，则*pos*的新值将设置为 NULL。

## <a name="cwinappgetprinterdevicedefaults"></a><a name="getprinterdevicedefaults"></a>CWinApp：：获取打印机设备默认值

调用此成员函数以准备用于打印的打印机设备上下文。

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>参数

*pPrintDlg*<br/>
指向[PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

从 Windows 检索当前打印机默认值。根据需要提交 INI 文件，或使用用户在"打印设置"中设置的最后一个打印机配置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

## <a name="cwinappgetprofilebinary"></a><a name="getprofilebinary"></a>CWinApp：获取配置文件二进制

调用此成员函数从应用程序注册表或 的指定部分中的条目中检索二进制数据。INI 文件。

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>参数

*lpsz节*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。

*lpszEntry*<br/>
指向以 null 结尾的字符串，该字符串包含要检索其值的条目。

*ppData*<br/>
指向将接收数据地址的指针。

*p字节*<br/>
指向将接收数据大小的 UINT（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数不区分大小写，因此*lpszSection*和*lpszEntry*参数中的字符串可能因情况而异。

> [!NOTE]
> `GetProfileBinary`分配缓冲区并在\**ppData*中返回其地址。 调用方负责使用**delete *** 释放缓冲区。

> [!IMPORTANT]
> 此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

有关其他示例，请参阅[CWinApp：：写入配置文件二进制](#writeprofilebinary)。

## <a name="cwinappgetprofileint"></a><a name="getprofileint"></a>CWinApp：获取配置文件

调用此成员函数以检索应用程序的注册表或 .INI 文件的指定部分中条目的整数的值。

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>参数

*lpsz节*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。

*lpszEntry*<br/>
指向以 null 结尾的字符串，该字符串包含要检索其值的条目。

*n默认*<br/>
指定在框架找不到条目时要返回的默认值。

### <a name="return-value"></a>返回值

如果函数成功，则为指定条目后面的字符串的整数值。 如果函数找不到条目，则返回值是*nDefault*参数的值。 如果与指定条目对应的值不为整数，则返回值为 0。

在 .INI 文件中，此成员函数支持值的十六进制表示法。 检索已签名整数时，应将该值转换为**int**。

### <a name="remarks"></a>备注

此成员函数不区分大小写，因此*lpszSection*和*lpszEntry*参数中的字符串可能因情况而异。

> [!IMPORTANT]
> 此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

有关其他示例，请参阅[CWinApp：：WriteProfileint](#writeprofileint)。

## <a name="cwinappgetprofilestring"></a><a name="getprofilestring"></a>CWinApp：获取配置文件字符串

调用此成员函数以检索与应用程序注册表或 中的指定节中的条目关联的字符串。INI 文件。

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>参数

*lpsz节*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。

*lpszEntry*<br/>
指向包含要检索其字符串的条目的 null 终止字符串。 此值不能为 NULL。

*lpszDefault*<br/>
如果在初始化文件中找不到该条目，则指向给定条目的默认字符串值。

### <a name="return-value"></a>返回值

返回值是应用程序的 的 字符串。如果找不到字符串，则 INI 文件或*lpszDefault。* 框架支持的最大字符串长度为_MAX_PATH。 如果*lpszDefault*为 NULL，则返回值为空字符串。

### <a name="remarks"></a>备注

> [!IMPORTANT]
> 此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

对于另一个示例，请参阅[CWinApp 的示例：：获取配置文件。](#getprofileint)

## <a name="cwinappgetsectionkey"></a><a name="getsectionkey"></a>CWinApp：获取节键

返回HKEY_CURRENT_USER"\\软件"的密钥\注册表项\AppName_lpszSection。

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*lpsz节*<br/>
要获取的键的名称。

*pTM*<br/>
指向 `CAtlTransactionManager` 对象的指针。

### <a name="return-value"></a>返回值

如果函数成功，则节键;否则 NULL。

### <a name="remarks"></a>备注

## <a name="cwinapphideapplication"></a><a name="hideapplication"></a>CWinApp：隐藏应用程序

在关闭打开的文档之前调用此成员函数以隐藏应用程序。

```cpp
void HideApplication();
```

## <a name="cwinapphtmlhelp"></a><a name="htmlhelp"></a>CWinApp：html帮助

调用此成员函数以调用 HTMLHelp 应用程序。

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>参数

*dwData*<br/>
指定其他数据。 使用的值取决于*nCmd*参数的值。 默认值`0x000F`，表示[HH_HELP_CONTEXT](/previous-versions/windows/desktop/htmlhelp/hh-help-context-command)。

*nCmd*<br/>
指定请求的帮助的类型。 有关可能值及其如何影响*dwData*参数的列表，请参阅 Windows SDK 中的[HtmlHelpW](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpw)或[HtmlHelpA](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpa) API 函数中描述的*uCommand*参数。

### <a name="remarks"></a>备注

框架还会调用此函数以调用 HTMLHelp 应用程序。

当应用程序终止时，框架将自动关闭 HTMLHelp 应用程序。

## <a name="cwinappinitinstance"></a><a name="initinstance"></a>CWinApp：ininininininininininininininininininininInin

Windows 允许同时运行同一程序的多个副本。

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>返回值

初始化成功时非零;否则 0。

### <a name="remarks"></a>备注

应用程序初始化在概念上分为两个部分：一次性应用程序初始化，在程序首次运行时完成，以及每次运行程序副本（包括第一次）时运行的实例初始化。 框架的实现`WinMain`调用此函数。

覆盖`InitInstance`以初始化在 Windows 下运行的应用程序的每个新实例。 通常，您可以重写`InitInstance`以构造主窗口对象，`CWinThread::m_pMainWnd`并将数据成员设置为指向该窗口。 有关重写此成员函数的详细信息，请参阅[CWinApp：应用程序类](../../mfc/cwinapp-the-application-class.md)。

> [!NOTE]
> MFC 应用程序必须初始化为单线程单元 （STA）。 如果在`InitInstance`重写中调用[Co初始化Ex，](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex)请指定COINIT_APARTMENTTHREADED（而不是COINIT_MULTITHREADED）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

## <a name="cwinappistaskbarinteractionenabled"></a><a name="istaskbarinteractionenabled"></a>CWinApp：是任务栏交互启用

告诉是否启用了 Windows 7 任务栏交互。

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>返回值

如果`EnableTaskbarInteraction`已调用，并且操作系统为 Windows 7 或更高版本，则返回 TRUE。

### <a name="remarks"></a>备注

任务栏交互意味着 MDI 应用程序在单独的选项卡式缩略图中显示 MDI 子项的内容，当鼠标指针位于应用程序任务栏按钮上时，这些缩略图会显示。

## <a name="cwinapploadcursor"></a><a name="loadcursor"></a>CWinApp：：加载光标

从当前可执行文件加载*由 lpszResourceName*命名或*nIDResource*指定的游标资源。

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>参数

*lpsz 资源名称*<br/>
指向包含游标资源名称的 null 端接字符串。 可以为此参数使用`CString`。

*nID资源*<br/>
游标资源的 ID。 有关资源列表，请参阅 Windows SDK 中的[LoadCursor。](/windows/win32/api/winuser/nf-winuser-loadcursorw)

### <a name="return-value"></a>返回值

游标的句柄（如果成功）;如果成功，则否则 NULL。

### <a name="remarks"></a>备注

`LoadCursor`仅当游标以前未加载时，才将光标加载到内存中;否则，它将检索现有资源的句柄。

使用[LoadStandardCursor](#loadstandardcursor)或[LoadOEMCursor](#loadoemcursor)成员函数访问预定义的 Windows 游标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

## <a name="cwinapploadicon"></a><a name="loadicon"></a>CWinApp：：加载图标

从可执行文件加载*由 lpszResourceName*命名或*nIDResource*指定的图标资源。

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>参数

*lpsz 资源名称*<br/>
指向包含图标资源名称的 null 端接字符串。 也可以为此参数使用`CString`。

*nID资源*<br/>
图标资源的 ID 号。

### <a name="return-value"></a>返回值

图标的句柄（如果成功）;图标的句柄否则 NULL。

### <a name="remarks"></a>备注

`LoadIcon`仅当之前未加载该图标时，才加载该图标;否则，它将检索现有资源的句柄。

您可以使用[LoadStandardIcon](#loadstandardicon)或[LoadOEMIcon](#loadoemicon)成员功能访问预定义的 Windows 图标。

> [!NOTE]
> 此成员函数调用 Win32 API 函数[LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)，它只能加载其大小符合SM_CXICON和SM_CYICON系统指标值的图标。

## <a name="cwinapploadoemcursor"></a><a name="loadoemcursor"></a>CWinApp：：加载OEM光标

加载*nIDCursor*指定的 Windows 预定义的游标资源。

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>参数

*nIDCursor*<br/>
指定预定义的 Windows 游标的**OCR_** 清单常量标识符。 您必须具有`#define OEMRESOURCE``#include \<afxwin.h>`以前才能访问 WINDOWS 中**OCR_** 常量。H。

### <a name="return-value"></a>返回值

游标的句柄（如果成功）;如果成功，则否则 NULL。

### <a name="remarks"></a>备注

使用`LoadOEMCursor`或[LoadStandardCursor](#loadstandardcursor)成员函数访问预定义的 Windows 游标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

## <a name="cwinapploadoemicon"></a><a name="loadoemicon"></a>CWinApp：：加载OEMIcon

加载*nIDIcon*指定的 Windows 预定义图标资源。

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>参数

*nIDIcon*<br/>
指定预定义的 Windows 图标**的OIC_** 清单常量标识符。 您必须具有`#define OEMRESOURCE`以前`#include \<afxwin.h>`才能访问 WINDOWS 中的**OIC_** 常量。H。

### <a name="return-value"></a>返回值

图标的句柄（如果成功）;图标的句柄否则 NULL。

### <a name="remarks"></a>备注

使用`LoadOEMIcon`或[LoadStandardIcon](#loadstandardicon)成员函数访问预定义的 Windows 图标。

## <a name="cwinapploadstandardcursor"></a><a name="loadstandardcursor"></a>CWinApp：：加载标准光标

加载*lpszCursorName*指定的 Windows 预定义的游标资源。

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>参数

*lpszCursor名称*<br/>
指定预定义的 Windows 游标的**IDC_** 清单常量标识符。 这些标识符在 WINDOWS 中定义。H。 下面的列表显示了*lpszCursorName*的可能预定义值和含义 ：

- IDC_ARROW标准箭头光标

- IDC_IBEAM标准文本插入光标

- IDC_WAIT Windows 执行耗时任务时使用的沙漏光标

- IDC_CROSS十字光标供选择

- IDC_UPARROW直向上指向的箭头

- IDC_SIZE过时且不受支持;使用IDC_SIZEALL

- IDC_SIZEALL四角箭头。 用于调整窗口大小的光标。

- IDC_ICON已过时且不受支持。 使用IDC_ARROW。

- IDC_SIZENWSE双头箭头，末端在左上角和右下角

- IDC_SIZENESW双头箭头，末端在右上方和左下角

- IDC_SIZEWE水平双头箭头

- IDC_SIZENS垂直双头箭头

### <a name="return-value"></a>返回值

游标的句柄（如果成功）;如果成功，则否则 NULL。

### <a name="remarks"></a>备注

使用`LoadStandardCursor`或[LoadOEMCursor](#loadoemcursor)成员函数访问预定义的 Windows 游标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

## <a name="cwinapploadstandardicon"></a><a name="loadstandardicon"></a>CWinApp：：加载标准图标

加载*lpszIconName*指定的 Windows 预定义图标资源。

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>参数

*lpszIcon 名称*<br/>
指定预定义的 Windows 图标的清单常量标识符。 这些标识符在 WINDOWS 中定义。H。 有关可能预定义值及其说明的列表，请参阅 Windows SDK 中的[LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)中的*lpIconName*参数。

### <a name="return-value"></a>返回值

图标的句柄（如果成功）;图标的句柄否则 NULL。

### <a name="remarks"></a>备注

使用`LoadStandardIcon`或[LoadOEMIcon](#loadoemicon)成员函数访问预定义的 Windows 图标。

## <a name="cwinapploadstdprofilesettings"></a><a name="loadstdprofilesettings"></a>CWinApp：：加载Std配置文件设置

从[InitA 成员](#initinstance)函数中调用此成员函数，以启用和加载最近使用 （MRU） 文件和上次预览状态的列表。

```cpp
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>参数

*nMaxMRU*<br/>
要跟踪的最近使用的文件数。

### <a name="remarks"></a>备注

如果*nMaxMRU*为 0，则不会保留 MRU 列表。

## <a name="cwinappm_bhelpmode"></a><a name="m_bhelpmode"></a>CWinApp：m_bHelpMode

如果应用程序处于帮助上下文模式（通常使用 SHIFT + F1 调用），则为 TRUE;否则 FALSE。

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>备注

在帮助上下文模式下，光标将成为问号，用户可以在屏幕上移动它。 如果要在帮助模式下实现特殊处理，请检查此标志。 `m_bHelpMode`是 BOOL 类型的公共变量。

## <a name="cwinappm_dwrestartmanagersupportflags"></a><a name="m_dwrestartmanagersupportflags"></a>CWinApp：m_dwRestartManagerSupportFlags

确定重新启动管理器如何执行的标志。

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>备注

要启用重新启动管理器，请设置为`m_dwRestartManagerSupportFlags`所需的行为。 下表显示了可用的标志。

|||
|-|-|
|标志|说明|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|该应用程序使用[CWinApp 注册：：注册与重新启动管理器](#registerwithrestartmanager)。 重新启动管理器负责重新启动应用程序，如果它意外退出。|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY|应用程序注册到重新启动管理器，重新启动管理器在重新启动应用程序时调用恢复回调功能。 默认恢复回调函数是[CWinApp：：应用程序恢复回调](#applicationrecoverycallback)。|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|启用自动保存，重新启动管理器在应用程序重新启动时自动保存任何打开的文档。|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|启用自动保存，重新启动管理器会定期自动保存任何打开的文档。 间隔由[CWinApp：：m_nAutosaveInterval](#m_nautosaveinterval)定义。|
|- AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|重新启动管理器在从意外退出中重新启动应用程序后打开以前打开的文档。 [CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)处理存储打开的文档列表并还原它们。|
|- AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|重新启动管理器提示用户在重新启动应用程序后还原自动保存的文件。 类`CDataRecoveryHandler`查询用户。|
|- AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|AFX_RESTART_MANAGER_SUPPORT_RESTART、AFX_RESTART_MANAGER_SUPPORT_RECOVER和AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES的结合。|
|- AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE、AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART、AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL和AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES的结合。|
|- AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_RESTART、AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART、AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES和AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES的结合。|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|工会ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY、AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL、AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES和AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES。|

## <a name="cwinappm_ehelptype"></a><a name="m_ehelptype"></a>CWinApp：m_eHelpType

此数据成员的类型是枚举类型AFX_HELP_TYPE，在类中`CWinApp`定义。

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>备注

AFX_HELP_TYPE枚举的定义如下：

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- 要将应用程序的帮助设置为 HTML 帮助，请调用[SetHelpMode](#sethelpmode) `afxHTMLHelp`并指定 。

- 要将应用程序的帮助设置为 WinHelp，请调用`SetHelpMode`并指定`afxWinHelp`。

## <a name="cwinappm_hinstance"></a><a name="m_hinstance"></a>CWinApp：m_hInstance

对应于 Windows 传递给`WinMain`*的 hInstance*参数。

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>备注

数据`m_hInstance`成员是 Windows 下运行的应用程序当前实例的句柄。 这由全局函数[AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)返回。 `m_hInstance`是 HINSTANCE 类型的公共变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

## <a name="cwinappm_lpcmdline"></a><a name="m_lpcmdline"></a>CWinApp：m_lpCmdLine

对应于 Windows 传递给`WinMain`的*lpCmdLine*参数。

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>备注

指向指定应用程序的命令行的 null 端接字符串。 用于`m_lpCmdLine`访问用户在启动应用程序时输入的任何命令行参数。 `m_lpCmdLine`是 LPTSTR 类型的公共变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappm_nautosaveinterval"></a><a name="m_nautosaveinterval"></a>CWinApp：m_nAutosaveInterval

自动保存之间的时间长度（以毫秒为单位）。

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>备注

您可以将重新启动管理器配置为按设定的时间间隔自动保存打开的文档。 如果应用程序不自动保存文件，则此参数不起作用。

## <a name="cwinappm_ncmdshow"></a><a name="m_ncmdshow"></a>CWinApp：m_nCmdShow

对应于 Windows 传递到 的*nCmdShow*参数`WinMain`。

```
int m_nCmdShow;
```

### <a name="remarks"></a>备注

当您为应用程序`m_nCmdShow`的主窗口调用[CWnd：：：ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)时，应作为参数传递。 `m_nCmdShow`是**int**类型的公共变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

## <a name="cwinappm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinApp：m_pActiveWnd

使用此数据成员可以存储指向 OLE 容器应用程序主窗口的指针，该窗口已激活 OLE 服务器应用程序就地。

### <a name="remarks"></a>备注

如果此数据成员为 NULL，则应用程序未就地处于活动状态。

当框架窗口由 OLE 容器应用程序激活时，框架将设置此成员变量。

## <a name="cwinappm_pdatarecoveryhandler"></a><a name="m_pdatarecoveryhandler"></a>CWinApp：m_pDataRecoveryHandler

指向应用程序的数据恢复处理程序的指针。

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>备注

应用程序的数据恢复处理程序监视打开的文档并自动保存它们。 当应用程序意外退出后重新启动时，框架使用数据恢复处理程序还原自动保存的文件。 有关详细信息，请参阅[CData 恢复处理程序类](../../mfc/reference/cdatarecoveryhandler-class.md)。

## <a name="cwinappm_pszappname"></a><a name="m_pszappname"></a>CWinApp：m_pszAppName

指定应用程序的名称。

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>备注

应用程序名称可以来自传递给[CWinApp](#cwinapp)构造函数的参数，或者（如果未指定）到 ID 为 AFX_IDS_APP_TITLE的资源字符串。 如果在资源中找不到应用程序名称，则它来自程序的 。EXE 文件名。

返回全局函数[AfxGetAppName](application-information-and-management.md#afxgetappname)。 `m_pszAppName`是类型**const char**<strong>\*</strong>的公共变量。

> [!NOTE]
> 如果将值分配给`m_pszAppName`，则必须在堆上动态分配该值。 析`CWinApp`构函数使用此指针调用**自由**（ ）。 您许多人希望使用`_tcsdup`（ ） 运行时库函数来执行分配。 此外，在分配新值之前，释放与当前指针关联的内存。 例如：

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

## <a name="cwinappm_pszexename"></a><a name="m_pszexename"></a>CWinApp：m_pszExeName

包含应用程序可执行文件的名称，没有扩展名。

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>备注

与[m_pszAppName](#m_pszappname)不同，此名称不能包含空白。 `m_pszExeName`是类型**const char**<strong>\*</strong>的公共变量。

> [!NOTE]
> 如果将值分配给`m_pszExeName`，则必须在堆上动态分配该值。 析`CWinApp`构函数使用此指针调用**自由**（ ）。 您许多人希望使用`_tcsdup`（ ） 运行时库函数来执行分配。 此外，在分配新值之前，释放与当前指针关联的内存。 例如：

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

## <a name="cwinappm_pszhelpfilepath"></a><a name="m_pszhelpfilepath"></a>CWinApp：m_pszHelpFilePath

包含应用程序的帮助文件的路径。

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>备注

默认情况下，框架用"初始化`m_pszHelpFilePath`到应用程序的名称。附加 HLP"。 要更改帮助文件的名称，将`m_pszHelpFilePath`设置为指向包含所需帮助文件的完整名称的字符串。 在应用程序的[InitInstance](#initinstance)函数中方便了执行此操作。 `m_pszHelpFilePath`是类型**const char**<strong>\*</strong>的公共变量。

> [!NOTE]
> 如果将值分配给`m_pszHelpFilePath`，则必须在堆上动态分配该值。 析`CWinApp`构函数使用此指针调用**自由**（ ）。 您许多人希望使用`_tcsdup`（ ） 运行时库函数来执行分配。 此外，在分配新值之前，释放与当前指针关联的内存。 例如：

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

## <a name="cwinappm_pszprofilename"></a><a name="m_pszprofilename"></a>CWinApp：m_pszProfileName

包含应用程序的 名称。INI 文件。

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>备注

`m_pszProfileName`是类型**const char**<strong>\*</strong>的公共变量。

> [!NOTE]
> 如果将值分配给`m_pszProfileName`，则必须在堆上动态分配该值。 析`CWinApp`构函数使用此指针调用**自由**（ ）。 您许多人希望使用`_tcsdup`（ ） 运行时库函数来执行分配。 此外，在分配新值之前，释放与当前指针关联的内存。 例如：

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

## <a name="cwinappm_pszregistrykey"></a><a name="m_pszregistrykey"></a>CWinApp：m_pszRegistryKey

用于确定在注册表或 INI 文件中存储应用程序配置文件设置的位置。

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>备注

通常，此数据成员被视为只读。

- 该值存储到注册表项。 应用程序配置文件设置的名称将追加到以下注册表项：HKEY_CURRENT_USER/软件/本地应用向导生成/。

如果将值分配给`m_pszRegistryKey`，则必须在堆上动态分配该值。 析`CWinApp`构函数使用此指针调用**自由**（ ）。 您许多人希望使用`_tcsdup`（ ） 运行时库函数来执行分配。 此外，在分配新值之前，释放与当前指针关联的内存。 例如：

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

## <a name="cwinappm_pszappid"></a><a name="m_pszappid"></a>CWinApp：m_pszAppID

应用程序用户型号 ID。

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>备注

## <a name="cwinapponcontexthelp"></a><a name="oncontexthelp"></a>CWinApp：在上下文帮助

在应用程序中处理 SHIFT_F1 帮助。

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>备注

您必须向`CWinApp`类消息`ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )`映射添加语句，并添加快捷键表条目（通常为 SHIFT_F1）才能启用此成员函数。

`OnContextHelp`将应用程序置于帮助模式。 光标将变为箭头和问号，然后用户可以移动鼠标指针并按鼠标左键选择对话框、窗口、菜单或命令按钮。 此成员函数检索光标下对象的帮助上下文，并调用 Windows 函数 WinHelp 与该帮助上下文。

## <a name="cwinapponddecommand"></a><a name="onddecommand"></a>CWinApp：OnDDE命令

当主框架窗口收到 DDE 执行消息时，由框架调用。

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>参数

*lpszCommand*<br/>
指向应用程序收到的 DDE 命令字符串。

### <a name="return-value"></a>返回值

处理命令时非零;否则 0。

### <a name="remarks"></a>备注

默认实现检查该命令是否是打开文档的请求，如果是，则打开指定的文档。 当用户双击数据文件时，Windows 文件管理器通常会发送此类 DDE 命令字符串。 重写此函数以处理其他 DDE 执行命令，如要打印的命令。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

## <a name="cwinapponfilenew"></a><a name="onfilenew"></a>CWinApp：在文件新

实现ID_FILE_NEW命令。

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>备注

您必须向`CWinApp`类消息`ON_COMMAND( ID_FILE_NEW, OnFileNew )`映射添加语句才能启用此成员函数。 如果启用，此函数将处理"文件新"命令的执行。

有关默认行为的信息以及如何重写此成员函数，请参阅[技术说明 22。](../../mfc/tn022-standard-commands-implementation.md)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileopen"></a><a name="onfileopen"></a>CWinApp：在文件打开

实现ID_FILE_OPEN命令。

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>备注

您必须向`CWinApp`类消息`ON_COMMAND( ID_FILE_OPEN, OnFileOpen )`映射添加语句才能启用此成员函数。 如果启用，此函数将处理文件打开命令的执行。

有关默认行为的信息以及如何重写此成员函数的指导，请参阅[技术说明 22](../../mfc/tn022-standard-commands-implementation.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileprintsetup"></a><a name="onfileprintsetup"></a>CWinApp：：在文件打印设置

实现ID_FILE_PRINT_SETUP命令。

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>备注

您必须向`CWinApp`类消息`ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )`映射添加语句才能启用此成员函数。 如果启用，此函数将处理文件打印命令的执行。

有关默认行为的信息以及如何重写此成员函数的指导，请参阅[技术说明 22](../../mfc/tn022-standard-commands-implementation.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponhelp"></a><a name="onhelp"></a>CWinApp：：上帮助

处理应用程序中的 F1 帮助（使用当前上下文）。

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>备注

通常，您还会为 F1 键添加加速器键条目。 启用 F1 密钥只是惯例，而不是要求。

您必须向`CWinApp`类消息`ON_COMMAND( ID_HELP, OnHelp )`映射添加语句才能启用此成员函数。 如果启用，则当用户按下 F1 键时由框架调用。

此消息处理程序函数的默认实现确定与当前窗口、对话框或菜单项对应的帮助上下文，然后调用 WINHELP。Exe。 如果当前没有可用的上下文，则函数使用默认上下文。

重写此成员函数，将"帮助"上下文设置为当前具有焦点的窗口、对话框、菜单项或工具栏按钮以外的内容。 使用`WinHelp`所需的帮助上下文 ID 调用。

## <a name="cwinapponhelpfinder"></a><a name="onhelpfinder"></a>CWinApp：：在帮助查找器上

处理ID_HELP_FINDER和ID_DEFAULT_HELP命令。

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>备注

您必须向`CWinApp`类消息`ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )`映射添加语句才能启用此成员函数。 如果启用，则当应用程序的用户选择帮助查找器命令以使用标准`WinHelp`**HELP_FINDER**主题调用时，框架将调用此消息处理程序函数。

## <a name="cwinapponhelpindex"></a><a name="onhelpindex"></a>CWinApp：：在帮助索引

处理ID_HELP_INDEX命令并提供默认帮助主题。

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>备注

您必须向`CWinApp`类消息`ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )`映射添加语句才能启用此成员函数。 如果启用，则当应用程序的用户选择帮助索引命令以使用标准`WinHelp`**HELP_INDEX**主题调用时，框架将调用此消息处理程序函数。

## <a name="cwinapponhelpusing"></a><a name="onhelpusing"></a>CWinApp：：在帮助使用

处理ID_HELP_USING命令。

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>备注

您必须向`CWinApp`类消息`ON_COMMAND( ID_HELP_USING, OnHelpUsing )`映射添加语句才能启用此成员函数。 当应用程序的用户选择"帮助使用"命令以使用标准`WinHelp`**HELP_HELPONHELP**主题调用应用程序时，框架将调用此消息处理程序函数。

## <a name="cwinapponidle"></a><a name="onidle"></a>CWinApp：：上

重写此成员函数以执行空闲时间处理。

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>参数

*lCount*<br/>
当应用程序的消息队列为空`OnIdle`时，每次调用一个计数器。 每次处理新消息时，此计数都会重置为 0。 可以使用*lCount*参数来确定应用程序空闲的相对时间长度，而无需处理消息。

### <a name="return-value"></a>返回值

非零接收更多的空闲处理时间;如果不再需要空闲时间，则为 0。

### <a name="remarks"></a>备注

`OnIdle`当应用程序的消息队列为空时，在默认消息循环中调用。 使用重写调用您自己的后台空闲处理程序任务。

`OnIdle`应返回 0 以指示不需要空闲处理时间。 每次`OnIdle`调用消息队列为空时，每次调用*lCount*参数都会增加，并且每次处理新消息时都重置为 0。 您可以基于此计数调用不同的空闲例程。

下面总结了空闲循环处理：

1. 如果 Microsoft 基础类库中的消息循环检查消息队列，但找不到挂起的消息，它将调用`OnIdle`应用程序对象并将 0 作为*lCount*参数提供。

2. `OnIdle`执行一些处理并返回非零值，以指示应再次调用该值以执行进一步处理。

3. 消息循环再次检查消息队列。 如果没有挂起的消息，它将再次调用`OnIdle`，从而增加*lCount*参数。

4. 最终，`OnIdle`完成处理其所有空闲任务并返回 0。 这告诉消息循环停止调用`OnIdle`，直到从消息队列收到下一条消息，此时空闲循环将重新启动，参数设置为 0。

在此期间`OnIdle`不要执行冗长的任务，因为应用程序在返回之前`OnIdle`无法处理用户输入。

> [!NOTE]
> 更新的`OnIdle`默认实现命令用户界面对象（如菜单项和工具栏按钮），并执行内部数据结构清理。 因此，如果重写`OnIdle`，则必须使用重写`CWinApp::OnIdle`版本中`lCount`的 调用。 首先调用所有基类空闲处理（即，直到基类`OnIdle`返回 0）。 如果需要在基类处理完成之前执行工作，请查看基类实现以选择正确的*lCount*以在其中完成工作。

如果不想`OnIdle`从消息队列中检索消息时被调用，则可以重写[CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage)。 如果应用程序设置了非常短的计时器，或者如果系统正在发送WM_SYSTIMER消息，则`OnIdle`将重复调用该消息并降低性能。

### <a name="example"></a>示例

以下两个示例演示如何使用`OnIdle`。 第一个示例使用*lCount*参数处理两个空闲任务，以确定任务的优先级。 第一个任务是高优先级的，您应该尽可能执行。 第二个任务不太重要，只有在用户输入长时间暂停时才应执行。 请注意对 的基类版本的`OnIdle`调用。 第二个示例管理一组具有不同优先级的空闲任务。

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

## <a name="cwinappopendocumentfile"></a><a name="opendocumentfile"></a>CWinApp：：打开文件文件

框架调用此方法来打开应用程序的命名[CDocument](../../mfc/reference/cdocument-class.md)文件。

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>参数

*lpszFile名称*<br/>
[在]要打开的文件的名称。

*bAddtoMRU*<br/>
[在]TRUE 表示文档是最新的文件之一;FALSE 表示文档不是最新的文件之一。

### <a name="return-value"></a>返回值

指向 的`CDocument`指针（如果成功）;如果成功，则指向否则 NULL。

### <a name="remarks"></a>备注

如果具有该名称的文档已打开，则包含该文档的第一个框架窗口将获取焦点。 如果应用程序支持多个文档模板，则框架使用文件名扩展名来查找适当的文档模板，以尝试加载文档。 如果成功，文档模板将创建一个框架窗口并为文档创建视图。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappparsecommandline"></a><a name="parsecommandline"></a>CWinApp：:P

调用此成员函数来分析命令行，并将参数（一次一个）发送到[CCommandLineInfo：:ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)。

```cpp
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>参数

*rCmdInfo*<br/>
对[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)对象的引用。

### <a name="remarks"></a>备注

使用应用程序向导启动新的 MFC 项目时，应用程序向导将`CCommandLineInfo`创建 的本地实例，然后在[InitA](#initinstance) `ParseCommandLine`成员函数中调用`ProcessShellCommand`。 命令行遵循下面描述的路由：

1. 在 中`InitInstance`创建后，`CCommandLineInfo`对象将传递给`ParseCommandLine`。

2. `ParseCommandLine`然后重复`CCommandLineInfo::ParseParam`调用，每个参数重复调用一次。

3. `ParseParam`填充`CCommandLineInfo`对象，然后传递给[进程ShellCommand](#processshellcommand)。

4. `ProcessShellCommand`处理命令行参数和标志。

请注意，您可以根据需要直接`ParseCommandLine`呼叫。

有关命令行标志的说明，请参阅[CCommandLineInfo：：m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)。

## <a name="cwinapppretranslatemessage"></a><a name="pretranslatemessage"></a>CWinApp：:P重新翻译消息

重写此函数以筛选窗口消息，然后再将其发送到 Windows 函数[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)默认实现执行快捷键转换，因此您必须在`CWinApp::PreTranslateMessage`重写版本中调用成员函数。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>参数

*pMsg*<br/>
指向包含要处理的消息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)结构的指针。

### <a name="return-value"></a>返回值

如果消息已完全处理，`PreTranslateMessage`则非零，不应进一步处理。 如果消息应以正常方式处理，则为零。

## <a name="cwinappprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinApp：:Process消息过滤器

框架的 hook 函数调用此成员函数来筛选和响应某些 Windows 消息。

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>参数

*code*<br/>
指定挂钩代码。 此成员函数使用代码来确定如何处理*lpMsg。*

*lpMsg*<br/>
指向 Windows [MSG](/windows/win32/api/winuser/ns-winuser-msg)truc 的指针。

### <a name="return-value"></a>返回值

处理消息时非零;否则 0。

### <a name="remarks"></a>备注

hook 函数在事件发送到应用程序的正常消息处理之前处理事件。

如果重写此高级功能，请确保调用基类版本以维护框架的挂钩处理。

## <a name="cwinappprocessshellcommand"></a><a name="processshellcommand"></a>CWinApp：:P罗塞斯舍尔命令

[InitInstance](#initinstance)调用此成员函数以接受从*rCmdInfo*`CCommandLineInfo`标识的对象传递的参数，并执行指示的操作。

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>参数

*rCmdInfo*<br/>
对[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)对象的引用。

### <a name="return-value"></a>返回值

如果外壳命令成功处理，则非零。 如果为 0，则从[Initinstance](#initinstance)返回 FALSE 。

### <a name="remarks"></a>备注

使用应用程序向导启动新的 MFC 项目时，应用程序向导`CCommandLineInfo`将创建 的本地实例，然后在`ProcessShellCommand``InitInstance`成员函数中调用 和[ParseCommandLine。](#parsecommandline) 命令行遵循下面描述的路由：

1. 在 中`InitInstance`创建后，`CCommandLineInfo`对象将传递给`ParseCommandLine`。

2. `ParseCommandLine`然后重复调用[CCommandLineInfo：:ParseParam，](../../mfc/reference/ccommandlineinfo-class.md#parseparam)每个参数一次。

3. `ParseParam`填充`CCommandLineInfo`对象，然后传递给`ProcessShellCommand`。

4. `ProcessShellCommand`处理命令行参数和标志。

[CCommandLineInfo：：m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)标识的对象`CCommandLineInfo``CCommandLineInfo`的数据成员属于以下枚举类型，在类中定义。

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

有关每个值的简要说明，请参阅`CCommandLineInfo::m_nShellCommand`。

## <a name="cwinappprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinApp：:P罗塞斯·温德普罗奇例外

每当处理程序未捕获应用程序的消息或命令处理程序中引发异常时，框架将调用此成员函数。

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>参数

*e*<br/>
指向未捕获异常的指针。

*pMsg*<br/>
包含导致框架引发异常的窗口消息的信息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)策略。

### <a name="return-value"></a>返回值

应返回到 Windows 的值。 通常，这是 0L 窗口消息， 1L （ TRUE） 的命令消息.

### <a name="remarks"></a>备注

不要直接调用此成员函数。

此成员函数的默认实现将创建一个消息框。 如果未捕获的异常源自菜单、工具栏或加速器命令失败，则消息框将显示"命令失败"消息;如果未捕获的异常源自菜单、工具栏或加速器命令失败。"否则，它会显示"内部应用程序错误"消息。

重写此成员函数，以提供异常的全局处理。 仅当希望显示消息框时，才调用基本功能。

## <a name="cwinappregister"></a><a name="register"></a>CWinApp：注册

执行未由`RegisterShellFileTypes`处理的任何注册任务。

```
virtual BOOL Register();
```

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="remarks"></a>备注

默认实现仅返回 TRUE。 重写此函数以提供任何自定义的注册步骤。

## <a name="cwinappregistershellfiletypes"></a><a name="registershellfiletypes"></a>CWinApp：：注册外壳文件类型

调用此成员函数向 Windows 文件管理器注册应用程序的所有文档类型。

```cpp
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>参数

*b 康波特*<br/>
[在]TRUE 添加 shell 命令"打印"和"打印到"的注册条目，允许用户直接从 shell 打印文件，或者将文件拖动到打印机对象。 它还添加了默认图标密钥。 默认情况下，此参数为 FALSE，用于向后兼容性。

### <a name="remarks"></a>备注

这允许用户通过从文件管理器中双击应用程序创建的数据文件来打开该文件。 在`RegisterShellFileTypes`调用应用程序中的每个文档模板后致电[AddDocTemplate。](#adddoctemplate) 调用`RegisterShellFileTypes`时还会调用[启用ShellOpen](#enableshellopen)成员函数。

`RegisterShellFileTypes`通过应用程序维护的[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象列表进行重新访问，并且为每个文档模板将条目添加到 Windows 为文件关联维护的注册数据库。 文件管理器使用这些条目在用户双击数据文件时打开数据文件。 这消除了发货的需要。注册文件与您的应用程序。

> [!NOTE]
> `RegisterShellFileTypes`仅当用户使用管理员权限运行程序时才有效。 如果程序没有管理员权限，则无法更改注册表项。

如果注册数据库已经将给定的文件名扩展名与另一种文件类型关联，则不会创建新关联。 有关注册`CDocTemplate`此信息所需的字符串格式，请参阅类。

## <a name="cwinappregisterwithrestartmanager"></a><a name="registerwithrestartmanager"></a>CWinApp：：注册与重新启动管理器

向重新启动管理器注册应用程序。

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
|参数|说明|
|*b 注册恢复回电*|[在]TRUE 指示应用程序的此实例使用恢复回调函数;FALSE 表示它不。 当应用程序意外退出时，框架调用恢复回调函数。 有关详细信息，请参阅[CWinApp：应用程序恢复回电](#applicationrecoverycallback)。|
|*strRestart标识符*|[在]标识重新启动管理器此实例的唯一字符串。 重新启动管理器标识符对于应用程序的每个实例是唯一的。|
|*pwzCommandLineArgs*|[在]包含命令行中任何额外参数的字符串。|
|*dwRestartFlags*|[在]重新启动管理器的可选标志。 有关详细信息，请参见“备注”部分。|
|*p 恢复回电*|[在]恢复回调功能。 此函数必须采用 LPVOID 参数作为输入并返回 DWORD。 默认恢复回调函数为`CWinApp::ApplicationRecoveryCallback`。|
|*lpvParam*|[在]恢复回调函数的输入参数。 有关详细信息，请参阅[CWinApp：应用程序恢复回电](#applicationrecoverycallback)。|
|*dwping 间隔*|[在]重新启动管理器等待恢复回调功能返回的时间长度。 此参数以毫秒为单位。|
|*dwCallbackFlags*|[在]传递给恢复回调功能的标志。 保留供将来使用。|

### <a name="return-value"></a>返回值

如果方法成功，S_OK;否则是错误代码。

### <a name="remarks"></a>备注

如果应用程序使用默认 MFC 实现进行自动保存文件，则应使用`RegisterWithRestartManager`的简单版本。 如果要自定义应用程序的自动保存`RegisterWithRestartManager`行为，请使用

如果使用*strRestart标识符*的空字符串调用此方法，请`RegisterWithRestartManager`为重新启动管理器的此实例创建一个唯一标识符字符串。

当应用程序意外退出时，重新启动管理器将从命令行重新启动应用程序，并提供唯一的重新启动标识符作为可选参数。 在这种情况下，框架调用`RegisterWithRestartManager`两次。 第一个调用来自[CWinApp：：InitInstance](#initinstance)具有字符串标识符的空字符串。 然后，方法[CWinApp：:ProcessShellCommand](#processshellcommand) `RegisterWithRestartManager`调用具有唯一的重新启动标识符。

向重新启动管理器注册应用程序后，重新启动管理器将监视应用程序。 如果应用程序意外退出，重新启动管理器将在关闭过程中调用恢复回调功能。 重新启动管理器等待*dwPingInterval，* 等待来自恢复回调函数的响应。 如果恢复回调函数在此时间内未响应，则应用程序将退出而不执行恢复回调功能。

默认情况下，dwRestartFlags 不受支持，但可供将来使用。 *dwRestartFlags*的可能值如下所示：

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappreopenpreviousfilesatrestart"></a><a name="reopenpreviousfilesatrestart"></a>CWinApp：：重新打开以前的文件在重新启动

确定重新启动管理器是否重新打开应用程序意外退出时打开的文件。

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>返回值

TRUE 表示重新启动管理器将重新打开以前打开的文件;如果重新启动，则表示重新启动管理器将重新打开以前打开的文件。FALSE 表示重新启动管理器没有。

## <a name="cwinapprestartinstance"></a><a name="restartinstance"></a>CWinApp：重新启动实例

处理重新启动管理器启动的应用程序重新启动。

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>返回值

如果数据恢复处理程序打开以前打开的文档，则为 TRUE;如果数据恢复处理程序出现错误或以前没有打开的文档，则 FALSE。

### <a name="remarks"></a>备注

重新启动管理器重新启动应用程序时，框架将调用此方法。 此方法检索数据恢复处理程序并还原自动保存的文件。 此方法调用[CDataRecoveryHandler：：还原自动保存的文档](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments)，以确定用户是否希望还原自动保存的文件。

如果[CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md)确定没有打开的文档，则此方法将返回 FALSE。 如果没有打开的文档，应用程序通常会启动。

## <a name="cwinapprestoreautosavedfilesatrestart"></a><a name="restoreautosavedfilesatrestart"></a>CWinApp：：恢复自动保存的文件在重新启动

确定重新启动管理器在重新启动应用程序时是否还原自动保存的文件。

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>返回值

TRUE 表示重新启动管理器还原自动保存的文件;FALSE 表示重新启动管理器没有。

## <a name="cwinapprun"></a><a name="run"></a>CWinApp：：运行

提供默认消息循环。

```
virtual int Run();
```

### <a name="return-value"></a>返回值

由`WinMain`返回**的 int**值。

### <a name="remarks"></a>备注

`Run`获取和调度 Windows 消息，直到应用程序收到WM_QUIT消息。 如果应用程序的消息队列当前不包含任何消息，请`Run`调用[OnIdle](#onidle)以执行空闲时间处理。 传入消息转到[PreTranslateMessage](#pretranslatemessage)成员函数进行特殊处理，然后转到 Windows`TranslateMessage`函数进行标准键盘转换;最后，`DispatchMessage`调用 Windows 函数。

`Run`很少重写，但您可以重写它以提供特殊行为。

## <a name="cwinapprunautomated"></a><a name="runautomated"></a>CWinApp：：运行自动

调用此函数以确定是否存在 **"/自动化**"或 **"-自动化**"选项，该选项指示服务器应用程序是否由客户端应用程序启动。

```
BOOL RunAutomated();
```

### <a name="return-value"></a>返回值

如果找到选项，则非零;否则 0。

### <a name="remarks"></a>备注

如果存在，则从命令行中删除该选项。 有关 OLE 自动化的详细信息，请参阅文章["自动化服务器](../../mfc/automation-servers.md)"。

## <a name="cwinapprunembedded"></a><a name="runembedded"></a>CWinApp：：运行嵌入式

调用此函数以确定是否存在 **"/嵌入**"或 **"-嵌入**"选项，该选项指示服务器应用程序是否由客户端应用程序启动。

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>返回值

如果找到选项，则非零;否则 0。

### <a name="remarks"></a>备注

如果存在，则从命令行中删除该选项。 有关嵌入的详细信息，请参阅文章["服务器：实现服务器](../../mfc/servers-implementing-a-server.md)"。

## <a name="cwinappsaveallmodified"></a><a name="saveallmodified"></a>CWinApp：：保存所有修改

由框架调用以在关闭应用程序的主框架窗口或通过WM_QUERYENDSESSION消息保存所有文档。

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>返回值

非零，如果安全终止应用程序;0 如果不安全，则终止应用程序。

### <a name="remarks"></a>备注

此成员函数的默认实现调用[CDocument：：保存修改](../../mfc/reference/cdocument-class.md#savemodified)的成员函数，依次用于应用程序中的所有修改文档。

## <a name="cwinappselectprinter"></a><a name="selectprinter"></a>CWinApp：：选择打印机

调用此成员功能以选择特定打印机，并释放以前在"打印对话框"中选择的打印机。

```cpp
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>参数

*hDevNames*<br/>
识别特定打印机的驱动程序、设备和输出端口名称的[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)分道的句柄。

*hDevMode*<br/>
指定有关打印机设备初始化和环境的信息的[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)结构的句柄。

*bFreeOld*<br/>
释放以前选择的打印机。

### <a name="remarks"></a>备注

如果*hDevMode*和*hDevNames* `SelectPrinter`均为 NULL，则使用当前默认打印机。

## <a name="cwinappsethelpmode"></a><a name="sethelpmode"></a>CWinApp：：设置帮助模式

设置应用程序的帮助类型。

```cpp
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>参数

*eHelpType*<br/>
指定要使用的帮助类型。 有关详细信息，请参阅[CWinApp：：m_eHelpType。](#m_ehelptype)

### <a name="remarks"></a>备注

设置应用程序的帮助类型。

要将应用程序的"帮助"类型设置为 HTML 帮助，可以调用[启用 HTML 帮助](#enablehtmlhelp)。 调用`EnableHTMLHelp`后，应用程序必须使用 HTMLHelp 作为其帮助应用程序。 如果要更改使用 WinHelp，可以调用`SetHelpMode`eHelpType 并将*eHelpType*设置为`afxWinHelp`。

## <a name="cwinappsetregistrykey"></a><a name="setregistrykey"></a>CWinApp：：设置注册密钥

导致应用程序设置存储在注册表中，而不是 INI 文件中。

```cpp
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>参数

*lpsz注册密钥*<br/>
指向包含键名称的字符串的指针。

*nID注册键*<br/>
包含注册表项名称的字符串资源的 ID。

### <a name="remarks"></a>备注

此函数集*m_pszRegistryKey* `GetProfileInt`，然后由 的 、`GetProfileString``WriteProfileInt`和`WriteProfileString`的成员函数使用`CWinApp`。 如果已调用此函数，则最近使用 （MRU） 文件的列表也会存储在注册表中。 注册表项通常是公司的名称。 它存储在以下形式的键：HKEY_CURRENT_USER_\\软件<公司名称\>\\<应用程序名称\>\\<节名称\>\\<值名称。\>

## <a name="cwinappsupportsapplicationrecovery"></a><a name="supportsapplicationrecovery"></a>CWinApp：：支持应用程序恢复

确定重新启动管理器是否恢复意外退出的应用程序。

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>返回值

TRUE 表示重新启动管理器正在恢复应用程序;FALSE 表示重新启动管理器没有。

## <a name="cwinappsupportsautosaveatinterval"></a><a name="supportsautosaveatinterval"></a>CWinApp：：支持自动保存At间隔

确定重新启动管理器是否以常规间隔自动保存打开的文档。

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>返回值

TRUE 表示重新启动管理器自动保存打开的文档;FALSE 表示重新启动管理器没有。

## <a name="cwinappsupportsautosaveatrestart"></a><a name="supportsautosaveatrestart"></a>CWinApp：：支持自动保存Atrestart

确定重新启动管理器在应用程序重新启动时是否自动保存任何打开的文档。

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>返回值

TRUE 指示重新启动管理器在应用程序重新启动时自动保存打开的文档;FALSE 表示重新启动管理器没有。

## <a name="cwinappsupportsrestartmanager"></a><a name="supportsrestartmanager"></a>CWinApp：：支持重新启动管理器

确定应用程序是否支持重新启动管理器。

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>返回值

TRUE 表示应用程序支持重新启动管理器;FALSE 表示应用程序没有。

## <a name="cwinappunregister"></a><a name="unregister"></a>CWinApp：：取消注册

取消注册应用程序对象注册的所有文件。

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="remarks"></a>备注

该`Unregister`函数撤消应用程序对象和[寄存器](#register)函数执行的注册。 通常，MFC 隐式调用这两个函数，因此不会显示在代码中。

重写此函数以执行自定义取消注册步骤。

## <a name="cwinappunregistershellfiletypes"></a><a name="unregistershellfiletypes"></a>CWinApp：：取消注册ShellFile类型

调用此成员函数，以在 Windows 文件管理器中取消注册应用程序的所有文档类型。

```cpp
void UnregisterShellFileTypes();
```

## <a name="cwinappwinhelp"></a><a name="winhelp"></a>CWinApp：：赢帮助

调用此成员函数以调用 WinHelp 应用程序。

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>参数

*dwData*<br/>
指定其他数据。 使用的值取决于*nCmd*参数的值。

*nCmd*<br/>
指定请求的帮助的类型。 有关可能值的列表及其如何影响*dwData*参数，请参阅[WinHelp](/windows/win32/api/winuser/nf-winuser-winhelpw) Windows 函数。

### <a name="remarks"></a>备注

框架还会调用此函数以调用 WinHelp 应用程序。

当您的应用程序终止时，框架将自动关闭 WinHelp 应用程序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

## <a name="cwinappwriteprofilebinary"></a><a name="writeprofilebinary"></a>CWinApp：：写配置文件二进制

调用此成员函数将二进制数据写入应用程序注册表或 的指定部分。INI 文件。

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>参数

*lpsz节*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果节不存在，则创建该节。 节的名称是案例独立的;字符串可以是大写字母和小写字母的任意组合。

*lpszEntry*<br/>
指向包含要写入该值的条目的 null 端接字符串。 如果该项在指定的节中不存在，则创建该条目。

*pData*<br/>
指向要写入的数据。

*n 字节*<br/>
包含要写入的字节数。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

此示例用于`CWinApp* pApp = AfxGetApp();`访问 CWinApp 类，`WriteProfileBinary``GetProfileBinary`说明可以从 MFC 应用程序中的任何函数使用的方法。

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

对于另一个示例，请参阅[CWinApp 的示例：：获取配置文件 Binary](#getprofilebinary)。

## <a name="cwinappwriteprofileint"></a><a name="writeprofileint"></a>CWinApp：：写配置文件

调用此成员函数将指定值写入应用程序注册表或 的指定部分。INI 文件。

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>参数

*lpsz节*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果节不存在，则创建该节。 节的名称是案例独立的;字符串可以是大写字母和小写字母的任意组合。

*lpszEntry*<br/>
指向包含要写入该值的条目的 null 端接字符串。 如果该项在指定的节中不存在，则创建该条目。

*n值*<br/>
包含要写入的值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

此示例`CWinApp* pApp = AfxGetApp();`用于在 CWinApp 类中说明一`WriteProfileString`种方法，该`WriteProfileInt`方法 可以从`GetProfileString`MFC 应用程序中的任何函数中使用 。 `GetProfileInt`

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

对于另一个示例，请参阅[CWinApp 的示例：：获取配置文件。](#getprofileint)

## <a name="cwinappwriteprofilestring"></a><a name="writeprofilestring"></a>CWinApp：：写配置文件字符串

调用此成员函数将指定的字符串写入应用程序注册表或 的指定部分。INI 文件。

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>参数

*lpsz节*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果节不存在，则创建该节。 节的名称是案例独立的;字符串可以是大写字母和小写字母的任意组合。

*lpszEntry*<br/>
指向包含要写入该值的条目的 null 端接字符串。 如果该项在指定的节中不存在，则创建该条目。 如果此参数为 NULL，则删除*lpszSection*指定的节。

*lpszValue*<br/>
指向要写入的字符串。 如果此参数为 NULL，则删除*lpszEntry*参数指定的条目。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

对于另一个示例，请参阅[CWinApp 的示例：：获取配置文件。](#getprofileint)

## <a name="cwinappsetappid"></a><a name="setappid"></a>CWinApp：：SetAppID

显式设置应用程序的应用程序用户模型 ID。 在向用户显示任何用户界面之前，应调用此方法（最佳位置是应用程序构造函数）。

```cpp
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>参数

*lpcszAppID*<br/>
指定应用程序用户型号 ID。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[CWinThread 类](../../mfc/reference/cwinthread-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[如何：添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)
