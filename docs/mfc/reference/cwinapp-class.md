---
title: "CWinApp Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinApp"
  - "hInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "application objects [C++]"
  - "CWinApp class"
  - "HINSTANCE"
  - "main object"
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CWinApp Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从派生一个Windows应用程序对象的基类。  
  
## 语法  
  
```  
class CWinApp : public CWinThread  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CWinApp::CWinApp](../Topic/CWinApp::CWinApp.md)|构造 `CWinApp` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWinApp::AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md)|添加一个文档模板到应用程序的列表可用文档模板。|  
|[CWinApp::AddToRecentFileList](../Topic/CWinApp::AddToRecentFileList.md)|添加一个文件名到最近使用的\(MRU\)文件列表。|  
|[CWinApp::ApplicationRecoveryCallback](../Topic/CWinApp::ApplicationRecoveryCallback.md)|调用由结构，当应用程序意外退出。|  
|[CWinApp::CloseAllDocuments](../Topic/CWinApp::CloseAllDocuments.md)|关闭所有打开的文档。|  
|[CWinApp::CreatePrinterDC](../Topic/CWinApp::CreatePrinterDC.md)|创建一个打印机上下文。|  
|[CWinApp::DelRegTree](../Topic/CWinApp::DelRegTree.md)|删除指定的键及其所有子级。|  
|[CWinApp::DoMessageBox](../Topic/CWinApp::DoMessageBox.md)|应用程序的实现 [AfxMessageBox](../Topic/AfxMessageBox.md)。|  
|[CWinApp::DoWaitCursor](../Topic/CWinApp::DoWaitCursor.md)|打开和关闭等待光标。|  
|[CWinApp::EnableD2DSupport](../Topic/CWinApp::EnableD2DSupport.md)|启用应用程序 `D2D` 支持。  在初始化主窗口之前，调用此方法。|  
|[CWinApp::EnableHtmlHelp](../Topic/CWinApp::EnableHtmlHelp.md)|应用程序的实现、HTMLHelp，而不是WinHelp。|  
|[CWinApp::EnableTaskbarInteraction](../Topic/CWinApp::EnableTaskbarInteraction.md)|启用任务栏交互。|  
|[CWinApp::ExitInstance](../Topic/CWinApp::ExitInstance.md)|清理的重写，当应用程序停止。|  
|[CWinApp::GetApplicationRecoveryParameter](../Topic/CWinApp::GetApplicationRecoveryParameter.md)|检索应用程序还原方法的输入参数。|  
|[CWinApp::GetApplicationRecoveryPingInterval](../Topic/CWinApp::GetApplicationRecoveryPingInterval.md)|返回重新启动管理器等待还原回调函数返回的时间长度。|  
|[CWinApp::GetApplicationRestartFlags](../Topic/CWinApp::GetApplicationRestartFlags.md)|返回重新启动管理器的标志。|  
|[CWinApp::GetAppRegistryKey](../Topic/CWinApp::GetAppRegistryKey.md)|HKEY\_CURRENT\_USER \\ software \\ “”的RegistryKey \\ ProfileName return键。|  
|[CWinApp::GetDataRecoveryHandler](../Topic/CWinApp::GetDataRecoveryHandler.md)|获取应用程序的此实例的数据还原处理程序。|  
|[CWinApp::GetFirstDocTemplatePosition](../Topic/CWinApp::GetFirstDocTemplatePosition.md)|检索位置第一个文档模板。|  
|[CWinApp::GetHelpMode](../Topic/CWinApp::GetHelpMode.md)|检索应用程序使用的帮助的类型。|  
|[CWinApp::GetNextDocTemplate](../Topic/CWinApp::GetNextDocTemplate.md)|检索文档模板的位置。  可以使用递归。|  
|[CWinApp::GetPrinterDeviceDefaults](../Topic/CWinApp::GetPrinterDeviceDefaults.md)|检索默认打印机。|  
|[CWinApp::GetProfileBinary](../Topic/CWinApp::GetProfileBinary.md)|从应用程序的.INI文件的项检索二进制数据。|  
|[CWinApp::GetProfileInt](../Topic/CWinApp::GetProfileInt.md)|从应用程序的.INI文件的项检索整数。|  
|[CWinApp::GetProfileString](../Topic/CWinApp::GetProfileString.md)|从应用程序的.INI文件的项检索字符串。|  
|[CWinApp::GetSectionKey](../Topic/CWinApp::GetSectionKey.md)|HKEY\_CURRENT\_USER \\ software \\ “”的RegistryKey \\ AppName \\ lpszSection return键。|  
|[CWinApp::HideApplication](../Topic/CWinApp::HideApplication.md)|在结束所有文档之前，隐藏应用程序。|  
|[CWinApp::HtmlHelp](../Topic/CWinApp::HtmlHelp.md)|调用 `HTMLHelp` Windows功能。|  
|[CWinApp::InitInstance](../Topic/CWinApp::InitInstance.md)|执行Windows实例初始化的重写，例如创建windows对象。|  
|[CWinApp::IsTaskbarInteractionEnabled](../Topic/CWinApp::IsTaskbarInteractionEnabled.md)|指示Windows 7任务栏交互是否启用。|  
|[CWinApp::LoadCursor](../Topic/CWinApp::LoadCursor.md)|加载一种光标资源。|  
|[CWinApp::LoadIcon](../Topic/CWinApp::LoadIcon.md)|加载一个图标资源。|  
|[CWinApp::LoadOEMCursor](../Topic/CWinApp::LoadOEMCursor.md)|加载 **OCR\_** 常数。WINDOWS.H.指定了Windows OEM预定义的光标。|  
|[CWinApp::LoadOEMIcon](../Topic/CWinApp::LoadOEMIcon.md)|加载 **OIC\_** 常数。WINDOWS.H.中指定了Windows OEM预定义的图标。|  
|[CWinApp::LoadStandardCursor](../Topic/CWinApp::LoadStandardCursor.md)|加载 **IDC\_** 常数。WINDOWS.H.指定了Windows预定义的光标。|  
|[CWinApp::LoadStandardIcon](../Topic/CWinApp::LoadStandardIcon.md)|加载 **IDI\_** 常数。WINDOWS.H.中指定了Windows预定义的图标。|  
|[CWinApp::OnDDECommand](../Topic/CWinApp::OnDDECommand.md)|调用由框架以响应动态数据交换\(dde\) \(DDE\)执行命令。|  
|[CWinApp::OnIdle](../Topic/CWinApp::OnIdle.md)|执行特定于应用程序空闲时间处理的重写。|  
|[CWinApp::OpenDocumentFile](../Topic/CWinApp::OpenDocumentFile.md)|调用由框架打开文档从文件。|  
|[CWinApp::ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)|分析各个参数和标志。命令行。|  
|[CWinApp::PreTranslateMessage](../Topic/CWinApp::PreTranslateMessage.md)|筛选器消息，并在调度到Windows之前函数 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)。|  
|[CWinApp::ProcessMessageFilter](../Topic/CWinApp::ProcessMessageFilter.md)|截获某些消息，然后在到达应用程序。|  
|[CWinApp::ProcessShellCommand](../Topic/CWinApp::ProcessShellCommand.md)|处理命令行参数和标志。|  
|[CWinApp::ProcessWndProcException](../Topic/CWinApp::ProcessWndProcException.md)|截获应用程序的消息和命令处理程序引发的异常。|  
|[CWinApp::Register](../Topic/CWinApp::Register.md)|performs自定义注册。|  
|[CWinApp::RegisterWithRestartManager](../Topic/CWinApp::RegisterWithRestartManager.md)|注册重新启动管理器的应用程序。|  
|[CWinApp::ReopenPreviousFilesAtRestart](../Topic/CWinApp::ReopenPreviousFilesAtRestart.md)|确定重新启动管理器是否重新打开已打开的文件，并且应用程序意外退出。|  
|[CWinApp::RestartInstance](../Topic/CWinApp::RestartInstance.md)|处理重新启动管理器启动的应用程序重新启动。|  
|[CWinApp::RestoreAutosavedFilesAtRestart](../Topic/CWinApp::RestoreAutosavedFilesAtRestart.md)|确定重新启动管理器是否还原已自动存储的文件，并在重新启动应用程序。|  
|[CWinApp::Run](../Topic/CWinApp::Run.md)|运行默认消息循环。  自定义消息循环的重写。|  
|[CWinApp::RunAutomated](../Topic/CWinApp::RunAutomated.md)|测试 **\/Automation** 选项的应用程序的命令行。  已过时。  相反，请使用值在 [CCommandLineInfo::m\_bRunAutomated](../Topic/CCommandLineInfo::m_bRunAutomated.md) 在调用 [ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)之后。|  
|[CWinApp::RunEmbedded](../Topic/CWinApp::RunEmbedded.md)|测试 **\/Embedding** 选项的应用程序的命令行。  已过时。  相反，请使用值在 [CCommandLineInfo::m\_bRunEmbedded](../Topic/CCommandLineInfo::m_bRunEmbedded.md) 在调用 [ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)之后。|  
|[CWinApp::SaveAllModified](../Topic/CWinApp::SaveAllModified.md)|提示用户保存所有修改文档。|  
|[CWinApp::SelectPrinter](../Topic/CWinApp::SelectPrinter.md)|选择用户以前表示的一台打印机通过"打印"对话框。|  
|[CWinApp::SetHelpMode](../Topic/CWinApp::SetHelpMode.md)|设置并初始化应用程序使用的帮助的类型。|  
|[CWinApp::SupportsApplicationRecovery](../Topic/CWinApp::SupportsApplicationRecovery.md)|确定重新启动管理器是恢复意外退出的应用程序。|  
|[CWinApp::SupportsAutosaveAtInterval](../Topic/CWinApp::SupportsAutosaveAtInterval.md)|确定重新启动管理器是否自动存储打开文档定期。|  
|[CWinApp::SupportsAutosaveAtRestart](../Topic/CWinApp::SupportsAutosaveAtRestart.md)|确定重新启动管理器是否自动存储任何打开的文档应用程序何时重新启动。|  
|[CWinApp::SupportsRestartManager](../Topic/CWinApp::SupportsRestartManager.md)|确定应用程序是否支持重新启动管理器。|  
|[CWinApp::Unregister](../Topic/CWinApp::Unregister.md)|注销已知的内容由 `CWinApp` 对象注册。|  
|[CWinApp::WinHelp](../Topic/CWinApp::WinHelp.md)|调用 `WinHelp` Windows功能。|  
|[CWinApp::WriteProfileBinary](../Topic/CWinApp::WriteProfileBinary.md)|对项的写入二进制数据在应用程序的.INI文件。|  
|[CWinApp::WriteProfileInt](../Topic/CWinApp::WriteProfileInt.md)|编写每对项的整数在应用程序的.INI文件。|  
|[CWinApp::WriteProfileString](../Topic/CWinApp::WriteProfileString.md)|写入项的字符串在应用程序的.INI文件。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CWinApp::EnableShellOpen](../Topic/CWinApp::EnableShellOpen.md)|允许用户从打开Windows文件管理器的数据文件。|  
|[CWinApp::LoadStdProfileSettings](../Topic/CWinApp::LoadStdProfileSettings.md)|加载标准.INI文件设置并启用MRU文件列表功能。|  
|[CWinApp::OnContextHelp](../Topic/CWinApp::OnContextHelp.md)|在应用程序中处理SHIFT\+F1帮助。|  
|[CWinApp::OnFileNew](../Topic/CWinApp::OnFileNew.md)|实现 `ID_FILE_NEW` 命令。|  
|[CWinApp::OnFileOpen](../Topic/CWinApp::OnFileOpen.md)|实现 `ID_FILE_OPEN` 命令。|  
|[CWinApp::OnFilePrintSetup](../Topic/CWinApp::OnFilePrintSetup.md)|实现 `ID_FILE_PRINT_SETUP` 命令。|  
|[CWinApp::OnHelp](../Topic/CWinApp::OnHelp.md)|在应用程序中处理F1帮助\(使用当前上下文）。|  
|[CWinApp::OnHelpFinder](../Topic/CWinApp::OnHelpFinder.md)|处理 `ID_HELP_FINDER` 和 `ID_DEFAULT_HELP` 命令。|  
|[CWinApp::OnHelpIndex](../Topic/CWinApp::OnHelpIndex.md)|处理 `ID_HELP_INDEX` 命令并提供一个默认的帮助主题。|  
|[CWinApp::OnHelpUsing](../Topic/CWinApp::OnHelpUsing.md)|处理 `ID_HELP_USING` 命令。|  
|[CWinApp::RegisterShellFileTypes](../Topic/CWinApp::RegisterShellFileTypes.md)|注册所有应用程序的Windows文件管理器的文件类型。|  
|[CWinApp::SetAppID](../Topic/CWinApp::SetAppID.md)|显式设置应用程序用户应用程序的设计ID。  应调用此方法，将所有用户界面呈现给用户之前\(最好的位置是应用程序构造函数）。|  
|[CWinApp::SetRegistryKey](../Topic/CWinApp::SetRegistryKey.md)|在注册表中导致应用程序设置中而不是.INI文件。|  
|[CWinApp::UnregisterShellFileTypes](../Topic/CWinApp::UnregisterShellFileTypes.md)|取消任何应用程序中使用Windows文件管理器的文件类型。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CWinApp::m\_bHelpMode](../Topic/CWinApp::m_bHelpMode.md)|指示用户是否在帮助上下文模式下\(通常为调用具有SHIFT\+F1）。|  
|[CWinApp::m\_eHelpType](../Topic/CWinApp::m_eHelpType.md)|指定应用程序使用的帮助的类型。|  
|[CWinApp::m\_hInstance](../Topic/CWinApp::m_hInstance.md)|标识应用程序的当前实例。|  
|[CWinApp::m\_lpCmdLine](../Topic/CWinApp::m_lpCmdLine.md)|指向指定应用程序的命令行一个Null终止的字符串。|  
|[CWinApp::m\_nCmdShow](../Topic/CWinApp::m_nCmdShow.md)|指定窗口如何将最初显示。|  
|[CWinApp::m\_pActiveWnd](../Topic/CWinApp::m_pActiveWnd.md)|指向容器应用程序的主窗口，当OLE服务器处于就地活动状态。|  
|[CWinApp::m\_pszAppID](../Topic/CWinApp::m_pszAppID.md)|应用程序用户模型ID.|  
|[CWinApp::m\_pszAppName](../Topic/CWinApp::m_pszAppName.md)|指定应用程序的名称。|  
|[CWinApp::m\_pszExeName](../Topic/CWinApp::m_pszExeName.md)|应用程序的模块名称。|  
|[CWinApp::m\_pszHelpFilePath](../Topic/CWinApp::m_pszHelpFilePath.md)|应用程序的帮助文件的路径。|  
|[CWinApp::m\_pszProfileName](../Topic/CWinApp::m_pszProfileName.md)|应用程序的.INI文件名。|  
|[CWinApp::m\_pszRegistryKey](../Topic/CWinApp::m_pszRegistryKey.md)|用于确定存储应用程序配置文件设置完整的注册表项。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CWinApp::m\_dwRestartManagerSupportFlags](../Topic/CWinApp::m_dwRestartManagerSupportFlags.md)|确定的标志重新启动管理器的行为方式。|  
|[CWinApp::m\_nAutosaveInterval](../Topic/CWinApp::m_nAutosaveInterval.md)|时间长度之间的毫秒自动存储。|  
|[CWinApp::m\_pDataRecoveryHandler](../Topic/CWinApp::m_pDataRecoveryHandler.md)|将数据还原处理程序的指针应用程序的。|  
  
## 备注  
 应用程序对象提供成员函数用于初始化应用程序\(和每个实例它\)以及运行应用程序。  
  
 使用Microsoft基础选件类的每个应用程序只能包含从 `CWinApp`派生的对象。  此对象构造，当其他C\+\+全局对象构造时且已可用，当Windows调用 `WinMain` 函数时，Microsoft基础选件类库提供。  声明您的派生 `CWinApp` 对象在全局级。  
  
 当从 `CWinApp`派生时应用程序选件类，请重写 [InitInstance](../Topic/CWinApp::InitInstance.md) 成员函数创建应用程序的主窗口对象。  
  
 除了 `CWinApp` 成员函数外，Microsoft基础选件类库提供以下全局函数访问您的 `CWinApp` 对象和其他全局信息:  
  
-   [AfxGetApp](../Topic/AfxGetApp.md) 获取指向 `CWinApp` 对象。  
  
-   [AfxGetInstanceHandle](../Topic/AfxGetInstanceHandle.md) 获取的句柄为当前应用程序实例。  
  
-   [AfxGetResourceHandle](../Topic/AfxGetResourceHandle.md) 获取的句柄。应用程序的资源。  
  
-   [AfxGetAppName](../Topic/AfxGetAppName.md) 获取指向包含应用程序名称的字符串。  或者，因此，如果您有指向 `CWinApp` 对象，请使用 `m_pszExeName` 保护应用程序名称。  
  
 有关更多参见 [CWinApp:应用程序选件类](../../mfc/cwinapp-the-application-class.md) 在 `CWinApp` 选件类，包括概述的如下:  
  
-   `CWinApp`\-应用程序向导编写的派生的代码。  
  
-   在应用程序执行顺序的`CWinApp`的效果。  
  
-   `CWinApp`的默认成员函数的实现。  
  
-   `CWinApp`的键overridables。  
  
 **m\_hPrevInstance** 数据成员不存在。  有关检测 `CWinApp`上一个实例的信息，请参见知识库文章“如何标识应用程序的前一个” \(KB106385\) [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;106385](http://support.microsoft.com/default.aspx?scid=kb;en-us;106385)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 `CWinApp`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CWinThread Class](../../mfc/reference/cwinthread-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [如何：添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)