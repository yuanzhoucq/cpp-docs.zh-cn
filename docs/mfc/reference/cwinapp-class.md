---
title: "CWinApp 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinApp
- hInstance
dev_langs:
- C++
helpviewer_keywords:
- CWinApp class
- application objects [C++]
- HINSTANCE
- main object
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 292816c8f753a7b47b563a3fcd0fa336e08acd6a
ms.lasthandoff: 02/24/2017

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
|[CWinApp::AddDocTemplate](#adddoctemplate)|将文档模板添加到应用程序的模板列表中可用的文档。|  
|[CWinApp::AddToRecentFileList](#addtorecentfilelist)|将文件名添加到最近使用过的 (MRU) 文件列表。|  
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|应用程序意外退出时由框架调用。|  
|[CWinApp::CloseAllDocuments](#closealldocuments)|关闭所有打开的文档。|  
|[CWinApp::CreatePrinterDC](#createprinterdc)|创建打印机设备上下文。|  
|[CWinApp::DelRegTree](#delregtree)|使用指定的项及其所有子项中删除。|  
|[CWinApp::DoMessageBox](#domessagebox)|实现[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)为应用程序。|  
|[CWinApp::DoWaitCursor](#dowaitcursor)|打开和关闭将等待光标。|  
|[CWinApp::EnableD2DSupport](#enabled2dsupport)|使应用程序`D2D`支持。 在初始化主窗口之前调用此方法。|  
|[CWinApp::EnableHtmlHelp](#enablehtmlhelp)|实现 HTMLHelp 以保证应用程序中，而不是 WinHelp。|  
|[CWinApp::EnableTaskbarInteraction](#enabletaskbarinteraction)|使任务栏交互。|  
|[CWinApp::ExitInstance](#exitinstance)|重写应用程序终止时进行清理。|  
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|检索应用程序恢复方法的输入的参数。|  
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|返回有关恢复回调函数以返回等待重新启动管理器的时间长度。|  
|[CWinApp::GetApplicationRestartFlags](#getapplicationrestartflags)|重新启动管理器返回的标志。|  
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|返回 HKEY_CURRENT_USER 键\\"简称软件"\RegistryKey\ProfileName。|  
|[CWinApp::GetDataRecoveryHandler](#getdatarecoveryhandler)|获取此实例的应用程序的数据恢复处理程序。|  
|[CWinApp::GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|检索第一个文档模板的位置。|  
|[CWinApp::GetHelpMode](#gethelpmode)|检索应用程序所使用的帮助的类型。|  
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|检索的文档模板的位置。 可以使用的递归。|  
|[CWinApp::GetPrinterDeviceDefaults](#getprinterdevicedefaults)|检索打印机设备默认值。|  
|[CWinApp::GetProfileBinary](#getprofilebinary)|将项记入应用程序的从检索二进制数据。INI 文件中。|  
|[CWinApp::GetProfileInt](#getprofileint)|检索将项记入应用程序的一个整数。INI 文件中。|  
|[CWinApp::GetProfileString](#getprofilestring)|将项记入应用程序的从检索的字符串。INI 文件中。|  
|[CWinApp::GetSectionKey](#getsectionkey)|返回 HKEY_CURRENT_USER 键\\"简称软件"\RegistryKey\AppName\lpszSection。|  
|[CWinApp::HideApplication](#hideapplication)|隐藏应用程序之前关闭所有文档。|  
|[CWinApp::HtmlHelp](#htmlhelp)|调用`HTMLHelp`Windows 函数。|  
|[Cwinapp:: Initinstance](#initinstance)|重写以执行 Windows 实例初始化，如创建窗口对象。|  
|[CWinApp::IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|指示是否启用了 Windows 7 任务栏交互。|  
|[CWinApp::LoadCursor](#loadcursor)|加载的光标资源。|  
|[CWinApp::LoadIcon](#loadicon)|加载图标资源。|  
|[CWinApp::LoadOEMCursor](#loadoemcursor)|加载 Windows OEM 预定义的游标， **OCR_**常量指定将在 WINDOWS 中。H。|  
|[CWinApp::LoadOEMIcon](#loadoemicon)|加载 Windows OEM 预定义的图标， **OIC_**常量指定将在 WINDOWS 中。H。|  
|[CWinApp::LoadStandardCursor](#loadstandardcursor)|加载 Windows 预定义的游标， **IDC_**常量指定将在 WINDOWS 中。H。|  
|[CWinApp::LoadStandardIcon](#loadstandardicon)|加载 Windows 预定义的图标， **IDI_**常量指定将在 WINDOWS 中。H。|  
|[CWinApp::OnDDECommand](#onddecommand)|调用由框架以响应动态数据交换 (DDE) 执行命令。|  
|[CWinApp::OnIdle](#onidle)|重写以执行特定于应用程序空闲时间处理。|  
|[CWinApp::OpenDocumentFile](#opendocumentfile)|调用由框架以从文件打开的文档。|  
|[CWinApp::ParseCommandLine](#parsecommandline)|分析单个参数并在命令行中的标志。|  
|[CWinApp::PreTranslateMessage](#pretranslatemessage)|在它们调度到 Windows 函数之前筛选消息[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)。|  
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|截获某些消息到达应用程序之前。|  
|[CWinApp::ProcessShellCommand](#processshellcommand)|处理命令行参数和标志。|  
|[CWinApp::ProcessWndProcException](#processwndprocexception)|截获由应用程序的消息和命令处理程序引发的所有未处理的异常。|  
|[CWinApp::Register](#register)|执行自定义的注册。|  
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|在重新启动管理器中注册该应用程序。|  
|[CWinApp::ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|确定是否重新启动管理器重新打开该应用程序意外退出时打开的文件。|  
|[CWinApp::RestartInstance](#restartinstance)|处理重新启动应用程序启动的重新启动管理器。|  
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|确定在重新启动该应用程序时，重新启动管理器是否恢复自动保存文件。|  
|[Cwinapp:: Run](#run)|将运行默认消息循环。 重写以自定义的消息循环。|  
|[CWinApp::RunAutomated](#runautomated)|测试应用程序的命令行**注册服务器对象**选项。 已过时。 请改用中的值[CCommandLineInfo::m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated)之后调用[ParseCommandLine](#parsecommandline)。|  
|[CWinApp::RunEmbedded](#runembedded)|测试应用程序的命令行**/嵌入**选项。 已过时。 请改用中的值[CCommandLineInfo::m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded)之后调用[ParseCommandLine](#parsecommandline)。|  
|[CWinApp::SaveAllModified](#saveallmodified)|将提示用户保存所有修改后的文档。|  
|[CWinApp::SelectPrinter](#selectprinter)|选择以前由用户通过一个打印对话框指示打印机。|  
|[CWinApp::SetHelpMode](#sethelpmode)|设置和初始化的应用程序所使用的帮助类型。|  
|[CWinApp::SupportsApplicationRecovery](#supportsapplicationrecovery)|确定是否重新启动管理器恢复的应用程序意外退出。|  
|[CWinApp::SupportsAutosaveAtInterval](#supportsautosaveatinterval)|确定是否重新启动管理器自动保存打开定期时间间隔的文档。|  
|[CWinApp::SupportsAutosaveAtRestart](#supportsautosaveatrestart)|确定是否重新启动管理器自动保存所有打开的文档的应用程序重新启动时。|  
|[CWinApp::SupportsRestartManager](#supportsrestartmanager)|确定应用程序是否支持重新启动管理器。|  
|[CWinApp::Unregister](#unregister)|注销所有已知要注册的`CWinApp`对象。|  
|[CWinApp::WinHelp](#winhelp)|调用`WinHelp`Windows 函数。|  
|[CWinApp::WriteProfileBinary](#writeprofilebinary)|将写入将项记入应用程序的二进制数据。INI 文件中。|  
|[Cwinapp:: Writeprofileint](#writeprofileint)|将整数写入到将项记入应用程序的。INI 文件中。|  
|[CWinApp::WriteProfileString](#writeprofilestring)|将字符串写入该应用程序中的条目。INI 文件中。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWinApp::EnableShellOpen](#enableshellopen)|允许用户从 Windows 文件管理器中打开数据文件。|  
|[CWinApp::LoadStdProfileSettings](#loadstdprofilesettings)|加载标准。INI 文件设置并启用 MRU 文件列表功能。|  
|[CWinApp::OnContextHelp](#oncontexthelp)|处理应用程序中的 SHIFT + F1 帮助。|  
|[CWinApp::OnFileNew](#onfilenew)|实现`ID_FILE_NEW`命令。|  
|[CWinApp::OnFileOpen](#onfileopen)|实现`ID_FILE_OPEN`命令。|  
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|实现`ID_FILE_PRINT_SETUP`命令。|  
|[CWinApp::OnHelp](#onhelp)|处理应用程序中的 F1 帮助（使用当前上下文）。|  
|[CWinApp::OnHelpFinder](#onhelpfinder)|处理 `ID_HELP_FINDER` 和 `ID_DEFAULT_HELP` 命令。|  
|[CWinApp::OnHelpIndex](#onhelpindex)|处理 `ID_HELP_INDEX` 命令，并提供默认帮助主题。|  
|[CWinApp::OnHelpUsing](#onhelpusing)|处理 `ID_HELP_USING` 命令。|  
|[CWinApp::RegisterShellFileTypes](#registershellfiletypes)|使用 Windows 文件管理器中注册应用程序的所有文档类型。|  
|[CWinApp::SetAppID](#setappid)|显式设置为应用程序的应用程序用户模型 ID。 任何用户界面呈现给用户 （的最佳位置是应用程序构造函数） 之前，应调用此方法。|  
|[CWinApp::SetRegistryKey](#setregistrykey)|导致应用程序设置存储在注册表中而不是。INI 文件。|  
|[CWinApp::UnregisterShellFileTypes](#unregistershellfiletypes)|取消注册该应用程序的所有文档类型使用 Windows 文件管理器。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CWinApp::m_bHelpMode](#m_bhelpmode)|指示用户是否属于 （通常使用 SHIFT + F1 调用） 的帮助上下文模式。|  
|[CWinApp::m_eHelpType](#m_ehelptype)|指定帮助应用程序所使用的类型。|  
|[CWinApp::m_hInstance](#m_hinstance)|标识应用程序的当前实例。|  
|[CWinApp::m_lpCmdLine](#m_lpcmdline)|指向以 null 结尾的字符串，指定应用程序的命令行。|  
|[CWinApp::m_nCmdShow](#m_ncmdshow)|指定窗口中的初始显示方式。|  
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|向容器应用程序是 OLE 服务器处于就地活动状态时的主窗口的指针。|  
|[CWinApp::m_pszAppID](#m_pszappid)|应用程序用户模型 id。|  
|[CWinApp::m_pszAppName](#m_pszappname)|指定应用程序的名称。|  
|[CWinApp::m_pszExeName](#m_pszexename)|应用程序的模块名称。|  
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|应用程序的帮助文件的路径。|  
|[CWinApp::m_pszProfileName](#m_pszprofilename)|应用程序的。INI 文件名。|  
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|用来确定用于存储应用程序配置文件设置的完整的注册表项。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|确定如何重新启动管理器中的行为的标志。|  
|[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)|以毫秒为单位之间自动保存的时间长度。|  
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|指针，指向该应用程序的数据恢复处理程序。|  
  
## <a name="remarks"></a>备注  
 应用程序对象提供成员函数，用于初始化您的应用程序 （和它的每个实例） 以及用于运行该应用程序。  
  
 每个应用程序使用 Microsoft 基础类只能包含一个对象，派生自`CWinApp`。 此对象时构造其他 c + + 的全局对象构造和 Windows 调用时已有`WinMain`函数，它由 Microsoft 基础类库提供。 声明派生`CWinApp`全局级别的对象。  
  
 从应用程序类的派生时`CWinApp`，重写[InitInstance](#initinstance)成员函数来创建应用程序的主窗口对象。  
  
 除了`CWinApp`成员函数，Microsoft 基础类库提供了以下全局函数，以访问您`CWinApp`对象和其他全球信息︰  
  
- [AfxGetApp](application-information-and-management.md#afxgetapp)获取指向的指针`CWinApp`对象。  
  
- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)获取当前应用程序实例的句柄。  
  
- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle)获取应用程序的资源的句柄。  
  
- [AfxGetAppName](application-information-and-management.md#afxgetappname)获取指向包含应用程序的名称的字符串的指针。 或者，如果您有一个指针指向`CWinApp`对象，请使用`m_pszExeName`若要获取应用程序的名称。  
  
 请参阅[CWinApp︰ 应用程序类](../../mfc/cwinapp-the-application-class.md)有关的详细信息`CWinApp`类，包括以下概述︰  
  
- `CWinApp`-派生应用程序向导编写的代码。  
  
- `CWinApp`应用程序的执行序列中的角色。  
  
- `CWinApp`默认成员函数实现。  
  
- `CWinApp`密钥可重写。  
  
 **M_hPrevInstance**数据成员也就不再存在。 有关检测以前的实例的信息`CWinApp`，请参阅知识库文章"如何确定上一实例的应用程序"(KB106385) 网址[http://support.microsoft.com/default.aspxscid=kb;en-us;106385](http://support.microsoft.com/default.aspxscid=kb;en-us;106385)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 `CWinApp`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="a-nameadddoctemplatea--cwinappadddoctemplate"></a><a name="adddoctemplate"></a>CWinApp::AddDocTemplate  
 调用该成员函数以将文档模板添加到应用程序进行维护的可用文档模板列表中。  
  
```  
void AddDocTemplate(CDocTemplate* pTemplate);
```  
  
### <a name="parameters"></a>参数  
 `pTemplate`  
 一个指向`CDocTemplate`要添加。  
  
### <a name="remarks"></a>备注  
 您应将添加所有文档的应用程序模板，然后才能调用[RegisterShellFileTypes](#registershellfiletypes)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&35;](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]  
  
##  <a name="a-nameaddtorecentfilelista--cwinappaddtorecentfilelist"></a><a name="addtorecentfilelist"></a>CWinApp::AddToRecentFileList  
 调用此成员函数来添加`lpszPathName`到 MRU 文件列表。  
  
```  
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 文件的路径。  
  
### <a name="remarks"></a>备注  
 应调用[LoadStdProfileSettings](#loadstdprofilesettings)成员函数以加载当前的 MRU 文件列表，然后使用此成员函数。  
  
 在打开的文件或执行另存为命令，以使用新名称保存文件时，框架将调用此成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&36;](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]  
  
##  <a name="a-nameapplicationrecoverycallbacka--cwinappapplicationrecoverycallback"></a><a name="applicationrecoverycallback"></a>CWinApp::ApplicationRecoveryCallback  
 应用程序意外退出时由框架调用。  
  
```  
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpvParam`  
 留待将来使用。  
  
### <a name="return-value"></a>返回值  
 如果此方法是成功，则为&0;如果发生错误，非零值。  
  
### <a name="remarks"></a>备注  
 如果您的应用程序支持重新启动管理器，框架将调用此函数时您的应用程序意外退出。  
  
 默认实现`ApplicationRecoveryCallback`使用`CDataRecoveryHandler`若要将当前打开的文档列表保存到注册表。 此方法不自动保存的任何文件。  
  
 若要自定义的行为，重写此函数在派生[CWinApp 类](../../mfc/reference/cwinapp-class.md)或将您自己的应用程序恢复方法作为参数传递[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)。  
  
##  <a name="a-nameclosealldocumentsa--cwinappclosealldocuments"></a><a name="closealldocuments"></a>CWinApp::CloseAllDocuments  
 调用该成员函数以在退出之前关闭所有打开的文档。  
  
```  
void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>参数  
 `bEndSession`  
 指定在 Windows 会话正在结束。 它是**TRUE**如果会话正在结束; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 调用[HideApplication](#hideapplication)之前调用`CloseAllDocuments`。  
  
##  <a name="a-namecreateprinterdca--cwinappcreateprinterdc"></a><a name="createprinterdc"></a>CWinApp::CreatePrinterDC  
 调用该成员函数以创建从所选打印机的打印机设备上下文 (DC)。  
  
```  
BOOL CreatePrinterDC(CDC& dc);
```  
  
### <a name="parameters"></a>参数  
 `dc`  
 对打印机设备上下文的引用。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则创建打印机设备上下文否则为 0。  
  
### <a name="remarks"></a>备注  
 `CreatePrinterDC`初始化您在通过引用传递，因此可以使用它来打印的设备上下文。  
  
 如果该函数成功，当您在完成打印时，您必须销毁的设备上下文。 您可以让的析构函数[CDC](../../mfc/reference/cdc-class.md)对象执行操作，也可以执行它显式通过调用[CDC::DeleteDC](../../mfc/reference/cdc-class.md#deletedc)。  
  
##  <a name="a-namecwinappa--cwinappcwinapp"></a><a name="cwinapp"></a>CWinApp::CWinApp  
 构造`CWinApp`对象并将传递`lpszAppName`存储为应用程序的名称。  
  
```  
CWinApp(LPCTSTR lpszAppName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszAppName`  
 以 null 结尾的字符串，其中包含 Windows 所使用的应用程序名称。 如果此参数未提供或为**NULL**，`CWinApp`使用资源字符串**AFX_IDS_APP_TITLE**或可执行文件的文件名。  
  
### <a name="remarks"></a>备注  
 您应将构造一个全局对象的您`CWinApp`的派生类。 只能有一个`CWinApp`应用程序中的对象。 构造函数存储的指针`CWinApp`对象以便`WinMain`可调用对象的成员函数来初始化和运行该应用程序。  
  
##  <a name="a-namedelregtreea--cwinappdelregtree"></a><a name="delregtree"></a>CWinApp::DelRegTree  
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
 如果函数成功，返回值将为 ERROR_SUCCESS。 如果函数失败，则返回值是在 Winerror.h 中定义的非零错误代码。  
  
### <a name="remarks"></a>备注  
 调用此函数可删除指定的项及其子项。  
  
##  <a name="a-namedomessageboxa--cwinappdomessagebox"></a><a name="domessagebox"></a>CWinApp::DoMessageBox  
 框架将调用该成员函数以实现全局函数一个消息框[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)。  
  
```  
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,  
    UINT nType,  
    UINT nIDPrompt);
```  
  
### <a name="parameters"></a>参数  
 *lpszPrompt*  
 消息框中的文本的地址。  
  
 `nType`  
 消息框[样式](../../mfc/reference/message-box-styles.md)。  
  
 `nIDPrompt`  
 帮助上下文字符串的索引。  
  
### <a name="return-value"></a>返回值  
 返回相同的值`AfxMessageBox`。  
  
### <a name="remarks"></a>备注  
 不调用该成员函数以打开一个消息框;使用`AfxMessageBox`相反。  
  
 重写该成员函数以自定义您的应用程序级处理`AfxMessageBox`调用。  
  
##  <a name="a-namedowaitcursora--cwinappdowaitcursor"></a><a name="dowaitcursor"></a>CWinApp::DoWaitCursor  
 此成员函数由框架调用以实现[CWaitCursor](../../mfc/reference/cwaitcursor-class.md)， [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)， [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)，和[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。  
  
```  
virtual void DoWaitCursor(int nCode);
```  
  
### <a name="parameters"></a>参数  
 `nCode`  
 如果此参数为 1，将显示等待光标。 如果为 0，将等待光标被还原时不用递增引用计数。 如果为 –&1;，而结束等待光标。  
  
### <a name="remarks"></a>备注  
 默认实现为沙漏光标。 `DoWaitCursor`保留引用计数。 当正数时，则会显示沙漏光标。  
  
 虽然您不会正常情况下调用`DoWaitCursor`直接，您可以重写该成员函数来更改将等待光标或执行其他处理，而会显示等待光标。  
  
 有关的更简单、 更简单方法来实现等待光标，使用`CWaitCursor`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&37;](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]  
  
##  <a name="a-nameenabled2dsupporta--cwinappenabled2dsupport"></a><a name="enabled2dsupport"></a>CWinApp::EnableD2DSupport  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 启用应用程序 D2D 支持。 在初始化主窗口之前调用此方法。  
  
```  
BOOL EnableD2DSupport(
D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>参数  
 `d2dFactoryType`  
 它创建 D2D 工厂和资源的线程模型。  
  
 `writeFactoryType`  
 一个值，指定是否将共享或隔离写工厂对象  
  
### <a name="return-value"></a>返回值  
 D2D 支持是否已启用，FALSE-否则将返回 TRUE  
  
##  <a name="a-nameenablehtmlhelpa--cwinappenablehtmlhelp"></a><a name="enablehtmlhelp"></a>CWinApp::EnableHtmlHelp  
 此从调用成员函数的构造函数内您`CWinApp`的派生类 HTMLHelp 用于应用程序的帮助。  
  
```  
void EnableHtmlHelp();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameenableshellopena--cwinappenableshellopen"></a><a name="enableshellopen"></a>CWinApp::EnableShellOpen  
 通常从调用此函数中，您`InitInstance`重写时，若要使应用程序的用户可以打开数据文件，当它们双击内 Windows 文件管理器中的文件。  
  
```  
void EnableShellOpen();
```  
  
### <a name="remarks"></a>备注  
 调用`RegisterShellFileTypes`成员函数结合使用此函数，或提供。REG 文件，您的应用程序的文档类型的手动注册。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&38;](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]  
  
##  <a name="a-nameenabletaskbarinteractiona--cwinappenabletaskbarinteraction"></a><a name="enabletaskbarinteraction"></a>CWinApp::EnableTaskbarInteraction  
 使任务栏交互。  
  
```  
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 指定是否应启用与 Windows 7 任务栏交互 ( `TRUE`)，还是禁用 ( `FALSE`)。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果任务栏交互可以启用或禁用。  
  
### <a name="remarks"></a>备注  
 必须在主窗口的创建之前调用此方法，否则为它断言并返回`FALSE`。  
  
##  <a name="a-nameexitinstancea--cwinappexitinstance"></a><a name="exitinstance"></a>CWinApp::ExitInstance  
 在由框架调用**运行**成员函数以退出应用程序的此实例。  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>返回值  
 应用程序的退出代码;0 表示没有错误，而值大于 0 表示出现错误。 此值用作从返回的值`WinMain`。  
  
### <a name="remarks"></a>备注  
 不调用该成员函数从任意位置之内**运行**成员函数。  
  
 此函数的默认实现将写入应用程序的框架选项。INI 文件中。 重写此函数可在您的应用程序终止时清除。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&39;](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]  
  
##  <a name="a-namegetapplicationrecoveryparametera--cwinappgetapplicationrecoveryparameter"></a><a name="getapplicationrecoveryparameter"></a>CWinApp::GetApplicationRecoveryParameter  
 检索应用程序恢复方法的输入的参数。  
  
```  
virtual LPVOID GetApplicationRecoveryParameter();
```  
  
### <a name="return-value"></a>返回值  
 应用程序恢复方法的默认输入的参数。  
  
### <a name="remarks"></a>备注  
 此函数的默认行为返回`NULL`。  
  
 有关详细信息，请参阅[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。  
  
##  <a name="a-namegetapplicationrecoverypingintervala--cwinappgetapplicationrecoverypinginterval"></a><a name="getapplicationrecoverypinginterval"></a>CWinApp::GetApplicationRecoveryPingInterval  
 返回有关恢复回调函数以返回等待重新启动管理器的时间长度。  
  
```  
virtual DWORD GetApplicationRecoveryPingInterval();
```  
  
### <a name="return-value"></a>返回值  
 以毫秒为单位的时间长度。  
  
### <a name="remarks"></a>备注  
 当应用程序注册的重新启动管理器退出意外时，应用程序尝试保存打开的文档，并调用恢复的回调函数。 默认恢复回调函数是[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。  
  
 有关恢复回调函数以返回框架等待的时间长度为 ping 时间间隔。 您可以通过重写来自定义 ping 时间间隔`CWinApp::GetApplicationRecoveryPingInterval`或通过提供自定义值到`RegisterWithRestartManager`。  
  
##  <a name="a-namegetapplicationrestartflagsa--cwinappgetapplicationrestartflags"></a><a name="getapplicationrestartflags"></a>CWinApp::GetApplicationRestartFlags  
 重新启动管理器返回的标志。  
  
```  
virtual DWORD GetApplicationRestartFlags();
```  
  
### <a name="return-value"></a>返回值  
 重新启动管理器的标志。 默认实现将返回 0。  
  
### <a name="remarks"></a>备注  
 重新启动管理器的标志不起作用的默认实现使用。 它们可供将来使用。  
  
 在重新启动管理器中使用注册该应用程序时设置的标志[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)。  
  
 重新启动管理器标志的可能值如下所示︰  
  
- `RESTART_NO_CRASH`  
  
- `RESTART_NO_HANG`  
  
- `RESTART_NO_PATCH`  
  
- `RESTART_NO_REBOOT`  
  
##  <a name="a-namegetappregistrykeya--cwinappgetappregistrykey"></a><a name="getappregistrykey"></a>CWinApp::GetAppRegistryKey  
 返回的键为 HKEY_CURRENT_USER\\"简称软件"\RegistryKey\ProfileName。  
  
```  
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pTM`  
 指向 `CAtlTransactionManager` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则应用程序密钥否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetdatarecoveryhandlera--cwinappgetdatarecoveryhandler"></a><a name="getdatarecoveryhandler"></a>CWinApp::GetDataRecoveryHandler  
 获取此实例的应用程序的数据恢复处理程序。  
  
```  
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```  
  
### <a name="return-value"></a>返回值  
 应用程序的此实例的数据恢复处理程序。  
  
### <a name="remarks"></a>备注  
 使用重新启动管理器每个应用程序必须具有的一个实例[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)。 此类负责监视打开的文档和自动保存文件。 行为`CDataRecoveryHandler`取决于重新启动管理器配置。 有关详细信息，请参阅[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)。  
  
 此方法返回`NULL`上的操作系统早于[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 重新启动管理器不支持的操作系统早于[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 如果应用程序当前不具有数据恢复处理程序，此方法创建一个存储帐户，并将指针返回到它。  
  
##  <a name="a-namegetfirstdoctemplatepositiona--cwinappgetfirstdoctemplateposition"></a><a name="getfirstdoctemplateposition"></a>CWinApp::GetFirstDocTemplatePosition  
 获取应用程序中的第一个文档模板的位置。  
  
```  
POSITION GetFirstDocTemplatePosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**位置**可以用于迭代或检索对象指针; 值**NULL**如果列表为空。  
  
### <a name="remarks"></a>备注  
 使用**位置**对的调用中返回值[GetNextDocTemplate](#getnextdoctemplate)来获取第一个[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象。  
  
##  <a name="a-namegethelpmodea--cwinappgethelpmode"></a><a name="gethelpmode"></a>CWinApp::GetHelpMode  
 检索应用程序所使用的帮助的类型。  
  
```  
AFX_HELP_TYPE GetHelpMode();
```  
  
### <a name="return-value"></a>返回值  
 使用应用程序的帮助类型。 请参阅[CWinApp::m_eHelpType](#m_ehelptype)有关详细信息。  
  
##  <a name="a-namegetnextdoctemplatea--cwinappgetnextdoctemplate"></a><a name="getnextdoctemplate"></a>CWinApp::GetNextDocTemplate  
 获取文档模板由标识`pos`，然后设置`pos`到**位置**值。  
  
```  
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 对引用**位置**的以前调用返回值`GetNextDocTemplate`或[GetFirstDocTemplatePosition](#getfirstdoctemplateposition)。 通过此调用至下一个位置更新的值。  
  
### <a name="return-value"></a>返回值  
 一个指向[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象。  
  
### <a name="remarks"></a>备注  
 您可以使用`GetNextDocTemplate`在向前迭代循环中，如果您建立的初始位置，通过调用`GetFirstDocTemplatePosition`。  
  
 您必须确保您**位置**值是否有效。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 如果检索到的文档模板是最后一个可用的新值然后`pos`设置为**NULL**。  
  
##  <a name="a-namegetprinterdevicedefaultsa--cwinappgetprinterdevicedefaults"></a><a name="getprinterdevicedefaults"></a>CWinApp::GetPrinterDeviceDefaults  
 调用该成员函数以准备用于打印的打印机设备上下文。  
  
```  
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```  
  
### <a name="parameters"></a>参数  
 *pPrintDlg*  
 一个指向[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 从 Windows 中检索当前打印机默认值。INI 文件根据需要，或使用由用户在打印设置中设置的最后一个打印机配置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&40;](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]  
  
##  <a name="a-namegetprofilebinarya--cwinappgetprofilebinary"></a><a name="getprofilebinary"></a>CWinApp::GetProfileBinary  
 调用此成员函数以检索应用程序的注册表的指定部分中条目的二进制数据或。INI 文件中。  
  
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
 指向将接收数据的地址的指针。  
  
 *pBytes*  
 指向将接收的大小 （以字节为单位） 的数据是 UINT。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数不区分大小写，因此中的字符串*lpszSection*和*lpszEntry*参数可能不同。  
  
> [!NOTE]
> **GetProfileBinary**分配一个缓冲区，并返回其地址在\* *ppData*。 调用方负责释放缓冲区使用**delete []**。  
  
> [!IMPORTANT]
>  此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&41;](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]  
  
 有关其他示例，请参阅[CWinApp::WriteProfileBinary](#writeprofilebinary)。  
  
##  <a name="a-namegetprofileinta--cwinappgetprofileint"></a><a name="getprofileint"></a>CWinApp::GetProfileInt  
 调用此成员函数以检索应用程序的注册表或 .INI 文件的指定部分中条目的整数的值。  
  
```  
UINT GetProfileInt(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    int nDefault);
```  
  
### <a name="parameters"></a>参数  
 `lpszSection`  
 指向以 null 结尾的字符串，该字符串指定包含条目的部分。  
  
 `lpszEntry`  
 指向以 null 结尾的字符串，该字符串包含要检索其值的条目。  
  
 `nDefault`  
 指定在框架找不到条目时要返回的默认值。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则为指定条目后面的字符串的整数值。 如果函数未找到条目，则返回值为 `nDefault` 参数的值。 如果与指定条目对应的值不为整数，则返回值为 0。  
  
 在 .INI 文件中，此成员函数支持值的十六进制表示法。 当您检索有符号整数时，应将此值强制转换为 `int`。  
  
### <a name="remarks"></a>备注  
 此成员函数不区分大小写，因此 `lpszSection` 和 `lpszEntry` 参数中的字符串的大小写可能不同。  
  
> [!IMPORTANT]
>  此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&42;](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]  
  
 有关其他示例，请参阅[cwinapp:: Writeprofileint](#writeprofileint)。  
  
##  <a name="a-namegetprofilestringa--cwinappgetprofilestring"></a><a name="getprofilestring"></a>CWinApp::GetProfileString  
 调用此成员函数以检索与应用程序的注册表中指定的部分中的项关联的字符串或。INI 文件中。  
  
```  
CString GetProfileString(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszDefault = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszSection`  
 指向以 null 结尾的字符串，该字符串指定包含条目的部分。  
  
 `lpszEntry`  
 指向以 null 结尾的字符串，其中包含要检索其字符串的条目。 此值不能**NULL**。  
  
 `lpszDefault`  
 指向以给定的项目如果在初始化文件中找不到该条目的默认字符串值。  
  
### <a name="return-value"></a>返回值  
 返回值是由应用程序的字符串。INI 文件或`lpszDefault`如果无法找到该字符串。 框架支持的最大字符串长度是`_MAX_PATH`。 如果`lpszDefault`是**NULL**，则返回值为空字符串。  
  
### <a name="remarks"></a>备注  
  
> [!IMPORTANT]
>  此函数返回的数据不一定是以 NULL 结尾的，并且调用方必须执行验证。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&43;](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 另一个示例，请参阅示例[CWinApp::GetProfileInt](#getprofileint)。  
  
##  <a name="a-namegetsectionkeya--cwinappgetsectionkey"></a><a name="getsectionkey"></a>CWinApp::GetSectionKey  
 返回的键为 HKEY_CURRENT_USER\\"简称软件"\RegistryKey\AppName\lpszSection。  
  
```  
HKEY GetSectionKey(
LPCTSTR lpszSection,  
CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszSection`  
 要获取的键的名称。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则部分密钥否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namehideapplicationa--cwinapphideapplication"></a><a name="hideapplication"></a>CWinApp::HideApplication  
 调用该成员函数以隐藏应用程序之前关闭所有打开的文档。  
  
```  
void HideApplication();
```  
  
##  <a name="a-namehtmlhelpa--cwinapphtmlhelp"></a><a name="htmlhelp"></a>CWinApp::HtmlHelp  
 调用此成员函数来调用 HTMLHelp 应用程序。  
  
```  
virtual void HtmlHelp(
    DWORD_PTR dwData,  
    UINT nCmd = 0x000F);
```  
  
### <a name="parameters"></a>参数  
 `dwData`  
 指定其他数据。 使用的值的值取决于`nCmd`参数。  
  
 `nCmd`  
 指定请求的帮助的类型。 有关的可能的值以及它们如何影响列表`dwData`参数，请参阅`uCommand`有关 HTMLHelp API 函数中所述的参数[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 框架还调用此函数可调用 HTMLHelp 应用程序。  
  
 当您的应用程序终止时，框架会自动关闭 HTMLHelp 应用程序。  
  
##  <a name="a-nameinitinstancea--cwinappinitinstance"></a><a name="initinstance"></a>Cwinapp:: Initinstance  
 Windows 允许同一个程序在同一时间运行的多个副本。  
  
```  
virtual BOOL InitInstance();
```  
  
### <a name="return-value"></a>返回值  
 如果初始化成功，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 应用程序初始化从概念上讲分为两个部分︰ 一次性应用程序初始化已完成第一次计划运行，和运行每个实例初始化时间一份程序运行，包括第一次。 框架的实现`WinMain`将调用此函数。  
  
 重写`InitInstance`初始化在 Windows 下运行的应用程序的每个新实例。 通常情况下，重写`InitInstance`来构造您的主窗口对象和设置`CWinThread::m_pMainWnd`数据成员，使其指向该窗口。 重写该成员函数的详细信息，请参阅[CWinApp︰ 应用程序类](../../mfc/cwinapp-the-application-class.md)。  
  
> [!NOTE]
>  MFC 应用程序必须初始化为单线程单元 (STA)。 如果调用[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)中您`InitInstance`重写中，指定`COINIT_APARTMENTTHREADED`(而不是`COINIT_MULTITHREADED`)。 有关详细信息，请参阅 PRB: MFC 应用程序停止响应时初始化该应用程序进行多线程单元 （828643） 在[http://support.microsoft.com/default.aspxscid=kb;en-us;828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCListView #&9;](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]  
  
##  <a name="a-nameistaskbarinteractionenableda--cwinappistaskbarinteractionenabled"></a><a name="istaskbarinteractionenabled"></a>CWinApp::IsTaskbarInteractionEnabled  
 指示是否启用了 Windows 7 任务栏交互。  
  
```  
virtual BOOL IsTaskbarInteractionEnabled();
```  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果`EnableTaskbarInteraction`已调用并且操作系统是 Windows 7 或更高版本。  
  
### <a name="remarks"></a>备注  
 任务栏交互意味着 MDI 应用程序在单独当鼠标指针位于应用程序的任务栏按钮时显示的选项卡式缩略图中显示 MDI 子窗体的内容。  
  
##  <a name="a-nameloadcursora--cwinapploadcursor"></a><a name="loadcursor"></a>CWinApp::LoadCursor  
 加载由名为的光标资源`lpszResourceName`或由指定`nIDResource`从当前的可执行文件。  
  
```  
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;  ```  
  
### Parameters  
 `lpszResourceName`  
 Points to a null-terminated string that contains the name of the cursor resource. You can use a `CString` for this argument.  
  
 `nIDResource`  
 ID of the cursor resource. For a list of resources, see [LoadCursor](http://msdn.microsoft.com/library/windows/desktop/ms648391) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Return Value  
 A handle to a cursor if successful; otherwise **NULL**.  
  
### Remarks  
 `LoadCursor` loads the cursor into memory only if it has not been previously loaded; otherwise, it retrieves a handle of the existing resource.  
  
 Use the [LoadStandardCursor](#loadstandardcursor) or [LoadOEMCursor](#loadoemcursor) member function to access the predefined Windows cursors.  
  
### Example  
 [!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]  
  
##  <a name="loadicon"></a>  CWinApp::LoadIcon  
 Loads the icon resource named by `lpszResourceName` or specified by `nIDResource` from the executable file.  
  
```  
HICON LoadIcon(LPCTSTR lpszResourceName) const; HICON LoadIcon(UINT nIDResource) const; ```  
  
### <a name="parameters"></a>参数  
 `lpszResourceName`  
 指向以 null 结尾的字符串，其中包含图标资源的名称。 您还可以使用`CString`为此参数。  
  
 `nIDResource`  
 图标资源的 ID 号。  
  
### <a name="return-value"></a>返回值  
 如果成功，则一个图标的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 `LoadIcon`仅当它尚未以前加载; 加载的图标否则，它将检索现有资源的句柄。  
  
 您可以使用[LoadStandardIcon](#loadstandardicon)或[LoadOEMIcon](#loadoemicon)成员函数来访问预定义的 Windows 图标。  
  
> [!NOTE]
>  此成员函数将调用 Win32 API 函数[LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072)，其中只能加载一个符合其大小的图标**SM_CXICON**和**SM_CYICON**系统指标值。  
  
##  <a name="a-nameloadoemcursora--cwinapploadoemcursor"></a><a name="loadoemcursor"></a>CWinApp::LoadOEMCursor  
 加载 Windows 预定义的由指定的光标资源`nIDCursor`。  
  
```  
HCURSOR LoadOEMCursor(UINT nIDCursor) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIDCursor`  
 **OCR_**清单常量指定预定义的 Windows 游标的标识符。 您必须具有**#define OEMRESOURCE**之前**#include \<afxwin.h&1;>**才能访问**OCR_** WINDOWS 中的常量。H。  
  
### <a name="return-value"></a>返回值  
 如果成功，则光标句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 使用`LoadOEMCursor`或[LoadStandardCursor](#loadstandardcursor)成员函数来访问预定义的 Windows cursor。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&45;](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]  
  
 [!code-cpp[NVC_MFCWindowing #&46;](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]  
  
##  <a name="a-nameloadoemicona--cwinapploadoemicon"></a><a name="loadoemicon"></a>CWinApp::LoadOEMIcon  
 加载 Windows 预定义的由指定的图标资源`nIDIcon`。  
  
```  
HICON LoadOEMIcon(UINT nIDIcon) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIDIcon`  
 **OIC_**清单常量指定预定义的 Windows 图标的标识符。 您必须具有**#define OEMRESOURCE**之前**#include \<afxwin.h&1;>**访问**OIC_** WINDOWS 中的常量。H。  
  
### <a name="return-value"></a>返回值  
 如果成功，则一个图标的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 使用`LoadOEMIcon`或[LoadStandardIcon](#loadstandardicon)成员函数来访问预定义的 Windows 图标。  
  
##  <a name="a-nameloadstandardcursora--cwinapploadstandardcursor"></a><a name="loadstandardcursor"></a>CWinApp::LoadStandardCursor  
 加载 Windows 预定义的光标资源的`lpszCursorName`指定。  
  
```  
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpszCursorName`  
 **IDC_**清单常量指定预定义的 Windows 游标的标识符。 在 WINDOWS 中定义这些标识符。H。 以下列表显示了可能的预定义的值以及有关的含义`lpszCursorName`:  
  
- **IDC_ARROW**标准箭头光标  
  
- **IDC_IBEAM**标准文本插入光标  
  
- **IDC_WAIT** Windows 将执行耗时的任务时使用的沙漏光标  
  
- **IDC_CROSS**十字准线光标所选内容  
  
- **IDC_UPARROW**垂直向上箭头  
  
- **IDC_SIZE**已过时，并不受支持; 使用**IDC_SIZEALL**  
  
- **IDC_SIZEALL**四向箭头。 要用于调整窗口大小的光标。  
  
- **IDC_ICON**过时和不受支持。 使用**IDC_ARROW**。  
  
- **IDC_SIZENWSE**带结束的左上角和右下方的两个箭头  
  
- **IDC_SIZENESW**右侧和较低的左上方的端点为双向箭头  
  
- **IDC_SIZEWE**水平双向箭头  
  
- **IDC_SIZENS**垂直双向箭头  
  
### <a name="return-value"></a>返回值  
 如果成功，则光标句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 使用`LoadStandardCursor`或[LoadOEMCursor](#loadoemcursor)成员函数来访问预定义的 Windows cursor。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&47;](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]  
  
##  <a name="a-nameloadstandardicona--cwinapploadstandardicon"></a><a name="loadstandardicon"></a>CWinApp::LoadStandardIcon  
 加载 Windows 预定义的图标资源，`lpszIconName`指定。  
  
```  
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpszIconName`  
 指定预定义的 Windows 图标一个清单常量标识符。 在 WINDOWS 中定义这些标识符。H。 可能的预定义的值及其说明的列表，请参阅*lpIconName*中的参数[LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果成功，则一个图标的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 使用`LoadStandardIcon`或[LoadOEMIcon](#loadoemicon)成员函数来访问预定义的 Windows 图标。  
  
##  <a name="a-nameloadstdprofilesettingsa--cwinapploadstdprofilesettings"></a><a name="loadstdprofilesettings"></a>CWinApp::LoadStdProfileSettings  
 在调用该成员函数[InitInstance](#initinstance)成员函数来启用和加载最近使用过 (的 MRU) 文件的列表和最后一次预览状态。  
  
```  
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```  
  
### <a name="parameters"></a>参数  
 `nMaxMRU`  
 最近使用过的文件来跟踪的数量。  
  
### <a name="remarks"></a>备注  
 如果`nMaxMRU`为 0，则将保留任何 MRU 列表。  
  
##  <a name="a-namembhelpmodea--cwinappmbhelpmode"></a><a name="m_bhelpmode"></a>CWinApp::m_bHelpMode  
 **TRUE**如果应用程序的帮助上下文模式 （按传统方法调用使用 SHIFT + F1）; 否则为**FALSE**。  
  
```  
BOOL m_bHelpMode;  
```  
  
### <a name="remarks"></a>备注  
 在帮助上下文模式中，光标将变为一个问号，用户可以将其移动屏幕信息。 如果您想要实现在帮助模式下的特殊处理，请检查此标志。 `m_bHelpMode`是类型的公共变量**BOOL**。  
  
##  <a name="a-namemdwrestartmanagersupportflagsa--cwinappmdwrestartmanagersupportflags"></a><a name="m_dwrestartmanagersupportflags"></a>CWinApp::m_dwRestartManagerSupportFlags  
 确定如何重新启动管理器中的行为的标志。  
  
```  
DWORD m_dwRestartManagerSupportFlags;  
```  
  
### <a name="remarks"></a>备注  
 若要启用重新启动管理器，设置`m_dwRestartManagerSupportFlags`到所需的行为。 下表显示可用的标志。  
  
|||  
|-|-|  
|Flag|描述|  
|`AFX_RESTART_MANAGER_SUPPORT_RESTART`|通过使用注册该应用程序[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)。 重新启动管理器负责重新启动该应用程序，如果意外退出。|  
|- `AFX_RESTART_MANAGER_SUPPORT_RECOVERY`|在重新启动管理器中注册该应用程序并重新启动该应用程序时，重新启动管理器调用恢复的回调函数。 默认恢复回调函数是[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。|  
|- `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`|启用了自动保存和重新启动管理器自动保存所有打开的文档的应用程序重新启动时。|  
|- `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL`|启用了自动保存和重新启动管理器自动保存所有打开的文档的定期时间间隔。 时间间隔由[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)。|  
|- `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`|重新启动从意外退出应用程序后，重新启动管理器打开以前打开的文档。 [CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)处理存储打开文档的列表和还原它们。|  
|- `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES`|重新启动管理器会提示用户在重新启动该应用程序后恢复自动保存文件。 `CDataRecoveryHandler`类会询问用户。|  
|- `AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE`|并集`AFX_RESTART_MANAGER_SUPPORT_RESTART`， `AFX_RESTART_MANAGER_SUPPORT_RECOVER`，和`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`。|  
|- `AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS`|The union of `AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE`, `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`, `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL`, and `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES`.|  
|- `AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS`|The union of `AFX_RESTART_MANAGER_SUPPORT_RESTART`, `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`, and `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES`.|  
|- `AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS`|The union of `AFX_RESTART_MANAGER_SUPPORT_RECOVERY`, `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL`, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`, and `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES`.|  
  
##  <a name="a-namemehelptypea--cwinappmehelptype"></a><a name="m_ehelptype"></a>CWinApp::m_eHelpType  
 此数据成员的类型是枚举的类型**AFX_HELP_TYPE**，其定义内`CWinApp`类。  
  
```  
AFX_HELP_TYPE m_eHelpType;  
```  
  
### <a name="remarks"></a>备注  
 **AFX_HELP_TYPE**枚举定义，如下所示︰  
  
 `enum AFX_HELP_TYPE`  
  
 `{`  
  
 `afxWinHelp = 0,`  
  
 `afxHTMLHelp = 1`  
  
 `};`  
  
-   若要设置到 HTML 帮助的应用程序的帮助，请调用[SetHelpMode](#sethelpmode)并指定**afxHTMLHelp**。  
  
-   若要设置到 WinHelp 的应用程序的帮助，请调用`SetHelpMode`并指定**afxWinHelp**。  
  
##  <a name="a-namemhinstancea--cwinappmhinstance"></a><a name="m_hinstance"></a>CWinApp::m_hInstance  
 对应于`hInstance`参数传递到 windows `WinMain`。  
  
```  
HINSTANCE m_hInstance;  
```  
  
### <a name="remarks"></a>备注  
 `m_hInstance`数据成员是在 Windows 下运行的应用程序的当前实例的句柄。 这由全局函数返回[AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)。 `m_hInstance`是类型的公共变量`HINSTANCE`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&55;](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]  
  
##  <a name="a-namemlpcmdlinea--cwinappmlpcmdline"></a><a name="m_lpcmdline"></a>CWinApp::m_lpCmdLine  
 对应于`lpCmdLine`参数传递到 windows `WinMain`。  
  
```  
LPTSTR m_lpCmdLine;  
```  
  
### <a name="remarks"></a>备注  
 指向以 null 结尾的字符串，指定应用程序的命令行。 使用`m_lpCmdLine`若要访问用户在应用程序启动时输入的任何命令行参数。 `m_lpCmdLine`是类型的公共变量`LPTSTR`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&52;](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]  
  
##  <a name="a-namemnautosaveintervala--cwinappmnautosaveinterval"></a><a name="m_nautosaveinterval"></a>CWinApp::m_nAutosaveInterval  
 以毫秒为单位之间自动保存的时间长度。  
  
```  
int m_nAutosaveInterval;  
```  
  
### <a name="remarks"></a>备注  
 可以在设置的时间间隔配置为自动保存打开的文档重新启动管理器。 如果您的应用程序不自动保存文件，则此参数无效。  
  
##  <a name="a-namemncmdshowa--cwinappmncmdshow"></a><a name="m_ncmdshow"></a>CWinApp::m_nCmdShow  
 对应于`nCmdShow`参数传递到 windows `WinMain`。  
  
```  
int m_nCmdShow;  
```  
  
### <a name="remarks"></a>备注  
 您应将传递`m_nCmdShow`作为参数调用时[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)应用程序主窗口。 `m_nCmdShow`是类型的公共变量`int`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&56;](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]  
  
##  <a name="a-namempactivewnda--cwinappmpactivewnd"></a><a name="m_pactivewnd"></a>CWinApp::m_pActiveWnd  
 使用此数据成员来存储指向具有您 OLE 服务器应用程序的就地激活的 OLE 容器应用程序的主窗口的指针。  
  
### <a name="remarks"></a>备注  
 如果此数据成员是**NULL**，该应用程序不处于就地活动状态。  
  
 框架窗口是就地激活的 OLE 容器应用程序时，框架将设置此成员变量。  
  
##  <a name="a-namempdatarecoveryhandlera--cwinappmpdatarecoveryhandler"></a><a name="m_pdatarecoveryhandler"></a>CWinApp::m_pDataRecoveryHandler  
 指针，指向该应用程序的数据恢复处理程序。  
  
```  
CDataRecoveryHandler* m_pDataRecoveryHandler;  
```  
  
### <a name="remarks"></a>备注  
 数据恢复处理程序的应用程序监视打开的文档和自动保存它们。 框架将使用数据恢复处理程序时意外退出后，重新启动应用程序恢复自动保存文件。 有关详细信息，请参阅[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)。  
  
##  <a name="a-namempszappnamea--cwinappmpszappname"></a><a name="m_pszappname"></a>CWinApp::m_pszAppName  
 指定应用程序的名称。  
  
```  
LPCTSTR m_pszAppName;  
```  
  
### <a name="remarks"></a>备注  
 应用程序的名称可能来自于传递给参数[CWinApp](#cwinapp)构造函数中，或者如果未指定给 resource 字符串 id 为**AFX_IDS_APP_TITLE**。 如果应用程序名称未找到资源中，它将来自该程序。EXE 文件名。  
  
 全局函数返回[AfxGetAppName](application-information-and-management.md#afxgetappname)。 `m_pszAppName`是类型的公共变量**const char\***。  
  
> [!NOTE]
>  如果您将值赋给`m_pszAppName`，堆上必须动态分配。 `CWinApp`析构函数调用**免费**（与此指针)。 许多想要使用`_tcsdup`（） 运行时库函数来执行分配。 此外，释放与当前的指针赋予新值之前关联的内存。 例如:   
  
 [!code-cpp[NVC_MFCWindowing #&57;](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&65;](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]  
  
##  <a name="a-namempszexenamea--cwinappmpszexename"></a><a name="m_pszexename"></a>CWinApp::m_pszExeName  
 包含不带扩展名的应用程序的可执行文件的名称。  
  
```  
LPCTSTR m_pszExeName;  
```  
  
### <a name="remarks"></a>备注  
 与不同[m_pszAppName](#m_pszappname)，此名称不能包含空格。 `m_pszExeName`是类型的公共变量**const char\***。  
  
> [!NOTE]
>  如果您将值赋给`m_pszExeName`，堆上必须动态分配。 `CWinApp`析构函数调用**免费**（与此指针)。 许多想要使用`_tcsdup`（） 运行时库函数来执行分配。 此外，释放与当前的指针赋予新值之前关联的内存。 例如：  
  
 [!code-cpp[NVC_MFCWindowing #&58; 页](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]  
  
##  <a name="a-namempszhelpfilepatha--cwinappmpszhelpfilepath"></a><a name="m_pszhelpfilepath"></a>CWinApp::m_pszHelpFilePath  
 包含指向应用程序的帮助文件的路径。  
  
```  
LPCTSTR m_pszHelpFilePath;  
```  
  
### <a name="remarks"></a>备注  
 默认情况下，框架初始化`m_pszHelpFilePath`与应用程序的名称为"。HLP"追加。 若要更改的帮助文件的名称，设置`m_pszHelpFilePath`以指向包含所需的帮助文件的完整名称的字符串。 若要这样做一个方便位置是在应用程序的[InitInstance](#initinstance)函数。 `m_pszHelpFilePath`是类型的公共变量**const char\***。  
  
> [!NOTE]
>  如果您将值赋给`m_pszHelpFilePath`，堆上必须动态分配。 `CWinApp`析构函数调用**免费**（与此指针)。 许多想要使用`_tcsdup`（） 运行时库函数来执行分配。 此外，释放与当前的指针赋予新值之前关联的内存。 例如:   
  
 [!code-cpp[NVC_MFCWindowing #&59;](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]  
  
##  <a name="a-namempszprofilenamea--cwinappmpszprofilename"></a><a name="m_pszprofilename"></a>CWinApp::m_pszProfileName  
 包含在应用程序的名称。INI 文件中。  
  
```  
LPCTSTR m_pszProfileName;  
```  
  
### <a name="remarks"></a>备注  
 `m_pszProfileName`是类型的公共变量**const char\***。  
  
> [!NOTE]
>  如果您将值赋给`m_pszProfileName`，堆上必须动态分配。 `CWinApp`析构函数调用**免费**（与此指针)。 许多想要使用`_tcsdup`（） 运行时库函数来执行分配。 此外，释放与当前的指针赋予新值之前关联的内存。 例如:   
  
 [!code-cpp[NVC_MFCWindowing #&60;](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]  
  
##  <a name="a-namempszregistrykeya--cwinappmpszregistrykey"></a><a name="m_pszregistrykey"></a>CWinApp::m_pszRegistryKey  
 用于确定，在注册表或 INI 文件中，应用程序配置文件设置的存储位置。  
  
```  
LPCTSTR m_pszRegistryKey;  
```  
  
### <a name="remarks"></a>备注  
 通常情况下，此数据成员将被视为是只读的。  
  
-   值存储到注册表项。 应用程序配置文件设置的名称追加到以下注册表项︰ HKEY_CURRENT_USER/软件/LocalAppWizard 生成 /。  
  
 如果您将值赋给`m_pszRegistryKey`，堆上必须动态分配。 `CWinApp`析构函数调用**免费**（与此指针)。 许多想要使用`_tcsdup`（） 运行时库函数来执行分配。 此外，释放与当前的指针赋予新值之前关联的内存。 例如：  
  
 [!code-cpp[NVC_MFCWindowing #&61;](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]  
  
##  <a name="a-namempszappida--cwinappmpszappid"></a><a name="m_pszappid"></a>CWinApp::m_pszAppID  
 应用程序用户模型 id。  
  
```  
LPCTSTR m_pszAppID;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameoncontexthelpa--cwinapponcontexthelp"></a><a name="oncontexthelp"></a>CWinApp::OnContextHelp  
 处理应用程序中的 SHIFT + F1 帮助。  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>备注  
 您必须添加`ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )`语句与您`CWinApp`类消息映射，还将添加一个快捷键表项，通常 SHIFT + F1，若要启用此成员函数。  
  
 `OnContextHelp`将应用程序进入帮助模式。 然后，光标将变为一个箭头和一个问号，以及用户可以将鼠标指针移动，并按鼠标左键来选择对话框、 窗口、 菜单上或命令按钮。 此成员函数检索光标下的对象的帮助上下文，并调用 Windows 函数 WinHelp 与该帮助上下文。  
  
##  <a name="a-nameonddecommanda--cwinapponddecommand"></a><a name="onddecommand"></a>CWinApp::OnDDECommand  
 当主框架窗口收到 DDE 由框架调用执行消息。  
  
```  
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```  
  
### <a name="parameters"></a>参数  
 *lpszCommand*  
 指向应用程序接收的 DDE 命令字符串。  
  
### <a name="return-value"></a>返回值  
 非零，如果处理该命令;否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现检查该命令是打开的文档的请求，是否是这样，将打开指定的文档。 当用户双击数据文件，Windows 文件管理器通常将发送此类 DDE 命令字符串。 重写此函数来处理其他 DDE 执行命令，如用于打印的命令。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&48;](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]  
  
##  <a name="a-nameonfilenewa--cwinapponfilenew"></a><a name="onfilenew"></a>CWinApp::OnFileNew  
 实现`ID_FILE_NEW`命令。  
  
```  
afx_msg void OnFileNew();
```  
  
### <a name="remarks"></a>备注  
 您必须添加`ON_COMMAND( ID_FILE_NEW, OnFileNew )`语句与您`CWinApp`类消息映射，以启用该成员函数。 如果启用，此函数将处理的新建文件命令的执行。  
  
 请参阅[技术说明 22](../../mfc/tn022-standard-commands-implementation.md)有关默认行为以及有关如何重写该成员函数的指导信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&49;](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing #&50;](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="a-nameonfileopena--cwinapponfileopen"></a><a name="onfileopen"></a>CWinApp::OnFileOpen  
 实现`ID_FILE_OPEN`命令。  
  
```  
afx_msg void OnFileOpen();
```  
  
### <a name="remarks"></a>备注  
 您必须添加`ON_COMMAND( ID_FILE_OPEN, OnFileOpen )`语句与您`CWinApp`类消息映射，以启用该成员函数。 如果启用，此函数将处理 File Open 命令执行。  
  
 默认行为的信息和有关如何重写该成员函数的指南，请参阅[技术说明 22](../../mfc/tn022-standard-commands-implementation.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&49;](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing #&50;](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="a-nameonfileprintsetupa--cwinapponfileprintsetup"></a><a name="onfileprintsetup"></a>CWinApp::OnFilePrintSetup  
 实现**ID_FILE_PRINT_SETUP**命令。  
  
```  
afx_msg void OnFilePrintSetup();
```  
  
### <a name="remarks"></a>备注  
 您必须添加`ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )`语句与您`CWinApp`类消息映射，以启用该成员函数。 如果启用，此函数将处理文件打印命令的执行。  
  
 默认行为的信息和有关如何重写该成员函数的指南，请参阅[技术说明 22](../../mfc/tn022-standard-commands-implementation.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&49;](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing #&50;](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="a-nameonhelpa--cwinapponhelp"></a><a name="onhelp"></a>CWinApp::OnHelp  
 处理应用程序中的 F1 帮助（使用当前上下文）。  
  
```  
afx_msg void OnHelp();
```  
  
### <a name="remarks"></a>备注  
 通常，您还将添加 F1 键的加速键条目。 启用 F1 键是仅一个约定，不是必需。  
  
 您必须添加`ON_COMMAND( ID_HELP, OnHelp )`语句与您`CWinApp`类消息映射，以启用该成员函数。 如果启用，由框架调用，当用户按 F1 键。  
  
 此消息处理程序函数的默认实现确定帮助上下文，对应于当前窗口、 对话框或菜单项，然后调用 WINHELP。EXE。 如果目前没有上下文，该函数将使用默认上下文。  
  
 重写该成员函数以设置为窗口、 对话框、 菜单项或当前具有焦点的工具栏按钮以外的帮助上下文。 调用`WinHelp`与所需帮助上下文 id。  
  
##  <a name="a-nameonhelpfindera--cwinapponhelpfinder"></a><a name="onhelpfinder"></a>CWinApp::OnHelpFinder  
 处理**ID_HELP_FINDER**和**ID_DEFAULT_HELP**命令。  
  
```  
afx_msg void OnHelpFinder();
```  
  
### <a name="remarks"></a>备注  
 您必须添加`ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )`语句与您`CWinApp`类消息映射，以启用该成员函数。 如果启用，框架将调用此消息处理程序函数，您的应用程序在用户选择要调用的帮助 Finder 命令时`WinHelp`与标准**HELP_FINDER**主题。  
  
##  <a name="a-nameonhelpindexa--cwinapponhelpindex"></a><a name="onhelpindex"></a>CWinApp::OnHelpIndex  
 处理**ID_HELP_INDEX**命令，并提供了默认的帮助主题。  
  
```  
afx_msg void OnHelpIndex();
```  
  
### <a name="remarks"></a>备注  
 您必须添加`ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )`语句与您`CWinApp`类消息映射，以启用该成员函数。 如果启用，框架将调用此消息处理程序函数，您的应用程序在用户选择要调用的帮助索引命令时`WinHelp`与标准**HELP_INDEX**主题。  
  
##  <a name="a-nameonhelpusinga--cwinapponhelpusing"></a><a name="onhelpusing"></a>CWinApp::OnHelpUsing  
 处理**ID_HELP_USING**命令。  
  
```  
afx_msg void OnHelpUsing();
```  
  
### <a name="remarks"></a>备注  
 您必须添加`ON_COMMAND( ID_HELP_USING, OnHelpUsing )`语句与您`CWinApp`类消息映射，以启用该成员函数。 您的应用程序在用户选择要调用的帮助使用命令时，框架将调用此消息处理程序函数`WinHelp`应用程序与标准**HELP_HELPONHELP**主题。  
  
##  <a name="a-nameonidlea--cwinapponidle"></a><a name="onidle"></a>CWinApp::OnIdle  
 重写该成员函数以执行空闲处理。  
  
```  
virtual BOOL OnIdle(LONG lCount);
```  
  
### <a name="parameters"></a>参数  
 `lCount`  
 每次递增一个计数器`OnIdle`当应用程序的消息队列为空时调用。 每次处理新消息时，此计数是置为 0。 您可以使用`lCount`参数，以确定相对的而不会处理一条消息的应用程序已被闲置的时间长度。  
  
### <a name="return-value"></a>返回值  
 非零值，接收更多空闲处理时间;如果需要没有更多的空闲时间为 0。  
  
### <a name="remarks"></a>备注  
 `OnIdle`默认消息循环中应用程序的消息队列为空时调用。 使用重写中调用您自己的背景空闲处理程序的任务。  
  
 `OnIdle`应返回 0 以指示需要没有空闲的处理时间。 `lCount`参数会在每次递增`OnIdle`消息队列为空，并且将重置为 0 每次处理新消息时调用。 您可以调用不同空闲例程根据此计数。  
  
 下表汇总了空闲循环处理︰  
  
1.  如果 Microsoft 基础类库中的消息循环检查消息队列，并查找不挂起消息，则会调用`OnIdle`的应用程序对象和提供 0 作为`lCount`参数。  
  
2. `OnIdle`执行一些处理，并返回一个非零值以指示它应再次调用，以做进一步处理。  
  
3.  消息循环会再次检查消息队列。 如果不不挂起任何消息，则会调用`OnIdle`再次重申，递增`lCount`参数。  
  
4.  最终，`OnIdle`完成处理所有空闲任务，并且返回 0。 这将告知消息循环来停止调用`OnIdle`之前从消息队列接收下一条消息，则此时空闲周期重启并将参数设置为 0。  
  
 不执行冗长任务期间`OnIdle`因为您的应用程序无法处理用户输入直到`OnIdle`返回。  
  
> [!NOTE]
>  默认实现`OnIdle`更新命令用户界面对象，如菜单项和工具栏按钮，并执行内部数据结构清理。 因此，如果重写`OnIdle`，必须调用`CWinApp::OnIdle`与`lCount`中重写版本。 首先调用所有基类空闲处理 (即，直到基类`OnIdle`，则返回 0)。 如果您需要执行工作，在基类处理完成之前，查看要选择适当的基类实现`lCount`期间完成工作。  
  
 如果不希望`OnIdle`为当从消息队列中检索消息时调用，可以重写[CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage)。 如果应用程序设置非常短的计时器，或者系统将要发送**WM_SYSTIMER**消息，然后`OnIdle`将重复调用，并降低性能。  
  
### <a name="example"></a>示例  
 下面的两个示例演示如何使用`OnIdle`。 第一个示例处理使用的两个空闲任务`lCount`参数来确定任务的优先级。 第一个任务是高优先级，您应尽可能。 第二个任务是不太重要，而且只有在没有用户输入中的暂停时间较长时间时应完成。 请注意调用基类版本的`OnIdle`。 第二个示例管理一的组具有不同优先级的空闲任务。  
  
 [!code-cpp[NVC_MFCWindowing #&51;](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]  
  
##  <a name="a-nameopendocumentfilea--cwinappopendocumentfile"></a><a name="opendocumentfile"></a>CWinApp::OpenDocumentFile  
 框架将调用此方法来打开命名[CDocument](../../mfc/reference/cdocument-class.md)应用程序文件。  
  
```  
virtual CDocument* OpenDocumentFile(
LPCTSTR lpszFileName  
BOOL bAddToMRU = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszFileName`  
 要打开的文件的名称。  
  
 [in] `bAddToMRU`  
 `TRUE`指示的文档是一个最新的文件;`FALSE`指示该文档不是最新的文件之一。  
  
### <a name="return-value"></a>返回值  
 一个指向`CDocument`如果成功，否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 如果具有该名称的文档已打开，包含该文档的第一个框架窗口会获得焦点。 如果应用程序支持多个文档模板，框架将使用的文件扩展名以查找相应的文档模板来尝试加载该文档。 如果成功，文档模板然后创建框架窗口和文档的视图。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&52;](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]  
  
##  <a name="a-nameparsecommandlinea--cwinappparsecommandline"></a><a name="parsecommandline"></a>CWinApp::ParseCommandLine  
 调用此成员函数以分析命令行并将参数，一次一个地发送给[CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)。  
  
```  
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```  
  
### <a name="parameters"></a>参数  
 `rCmdInfo`  
 对引用[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)对象。  
  
### <a name="remarks"></a>备注  
 当你开始使用应用程序向导新建一个 MFC 项目时，应用程序向导将创建的本地实例`CCommandLineInfo`，然后调用`ProcessShellCommand`和`ParseCommandLine`中[InitInstance](#initinstance)成员函数。 命令行如下所示如下所述的路由︰  
  
1.  之后在中创建`InitInstance`、`CCommandLineInfo`对象传递给`ParseCommandLine`。  
  
2. `ParseCommandLine`然后，调用`CCommandLineInfo::ParseParam`重复一次为每个参数。  
  
3. `ParseParam`填充`CCommandLineInfo`对象，然后传递给[ProcessShellCommand](#processshellcommand)。  
  
4. `ProcessShellCommand`处理命令行参数和标志。  
  
 请注意，您可以调用`ParseCommandLine`直接需要。  
  
 有关命令行的标志的说明，请参阅[CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)。  
  
##  <a name="a-namepretranslatemessagea--cwinapppretranslatemessage"></a><a name="pretranslatemessage"></a>CWinApp::PreTranslateMessage  
 重写此函数可对筛选器窗口消息被发送到 Windows 函数之前[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)默认实现将执行加速键转换，因此您必须调用`CWinApp::PreTranslateMessage`成员函数在重写版本。  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 `pMsg`  
 一个指向[MSG](../../mfc/reference/msg-structure1.md)结构，其中包含要处理的消息。  
  
### <a name="return-value"></a>返回值  
 如果在完全处理了消息，则为非`PreTranslateMessage`，并且不应进一步处理。 如果应以正常方式处理该消息，则为零。  
  
##  <a name="a-nameprocessmessagefiltera--cwinappprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinApp::ProcessMessageFilter  
 框架的挂钩函数调用该成员函数以筛选和响应特定 Windows 消息。  
  
```  
virtual BOOL ProcessMessageFilter(
    int code,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>参数  
 `code`  
 指定挂钩代码。 此成员函数将使用代码确定如何处理`lpMsg.`  
  
 `lpMsg`  
 一个指向 Windows [MSG](../../mfc/reference/msg-structure1.md)结构。  
  
### <a name="return-value"></a>返回值  
 如果处理了消息; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 挂钩函数将处理事件之前它们被发送到应用程序的正常消息处理。  
  
 如果重写此高级的功能时，一定要调用基类版本以维护框架的挂钩处理。  
  
##  <a name="a-nameprocessshellcommanda--cwinappprocessshellcommand"></a><a name="processshellcommand"></a>CWinApp::ProcessShellCommand  
 调用此成员函数[InitInstance](#initinstance)以接受从传递的参数`CCommandLineInfo`标识对象`rCmdInfo`，然后执行所指示的操作。  
  
```  
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```  
  
### <a name="parameters"></a>参数  
 `rCmdInfo`  
 对引用[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果 shell 命令成功处理了非零。 如果为 0，则返回**FALSE**从[InitInstance](#initinstance)。  
  
### <a name="remarks"></a>备注  
 当你开始使用应用程序向导新建一个 MFC 项目时，应用程序向导将创建的本地实例`CCommandLineInfo`，然后调用`ProcessShellCommand`和[ParseCommandLine](#parsecommandline)中`InitInstance`成员函数。 命令行如下所示如下所述的路由︰  
  
1.  之后在中创建`InitInstance`、`CCommandLineInfo`对象传递给`ParseCommandLine`。  
  
2. `ParseCommandLine`然后，调用[CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)重复一次为每个参数。  
  
3. `ParseParam`填充`CCommandLineInfo`对象，然后传递给`ProcessShellCommand`。  
  
4. `ProcessShellCommand`处理命令行参数和标志。  
  
 数据成员`CCommandLineInfo`标识的对象[CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)，以下在中定义的枚举类型的`CCommandLineInfo`类。  
  
 `enum {`  
  
 `FileNew,`  
  
 `FileOpen,`  
  
 `FilePrint,`  
  
 `FilePrintTo,`  
  
 `FileDDE,`  
  
 `};`  
  
 有关这些值的每个的简要说明，请参阅`CCommandLineInfo::m_nShellCommand`。  
  
##  <a name="a-nameprocesswndprocexceptiona--cwinappprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinApp::ProcessWndProcException  
 框架调用此成员函数，只要该处理程序不捕获中的一个应用程序的消息或命令处理程序引发的异常。  
  
```  
virtual LRESULT ProcessWndProcException(
    CException* e,  
    const MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 *e*  
 一个指向未捕获的异常。  
  
 `pMsg`  
 一个[MSG](../../mfc/reference/msg-structure1.md)结构，其中包含有关导致引发异常的框架的 windows 消息的信息。  
  
### <a name="return-value"></a>返回值  
 该值应返回到 Windows。 通常这是用于 windows 消息，1l 0l ( **TRUE**) 的命令消息。  
  
### <a name="remarks"></a>备注  
 不要直接调用此成员函数。  
  
 此成员函数的默认实现将创建一个消息框。 如果未捕获的异常源自菜单、 工具栏或快捷键命令失败，消息框将显示"命令失败"消息;否则，它显示一条"内部应用程序错误"消息。  
  
 重写该成员函数以提供全局处理的异常。 如果您想要显示的消息框，只能调用的基本功能。  
  
##  <a name="a-nameregistera--cwinappregister"></a><a name="register"></a>CWinApp::Register  
 执行未由任何注册任务`RegisterShellFileTypes`。  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现只是返回 TRUE。 重写此函数可提供任何自定义的注册步骤。  
  
##  <a name="a-nameregistershellfiletypesa--cwinappregistershellfiletypes"></a><a name="registershellfiletypes"></a>CWinApp::RegisterShellFileTypes  
 调用该成员函数以使用 Windows 文件管理器注册的所有应用程序的文档类型。  
  
```  
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bCompat`  
 `TRUE`将添加 shell 命令打印和打印到，从而使用户可以直接从命令行程序，或通过将文件拖动到 printer 对象打印文件的注册表项。 它还添加 DefaultIcon 键。 默认情况下，此参数是`FALSE`为了向后兼容。  
  
### <a name="remarks"></a>备注  
 这允许用户通过双击将其从文件管理器中创建您的应用程序的数据文件中打开。 调用`RegisterShellFileTypes`调用后[AddDocTemplate](#adddoctemplate)为每个应用程序中的文档模板。 此外调用[EnableShellOpen](#enableshellopen)成员函数在调用时`RegisterShellFileTypes`。  
  
 `RegisterShellFileTypes`循环访问列表[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)应用程序维护和，对于每个文档模板，将项添加到 Windows 保留的文件关联的注册数据库对象。 文件管理器使用这些项来打开数据文件，当用户双击它。 这消除了需要装运。REG 文件，您的应用程序。  
  
> [!NOTE]
> `RegisterShellFileTypes`仅适用于用户具有管理员权限运行此程序。 如果该程序不具有管理员权限，它不能更改注册表项。  
  
 如果注册数据库已将给定的文件扩展名与另一种文件类型相关联，则会不创建任何新的关联。 请参阅`CDocTemplate`格式的字符串必须注册此信息的类。  
  
##  <a name="a-nameregisterwithrestartmanagera--cwinappregisterwithrestartmanager"></a><a name="registerwithrestartmanager"></a>CWinApp::RegisterWithRestartManager  
 在重新启动管理器中注册该应用程序。  
  
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
|[in] `bRegisterRecoveryCallback`|`TRUE`指示此实例的应用程序使用恢复回调函数;`FALSE`表示它将不做。 当应用程序意外退出时，框架将调用恢复回调函数。 有关详细信息，请参阅[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。|  
|[in] `strRestartIdentifier`|用于标识此重新启动管理器实例的唯一字符串。 重新启动管理器标识符是应用的唯一程序的每个实例。|  
|[in] `pwzCommandLineArgs`|一个字符串，包含从命令行的任何额外参数。|  
|[in] `dwRestartFlags`|重新启动管理器的可选标志。 有关详细信息，请参阅“备注”部分。|  
|[in] `pRecoveryCallback`|恢复回调函数。 此函数必须将`LPVOID`参数作为输入并返回`DWORD`。 默认恢复回调函数是`CWinApp::ApplicationRecoveryCallback`。|  
|[in] `lpvParam`|用于恢复的回调函数的输入的参数。 有关详细信息，请参阅[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。|  
|[in] `dwPingInterval`|有关恢复回调函数以返回等待重新启动管理器的时间长度。 此参数是以毫秒为单位。|  
|[in] `dwCallbackFlags`|标志传递给恢复回调函数。 留待将来使用。|  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，则此方法否则为错误代码。  
  
### <a name="remarks"></a>备注  
 如果您的应用程序使用默认 MFC 实现自动保存文件，则应使用的简单版本`RegisterWithRestartManager`。 使用的复杂版本`RegisterWithRestartManager`如果您想要自定义您的应用程序的自动保存行为。  
  
 如果调用此方法与空字符串作为`strRestartIdentifier`， `RegisterWithRestartManager` manager 中创建的重新启动此实例的唯一标识符字符串。  
  
 当应用程序意外退出时，请重新启动管理器重新启动从命令行应用程序，并提供重新启动的唯一标识符，则为可选参数。 在此方案中，框架将调用`RegisterWithRestartManager`两次。 第一个调用是来自[cwinapp:: Initinstance](#initinstance)使用空字符串的字符串标识符。 然后，该方法[CWinApp::ProcessShellCommand](#processshellcommand)调用`RegisterWithRestartManager`具有唯一的重启标识符。  
  
 在重新启动管理器注册应用程序后，重新启动管理器监视应用程序。 如果应用程序意外退出，请重新启动管理器在关闭过程中调用恢复回调函数。 重新启动管理器等待`dwPingInterval`恢复回调函数的响应。 如果恢复回调函数在此时间内未作出响应，该应用程序将退出而不执行恢复的回调函数。  
  
 默认情况下，dwRestartFlags 不受支持，但提供供将来使用。 可能的值`dwRestartFlags`如下︰  
  
- `RESTART_NO_CRASH`  
  
- `RESTART_NO_HANG`  
  
- `RESTART_NO_PATCH`  
  
- `RESTART_NO_REBOOT`  
  
##  <a name="a-namereopenpreviousfilesatrestarta--cwinappreopenpreviousfilesatrestart"></a><a name="reopenpreviousfilesatrestart"></a>CWinApp::ReopenPreviousFilesAtRestart  
 确定是否重新启动管理器重新打开该应用程序意外退出时打开的文件。  
  
```  
virtual BOOL ReopenPreviousFilesAtRestart() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`指示重新启动管理器重新打开以前打开的文件;`FALSE`表明没有重新启动管理器。  
  
##  <a name="a-namerestartinstancea--cwinapprestartinstance"></a><a name="restartinstance"></a>CWinApp::RestartInstance  
 处理重新启动应用程序启动的重新启动管理器。  
  
```  
virtual BOOL CWinApp::RestartInstance();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果数据恢复处理程序将打开以前打开的文档;`FALSE`数据恢复处理程序是否出错，或者如果不有任何以前打开的文档。  
  
### <a name="remarks"></a>备注  
 重新启动管理器重新启动时应用程序，框架将调用此方法。 此方法检索数据恢复处理程序并还原自动保存文件。 此方法调用[CDataRecoveryHandler::RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments)来确定用户想要恢复自动保存文件。  
  
 此方法返回`FALSE`如果[CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md)确定没有任何打开的文档。 如果存在任何打开的文档，在应用程序通常启动。  
  
##  <a name="a-namerestoreautosavedfilesatrestarta--cwinapprestoreautosavedfilesatrestart"></a><a name="restoreautosavedfilesatrestart"></a>CWinApp::RestoreAutosavedFilesAtRestart  
 确定在重新启动该应用程序时，重新启动管理器是否恢复自动保存文件。  
  
```  
virtual BOOL RestoreAutosavedFilesAtRestart() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`将显示的重新启动管理器恢复自动保存文件;`FALSE`表明没有重新启动管理器。  
  
##  <a name="a-nameruna--cwinapprun"></a><a name="run"></a>Cwinapp:: Run  
 提供一个默认的消息循环。  
  
```  
virtual int Run();
```  
  
### <a name="return-value"></a>返回值  
 `int`返回的值`WinMain`。  
  
### <a name="remarks"></a>备注  
 **运行**获取，并将 Windows 消息调度直到应用程序收到**WM_QUIT**消息。 如果应用程序的消息队列当前不包含任何消息，**运行**调用[OnIdle](#onidle)来执行空闲处理。 传入消息将转到[PreTranslateMessage](#pretranslatemessage)成员函数以进行特殊处理，然后执行到 Windows 函数**TranslateMessage**标准键盘翻译; 最后， **DispatchMessage**调用 Windows 函数。  
  
 **运行**很少会重写，但您可以覆盖它能够以特殊行为。  
  
##  <a name="a-namerunautomateda--cwinapprunautomated"></a><a name="runautomated"></a>CWinApp::RunAutomated  
 调用此函数可确定是否"**注册服务器对象**" **-自动化**"选项是否存在，它指示是否通过客户端应用程序启动服务器应用程序。  
  
```  
BOOL RunAutomated();
```  
  
### <a name="return-value"></a>返回值  
 如果该选项; 如果未找到，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 如果存在，将从命令行中删除该选项。 OLE 自动化的详细信息，请参阅文章[自动化服务器](../../mfc/automation-servers.md)。  
  
##  <a name="a-namerunembeddeda--cwinapprunembedded"></a><a name="runembedded"></a>CWinApp::RunEmbedded  
 调用此函数可确定是否" **/嵌入**" **-Embedding**"选项是否存在，它指示是否通过客户端应用程序启动服务器应用程序。  
  
```  
BOOL RunEmbedded();
```  
  
### <a name="return-value"></a>返回值  
 如果该选项; 如果未找到，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 如果存在，将从命令行中删除该选项。 嵌入的详细信息，请参阅文章[服务器︰ 实现服务器](../../mfc/servers-implementing-a-server.md)。  
  
##  <a name="a-namesaveallmodifieda--cwinappsaveallmodified"></a><a name="saveallmodified"></a>CWinApp::SaveAllModified  
 由框架调用到保存应用程序的主框架窗口时要关闭的所有文档或通过`WM_QUERYENDSESSION`消息。  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果可以安全地终止该应用程序。如果不安全，终止该应用程序，则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数的默认实现调用[CDocument::SaveModified](../../mfc/reference/cdocument-class.md#savemodified)成员函数反过来，应用程序中的所有修改后的文档。  
  
##  <a name="a-nameselectprintera--cwinappselectprinter"></a><a name="selectprinter"></a>CWinApp::SelectPrinter  
 调用此成员函数以选择特定打印机，然后释放以前曾在打印对话框中选定的打印机。  
  
```  
void SelectPrinter(
    HANDLE hDevNames,  
    HANDLE hDevMode,  
    BOOL bFreeOld = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `hDevNames`  
 句柄[DEVNAMES](../../mfc/reference/devnames-structure.md)标识驱动程序、 设备和特定打印机的输出端口名称的结构。  
  
 `hDevMode`  
 句柄[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)结构，它指定有关设备初始化和环境的打印机的信息。  
  
 *bFreeOld*  
 释放以前所选打印机。  
  
### <a name="remarks"></a>备注  
 如果两个`hDevMode`和`hDevNames`是**NULL**，`SelectPrinter`使用当前的默认打印机。  
  
##  <a name="a-namesethelpmodea--cwinappsethelpmode"></a><a name="sethelpmode"></a>CWinApp::SetHelpMode  
 将应用程序的帮助类型设置。  
  
```  
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```  
  
### <a name="parameters"></a>参数  
 `eHelpType`  
 指定要使用帮助的类型。 请参阅[CWinApp::m_eHelpType](#m_ehelptype)有关详细信息。  
  
### <a name="remarks"></a>备注  
 将应用程序的帮助类型设置。  
  
 若要将应用程序的帮助类型设置为 HTMLHelp，可以调用[EnableHTMLHelp](#enablehtmlhelp)。 一旦调用`EnableHTMLHelp`，您的应用程序必须使用 HTMLHelp 作为其帮助应用程序。 如果你想要改为使用 WinHelp，则可以调用`SetHelpMode`并设置`eHelpType`到**afxWinHelp**。  
  
##  <a name="a-namesetregistrykeya--cwinappsetregistrykey"></a><a name="setregistrykey"></a>CWinApp::SetRegistryKey  
 导致应用程序设置存储在注册表中而不是 INI 文件。  
  
```  
void SetRegistryKey(LPCTSTR lpszRegistryKey);  
void SetRegistryKey(UINT nIDRegistryKey);
```  
  
### <a name="parameters"></a>参数  
 *lpszRegistryKey*  
 包含密钥的名称的字符串的指针。  
  
 *nIDRegistryKey*  
 包含的注册表项名称的字符串资源的 ID。  
  
### <a name="remarks"></a>备注  
 此函数设置*m_pszRegistryKey*，然后使用`GetProfileInt`， `GetProfileString`， `WriteProfileInt`，和`WriteProfileString`的成员函数`CWinApp`。 如果已调用此函数，则最近使用 (过的 MRU) 文件的列表也会存储在注册表中。 注册表项通常是一家公司的名称。 存储在以下形式的密钥︰ HKEY_CURRENT_USER\Software\\<company></company>\>\\<application></application>\>\\<section></section>\>\\<value></value>\>。  
  
##  <a name="a-namesupportsapplicationrecoverya--cwinappsupportsapplicationrecovery"></a><a name="supportsapplicationrecovery"></a>CWinApp::SupportsApplicationRecovery  
 确定是否重新启动管理器恢复的应用程序意外退出。  
  
```  
virtual BOOL SupportsApplicationRecovery() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`指示重新启动管理器恢复的应用程序;`FALSE`表明没有重新启动管理器。  
  
##  <a name="a-namesupportsautosaveatintervala--cwinappsupportsautosaveatinterval"></a><a name="supportsautosaveatinterval"></a>CWinApp::SupportsAutosaveAtInterval  
 确定是否重新启动管理器自动保存打开定期时间间隔的文档。  
  
```  
virtual BOOL SupportsAutosaveAtInterval() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`指示重新启动管理器自动保存打开的文档;`FALSE`表明没有重新启动管理器。  
  
##  <a name="a-namesupportsautosaveatrestarta--cwinappsupportsautosaveatrestart"></a><a name="supportsautosaveatrestart"></a>CWinApp::SupportsAutosaveAtRestart  
 确定是否重新启动管理器自动保存所有打开的文档的应用程序重新启动时。  
  
```  
virtual BOOL SupportsAutosaveAtRestart() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`指示当应用程序重新启动; 重新启动管理器自动保存打开的文档`FALSE`表明没有重新启动管理器。  
  
##  <a name="a-namesupportsrestartmanagera--cwinappsupportsrestartmanager"></a><a name="supportsrestartmanager"></a>CWinApp::SupportsRestartManager  
 确定应用程序是否支持重新启动管理器。  
  
```  
virtual BOOL SupportsRestartManager() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`指示应用程序支持重新启动管理器;`FALSE`表明该应用程序没有。  
  
##  <a name="a-nameunregistera--cwinappunregister"></a><a name="unregister"></a>CWinApp::Unregister  
 注销注册的应用程序对象的所有文件。  
  
```  
virtual BOOL Unregister();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 `Unregister`函数撤消注册应用程序对象执行的与[注册](#register)函数。 通常情况下，这两个函数由 MFC 隐式调用，并因此不会出现在您的代码。  
  
 重写此函数可执行的自定义注销步骤。  
  
##  <a name="a-nameunregistershellfiletypesa--cwinappunregistershellfiletypes"></a><a name="unregistershellfiletypes"></a>CWinApp::UnregisterShellFileTypes  
 调用此成员函数可注销所有应用程序的文档类型使用 Windows 文件管理器。  
  
```  
void UnregisterShellFileTypes();
```  
  
##  <a name="a-namewinhelpa--cwinappwinhelp"></a><a name="winhelp"></a>CWinApp::WinHelp  
 调用该成员函数以调用 WinHelp 的应用程序。  
  
```  
virtual void WinHelp(
    DWORD_PTR dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>参数  
 `dwData`  
 指定其他数据。 使用的值的值取决于`nCmd`参数。  
  
 `nCmd`  
 指定请求的帮助的类型。 有关的可能的值以及它们如何影响列表`dwData`参数，请参阅[WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267) Windows 函数。  
  
### <a name="remarks"></a>备注  
 框架还调用此函数可调用 WinHelp 的应用程序。  
  
 当您的应用程序终止时，框架会自动关闭 WinHelp 应用程序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&53;](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]  
  
##  <a name="a-namewriteprofilebinarya--cwinappwriteprofilebinary"></a><a name="writeprofilebinary"></a>CWinApp::WriteProfileBinary  
 调用此成员函数可将二进制数据写入到应用程序的注册表的指定部分或。INI 文件中。  
  
```  
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPBYTE pData,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>参数  
 `lpszSection`  
 指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果该节不存在，则创建它。 节的名称是区分大小写;字符串可以是任何组合的大写和小写字母。  
  
 `lpszEntry`  
 指向以 null 结尾的字符串，其中包含向其中写入值的条目。 如果该条目不存在于指定的节，则创建它。  
  
 `pData`  
 指向要写入的数据。  
  
 `nBytes`  
 包含要写入字节数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 此示例使用`CWinApp* pApp = AfxGetApp();`CWinApp 类来说明一种方法获取，`WriteProfileBinary`和`GetProfileBinary`可以从 MFC 应用程序中的任意函数使用。  
  
 [!code-cpp[NVC_MFCWindowing #&54;](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]  
  
 另一个示例，请参阅示例[CWinApp::GetProfileBinary](#getprofilebinary)。  
  
##  <a name="a-namewriteprofileinta--cwinappwriteprofileint"></a><a name="writeprofileint"></a>Cwinapp:: Writeprofileint  
 调用此成员函数可将指定的值写入到应用程序的注册表的指定部分或。INI 文件中。  
  
```  
BOOL WriteProfileInt(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    int nValue);
```  
  
### <a name="parameters"></a>参数  
 `lpszSection`  
 指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果该节不存在，则创建它。 节的名称是区分大小写;字符串可以是任何组合的大写和小写字母。  
  
 `lpszEntry`  
 指向以 null 结尾的字符串，其中包含向其中写入值的条目。 如果该条目不存在于指定的节，则创建它。  
  
 `nValue`  
 包含要写入的值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 此示例使用`CWinApp* pApp = AfxGetApp();`CWinApp 类来说明一种方法获取， `WriteProfileString`， `WriteProfileInt`， `GetProfileString`，和`GetProfileInt`可以从 MFC 应用程序中的任意函数使用。  
  
 [!code-cpp[NVC_MFCWindowing #&43;](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 另一个示例，请参阅示例[CWinApp::GetProfileInt](#getprofileint)。  
  
##  <a name="a-namewriteprofilestringa--cwinappwriteprofilestring"></a><a name="writeprofilestring"></a>CWinApp::WriteProfileString  
 调用此成员函数可将指定的字符串写入到应用程序的注册表的指定部分或。INI 文件中。  
  
```  
BOOL WriteProfileString(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>参数  
 `lpszSection`  
 指向以 null 结尾的字符串，该字符串指定包含条目的部分。 如果该节不存在，则创建它。 节的名称是区分大小写;字符串可以是任何组合的大写和小写字母。  
  
 `lpszEntry`  
 指向以 null 结尾的字符串，其中包含向其中写入值的条目。 如果该条目不存在于指定的节，则创建它。 如果此参数为`NULL`，通过指定节`lpszSection`被删除。  
  
 `lpszValue`  
 指向要写入的字符串。 如果此参数为`NULL`，指定的条目`lpszEntry`删除参数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&43;](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 另一个示例，请参阅示例[CWinApp::GetProfileInt](#getprofileint)。  
  
##  <a name="a-namesetappida--cwinappsetappid"></a><a name="setappid"></a>CWinApp::SetAppID  
 显式设置为应用程序的应用程序用户模型 ID。 任何用户界面显示给用户 （的最佳位置是应用程序构造函数） 之前，应调用此方法。  
  
```  
void SetAppID(LPCTSTR lpcszAppID);
```  
  
### <a name="parameters"></a>参数  
 `lpcszAppID`  
 指定应用程序用户模型 id。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [CWinThread 类](../../mfc/reference/cwinthread-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [如何︰ 添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)




