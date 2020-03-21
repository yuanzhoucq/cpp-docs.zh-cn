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
ms.openlocfilehash: 9e0af33bd6b95f7853cc989532b6fc18a658dc34
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079392"
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
|[CWinApp：： CWinApp](#cwinapp)|构造 `CWinApp` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWinApp：： AddDocTemplate](#adddoctemplate)|向应用程序的可用文档模板列表添加文档模板。|
|[CWinApp：： AddToRecentFileList](#addtorecentfilelist)|将文件名添加到最近使用的（MRU）文件列表。|
|[CWinApp：： ApplicationRecoveryCallback](#applicationrecoverycallback)|当应用程序意外退出时由框架调用。|
|[CWinApp：： CloseAllDocuments](#closealldocuments)|关闭所有打开的文档。|
|[CWinApp：： CreatePrinterDC](#createprinterdc)|创建打印机设备上下文。|
|[CWinApp：:D elRegTree](#delregtree)|删除指定的键及其所有子项。|
|[CWinApp：:D oMessageBox](#domessagebox)|实现应用程序的[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) 。|
|[CWinApp：:D oWaitCursor](#dowaitcursor)|打开和关闭等待光标。|
|[CWinApp：： EnableD2DSupport](#enabled2dsupport)|启用应用程序 D2D 支持。 在初始化主窗口之前调用此方法。|
|[CWinApp：： EnableHtmlHelp](#enablehtmlhelp)|实现应用程序的 HTMLHelp，而不是 WinHelp。|
|[CWinApp：： EnableTaskbarInteraction](#enabletaskbarinteraction)|启用任务栏交互。|
|[CWinApp：： ExitInstance](#exitinstance)|重写以在应用程序终止时进行清理。|
|[CWinApp：： GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|检索应用程序恢复方法的输入参数。|
|[CWinApp：： GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|返回重新启动管理器等待恢复回调函数返回的时间长度。|
|[CWinApp：： GetApplicationRestartFlags](#getapplicationrestartflags)|返回重新启动管理器的标志。|
|[CWinApp：： GetAppRegistryKey](#getappregistrykey)|返回 HKEY_CURRENT_USER\\"Software" \RegistryKey\ProfileName. 的密钥|
|[CWinApp：： GetDataRecoveryHandler](#getdatarecoveryhandler)|获取此应用程序实例的数据恢复处理程序。|
|[CWinApp：： GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|检索第一个文档模板的位置。|
|[CWinApp：： GetHelpMode](#gethelpmode)|检索应用程序使用的帮助的类型。|
|[CWinApp：： GetNextDocTemplate](#getnextdoctemplate)|检索文档模板的位置。 可以递归使用。|
|[CWinApp：： GetPrinterDeviceDefaults](#getprinterdevicedefaults)|检索打印机设备默认值。|
|[CWinApp：： GetProfileBinary](#getprofilebinary)|从应用程序的中的项检索二进制数据。INI 文件。|
|[CWinApp：： GetProfileInt](#getprofileint)|检索应用程序的项中的一个整数。INI 文件。|
|[CWinApp：： GetProfileString](#getprofilestring)|从应用程序的中的项检索字符串。INI 文件。|
|[CWinApp：： GetSectionKey](#getsectionkey)|返回 HKEY_CURRENT_USER\\"Software" \RegistryKey\AppName\lpszSection. 的密钥|
|[CWinApp：： HideApplication](#hideapplication)|关闭所有文档之前，隐藏应用程序。|
|[CWinApp：： HtmlHelp](#htmlhelp)|调用 `HTMLHelp` Windows 函数。|
|[CWinApp：： InitInstance](#initinstance)|重写以执行 Windows 实例初始化，如创建窗口对象。|
|[CWinApp：： IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|指示是否启用 Windows 7 任务栏交互。|
|[CWinApp：： LoadCursor](#loadcursor)|加载游标资源。|
|[CWinApp：： LoadIcon](#loadicon)|加载图标资源。|
|[CWinApp：： LoadOEMCursor](#loadoemcursor)|加载**OCR_** 常数在 windows 中指定的 windows OEM 预定义光标。高.|
|[CWinApp：： LoadOEMIcon](#loadoemicon)|加载**OIC_** 常数在 windows 中指定的 windows OEM 预定义图标。高.|
|[CWinApp：： LoadStandardCursor](#loadstandardcursor)|加载**IDC_** 常数在 windows 中指定的 windows 预定义光标。高.|
|[CWinApp：： LoadStandardIcon](#loadstandardicon)|加载**IDI_** 常数在 windows 中指定的 windows 预定义图标。高.|
|[CWinApp：： OnDDECommand](#onddecommand)|由框架调用以响应动态数据交换（DDE）执行命令。|
|[CWinApp：： OnIdle](#onidle)|重写以执行应用程序特定的空闲时间处理。|
|[CWinApp：： OpenDocumentFile](#opendocumentfile)|由框架调用，以从文件打开文档。|
|[CWinApp：:P arseCommandLine](#parsecommandline)|分析命令行中的单个参数和标志。|
|[CWinApp：:P reTranslateMessage](#pretranslatemessage)|在将消息调度到 Windows 函数[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)之前筛选消息。|
|[CWinApp：:P rocessMessageFilter](#processmessagefilter)|在某些消息到达应用程序之前截获这些消息。|
|[CWinApp：:P rocessShellCommand](#processshellcommand)|处理命令行参数和标志。|
|[CWinApp：:P rocessWndProcException](#processwndprocexception)|截获应用程序的消息和命令处理程序引发的所有未经处理的异常。|
|[CWinApp：： Register](#register)|执行自定义注册。|
|[CWinApp：： RegisterWithRestartManager](#registerwithrestartmanager)|向重新启动管理器注册应用程序。|
|[CWinApp：： ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|确定重新启动管理器是否重新打开应用程序意外退出时打开的文件。|
|[CWinApp：： RestartInstance](#restartinstance)|处理重新启动管理器启动的应用程序重启。|
|[CWinApp：： RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|确定重新启动管理器是否在重新启动应用程序时还原自动保存的文件。|
|[CWinApp：： Run](#run)|运行默认消息循环。 重写以自定义消息循环。|
|[CWinApp：： RunAutomated](#runautomated)|测试应用程序的命令行中的 **/Automation**选项。 已过时。 请改为在调用[ParseCommandLine](#parsecommandline)后，使用[CCommandLineInfo：： m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated)中的值。|
|[CWinApp：： RunEmbedded](#runembedded)|测试应用程序的命令行中的 **/Embedding**选项。 已过时。 请改为在调用[ParseCommandLine](#parsecommandline)后，使用[CCommandLineInfo：： m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded)中的值。|
|[CWinApp：： SaveAllModified](#saveallmodified)|提示用户保存所有已修改的文档。|
|[CWinApp：： SelectPrinter](#selectprinter)|选择先前由用户通过 "打印" 对话框指示的打印机。|
|[CWinApp：： SetHelpMode](#sethelpmode)|设置和初始化应用程序使用的帮助的类型。|
|[CWinApp：： SupportsApplicationRecovery](#supportsapplicationrecovery)|确定重新启动管理器是否恢复意外退出的应用程序。|
|[CWinApp：： SupportsAutosaveAtInterval](#supportsautosaveatinterval)|确定重新启动管理器是否自动保存按固定间隔打开文档。|
|[CWinApp：： SupportsAutosaveAtRestart](#supportsautosaveatrestart)|确定在应用程序重新启动时重新启动管理器是否自动保存任何打开的文档。|
|[CWinApp：： SupportsRestartManager](#supportsrestartmanager)|确定应用程序是否支持重新启动管理器。|
|[CWinApp：：注销](#unregister)|注销 `CWinApp` 对象注册的所有已知的内容。|
|[CWinApp：： WinHelp](#winhelp)|调用 `WinHelp` Windows 函数。|
|[CWinApp：： WriteProfileBinary](#writeprofilebinary)|将二进制数据写入应用程序的中的条目。INI 文件。|
|[CWinApp：： WriteProfileInt](#writeprofileint)|在应用程序的中将整数写入项。INI 文件。|
|[CWinApp：： WriteProfileString](#writeprofilestring)|向应用程序的中的项写入一个字符串。INI 文件。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[CWinApp：： EnableShellOpen](#enableshellopen)|允许用户从 Windows 文件管理器打开数据文件。|
|[CWinApp：： LoadStdProfileSettings](#loadstdprofilesettings)|加载 standard。INI 文件设置并启用 MRU 文件列表功能。|
|[CWinApp：： OnContextHelp](#oncontexthelp)|处理应用程序中的 SHIFT + F1 帮助。|
|[CWinApp：： OnFileNew](#onfilenew)|实现 ID_FILE_NEW 命令。|
|[CWinApp：： OnFileOpen](#onfileopen)|实现 ID_FILE_OPEN 命令。|
|[CWinApp：： OnFilePrintSetup](#onfileprintsetup)|实现 ID_FILE_PRINT_SETUP 命令。|
|[CWinApp：： OnHelp](#onhelp)|处理应用程序中的 F1 帮助（使用当前上下文）。|
|[CWinApp：： OnHelpFinder](#onhelpfinder)|处理 ID_HELP_FINDER 和 ID_DEFAULT_HELP 命令。|
|[CWinApp：： OnHelpIndex](#onhelpindex)|处理 ID_HELP_INDEX 命令并提供默认帮助主题。|
|[CWinApp：： OnHelpUsing](#onhelpusing)|处理 ID_HELP_USING 命令。|
|[CWinApp：： RegisterShellFileTypes](#registershellfiletypes)|将所有应用程序的文档类型注册到 Windows 文件管理器。|
|[CWinApp：： SetAppID](#setappid)|显式设置应用程序的应用程序用户模型 ID。 应在向用户显示任何用户界面之前调用此方法（最佳位置是应用程序构造函数）。|
|[CWinApp：： SetRegistryKey](#setregistrykey)|导致应用程序设置存储在注册表中，而不是存储在中。INI 文件。|
|[CWinApp：： UnregisterShellFileTypes](#unregistershellfiletypes)|通过 Windows 文件管理器注销所有应用程序的文档类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CWinApp：： m_bHelpMode](#m_bhelpmode)|指示用户是否处于帮助上下文模式（通常用 SHIFT + F1 调用）。|
|[CWinApp：： m_eHelpType](#m_ehelptype)|指定应用程序使用的帮助的类型。|
|[CWinApp：： m_hInstance](#m_hinstance)|标识应用程序的当前实例。|
|[CWinApp：： m_lpCmdLine](#m_lpcmdline)|指向以 null 结尾的字符串，它指定应用程序的命令行。|
|[CWinApp：： m_nCmdShow](#m_ncmdshow)|指定最初显示窗口的方式。|
|[CWinApp：： m_pActiveWnd](#m_pactivewnd)|OLE 服务器处于就地活动状态时，指向容器应用程序的主窗口的指针。|
|[CWinApp：： m_pszAppID](#m_pszappid)|应用程序用户模型 ID。|
|[CWinApp：： m_pszAppName](#m_pszappname)|指定应用程序的名称。|
|[CWinApp：： m_pszExeName](#m_pszexename)|应用程序的模块名称。|
|[CWinApp：： m_pszHelpFilePath](#m_pszhelpfilepath)|应用程序的帮助文件的路径。|
|[CWinApp：： m_pszProfileName](#m_pszprofilename)|应用程序的。INI 文件名。|
|[CWinApp：： m_pszRegistryKey](#m_pszregistrykey)|用于确定用于存储应用程序配置文件设置的完整注册表项。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CWinApp：： m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|确定重新启动管理器的行为方式的标志。|
|[CWinApp：： m_nAutosaveInterval](#m_nautosaveinterval)|自动保存之间的时间长度（以毫秒为单位）。|
|[CWinApp：： m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|指向应用程序的数据恢复处理程序的指针。|

## <a name="remarks"></a>备注

应用程序对象提供用于初始化应用程序的成员函数（及其每个实例）以及运行应用程序的成员函数。

使用 Microsoft 基础类的每个应用程序只能包含一个派生自 `CWinApp`的对象。 当构造其他C++全局对象并在 Windows 调用由 Microsoft 基础类库提供的 `WinMain` 函数时，将构造此对象。 在全局级别声明派生的 `CWinApp` 对象。

从 `CWinApp`派生应用程序类时，请重写[InitInstance](#initinstance)成员函数，以创建应用程序的主窗口对象。

除了 `CWinApp` 成员函数外，Microsoft 基础类库提供以下全局函数来访问 `CWinApp` 对象和其他全局信息：

- [AfxGetApp](application-information-and-management.md#afxgetapp)获取指向 `CWinApp` 对象的指针。

- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)获取当前应用程序实例的句柄。

- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle)获取应用程序资源的句柄。

- [AfxGetAppName](application-information-and-management.md#afxgetappname)获取一个指针，该指针指向包含应用程序名称的字符串。 或者，如果有指向 `CWinApp` 对象的指针，请使用 `m_pszExeName` 获取应用程序的名称。

有关 `CWinApp` 类的详细信息，请参阅[CWinApp：应用程序类](../../mfc/cwinapp-the-application-class.md)，包括以下概述：

- 由应用程序向导编写的 `CWinApp`派生代码。

- `CWinApp`在应用程序的执行顺序中的角色。

- `CWinApp`的默认成员函数实现。

- `CWinApp`的密钥可重写。

`m_hPrevInstance` 数据成员不再存在。 若要确定应用程序的另一个实例是否正在运行，请使用已命名的 mutex。 如果打开互斥体失败，则没有应用程序的其他实例正在运行。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cwinappadddoctemplate"></a><a name="adddoctemplate"></a>CWinApp：： AddDocTemplate

调用此成员函数可将文档模板添加到应用程序维护的可用文档模板列表。

```
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>parameters

*pTemplate*<br/>
指向要添加的 `CDocTemplate` 的指针。

### <a name="remarks"></a>备注

在调用[RegisterShellFileTypes](#registershellfiletypes)之前，应将所有文档模板添加到应用程序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

##  <a name="cwinappaddtorecentfilelist"></a><a name="addtorecentfilelist"></a>CWinApp：： AddToRecentFileList

调用此成员函数以将*lpszPathName*添加到 MRU 文件列表。

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>parameters

*lpszPathName*<br/>
文件的路径。

### <a name="remarks"></a>备注

在使用此成员函数之前，应调用[LoadStdProfileSettings](#loadstdprofilesettings)成员函数以加载当前的 MRU 文件列表。

框架在打开文件或执行 "另存为" 命令以使用新名称保存文件时调用此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

##  <a name="cwinappapplicationrecoverycallback"></a><a name="applicationrecoverycallback"></a>CWinApp：： ApplicationRecoveryCallback

当应用程序意外退出时由框架调用。

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>parameters

*lpvParam*<br/>
中保留供将来使用。

### <a name="return-value"></a>返回值

如果此方法成功，则为 0;如果发生错误，则为非零值。

### <a name="remarks"></a>备注

如果你的应用程序支持重新启动管理器，则在应用程序意外退出时，框架会调用此函数。

`ApplicationRecoveryCallback` 的默认实现使用 `CDataRecoveryHandler` 将当前打开的文档的列表保存到注册表中。 此方法不自动保存任何文件。

若要自定义行为，请在派生的[CWinApp 类](../../mfc/reference/cwinapp-class.md)中重写此函数，或将您自己的应用程序恢复方法作为参数传递给[CWinApp：： RegisterWithRestartManager](#registerwithrestartmanager)。

##  <a name="cwinappclosealldocuments"></a><a name="closealldocuments"></a>CWinApp：： CloseAllDocuments

在退出之前调用此成员函数以关闭所有打开的文档。

```
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>parameters

*bEndSession*<br/>
指定是否将结束 Windows 会话。 如果会话正在结束，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

调用[HideApplication](#hideapplication) ，然后调用 `CloseAllDocuments`。

##  <a name="cwinappcreateprinterdc"></a><a name="createprinterdc"></a>CWinApp：： CreatePrinterDC

调用此成员函数以从所选打印机创建打印机设备上下文（DC）。

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>parameters

*dc*<br/>
对打印机设备上下文的引用。

### <a name="return-value"></a>返回值

如果成功创建打印机设备上下文，则为非零值;否则为0。

### <a name="remarks"></a>备注

`CreatePrinterDC` 初始化通过引用传递的设备上下文，因此可以使用它进行打印。

如果此函数成功，则在完成打印后，必须销毁设备上下文。 可以让[CDC](../../mfc/reference/cdc-class.md)对象的析构函数执行该操作，也可以通过调用[Cdc：:D eletedc](../../mfc/reference/cdc-class.md#deletedc)来显式执行此操作。

##  <a name="cwinappcwinapp"></a><a name="cwinapp"></a>CWinApp：： CWinApp

构造 `CWinApp` 对象并传递要存储为应用程序名称的*lpszAppName* 。

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>parameters

*lpszAppName*<br/>
一个以 null 结尾的字符串，其中包含 Windows 使用的应用程序名称。 如果未提供此参数或该参数为 NULL，`CWinApp` 将使用资源字符串 AFX_IDS_APP_TITLE 或可执行文件的文件名。

### <a name="remarks"></a>备注

应构造 `CWinApp`派生类的一个全局对象。 您的应用程序中只能有一个 `CWinApp` 对象。 构造函数存储指向 `CWinApp` 对象的指针，以便 `WinMain` 可以调用该对象的成员函数以初始化并运行该应用程序。

##  <a name="cwinappdelregtree"></a><a name="delregtree"></a>CWinApp：:D elRegTree

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

### <a name="parameters"></a>parameters

*hParentKey*<br/>
注册表项的句柄。

*strKeyName*<br/>
要删除的注册表项的名称。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针。

### <a name="return-value"></a>返回值

如果该函数成功，则返回值为 ERROR_SUCCESS。 如果函数失败，则返回值为 Winerror.h 中定义的非零错误代码。

### <a name="remarks"></a>备注

调用此函数可删除指定的键及其子项。

##  <a name="cwinappdomessagebox"></a><a name="domessagebox"></a>CWinApp：:D oMessageBox

框架调用此成员函数来实现全局函数[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)的消息框。

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>parameters

*lpszPrompt*<br/>
消息框中的文本地址。

nType<br/>
消息框[样式](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)。

*nIDPrompt*<br/>
帮助上下文字符串的索引。

### <a name="return-value"></a>返回值

返回与 `AfxMessageBox`相同的值。

### <a name="remarks"></a>备注

不要调用此成员函数来打开消息框;改用 `AfxMessageBox`。

重写此成员函数以自定义应用程序范围的 `AfxMessageBox` 调用处理。

##  <a name="cwinappdowaitcursor"></a><a name="dowaitcursor"></a>CWinApp：:D oWaitCursor

框架调用此成员函数来实现[CWaitCursor](../../mfc/reference/cwaitcursor-class.md)、 [CCmdTarget：： BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)、 [CCmdTarget：： EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)和[CCmdTarget：： RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>parameters

*nCode*<br/>
如果此参数为1，则将显示等待光标。 如果为0，则在不递增引用计数的情况下还原等待光标。 如果为-1，则等待光标结束。

### <a name="remarks"></a>备注

默认实现沙漏光标。 `DoWaitCursor` 维护引用计数。 如果为正，则显示沙漏光标。

虽然通常不会直接调用 `DoWaitCursor`，但你可以重写此成员函数以更改等待游标，或在显示等待光标时执行其他处理。

对于实现等待光标的更简单、更简单的方法，请使用 `CWaitCursor`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

##  <a name="cwinappenabled2dsupport"></a><a name="enabled2dsupport"></a>CWinApp：： EnableD2DSupport

需要 Visual Studio 2010 SP1。

启用应用程序 D2D 支持。 在初始化主窗口之前调用此方法。

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>parameters

*d2dFactoryType*<br/>
D2D 工厂及其创建的资源的线程模型。

*writeFactoryType*<br/>
一个值，该值指定是共享还是隔离写入工厂对象

### <a name="return-value"></a>返回值

如果支持 D2D，则返回 TRUE; 否则返回 FALSE

##  <a name="cwinappenablehtmlhelp"></a><a name="enablehtmlhelp"></a>CWinApp：： EnableHtmlHelp

从 `CWinApp`派生类的构造函数中调用此成员函数，以使用 HTMLHelp 作为应用程序的帮助。

```
void EnableHtmlHelp();
```

### <a name="remarks"></a>备注

##  <a name="cwinappenableshellopen"></a><a name="enableshellopen"></a>CWinApp：： EnableShellOpen

通常从 `InitInstance` 重写调用此函数，使应用程序的用户在双击 Windows 文件管理器中的文件时可以打开数据文件。

```
void EnableShellOpen();
```

### <a name="remarks"></a>备注

与此函数一起调用 `RegisterShellFileTypes` 成员函数，或提供。注册文件和应用程序，用于手动注册文档类型。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

##  <a name="cwinappenabletaskbarinteraction"></a><a name="enabletaskbarinteraction"></a>CWinApp：： EnableTaskbarInteraction

启用任务栏交互。

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>parameters

*bEnable*<br/>
指定应启用（TRUE）还是禁用（FALSE）与 Windows 7 任务栏的交互。

### <a name="return-value"></a>返回值

如果可以启用或禁用任务栏交互，则返回 TRUE。

### <a name="remarks"></a>备注

必须先调用此方法，然后才能创建主窗口，否则它将断言并返回 FALSE。

##  <a name="cwinappexitinstance"></a><a name="exitinstance"></a>CWinApp：： ExitInstance

由框架从 `Run` 成员函数中调用以退出应用程序实例。

```
virtual int ExitInstance();
```

### <a name="return-value"></a>返回值

应用程序的退出代码;0表示没有错误，大于0的值表示错误。 此值用作 `WinMain`的返回值。

### <a name="remarks"></a>备注

不要从任何位置调用此成员函数，但在 `Run` 成员函数中。

此函数的默认实现将框架选项写入应用程序的。INI 文件。 重写此函数以在应用程序终止时进行清理。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

##  <a name="cwinappgetapplicationrecoveryparameter"></a><a name="getapplicationrecoveryparameter"></a>CWinApp：： GetApplicationRecoveryParameter

检索应用程序恢复方法的输入参数。

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>返回值

应用程序恢复方法的默认输入参数。

### <a name="remarks"></a>备注

此函数的默认行为返回 NULL。

有关详细信息，请参阅[CWinApp：： ApplicationRecoveryCallback](#applicationrecoverycallback)。

##  <a name="cwinappgetapplicationrecoverypinginterval"></a><a name="getapplicationrecoverypinginterval"></a>CWinApp：： GetApplicationRecoveryPingInterval

返回重新启动管理器等待恢复回调函数返回的时间长度。

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>返回值

时间长度（以毫秒为单位）。

### <a name="remarks"></a>备注

当向重新启动管理器注册的应用程序意外退出时，应用程序会尝试保存打开的文档并调用恢复回叫函数。 默认恢复回调函数为[CWinApp：： ApplicationRecoveryCallback](#applicationrecoverycallback)。

框架等待恢复回调函数返回的时间长度为 ping 间隔。 可以通过重写 `CWinApp::GetApplicationRecoveryPingInterval` 或提供自定义值来自定义 ping 间隔以 `RegisterWithRestartManager`。

##  <a name="cwinappgetapplicationrestartflags"></a><a name="getapplicationrestartflags"></a>CWinApp：： GetApplicationRestartFlags

返回重新启动管理器的标志。

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>返回值

重新启动管理器的标志。 默认实现返回0。

### <a name="remarks"></a>备注

重新启动管理器的标志不会对默认实现产生任何影响。 它们供将来使用。

使用[CWinApp：： RegisterWithRestartManager](#registerwithrestartmanager)将应用程序注册到重新启动管理器时，可以设置标志。

重新启动管理器标志的可能值如下：

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="cwinappgetappregistrykey"></a><a name="getappregistrykey"></a>CWinApp：： GetAppRegistryKey

返回 HKEY_CURRENT_USER\\"Software" \RegistryKey\ProfileName. 的密钥

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>parameters

*pTM*<br/>
指向 `CAtlTransactionManager` 对象的指针。

### <a name="return-value"></a>返回值

如果函数成功，则为应用程序键;否则为 NULL。

### <a name="remarks"></a>备注

##  <a name="cwinappgetdatarecoveryhandler"></a><a name="getdatarecoveryhandler"></a>CWinApp：： GetDataRecoveryHandler

获取此应用程序实例的数据恢复处理程序。

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>返回值

此应用程序实例的数据恢复处理程序。

### <a name="remarks"></a>备注

使用重启管理器的每个应用程序都必须具有[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)的一个实例。 此类负责监视打开的文档和正在文件。 `CDataRecoveryHandler` 的行为取决于重新启动管理器的配置。 有关详细信息，请参阅[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)。

在早于 Windows Vista 的操作系统上，此方法返回 NULL。 Windows Vista 之前的操作系统不支持重新启动管理器。

如果应用程序当前没有数据恢复处理程序，则此方法将创建一个，并返回指向它的指针。

##  <a name="cwinappgetfirstdoctemplateposition"></a><a name="getfirstdoctemplateposition"></a>CWinApp：： GetFirstDocTemplatePosition

获取应用程序中第一个文档模板的位置。

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>返回值

可用于迭代或对象指针检索的位置值;如果列表为空，则为 NULL。

### <a name="remarks"></a>备注

使用在对[GetNextDocTemplate](#getnextdoctemplate)的调用中返回的位置值获取第一个[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象。

##  <a name="cwinappgethelpmode"></a><a name="gethelpmode"></a>CWinApp：： GetHelpMode

检索应用程序使用的帮助的类型。

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>返回值

应用程序使用的帮助类型。 有关详细信息，请参阅[CWinApp：： m_eHelpType](#m_ehelptype) 。

##  <a name="cwinappgetnextdoctemplate"></a><a name="getnextdoctemplate"></a>CWinApp：： GetNextDocTemplate

获取由*pos*标识的文档模板，然后将 " *pos* " 设置为 "位置" 值。

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>parameters

pos<br/>
对 `GetNextDocTemplate` 或[GetFirstDocTemplatePosition](#getfirstdoctemplateposition)的前一次调用所返回的位置值的引用。 此调用会将值更新到下一个位置。

### <a name="return-value"></a>返回值

指向[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象的指针。

### <a name="remarks"></a>备注

如果使用对 `GetFirstDocTemplatePosition`的调用建立初始位置，则可以在向前迭代循环中使用 `GetNextDocTemplate`。

您必须确保您的位置值有效。 如果无效，则 Microsoft 基础类库断言的调试版本。

如果检索到的文档模板是最后一个可用的模板，则*pos*的新值将设置为 NULL。

##  <a name="cwinappgetprinterdevicedefaults"></a><a name="getprinterdevicedefaults"></a>CWinApp：： GetPrinterDeviceDefaults

调用此成员函数以为打印提供打印机设备上下文。

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>parameters

*pPrintDlg*<br/>
指向[PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

从 Windows 检索当前打印机默认值。INI 文件，或者在打印设置中使用用户设置的最后一个打印机配置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

##  <a name="cwinappgetprofilebinary"></a><a name="getprofilebinary"></a>CWinApp：： GetProfileBinary

调用此成员函数以从应用程序的注册表的指定部分或中的项检索二进制数据。INI 文件。

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>parameters

*lpszSection*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。

*lpszEntry*<br/>
指向以 null 结尾的字符串，该字符串包含要检索其值的条目。

*ppData*<br/>
指向将接收数据地址的指针。

*pBytes*<br/>
指向将接收数据大小（以字节为单位）的 UINT。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数不区分大小写，因此*lpszSection*和*lpszEntry*参数中的字符串可能会有所不同。

> [!NOTE]
> `GetProfileBinary` 分配一个缓冲区并在 \* *ppData*中返回其地址。 调用方负责使用**delete []** 释放缓冲区。

> [!IMPORTANT]
> 此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

有关其他示例，请参阅[CWinApp：： WriteProfileBinary](#writeprofilebinary)。

##  <a name="cwinappgetprofileint"></a><a name="getprofileint"></a>CWinApp：： GetProfileInt

调用此成员函数以检索应用程序的注册表或 .INI 文件的指定部分中条目的整数的值。

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>parameters

*lpszSection*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。

*lpszEntry*<br/>
指向以 null 结尾的字符串，该字符串包含要检索其值的条目。

*nDefault*<br/>
指定在框架找不到条目时要返回的默认值。

### <a name="return-value"></a>返回值

如果函数成功，则为指定条目后面的字符串的整数值。 如果该函数找不到该条目，则返回值为*nDefault*参数的值。 如果与指定条目对应的值不为整数，则返回值为 0。

在 .INI 文件中，此成员函数支持值的十六进制表示法。 检索带符号的整数时，应将值强制转换为**int**。

### <a name="remarks"></a>备注

此成员函数不区分大小写，因此*lpszSection*和*lpszEntry*参数中的字符串可能会有所不同。

> [!IMPORTANT]
> 此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

有关其他示例，请参阅[CWinApp：： WriteProfileInt](#writeprofileint)。

##  <a name="cwinappgetprofilestring"></a><a name="getprofilestring"></a>CWinApp：： GetProfileString

调用此成员函数以检索与应用程序的注册表或中指定节内的条目关联的字符串。INI 文件。

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>parameters

*lpszSection*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。

*lpszEntry*<br/>
指向以 null 结尾的字符串，该字符串包含要检索其字符串的项。 此值不得为 NULL。

*lpszDefault*<br/>
如果在初始化文件中找不到该项，则指向给定项的默认字符串值。

### <a name="return-value"></a>返回值

返回值为应用程序的中的字符串。INI 文件或*lpszDefault* （如果找不到该字符串）。 _MAX_PATH 框架支持的最大字符串长度。 如果*lpszDefault*为 NULL，则返回值为空字符串。

### <a name="remarks"></a>备注

> [!IMPORTANT]
> 此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

对于另一个示例，请参阅[CWinApp：： GetProfileInt](#getprofileint)的示例。

##  <a name="cwinappgetsectionkey"></a><a name="getsectionkey"></a>CWinApp：： GetSectionKey

返回 HKEY_CURRENT_USER\\"Software" \RegistryKey\AppName\lpszSection. 的密钥

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>parameters

*lpszSection*<br/>
要获取的密钥的名称。

*pTM*<br/>
指向 `CAtlTransactionManager` 对象的指针。

### <a name="return-value"></a>返回值

如果函数成功，则为节键;否则为 NULL。

### <a name="remarks"></a>备注

##  <a name="cwinapphideapplication"></a><a name="hideapplication"></a>CWinApp：： HideApplication

在关闭打开的文档之前，调用此成员函数以隐藏应用程序。

```
void HideApplication();
```

##  <a name="cwinapphtmlhelp"></a><a name="htmlhelp"></a>CWinApp：： HtmlHelp

调用此成员函数以调用 HTMLHelp 应用程序。

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>parameters

*dwData*<br/>
指定其他数据。 使用的值取决于*nCmd*参数的值。 默认为 `0x000F` 这意味着[HH_HELP_CONTEXT](/previous-versions/windows/desktop/htmlhelp/hh-help-context-command)。

*nCmd*<br/>
指定请求的帮助的类型。 有关可能值的列表以及这些值如何影响*dwData*参数，请参阅 Windows SDK 中的[HtmlHelpW](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpw)或[HtmlHelpA](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpa) API 函数中描述的*uCommand*参数。

### <a name="remarks"></a>备注

框架还调用此函数来调用 HTMLHelp 应用程序。

当应用程序终止时，框架将自动关闭 HTMLHelp 应用程序。

##  <a name="cwinappinitinstance"></a><a name="initinstance"></a>CWinApp：： InitInstance

Windows 允许同时运行同一程序的多个副本。

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>返回值

如果初始化成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

应用程序初始化在概念上分为两部分：首次运行程序时执行的一次性应用程序初始化，以及在每次运行程序副本时运行的实例初始化（包括第一次）。 的框架实现 `WinMain` 调用此函数。

重写 `InitInstance` 以初始化在 Windows 下运行的应用程序的每个新实例。 通常，重写 `InitInstance` 来构造主窗口对象，并将 `CWinThread::m_pMainWnd` 数据成员设置为指向该窗口。 有关重写此成员函数的详细信息，请参阅[CWinApp：应用程序类](../../mfc/cwinapp-the-application-class.md)。

> [!NOTE]
> MFC 应用程序必须初始化为单线程单元（STA）。 如果在 `InitInstance` 重写中调用[CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) ，请指定 COINIT_APARTMENTTHREADED （而不是 COINIT_MULTITHREADED）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

##  <a name="cwinappistaskbarinteractionenabled"></a><a name="istaskbarinteractionenabled"></a>CWinApp：： IsTaskbarInteractionEnabled

指示是否启用 Windows 7 任务栏交互。

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>返回值

如果已调用 `EnableTaskbarInteraction` 并且操作系统为 Windows 7 或更高版本，则返回 TRUE。

### <a name="remarks"></a>备注

任务栏交互是指在鼠标指针位于应用程序任务栏按钮上时，MDI 应用程序会在单独的选项卡式缩略图中显示 MDI 子级的内容。

##  <a name="cwinapploadcursor"></a><a name="loadcursor"></a>CWinApp：： LoadCursor

从当前可执行文件加载由*lpszResourceName*命名的或由*nIDResource*指定的游标资源。

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>parameters

*lpszResourceName*<br/>
指向以 null 结尾的字符串，该字符串包含游标资源的名称。 可以为此参数使用 `CString`。

*nIDResource*<br/>
游标资源的 ID。 有关资源列表，请参阅 Windows SDK 中的[LoadCursor](/windows/win32/api/winuser/nf-winuser-loadcursorw) 。

### <a name="return-value"></a>返回值

如果成功，则为游标的句柄;否则为 NULL。

### <a name="remarks"></a>备注

`LoadCursor` 仅在之前尚未加载游标时将其加载到内存中;否则，它将检索现有资源的句柄。

使用[LoadStandardCursor](#loadstandardcursor)或[LoadOEMCursor](#loadoemcursor)成员函数访问预定义的 Windows 游标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

##  <a name="cwinapploadicon"></a><a name="loadicon"></a>CWinApp：： LoadIcon

从可执行文件加载*lpszResourceName*或*nIDResource*指定的图标资源。

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>parameters

*lpszResourceName*<br/>
指向以 null 结尾的字符串，该字符串包含图标资源的名称。 还可以对此参数使用 `CString`。

*nIDResource*<br/>
图标资源的 ID 号。

### <a name="return-value"></a>返回值

如果成功，则为图标的句柄;否则为 NULL。

### <a name="remarks"></a>备注

仅当之前未加载图标时，`LoadIcon` 才加载该图标;否则，它将检索现有资源的句柄。

可以使用[LoadStandardIcon](#loadstandardicon)或[LoadOEMIcon](#loadoemicon)成员函数访问预定义的 Windows 图标。

> [!NOTE]
> 此成员函数调用 Win32 API 函数[LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)，该函数只能加载其大小符合 SM_CXICON 和 SM_CYICON 系统指标值的图标。

##  <a name="cwinapploadoemcursor"></a><a name="loadoemcursor"></a>CWinApp：： LoadOEMCursor

加载*nIDCursor*指定的 Windows 预定义游标资源。

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>parameters

*nIDCursor*<br/>
一个**OCR_** 清单常量标识符，它指定预定义的 Windows 光标。 你必须在 `#include \<afxwin.h>` 之前具有 `#define OEMRESOURCE`，才能获得对 WINDOWS 中**OCR_** 常量的访问权限。高.

### <a name="return-value"></a>返回值

如果成功，则为游标的句柄;否则为 NULL。

### <a name="remarks"></a>备注

使用 `LoadOEMCursor` 或[LoadStandardCursor](#loadstandardcursor)成员函数访问预定义的 Windows 游标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

##  <a name="cwinapploadoemicon"></a><a name="loadoemicon"></a>CWinApp：： LoadOEMIcon

加载*nIDIcon*指定的 Windows 预定义图标资源。

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>parameters

*nIDIcon*<br/>
一个**OIC_** 清单常量标识符，它指定预定义的 Windows 图标。 在 `#include \<afxwin.h>` 访问 WINDOWS 中的**OIC_** 常量之前，您必须具有 `#define OEMRESOURCE`。高.

### <a name="return-value"></a>返回值

如果成功，则为图标的句柄;否则为 NULL。

### <a name="remarks"></a>备注

使用 `LoadOEMIcon` 或[LoadStandardIcon](#loadstandardicon)成员函数访问预定义的 Windows 图标。

##  <a name="cwinapploadstandardcursor"></a><a name="loadstandardcursor"></a>CWinApp：： LoadStandardCursor

加载*lpszCursorName*指定的 Windows 预定义光标资源。

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>parameters

*lpszCursorName*<br/>
一个**IDC_** 清单常量标识符，它指定预定义的 Windows 光标。 这些标识符在 WINDOWS 中定义。高. 以下列表显示了可能的预定义值和*lpszCursorName*的含义：

- IDC_ARROW 标准箭头光标

- IDC_IBEAM 标准文本插入光标

- 当 Windows 执行耗时的任务时使用 IDC_WAIT 沙漏光标

- IDC_CROSS 所选内容的十字线光标

- 向上 IDC_UPARROW 箭头

- IDC_SIZE 已过时且不受支持;使用 IDC_SIZEALL

- IDC_SIZEALL 四向箭头。 用于调整窗口大小的光标。

- IDC_ICON 过时且不受支持。 使用 IDC_ARROW。

- IDC_SIZENWSE 的双向箭头，并以左上角和右下角结束

- 向右和左下方 IDC_SIZENESW 双向箭头

- IDC_SIZEWE 水平双头箭头

- IDC_SIZENS 竖双头箭头

### <a name="return-value"></a>返回值

如果成功，则为游标的句柄;否则为 NULL。

### <a name="remarks"></a>备注

使用 `LoadStandardCursor` 或[LoadOEMCursor](#loadoemcursor)成员函数访问预定义的 Windows 游标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

##  <a name="cwinapploadstandardicon"></a><a name="loadstandardicon"></a>CWinApp：： LoadStandardIcon

加载*lpszIconName*指定的 Windows 预定义图标资源。

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>parameters

*lpszIconName*<br/>
一个清单常量标识符，它指定预定义的 Windows 图标。 这些标识符在 WINDOWS 中定义。高. 有关可能的预定义值及其说明的列表，请参阅 Windows SDK 的[LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)中的*lpIconName*参数。

### <a name="return-value"></a>返回值

如果成功，则为图标的句柄;否则为 NULL。

### <a name="remarks"></a>备注

使用 `LoadStandardIcon` 或[LoadOEMIcon](#loadoemicon)成员函数访问预定义的 Windows 图标。

##  <a name="cwinapploadstdprofilesettings"></a><a name="loadstdprofilesettings"></a>CWinApp：： LoadStdProfileSettings

从[InitInstance](#initinstance)成员函数中调用此成员函数，以启用和加载最近使用的（MRU）文件和上次预览状态的列表。

```
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>parameters

*nMaxMRU*<br/>
要跟踪的最近使用的文件数。

### <a name="remarks"></a>备注

如果*nMaxMRU*为0，则不保留 MRU 列表。

##  <a name="cwinappm_bhelpmode"></a><a name="m_bhelpmode"></a>CWinApp：： m_bHelpMode

如果应用程序处于帮助上下文模式（采用 SHIFT + F1 的逆调用），则为 TRUE;否则为 FALSE。

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>备注

在帮助上下文模式下，光标变成问号，用户可以在屏幕上移动它。 如果要在帮助模式下实现特殊处理，请检查此标志。 `m_bHelpMode` 是 BOOL 类型的公共变量。

##  <a name="cwinappm_dwrestartmanagersupportflags"></a><a name="m_dwrestartmanagersupportflags"></a>CWinApp：： m_dwRestartManagerSupportFlags

确定重新启动管理器的行为方式的标志。

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>备注

若要启用重新启动管理器，请将 `m_dwRestartManagerSupportFlags` 设置为所需的行为。 下表显示了可用的标志。

|||
|-|-|
|标志|说明|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|使用[CWinApp：： RegisterWithRestartManager](#registerwithrestartmanager)注册应用程序。 如果应用程序意外退出，则重新启动管理器负责重新启动该应用程序。|
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY|该应用程序在重新启动管理器中注册，重新启动管理器将在重新启动该应用程序时调用恢复回调函数。 默认恢复回调函数为[CWinApp：： ApplicationRecoveryCallback](#applicationrecoverycallback)。|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|启用自动保存后，在应用程序重新启动时，重新启动管理器将自动保存任何打开的文档。|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|启用自动保存，然后重新启动管理器定期自动保存任何打开的文档。 间隔由[CWinApp：： m_nAutosaveInterval](#m_nautosaveinterval)定义。|
|-AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|重新启动应用程序后，重新启动管理器将打开以前打开的文档。 [CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)处理打开的文档的列表并将其还原。|
|-AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|重新启动管理器后，重新启动管理器会提示用户还原自动保存的文件。 `CDataRecoveryHandler` 类查询用户。|
|-AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|AFX_RESTART_MANAGER_SUPPORT_RESTART、AFX_RESTART_MANAGER_SUPPORT_RECOVER 和 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 的并集。|
|-AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE、AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART、AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL 和 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES 的联合。|
|-AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_RESTART、AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART、AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 和 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES 的联合。|
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|联合 ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY、AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL、AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 和 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES。|

##  <a name="cwinappm_ehelptype"></a><a name="m_ehelptype"></a>CWinApp：： m_eHelpType

此数据成员的类型是在 `CWinApp` 类中定义 AFX_HELP_TYPE 的枚举类型。

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>备注

AFX_HELP_TYPE 枚举定义如下：

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- 若要将应用程序的帮助设置为 HTML 帮助，请调用[SetHelpMode](#sethelpmode)并指定 `afxHTMLHelp`。

- 若要将应用程序的帮助设置为 WinHelp，请调用 `SetHelpMode` 并指定 `afxWinHelp`。

##  <a name="cwinappm_hinstance"></a><a name="m_hinstance"></a>CWinApp：： m_hInstance

对应于 Windows 传递到 `WinMain`的*hInstance*参数。

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>备注

`m_hInstance` 数据成员是在 Windows 下运行的应用程序的当前实例的句柄。 这是由全局函数[AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)返回的。 `m_hInstance` 是 HINSTANCE 类型的公共变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

##  <a name="cwinappm_lpcmdline"></a><a name="m_lpcmdline"></a>CWinApp：： m_lpCmdLine

对应于 Windows 传递到 `WinMain`的*lpCmdLine*参数。

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>备注

指向以 null 结尾的字符串，它指定应用程序的命令行。 使用 `m_lpCmdLine` 可访问用户在启动应用程序时输入的任何命令行参数。 `m_lpCmdLine` 是 LPTSTR 类型的公共变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="cwinappm_nautosaveinterval"></a><a name="m_nautosaveinterval"></a>CWinApp：： m_nAutosaveInterval

自动保存之间的时间长度（以毫秒为单位）。

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>备注

可以将重新启动管理器配置为按设置的时间间隔自动保存打开的文档。 如果应用程序未自动保存文件，此参数不起作用。

##  <a name="cwinappm_ncmdshow"></a><a name="m_ncmdshow"></a>CWinApp：： m_nCmdShow

对应于 Windows 传递到 `WinMain`的*nCmdShow*参数。

```
int m_nCmdShow;
```

### <a name="remarks"></a>备注

为应用程序的主窗口调用[CWnd：： ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)时，应将 `m_nCmdShow` 作为参数传递。 `m_nCmdShow` 是**int**类型的公共变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

##  <a name="cwinappm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinApp：： m_pActiveWnd

使用此数据成员可以存储一个指针，该指针指向 ole 容器应用程序的主窗口，该窗口就地激活 OLE 服务器应用程序。

### <a name="remarks"></a>备注

如果此数据成员为 NULL，则该应用程序不是就地活动应用程序。

当框架窗口就地由 OLE 容器应用程序激活时，框架将设置此成员变量。

##  <a name="cwinappm_pdatarecoveryhandler"></a><a name="m_pdatarecoveryhandler"></a>CWinApp：： m_pDataRecoveryHandler

指向应用程序的数据恢复处理程序的指针。

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>备注

应用程序的数据恢复处理程序监视打开的文档并自动保存它们。 当应用程序意外退出后重新启动时，框架使用数据恢复处理程序还原自动保存的文件。 有关详细信息，请参阅[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)。

##  <a name="cwinappm_pszappname"></a><a name="m_pszappname"></a>CWinApp：： m_pszAppName

指定应用程序的名称。

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>备注

应用程序名称可以来自传递到[CWinApp](#cwinapp)构造函数的参数，如果未指定，则为 ID 为 AFX_IDS_APP_TITLE 的资源字符串。 如果在资源中找不到应用程序名称，则它来自程序的。EXE 文件名。

由全局函数[AfxGetAppName](application-information-and-management.md#afxgetappname)返回。 `m_pszAppName` 是**const char** <strong>\*</strong>类型的公共变量。

> [!NOTE]
> 如果将值分配到 `m_pszAppName`，则必须在堆上动态分配该值。 `CWinApp` 析构函数通过此指针调用**free**（）。 很多时候需要使用 `_tcsdup`（）运行时库函数来执行分配。 此外，在分配新值之前，释放与当前指针关联的内存。 例如：

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

##  <a name="cwinappm_pszexename"></a><a name="m_pszexename"></a>CWinApp：： m_pszExeName

包含应用程序的可执行文件的名称，但不包含扩展名。

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>备注

与[m_pszAppName](#m_pszappname)不同，此名称不能包含空格。 `m_pszExeName` 是**const char** <strong>\*</strong>类型的公共变量。

> [!NOTE]
> 如果将值分配到 `m_pszExeName`，则必须在堆上动态分配该值。 `CWinApp` 析构函数通过此指针调用**free**（）。 很多时候需要使用 `_tcsdup`（）运行时库函数来执行分配。 此外，在分配新值之前，释放与当前指针关联的内存。 例如：

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

##  <a name="cwinappm_pszhelpfilepath"></a><a name="m_pszhelpfilepath"></a>CWinApp：： m_pszHelpFilePath

包含应用程序的帮助文件的路径。

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>备注

默认情况下，框架使用 "" 将 `m_pszHelpFilePath` 初始化为应用程序的名称。尚未附加。 若要更改帮助文件的名称，请将 `m_pszHelpFilePath` 设置为指向包含所需帮助文件的完整名称的字符串。 用于执行此操作的一个方便的位置是在应用程序的[InitInstance](#initinstance)函数中。 `m_pszHelpFilePath` 是**const char** <strong>\*</strong>类型的公共变量。

> [!NOTE]
> 如果将值分配到 `m_pszHelpFilePath`，则必须在堆上动态分配该值。 `CWinApp` 析构函数通过此指针调用**free**（）。 很多时候需要使用 `_tcsdup`（）运行时库函数来执行分配。 此外，在分配新值之前，释放与当前指针关联的内存。 例如：

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

##  <a name="cwinappm_pszprofilename"></a><a name="m_pszprofilename"></a>CWinApp：： m_pszProfileName

包含应用程序的名称。INI 文件。

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>备注

`m_pszProfileName` 是**const char** <strong>\*</strong>类型的公共变量。

> [!NOTE]
> 如果将值分配到 `m_pszProfileName`，则必须在堆上动态分配该值。 `CWinApp` 析构函数通过此指针调用**free**（）。 很多时候需要使用 `_tcsdup`（）运行时库函数来执行分配。 此外，在分配新值之前，释放与当前指针关联的内存。 例如：

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

##  <a name="cwinappm_pszregistrykey"></a><a name="m_pszregistrykey"></a>CWinApp：： m_pszRegistryKey

用于确定在注册表或 INI 文件中存储应用程序配置文件设置的位置。

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>备注

通常，此数据成员被视为只读。

- 值存储在注册表项中。 应用程序配置文件设置的名称将追加到以下注册表项： HKEY_CURRENT_USER/Software/LocalAppWizard-Generated/。

如果将值分配到 `m_pszRegistryKey`，则必须在堆上动态分配该值。 `CWinApp` 析构函数通过此指针调用**free**（）。 很多时候需要使用 `_tcsdup`（）运行时库函数来执行分配。 此外，在分配新值之前，释放与当前指针关联的内存。 例如：

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

##  <a name="cwinappm_pszappid"></a><a name="m_pszappid"></a>CWinApp：： m_pszAppID

应用程序用户模型 ID。

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>备注

##  <a name="cwinapponcontexthelp"></a><a name="oncontexthelp"></a>CWinApp：： OnContextHelp

处理应用程序中的 SHIFT + F1 帮助。

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>备注

您必须将 `ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )` 语句添加到 `CWinApp` 类消息映射，同时添加一个快捷键对应表项（通常为 SHIFT + F1）来启用此成员函数。

`OnContextHelp` 将应用程序置于帮助模式。 光标更改为箭头和问号，然后用户可以移动鼠标指针并按鼠标左键以选择对话框、窗口、菜单或命令按钮。 此成员函数检索光标下的对象的帮助上下文，并通过该帮助上下文调用 Windows 函数 WinHelp。

##  <a name="cwinapponddecommand"></a><a name="onddecommand"></a>CWinApp：： OnDDECommand

在主框架窗口接收 DDE 执行消息时由框架调用。

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>parameters

*lpszCommand*<br/>
指向应用程序收到的 DDE 命令字符串。

### <a name="return-value"></a>返回值

如果处理该命令，则为非零值;否则为0。

### <a name="remarks"></a>备注

默认实现检查命令是否是打开文档的请求，如果是，则打开指定的文档。 当用户双击数据文件时，Windows 文件管理器通常会发送此类 DDE 命令字符串。 重写此函数可处理其他 DDE 执行命令，如要打印的命令。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

##  <a name="cwinapponfilenew"></a><a name="onfilenew"></a>CWinApp：： OnFileNew

实现 ID_FILE_NEW 命令。

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>备注

必须将 `ON_COMMAND( ID_FILE_NEW, OnFileNew )` 语句添加到 `CWinApp` 类消息映射，才能启用此成员函数。 如果启用，此函数将处理 File New 命令的执行。

有关默认行为的信息以及有关如何重写此成员函数的指导信息，请参阅[技术说明 22](../../mfc/tn022-standard-commands-implementation.md) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="cwinapponfileopen"></a><a name="onfileopen"></a>CWinApp：： OnFileOpen

实现 ID_FILE_OPEN 命令。

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>备注

必须将 `ON_COMMAND( ID_FILE_OPEN, OnFileOpen )` 语句添加到 `CWinApp` 类消息映射，才能启用此成员函数。 如果启用，此函数将处理文件打开命令的执行。

有关如何重写此成员函数的默认行为和指南的信息，请参阅[技术说明 22](../../mfc/tn022-standard-commands-implementation.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="cwinapponfileprintsetup"></a><a name="onfileprintsetup"></a>CWinApp：： OnFilePrintSetup

实现 ID_FILE_PRINT_SETUP 命令。

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>备注

必须将 `ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )` 语句添加到 `CWinApp` 类消息映射，才能启用此成员函数。 如果启用，此函数将处理文件打印命令的执行。

有关如何重写此成员函数的默认行为和指南的信息，请参阅[技术说明 22](../../mfc/tn022-standard-commands-implementation.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="cwinapponhelp"></a><a name="onhelp"></a>CWinApp：： OnHelp

处理应用程序中的 F1 帮助（使用当前上下文）。

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>备注

通常还会为 F1 键添加快捷键输入。 启用 F1 键只是一种约定，而不是要求。

必须将 `ON_COMMAND( ID_HELP, OnHelp )` 语句添加到 `CWinApp` 类消息映射，才能启用此成员函数。 如果启用，则在用户按 F1 键时由框架调用。

此消息处理函数的默认实现确定与当前窗口、对话框或菜单项对应的帮助上下文，然后调用 WINHELP.EXE. 如果当前没有可用的上下文，则函数将使用默认上下文。

重写此成员函数以将帮助上下文设置为当前具有焦点的窗口、对话框、菜单项或工具栏按钮以外的内容。 用所需的帮助上下文 ID 调用 `WinHelp`。

##  <a name="cwinapponhelpfinder"></a><a name="onhelpfinder"></a>CWinApp：： OnHelpFinder

处理 ID_HELP_FINDER 和 ID_DEFAULT_HELP 命令。

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>备注

必须将 `ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )` 语句添加到 `CWinApp` 类消息映射，才能启用此成员函数。 如果已启用，则当应用程序的用户选择 "帮助查找程序" 命令以调用标准**HELP_FINDER**主题 `WinHelp` 时，框架会调用此消息处理程序函数。

##  <a name="cwinapponhelpindex"></a><a name="onhelpindex"></a>CWinApp：： OnHelpIndex

处理 ID_HELP_INDEX 命令并提供默认帮助主题。

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>备注

必须将 `ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )` 语句添加到 `CWinApp` 类消息映射，才能启用此成员函数。 如果已启用，则当应用程序的用户选择 "帮助索引" 命令以调用标准**HELP_INDEX**主题 `WinHelp` 时，框架会调用此消息处理程序函数。

##  <a name="cwinapponhelpusing"></a><a name="onhelpusing"></a>CWinApp：： OnHelpUsing

处理 ID_HELP_USING 命令。

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>备注

必须将 `ON_COMMAND( ID_HELP_USING, OnHelpUsing )` 语句添加到 `CWinApp` 类消息映射，才能启用此成员函数。 当应用程序的用户使用命令调用具有标准**HELP_HELPONHELP**主题的 `WinHelp` 应用程序时，框架会调用此消息处理程序函数。

##  <a name="cwinapponidle"></a><a name="onidle"></a>CWinApp：： OnIdle

重写此成员函数以执行空闲时处理。

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>parameters

*lCount*<br/>
当应用程序的消息队列为空时，每次调用 `OnIdle` 时，计数器就会递增。 每次处理新消息时，此计数都将重置为0。 你可以使用*lCount*参数来确定应用程序处于空闲状态的时间，而不处理消息。

### <a name="return-value"></a>返回值

若要接收更多空闲处理时间，则为非零值;如果不再需要空闲时间，则为0。

### <a name="remarks"></a>备注

当应用程序的消息队列为空时，在默认消息循环中调用 `OnIdle`。 使用替代来调用自己的后台空闲处理程序任务。

`OnIdle` 应返回0以指示不需要空闲处理时间。 每当在消息队列为空时调用 `OnIdle` 时， *lCount*参数会递增，每次处理新消息时都会重置为0。 可以根据此计数调用不同的空闲例程。

下面汇总了空闲循环处理：

1. 如果 Microsoft 基础类库中的消息循环检查消息队列并找不到任何挂起消息，它将调用应用程序对象的 `OnIdle` 并提供0作为*lCount*参数。

2. `OnIdle` 执行一些处理并返回一个非零值，以指示应再次调用它以执行进一步处理。

3. 消息循环再次检查消息队列。 如果没有挂起的消息，它将再次调用 `OnIdle`，从而递增*lCount*参数。

4. 最后，`OnIdle` 处理完所有空闲任务并返回0。 这会告知消息循环停止调用 `OnIdle`，直到从消息队列接收到下一条消息为止，此时空闲周期会重新启动，并将参数设置为0。

在 `OnIdle` 期间，不会执行较长的任务，因为在 `OnIdle` 返回之前，应用程序无法处理用户输入。

> [!NOTE]
> `OnIdle` 的默认实现将更新命令用户界面对象（如菜单项和工具栏按钮），并执行内部数据结构清理。 因此，如果重写 `OnIdle`，则必须与重写的版本中的 `lCount` 调用 `CWinApp::OnIdle`。 首先调用所有基类空闲处理（即，在基类 `OnIdle` 返回0之前）。 如果需要在基本类处理完成之前执行工作，请查看基类实现，以选择要在其中执行工作的适当*lCount* 。

如果您不希望在从消息队列中检索消息时调用 `OnIdle`，则可以重写[CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage)。 如果应用程序设置了非常短的计时器，或者系统正在发送 WM_SYSTIMER 消息，则 `OnIdle` 将反复调用，从而降低性能。

### <a name="example"></a>示例

下面两个示例演示如何使用 `OnIdle`。 第一个示例使用*lCount*参数处理两个空闲任务，以确定任务的优先级。 第一个任务的优先级较高，应尽可能执行此任务。 第二个任务不太重要，只应在用户输入中存在长时间暂停时才执行。 请注意对 `OnIdle`的基类版本的调用。 第二个示例管理一组具有不同优先级的空闲任务。

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

##  <a name="cwinappopendocumentfile"></a><a name="opendocumentfile"></a>CWinApp：： OpenDocumentFile

框架调用此方法以打开应用程序的命名[CDocument](../../mfc/reference/cdocument-class.md)文件。

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>parameters

*lpszFileName*<br/>
中要打开的文件的名称。

*bAddToMRU*<br/>
中如果为 TRUE，则表示文档是最新的文件之一;FALSE 表示文档不是最新的文件之一。

### <a name="return-value"></a>返回值

如果成功，则为指向 `CDocument` 的指针;否则为 NULL。

### <a name="remarks"></a>备注

如果具有该名称的文档已打开，则包含该文档的第一个框架窗口将获得焦点。 如果应用程序支持多个文档模板，则框架将使用文件扩展名查找适当的文档模板以尝试加载文档。 如果成功，文档模板将为文档创建框架窗口和视图。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="cwinappparsecommandline"></a><a name="parsecommandline"></a>CWinApp：:P arseCommandLine

调用此成员函数以分析命令行，并一次将参数发送到[CCommandLineInfo：:P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)。

```
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>parameters

*rCmdInfo*<br/>
对[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)对象的引用。

### <a name="remarks"></a>备注

使用应用程序向导启动新的 MFC 项目时，应用程序向导将创建 `CCommandLineInfo`的本地实例，然后在[InitInstance](#initinstance)成员函数中调用 `ProcessShellCommand` 和 `ParseCommandLine`。 命令行遵循如下所述的路由：

1. 在 `InitInstance`中创建 `CCommandLineInfo` 对象后，会将该对象传递给 `ParseCommandLine`。

2. 然后 `ParseCommandLine` 为每个参数重复调用 `CCommandLineInfo::ParseParam`。

3. `ParseParam` 填充 `CCommandLineInfo` 对象，然后将该对象传递给[ProcessShellCommand](#processshellcommand)。

4. `ProcessShellCommand` 处理命令行参数和标志。

请注意，你可以根据需要直接调用 `ParseCommandLine`。

有关命令行标志的说明，请参阅[CCommandLineInfo：： m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)。

##  <a name="cwinapppretranslatemessage"></a><a name="pretranslatemessage"></a>CWinApp：:P reTranslateMessage

重写此函数以在将窗口消息调度到 Windows 函数[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)之前筛选窗口消息。默认实现将执行快捷键转换，因此必须在重写的版本中调用 `CWinApp::PreTranslateMessage` 成员函数。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>parameters

*pMsg*<br/>
指向包含要处理的消息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)结构的指针。

### <a name="return-value"></a>返回值

如果消息是在 `PreTranslateMessage` 中完全处理的，则为非零值。 如果应以正常方式处理消息，则为零。

##  <a name="cwinappprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinApp：:P rocessMessageFilter

框架的挂钩函数调用此成员函数来筛选和响应某些 Windows 消息。

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>parameters

*code*<br/>
指定挂钩代码。 此成员函数使用代码来确定如何处理*lpMsg。*

*lpMsg*<br/>
指向 Windows [MSG](/windows/win32/api/winuser/ns-winuser-msg)结构的指针。

### <a name="return-value"></a>返回值

如果处理消息，则为非零值;否则为0。

### <a name="remarks"></a>备注

挂钩函数在将事件发送到应用程序的正常消息处理之前处理这些事件。

如果重写此高级功能，请确保调用基类版本以维护框架的挂钩处理。

##  <a name="cwinappprocessshellcommand"></a><a name="processshellcommand"></a>CWinApp：:P rocessShellCommand

此成员函数由[InitInstance](#initinstance)调用，以接受从*rCmdInfo*标识的 `CCommandLineInfo` 对象传递的参数，并执行指定的操作。

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>parameters

*rCmdInfo*<br/>
对[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)对象的引用。

### <a name="return-value"></a>返回值

如果成功处理 shell 命令，则为非零值。 如果为0，则从[InitInstance](#initinstance)返回 FALSE。

### <a name="remarks"></a>备注

使用应用程序向导启动新的 MFC 项目时，应用程序向导将创建 `CCommandLineInfo`的本地实例，然后在 `InitInstance` 成员函数中调用 `ProcessShellCommand` 和[ParseCommandLine](#parsecommandline) 。 命令行遵循如下所述的路由：

1. 在 `InitInstance`中创建 `CCommandLineInfo` 对象后，会将该对象传递给 `ParseCommandLine`。

2. 然后 `ParseCommandLine` 为每个参数重复调用[CCommandLineInfo：:P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) 。

3. `ParseParam` 填充 `CCommandLineInfo` 对象，然后将该对象传递给 `ProcessShellCommand`。

4. `ProcessShellCommand` 处理命令行参数和标志。

`CCommandLineInfo` 对象（由[CCommandLineInfo：： m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)标识）的数据成员为以下枚举类型，该类型在 `CCommandLineInfo` 类中定义。

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

有关其中每个值的简要说明，请参阅 `CCommandLineInfo::m_nShellCommand`。

##  <a name="cwinappprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinApp：:P rocessWndProcException

每当处理程序未捕获某个应用程序的消息或命令处理程序中引发的异常时，框架都会调用此成员函数。

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>parameters

*e*<br/>
指向未捕获的异常的指针。

*pMsg*<br/>
一种[MSG](/windows/win32/api/winuser/ns-winuser-msg)结构，其中包含导致框架引发异常的 windows 消息的相关信息。

### <a name="return-value"></a>返回值

应返回给 Windows 的值。 通常，这是适用于 windows 消息的0L，是命令消息的1L （TRUE）。

### <a name="remarks"></a>备注

请勿直接调用此成员函数。

此成员函数的默认实现将创建一个消息框。 如果未捕获的异常是由菜单、工具栏或快捷键命令失败产生的，则消息框将显示 "命令失败" 消息;否则，它会显示 "内部应用程序错误" 消息。

重写此成员函数以提供异常的全局处理。 如果希望显示消息框，请仅调用基本功能。

##  <a name="cwinappregister"></a><a name="register"></a>CWinApp：： Register

执行 `RegisterShellFileTypes`未处理的任何注册任务。

```
virtual BOOL Register();
```

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="remarks"></a>备注

默认实现只返回 TRUE。 重写此函数以提供任何自定义注册步骤。

##  <a name="cwinappregistershellfiletypes"></a><a name="registershellfiletypes"></a>CWinApp：： RegisterShellFileTypes

调用此成员函数以通过 Windows 文件管理器注册应用程序的所有文档类型。

```
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>parameters

*bCompat*<br/>
中如果为 TRUE，则会向打印和打印 shell 命令的注册项，允许用户从 shell 直接打印文件，或通过将文件拖动到打印机对象。 它还会添加一个 DefaultIcon 键。 默认情况下，此参数为 FALSE，以便向后兼容。

### <a name="remarks"></a>备注

这样，用户就可以通过在文件管理器中双击应用程序来打开它创建的数据文件。 为应用程序中的每个文档模板调用[AddDocTemplate](#adddoctemplate)后，调用 `RegisterShellFileTypes`。 调用 `RegisterShellFileTypes`时，还应调用[EnableShellOpen](#enableshellopen)成员函数。

`RegisterShellFileTypes` 循环访问应用程序维护的[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象的列表，并且对于每个文档模板，会将条目添加到 Windows 为文件关联维护的注册数据库。 用户双击时，文件管理器使用这些项打开数据文件。 这样就无需寄送。应用程序的 REG 文件。

> [!NOTE]
> 仅当用户使用管理员权限运行该程序时，`RegisterShellFileTypes` 才起作用。 如果该程序没有管理员权限，则它不能更改注册表项。

如果注册数据库已将给定的文件扩展名与其他文件类型关联，则不会创建新的关联。 请参阅 `CDocTemplate` 类，了解注册此信息所需的字符串格式。

##  <a name="cwinappregisterwithrestartmanager"></a><a name="registerwithrestartmanager"></a>CWinApp：： RegisterWithRestartManager

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

### <a name="parameters"></a>parameters

|||
|-|-|
|参数|说明|
|*bRegisterRecoveryCallback*|中如果为 TRUE，则表示应用程序的此实例使用恢复回调函数;FALSE 指示它不存在。 当应用程序意外退出时，框架将调用恢复回调函数。 有关详细信息，请参阅[CWinApp：： ApplicationRecoveryCallback](#applicationrecoverycallback)。|
|*strRestartIdentifier*|中标识重新启动管理器实例的唯一字符串。 重新启动管理器标识符对于应用程序的每个实例都是唯一的。|
|*pwzCommandLineArgs*|中一个字符串，其中包含命令行中的任何额外参数。|
|*dwRestartFlags*|中重新启动管理器的可选标志。 有关详细信息，请参见“备注”部分。|
|*pRecoveryCallback*|中恢复回调函数。 此函数必须采用 LPVOID 参数作为输入并返回 DWORD。 默认恢复回调函数为 `CWinApp::ApplicationRecoveryCallback`。|
|*lpvParam*|中恢复回调函数的输入参数。 有关详细信息，请参阅[CWinApp：： ApplicationRecoveryCallback](#applicationrecoverycallback)。|
|*dwPingInterval*|中重新启动管理器等待恢复回调函数返回的时间长度。 此参数以毫秒为单位。|
|*dwCallbackFlags*|中传递给恢复回调函数的标志。 保留供将来使用。|

### <a name="return-value"></a>返回值

如果方法成功，则 S_OK;否则为错误代码。

### <a name="remarks"></a>备注

如果你的应用程序使用正在文件的默认 MFC 实现，则应使用 `RegisterWithRestartManager`的简单版本。 如果要自定义应用程序的自动保存行为，请使用 `RegisterWithRestartManager` 的复杂版本。

如果使用*strRestartIdentifier*的空字符串调用此方法，`RegisterWithRestartManager` 将为重新启动管理器的此实例创建唯一标识符字符串。

当应用程序意外退出时，重新启动管理器将从命令行重启应用程序，并提供唯一的重新启动标识符作为可选参数。 在此方案中，框架调用两次 `RegisterWithRestartManager`。 第一次调用来自[CWinApp：： InitInstance](#initinstance) ，字符串标识符的字符串为空。 然后，方法[CWinApp：:P rocessshellcommand](#processshellcommand)调用具有唯一重新启动标识符的 `RegisterWithRestartManager`。

使用重新启动管理器注册应用程序之后，重新启动管理器将监视该应用程序。 如果应用程序意外退出，则重新启动管理器会在关闭过程中调用恢复回调函数。 重新启动管理器将等待*dwPingInterval*响应恢复回调函数的响应。 如果恢复回调函数在这段时间内没有响应，则会退出应用程序，而不执行恢复回调函数。

默认情况下，不支持 dwRestartFlags，但可供将来使用。 *DwRestartFlags*的可能值如下：

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="cwinappreopenpreviousfilesatrestart"></a><a name="reopenpreviousfilesatrestart"></a>CWinApp：： ReopenPreviousFilesAtRestart

确定重新启动管理器是否重新打开应用程序意外退出时打开的文件。

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>返回值

TRUE 表示重新启动管理器重新打开以前打开的文件;FALSE 表示重新启动管理器未执行。

##  <a name="cwinapprestartinstance"></a><a name="restartinstance"></a>CWinApp：： RestartInstance

处理重新启动管理器启动的应用程序重启。

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>返回值

如果数据恢复处理程序打开以前打开的文档，则为 TRUE;如果数据恢复处理程序出现错误，或者没有以前打开的文档，则为 FALSE。

### <a name="remarks"></a>备注

当重新启动管理器重新启动应用程序时，框架会调用此方法。 此方法检索数据恢复处理程序并还原自动保存的文件。 此方法调用[CDataRecoveryHandler：： RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments)来确定用户是否要还原自动保存的文件。

如果[CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md)确定没有打开的文档，则此方法返回 FALSE。 如果没有打开的文档，应用程序将正常启动。

##  <a name="cwinapprestoreautosavedfilesatrestart"></a><a name="restoreautosavedfilesatrestart"></a>CWinApp：： RestoreAutosavedFilesAtRestart

确定重新启动管理器是否在重新启动应用程序时还原自动保存的文件。

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>返回值

TRUE 表示重新启动管理器还原自动保存的文件;FALSE 表示重新启动管理器未执行。

##  <a name="cwinapprun"></a><a name="run"></a>CWinApp：： Run

提供默认的消息循环。

```
virtual int Run();
```

### <a name="return-value"></a>返回值

`WinMain`返回的**整数**值。

### <a name="remarks"></a>备注

`Run` 获取并调度 Windows 消息，直到应用程序收到 WM_QUIT 消息。 如果应用程序的消息队列当前不包含任何消息，`Run` 将调用[OnIdle](#onidle)来执行空闲时处理。 传入消息将进入[PreTranslateMessage](#pretranslatemessage)成员函数以进行特殊处理，然后进入 Windows function `TranslateMessage` 用于标准键盘转换;最后，调用 `DispatchMessage` Windows 函数。

很少会重写 `Run`，但你可以重写它以提供特殊行为。

##  <a name="cwinapprunautomated"></a><a name="runautomated"></a>CWinApp：： RunAutomated

调用此函数可确定是否存在 " **/Automation**" 或 " **-Automation**" 选项，该选项指示服务器应用程序是否已由客户端应用程序启动。

```
BOOL RunAutomated();
```

### <a name="return-value"></a>返回值

如果找到该选项，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果存在，则从命令行中删除该选项。 有关 OLE 自动化的详细信息，请参阅[自动化服务器](../../mfc/automation-servers.md)一文。

##  <a name="cwinapprunembedded"></a><a name="runembedded"></a>CWinApp：： RunEmbedded

调用此函数可确定是否存在 " **/Embedding**" 或 " **-嵌入**" 选项，该选项指示服务器应用程序是否已由客户端应用程序启动。

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>返回值

如果找到该选项，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果存在，则从命令行中删除该选项。 有关嵌入的详细信息，请参阅文章[服务器：实现服务器](../../mfc/servers-implementing-a-server.md)。

##  <a name="cwinappsaveallmodified"></a><a name="saveallmodified"></a>CWinApp：： SaveAllModified

由框架调用，以便在应用程序的主框架窗口关闭或通过 WM_QUERYENDSESSION 消息时保存所有文档。

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>返回值

如果终止应用程序，则为非零值;如果终止应用程序不安全，则为0。

### <a name="remarks"></a>备注

此成员函数的默认实现为应用程序中的所有已修改的文档依次调用[CDocument：： SaveModified](../../mfc/reference/cdocument-class.md#savemodified)成员函数。

##  <a name="cwinappselectprinter"></a><a name="selectprinter"></a>CWinApp：： SelectPrinter

调用此成员函数以选择特定打印机，并释放之前在 "打印" 对话框中选择的打印机。

```
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>parameters

*hDevNames*<br/>
标识特定打印机的驱动程序、设备和输出端口名称的[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)结构的句柄。

*hDevMode*<br/>
[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)结构的句柄，它指定有关打印机的设备初始化和环境的信息。

*bFreeOld*<br/>
释放以前选择的打印机。

### <a name="remarks"></a>备注

如果*hDevMode*和*HDEVNAMES*都为 NULL，`SelectPrinter` 将使用当前的默认打印机。

##  <a name="cwinappsethelpmode"></a><a name="sethelpmode"></a>CWinApp：： SetHelpMode

设置应用程序的帮助类型。

```
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>parameters

*eHelpType*<br/>
指定要使用的帮助的类型。 有关详细信息，请参阅[CWinApp：： m_eHelpType](#m_ehelptype) 。

### <a name="remarks"></a>备注

设置应用程序的帮助类型。

若要将应用程序的帮助类型设置为 HTMLHelp，可以调用[EnableHTMLHelp](#enablehtmlhelp)。 调用 `EnableHTMLHelp`后，应用程序必须使用 HTMLHelp 作为其帮助应用程序。 如果要更改为使用 WinHelp，可以调用 `SetHelpMode`，并将*eHelpType*设置为 `afxWinHelp`。

##  <a name="cwinappsetregistrykey"></a><a name="setregistrykey"></a>CWinApp：： SetRegistryKey

导致应用程序设置存储在注册表中而不是 INI 文件中。

```
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>parameters

*lpszRegistryKey*<br/>
指向包含密钥名称的字符串的指针。

*nIDRegistryKey*<br/>
包含注册表项名称的字符串资源的 ID。

### <a name="remarks"></a>备注

此函数设置*m_pszRegistryKey*，然后由 `WriteProfileString` 的 `GetProfileInt`、`GetProfileString`、`WriteProfileInt`和 `CWinApp`成员函数使用。 如果调用了此函数，则最近使用的（MRU）文件列表也会存储在注册表中。 注册表项通常是公司的名称。 它存储在以下形式的密钥中： HKEY_CURRENT_USER \Software\\< 公司名称\>\\<\>\\<\>\\值名称 <\>部分名称

##  <a name="cwinappsupportsapplicationrecovery"></a><a name="supportsapplicationrecovery"></a>CWinApp：： SupportsApplicationRecovery

确定重新启动管理器是否恢复意外退出的应用程序。

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>返回值

如果为 TRUE，则表示重新启动管理器恢复应用程序;FALSE 表示重新启动管理器未执行。

##  <a name="cwinappsupportsautosaveatinterval"></a><a name="supportsautosaveatinterval"></a>CWinApp：： SupportsAutosaveAtInterval

确定重新启动管理器是否自动保存按固定间隔打开文档。

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>返回值

TRUE 表示重新启动管理器自动保存打开的文档;FALSE 表示重新启动管理器未执行。

##  <a name="cwinappsupportsautosaveatrestart"></a><a name="supportsautosaveatrestart"></a>CWinApp：： SupportsAutosaveAtRestart

确定在应用程序重新启动时重新启动管理器是否自动保存任何打开的文档。

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>返回值

TRUE 表示在应用程序重新启动时重新启动管理器自动保存打开文档;FALSE 表示重新启动管理器未执行。

##  <a name="cwinappsupportsrestartmanager"></a><a name="supportsrestartmanager"></a>CWinApp：： SupportsRestartManager

确定应用程序是否支持重新启动管理器。

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>返回值

如果为 TRUE，则表示应用程序支持重新启动管理器;FALSE 指示该应用程序不存在。

##  <a name="cwinappunregister"></a><a name="unregister"></a>CWinApp：：注销

注销应用程序对象注册的所有文件。

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="remarks"></a>备注

`Unregister` 函数将撤消应用程序对象和[Register](#register)函数执行的注册。 通常，这两个函数都是由 MFC 隐式调用的，因此不会显示在代码中。

重写此函数以执行自定义注销步骤。

##  <a name="cwinappunregistershellfiletypes"></a><a name="unregistershellfiletypes"></a>CWinApp：： UnregisterShellFileTypes

调用此成员函数可通过 Windows 文件管理器注销应用程序的所有文档类型。

```
void UnregisterShellFileTypes();
```

##  <a name="cwinappwinhelp"></a><a name="winhelp"></a>CWinApp：： WinHelp

调用此成员函数以调用 WinHelp 应用程序。

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>parameters

*dwData*<br/>
指定其他数据。 使用的值取决于*nCmd*参数的值。

*nCmd*<br/>
指定请求的帮助的类型。 有关可能值的列表以及这些值如何影响*dwData*参数，请参阅[WinHelp](/windows/win32/api/winuser/nf-winuser-winhelpw) Windows 函数。

### <a name="remarks"></a>备注

框架还调用此函数来调用 WinHelp 应用程序。

当应用程序终止时，框架将自动关闭 WinHelp 应用程序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

##  <a name="cwinappwriteprofilebinary"></a><a name="writeprofilebinary"></a>CWinApp：： WriteProfileBinary

调用此成员函数将二进制数据写入应用程序的注册表或的指定部分。INI 文件。

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>parameters

*lpszSection*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果该节不存在，则创建它。 部分的名称独立于大小写;字符串可以是大写字母和小写字母的任意组合。

*lpszEntry*<br/>
指向以 null 结尾的字符串，该字符串包含要将值写入到其中的项。 如果该条目不存在于指定的节中，则会创建它。

*pData*<br/>
指向要写入的数据。

*nBytes*<br/>
包含要写入的字节数。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

此示例使用 `CWinApp* pApp = AfxGetApp();` 来获取 CWinApp 类，其中说明了可从 MFC 应用程序中的任何函数使用 `WriteProfileBinary` 和 `GetProfileBinary` 的方式。

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

对于另一个示例，请参阅[CWinApp：： GetProfileBinary](#getprofilebinary)的示例。

##  <a name="cwinappwriteprofileint"></a><a name="writeprofileint"></a>CWinApp：： WriteProfileInt

调用此成员函数以将指定的值写入应用程序的注册表的指定部分或。INI 文件。

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>parameters

*lpszSection*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果该节不存在，则创建它。 部分的名称独立于大小写;字符串可以是大写字母和小写字母的任意组合。

*lpszEntry*<br/>
指向以 null 结尾的字符串，该字符串包含要将值写入到其中的项。 如果该条目不存在于指定的节中，则会创建它。

*N 值*<br/>
包含要写入的值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

此示例使用 `CWinApp* pApp = AfxGetApp();` 来获取 CWinApp 类，其中阐释了可从 MFC 应用程序中的任何函数使用 `WriteProfileString`、`WriteProfileInt`、`GetProfileString`和 `GetProfileInt` 的方式。

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

对于另一个示例，请参阅[CWinApp：： GetProfileInt](#getprofileint)的示例。

##  <a name="cwinappwriteprofilestring"></a><a name="writeprofilestring"></a>CWinApp：： WriteProfileString

调用此成员函数以将指定的字符串写入到应用程序的注册表的指定部分或。INI 文件。

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>parameters

*lpszSection*<br/>
指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果该节不存在，则创建它。 部分的名称独立于大小写;字符串可以是大写字母和小写字母的任意组合。

*lpszEntry*<br/>
指向以 null 结尾的字符串，该字符串包含要将值写入到其中的项。 如果该条目不存在于指定的节中，则会创建它。 如果此参数为 NULL，则将删除由*lpszSection*指定的节。

*lpszValue*<br/>
指向要写入的字符串。 如果此参数为 NULL，则删除由*lpszEntry*参数指定的条目。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

对于另一个示例，请参阅[CWinApp：： GetProfileInt](#getprofileint)的示例。

##  <a name="cwinappsetappid"></a><a name="setappid"></a>CWinApp：： SetAppID

显式设置应用程序的应用程序用户模型 ID。 应在向用户显示任何用户界面之前调用此方法（最佳位置是应用程序构造函数）。

```
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>parameters

*lpcszAppID*<br/>
指定应用程序用户模型 ID。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[CWinThread 类](../../mfc/reference/cwinthread-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[如何：添加重启管理器支持](../../mfc/how-to-add-restart-manager-support.md)
