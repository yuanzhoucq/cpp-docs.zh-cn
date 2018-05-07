---
title: 应用程序信息和管理 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41b6aa602956c6dcdeda8f6b8c24c1be48c58ce2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="application-information-and-management"></a>应用程序信息和管理
当你编写应用程序时，创建单个[CWinApp](../../mfc/reference/cwinapp-class.md)-派生对象。 有时，你可能想要获取有关从外部此对象的信息`CWinApp`-派生对象。 或者，你可能需要对其他全局"管理器"对象的访问。
  
 Microsoft 基础类库提供了以下全局函数，以帮助你完成这些任务：  
  
### <a name="application-information-and-management-functions"></a>应用程序信息和管理功能  
  
|||  
|-|-|  
|[AfxBeginThread](#afxbeginthread)|创建一个新线程。|  
|[AfxContextMenuManager](#afxcontextmenumanager)|指向全局[上下文菜单管理器](ccontextmenumanager-class.md)。|
|[AfxEndThread](#afxendthread)|终止当前线程。|  
|[AfxFindResourceHandle](#afxfindresourcehandle)|指导资源链并找到特定资源的资源 ID 和资源类型。 |
|[AfxFreeLibrary](#afxfreelibrary)|递减引用计数的加载的动态链接库 (DLL) 模块中;当引用计数达到零时，该模块未映射。|  
|[AfxGetApp](#afxgetapp)|返回指向应用程序的单个`CWinApp`对象。|  
|[AfxGetAppName](#afxgetappname)|返回包含应用程序的名称的字符串。|  
|[AfxGetInstanceHandle](#afxgetinstancehandle)|返回`HINSTANCE`表示此实例的应用程序。|  
|[AfxGetMainWnd](#afxgetmainwnd)|将指针返回到当前的"主"窗口非 OLE 应用程序或服务器应用程序的就地框架窗口。|  
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|使用此函数可确定应用程序是否将注册表访问重定向**HKEY_CURRENT_USER** ( **HKCU**) 节点。|  
|[AfxGetResourceHandle](#afxgetresourcehandle)|返回`HINSTANCE`应用程序的默认资源的来源。 用于直接访问应用程序的资源。|  
|[AfxGetThread](#afxgetthread)|检索指向当前[CWinThread](../../mfc/reference/cwinthread-class.md)对象。|  
|[AfxInitRichEdit](#afxinitrichedit)|初始化 1.0 rich edit 控件的应用程序的版本。|  
|[AfxInitRichEdit2](#afxinitrichedit2)|初始化 2.0 及更高版本 rich edit 控件的应用程序的版本。| 
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|确定给定窗口是否是扩展框架对象。|
|[AfxIsMFCToolBar](#afxismfctoolbar)|确定给定窗口是否为工具栏对象。|
|[AfxKeyboardManager](#afxkeyboardmanager)|指向全局[键盘管理器](ckeyboardmanager-class.md)。|
|[AfxLoadLibrary](#afxloadlibrary)|映射 DLL 模块，并返回一个句柄，可用于获取 DLL 函数的地址。|  
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|指向全局[便捷菜单管理器](cmenutearoffmanager-class.md)。|
|[AfxMouseManager](#afxmousemanager)|指向全局[鼠标管理器](cmousemanager-class.md)。|
|[AfxRegisterClass](#afxregisterclass)|在使用 MFC 的 DLL 中注册窗口类。|  
|[AfxRegisterWndClass](#afxregisterwndclass)|注册的 Windows 窗口类来补充这些由 MFC 自动注册。|  
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|设置是否应用程序将注册表访问重定向**HKEY_CURRENT_USER** ( **HKCU**) 节点。|  
|[AfxSetResourceHandle](#afxsetresourcehandle)|集`HINSTANCE`句柄的默认资源的应用程序加载的位置。|  
|[AfxShellManager](#afxshellmanager)|指向全局[shell 管理器](cshellmanager-class.md)。 |
|[AfxSocketInit](#afxsocketinit)|在中调用`CWinApp::InitInstance`替代用于初始化 Windows 套接字。|  
|[AfxUserToolsManager](#afxusertoolsmanager)|指向全局[用户工具管理器](cusertoolsmanager-class.md)。|
|[AfxWinInit](#afxwininit)|由 MFC 提供`WinMain`函数，作为的一部分[CWinApp](../../mfc/reference/cwinapp-class.md)基于 GUI 的应用程序，以初始化 MFC 的初始化。 必须为使用 MFC 的控制台应用程序直接调用。|  
  

  
##  <a name="afxbeginthread"></a>  AfxBeginThread  
 调用此函数可创建新线程。  
  
```   
CWinThread* AfxBeginThread(
    AFX_THREADPROC pfnThreadProc,  
    LPVOID pParam,  
    int nPriority = THREAD_PRIORITY_NORMAL,  
    UINT nStackSize = 0,  
    DWORD dwCreateFlags = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);

CWinThread* AfxBeginThread(
    CRuntimeClass* pThreadClass,  
    int nPriority = THREAD_PRIORITY_NORMAL,  
    UINT nStackSize = 0,  
    DWORD dwCreateFlags = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL); 
```  
  
### <a name="parameters"></a>参数  
 `pfnThreadProc`  
 指向辅助线程的控制函数。 不能为**NULL**。 此函数必须声明如下：  
  
 `UINT __cdecl MyControllingFunction( LPVOID pParam );`  
  
 *pThreadClass*  
 对象的 RUNTIME_CLASS 派生自[CWinThread](../../mfc/reference/cwinthread-class.md)。  
  
 *pParam*  
 参数传递给控制函数，如图所示的参数中的函数声明中`pfnThreadProc`。  
  
 `nPriority`  
 所需的线程的优先级。 有关完整列表和说明可用的优先级，请参阅[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) Windows SDK 中。  
  
 `nStackSize`  
 以字节为单位的新线程的堆栈中指定的大小。 如果为 0，堆栈大小将默认为相同大小堆栈上为创建的线程。  
  
 `dwCreateFlags`  
 指定控制的线程创建一个附加标志。 此标志可以包含两个值之一：  
  
- **CREATE_SUSPENDED**与一个挂起计数启动线程。 使用**CREATE_SUSPENDED**如果你想要初始化的任何成员数据`CWinThread`对象，如[m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete)或派生类中，在该线程开始运行前的任何成员。 你初始化完成后，使用[CWinThread::ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread)开始运行的线程。 将才会执行线程`CWinThread::ResumeThread`调用。  
  
- **0**创建后立即启动线程。  
  
 `lpSecurityAttrs`  
 指向[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)结构，它指定线程的安全属性。 如果**NULL**，相同的安全属性，如将使用创建的线程。 此结构的详细信息，请参阅 Windows SDK。  
  
### <a name="return-value"></a>返回值  
 指向新创建的线程对象，或**NULL**如果发生故障。  
  
### <a name="remarks"></a>备注  
 第一种形式的`AfxBeginThread`创建工作线程。 第二种形式创建线程可能会为其提供服务，为用户界面线程或工作线程。  
  
 `AfxBeginThread` 创建一个新`CWinThread`对象、 调用其[CreateThread](../../mfc/reference/cwinthread-class.md#createthread)函数开始执行线程，并将指针返回到该线程。 在整个过程进行检查以确保所有对象都都释放正确应创建的任何部分出现故障。 若要结束该线程，请调用[AfxEndThread](#afxendthread)从内的线程或从工作线程控制函数返回。  
  
 多线程处理必须启用该应用程序。否则，此函数将失败。 有关启用多线程处理的详细信息，请参阅[/MD、 /MT、 /LD （使用运行时库）](../../build/reference/md-mt-ld-use-run-time-library.md)下*Visual c + + 编译器选项*。  
  
 有关详细信息`AfxBeginThread`，请参阅文章[多线程处理： 创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)和[多线程处理： 创建用户界面线程](../../parallel/multithreading-creating-user-interface-threads.md)。  
  
### <a name="example"></a>示例  
 请参阅示例[CSocket::Attach](../../mfc/reference/csocket-class.md#attach)。  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  

## <a name="afxcontextmenumanager"></a> AfxContextMenuManager
指向全局[上下文菜单管理器](ccontextmenumanager-class.md)。  
   
### <a name="syntax"></a>语法    
```  
CContextMenuManager* afxContextMenuManager;  
```     
### <a name="requirements"></a>要求  
 **标头：** afxcontextmenumanager.h     

### <a name="see-also"></a>请参阅   
 [CContextMenuManager 类](ccontextmenumanager-class.md)

  
##  <a name="afxendthread"></a>  AfxEndThread  
 调用此函数可终止当前正在执行的线程。  
  
```   
void AFXAPI AfxEndThread(
    UINT nExitCode,  
    BOOL bDelete  = TRUE); 
```  
  
### <a name="parameters"></a>参数  
 *nExitCode*  
 指定线程的退出代码。  
  
 *bDelete*  
 从内存中删除使线程对象。  
  
### <a name="remarks"></a>备注  
 必须从中进行调用的线程将被终止。  
  
 有关详细信息`AfxEndThread`，请参阅文章[多线程处理： 终止线程](../../parallel/multithreading-terminating-threads.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
使用 `AfxFindResourceHandle` 处理资源链并按资源 ID 和资源类型找到特定资源。  
   
### <a name="syntax"></a>语法    
```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );  
```
### <a name="parameters"></a>参数  
 `lpszName`  
 指向包含资源 ID 的字符串的指针。    
 *lpszType*  
 指向资源的类型的指针。 资源类型的列表，请参阅[FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) Windows SDK 中。  
   
### <a name="return-value"></a>返回值  
 包含资源的模块的句柄。  
   
### <a name="remarks"></a>备注  
 `AfxFindResourceHandle` 查找特定资源并返回包含该资源的模块的句柄。 该资源可能位于任何 MFC 扩展 DLL 已加载。 `AfxFindResourceHandle` 将告知您哪个 DLL 包含该资源。  
  
 模块将按以下顺序进行搜索：  
  
1.  主模块 （如果它是 MFC 扩展 DLL）。  
  
2.  非系统模块。  
  
3.  语言特定的模块。  
  
4.  主模块（如果它是系统 DLL）。  
  
5.  系统模块。  
   
### <a name="requirements"></a>要求  
 **标头:** afxwin.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
  
##  <a name="afxfreelibrary"></a>  AfxFreeLibrary  
 `AfxFreeLibrary` 和 `AfxLoadLibrary` 用于维护每个已加载库模块的引用计数。  
  
```   
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib); 
```  
  
### <a name="parameters"></a>参数  
 *hInstLib*  
 已加载库模块的句柄。 [AfxLoadLibrary](#afxloadlibrary)返回此句柄。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果函数成功; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 `AfxFreeLibrary` 减少已加载动态链接库 (DLL) 模块的引用计数。 当引用计数达到零时，将从调用进程的地址空间取消映射模块，并且句柄不再有效。 每次调用 `AfxLoadLibrary` 时都会增加此引用计数。  
  
 在取消映射库模块之前，系统将使 DLL 从使用其的进程分离。 为此，为 DLL 提供机会清理代表当前进程分配的资源。 在入口点函数返回之后，将从当前进程的地址空间移除库模板。  
  
 使用 `AfxLoadLibrary` 映射 DLL 模块。  
  
 请务必使用`AfxFreeLibrary`和`AfxLoadLibrary`(而不是 Win32 函数**FreeLibrary**和**LoadLibrary**) 如果你的应用程序使用多个线程。 使用`AfxLoadLibrary`和`AfxFreeLibrary`确保在 MFC 扩展 DLL 加载和卸载不会损坏全局 MFC 状态时执行的启动和关闭代码。  
  
### <a name="example"></a>示例  
 请参阅示例[AfxLoadLibrary](#afxloadlibrary)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdll_.h  
  
##  <a name="afxgetapp"></a>  AfxGetApp  
 返回此函数的指针可以用于访问应用程序的信息，例如主要的消息调度代码或最顶端窗口。  
  
```   
CWinApp* AFXAPI AfxGetApp(); 
```  
  
### <a name="return-value"></a>返回值  
 指向单`CWinApp`应用程序的对象。  
  
### <a name="remarks"></a>备注  
 如果此方法将返回 NULL，则可能指示，应用程序主窗口具有尚未完全初始化。 它也可能表明有问题。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxgetappname"></a>  AfxGetAppName  
 此函数返回的字符串可用于诊断消息或用作临时字符串名称的根。  
  
```   
LPCTSTR AFXAPI AfxGetAppName(); 
```  
  
### <a name="return-value"></a>返回值  
 包含应用程序名称的以 null 结尾的字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxgetinstancehandle"></a>  AfxGetInstanceHandle  
 此函数使您能够检索当前应用程序的实例句柄。  
  
```   
HINSTANCE  AFXAPI AfxGetInstanceHandle(); 
```  
  
### <a name="return-value"></a>返回值  
 当前应用程序实例的 `HINSTANCE`。 如果从某个与 MFC 的 USRDLL 版本链接的 DLL 中进行调用，则会返回该 DLL 的 `HINSTANCE`。  
  
### <a name="remarks"></a>备注  
 `AfxGetInstanceHandle` 始终返回可执行文件 (.EXE) 的 `HINSTANCE`，除非从某个与 MFC 的 USRDLL 版本链接的 DLL 中进行调用。 在这种情况下，它将返回该 DLL 的 `HINSTANCE`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxgetmainwnd"></a>  AfxGetMainWnd  
 如果你的应用程序是 OLE 服务器，调用此函数可检索指向而不是直接引用应用程序的活动主窗口的指针[m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd)应用程序对象的成员。  
  
```   
CWnd* AFXAPI AfxGetMainWnd(); 
```  
  
### <a name="return-value"></a>返回值  
 如果服务器具有在容器内处于就地活动状态的对象，并且此容器处于活动状态，此函数将返回一个指针，该指针指向包含就地活动文档的框架窗口对象。  
  
 如果没有在容器中处于就地活动状态的对象，或者您的应用程序不是一个 OLE 服务器，则此函数仅返回您的应用程序对象的 `m_pMainWnd`。  
  
 如果 `AfxGetMainWnd` 是从应用程序的主线程调用的，它将根据上述规则返回应用程序的主窗口。 如果该函数是从应用程序中的辅助线程调用的，它将返回与执行调用的线程关联的主窗口。  
  
### <a name="remarks"></a>备注  
 如果您的应用程序不是 OLE 服务器，调用此函数相当于直接引用应用程序对象的 `m_pMainWnd` 成员。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxgetperuserregistration"></a>  AfxGetPerUserRegistration  
 使用此函数可确定应用程序是否将注册表访问重定向**HKEY_CURRENT_USER** ( **HKCU**) 节点。  
  
```  
BOOL AFXAPI AfxGetPerUserRegistration();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 指示注册表信息将定向至**HKCU**节点;`FALSE`指示，则应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** ( **HKCR**)。  
  
### <a name="remarks"></a>备注  
 如果启用注册表重定向，框架将从访问重定向**HKCR**到**HKEY_CURRENT_USER\Software\Classes**。 仅 MFC 和 ATL 框架受重定向影响。  
  
 若要更改是否应用程序将注册表访问重定向，请使用[AfxSetPerUserRegistration](#afxsetperuserregistration)。  
  
### <a name="requirements"></a>要求  
  **标头**afxstat_.h    
  
##  <a name="afxgetresourcehandle"></a>  AfxGetResourceHandle  
 使用`HINSTANCE`应用程序的资源直接访问，例如，在对 Windows 函数的调用此函数返回的句柄**FindResource**。  
  
```   
extern HINSTANCE  AfxGetResourceHandle(); 
```  
  
### <a name="return-value"></a>返回值  
 `HINSTANCE`句柄的默认资源的应用程序加载的位置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxgetthread"></a>  AfxGetThread  
 调用此函数可获取指向的指针[CWinThread](../../mfc/reference/cwinthread-class.md)对象表示当前执行线程。  
  
```   
CWinThread* AfxGetThread(); 
```  
  
### <a name="return-value"></a>返回值  
 指向当前正在执行的线程;否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 必须从所需线程内部调用。  
  
> [!NOTE]
>  如果要移植 MFC 项目调用`AfxGetThread`Visual c + + 版本 4.2、 5.0 或 6.0 中，从`AfxGetThread`调用[AfxGetApp](#afxgetapp)如果未找到线程时。 在较新版本的编译器，`AfxGetThread`返回**NULL**如果未找到线程时。 如果需要应用程序线程，则必须调用 `AfxGetApp`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxinitrichedit"></a>  AfxInitRichEdit  
 调用此函数可初始化 rich edit 控件 （1.0 版） 应用程序。  
  
```   
BOOL AFXAPI AfxInitRichEdit(); 
```  
  
### <a name="remarks"></a>备注  
 提供此函数是为了向后兼容性。 新的应用程序应使用[AfxInitRichEdit2](#afxinitrichedit2)。  
  
 `AfxInitRichEdit` 加载 RICHED32。若要初始化 rich edit 控件的 1.0 版的 DLL。 若要使用版本 2.0 和 3.0 rich edit 控件，RICHED20。要加载的 DLL 要求。 这通过调用来实现[AfxInitRichEdit2](#afxinitrichedit2)。  
  
 若要更新到 2.0 版的现有 Visual c + + 应用程序中的格式文本编辑控件，打开。RC 文件作为文本，更改从"RICHEDIT"到"RichEdit20a"每个 rich edit 控件的类名称。 然后将对的调用`AfxInitRichEdit`与`AfxInitRichEdit2`。  
  
 此函数还初始化公共控件库中，如果库尚未已初始化的进程。 如果直接从 MFC 应用程序使用 rich edit 控件，则应调用此函数可确保 MFC 已正确初始化格式文本编辑控件运行时。 如果调用的 Create 方法[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)， [CRichEditView](../../mfc/reference/cricheditview-class.md)，或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，通常不需要调用此函数，但在某些情况下它可能被必需。  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxinitrichedit2"></a>  AfxInitRichEdit2  
 调用此函数为应用程序初始化 Rich Edit 控件（2.0 版和更高版本）。  
  
```   
BOOL AFXAPI AfxInitRichEdit2(); 
```  
  
### <a name="remarks"></a>备注  
 调用此函数以加载 RICHED20.DLL 并初始化 Rich Edit 控件 2.0 版。 如果调用的 Create 方法[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)， [CRichEditView](../../mfc/reference/cricheditview-class.md)，或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，通常不需要调用此函数，但在某些情况下它可能被必需。  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  

  ## <a name="afxisextendedframeclass"></a>  AfxIsExtendedFrameClass
确定给定窗口是否是扩展框架对象。  
   
### <a name="syntax"></a>语法    
```  
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );  
```
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 指向派生自 `CWnd`的对象的指针。  
   
### <a name="return-value"></a>返回值  
 `TRUE` 如果提供的窗口为扩展的框架对象;否则为`FALSE`。  
   
### <a name="remarks"></a>备注  
 如果 `TRUE` 从以下类之一派生，则此方法返回 `pWnd` ：  
  
-   `CFrameWndEx`  
  
-   `CMDIFrameWndEx`  
  
-   `COleIPFrameWndEx`  
  
-   `COleDocIPFrameWndEx`  
  
-   `CMDIChildWndEx`  
  
 此方法在你必须验证函数或方法参数是否是扩展框架窗口时很有用。  
   
### <a name="requirements"></a>要求  
 **标头：** afxpriv.h  
   
### <a name="see-also"></a>请参阅  
 [CWnd 类](cwnd-class.md)   
 [CFrameWndEx 类](cframewndex-class.md)   

## <a name="afxismfctoolbar"></a> AfxIsMFCToolBar
确定给定窗口是否为工具栏对象。  
   
### <a name="syntax"></a>语法    
```  
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);  
```
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 指向派生自 `CWnd`的对象的指针。  
   
### <a name="return-value"></a>返回值  
 如果提供的窗口为工具栏对象，则为 `TRUE`；否则为 `FALSE`。  
   
### <a name="remarks"></a>备注  
 如果 `TRUE` 派生自 `pWnd`，则此方法将返回 `CMFCToolBar`。 此方法在您必须验证函数或方法参数是否是 `CMFCToolBar` 对象时很有用。  
   
### <a name="requirements"></a>要求  
 **标头：** afxpriv.h  
   
### <a name="see-also"></a>请参阅  
 [CWnd 类](cwnd-class.md)   
 [CMFCToolBar 类](cmfctoolbar-class.md)

 
## <a name="afxkeyboardmanager"></a> AfxKeyboardManager
指向全局[键盘管理器](ckeyboardmanager-class.md)。  
   
### <a name="syntax"></a>语法    
```  
CKeyboardManager* afxKeyboardManager;  
```  
### <a name="requirements"></a>要求  
 **标头：** afxkeyboardmanager.h  
   
### <a name="see-also"></a>请参阅  

 [宏、 全局函数和全局变量](mfc-macros-and-globals.md)   
 [CKeyboardManager 类](ckeyboardmanager-class.md)


##  <a name="afxloadlibrary"></a>  AfxLoadLibrary  
 使用 `AfxLoadLibrary` 映射 DLL 模块。  
  
```   
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName); 
```  
  
### <a name="parameters"></a>参数  
 *lpszModuleName*  
 指向以 null 结尾的字符串，其中包含模块名称 (任一。DLL 或。EXE 文件）。 指定的名称是模块的文件名。  
  
 如果该字符串指定的路径，但该文件中指定的目录不存在，该函数将失败。  
  
 如果未指定路径和文件扩展名省略，默认扩展插件。追加 DLL。 但是，filename 字符串可不包含的尾随点字符 （.） 来指示模块名称包含任何扩展。 当未指定路径时，该函数搜索的文件按以下顺序：  
  
-   从中加载应用程序目录。  
  
-   当前目录中。  
  
- **Windows 95/98:** Windows 系统目录。 **Windows NT:** 32 位 Windows 系统目录。 此目录的名称是 SYSTEM32。  
  
- **仅 Windows NT:** 16 位 Windows 系统目录。 获取此目录的路径没有 Win32 函数，但它会搜索。 此目录的名称是系统。  
  
-   Windows 目录中。  
  
-   在 PATH 环境变量中列出的目录。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，返回值是模块的句柄。 如果函数失败，返回值为 NULL。  
  
### <a name="remarks"></a>备注  
 它将返回一个句柄，可在[GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212)若要获取的 DLL 函数的地址。 `AfxLoadLibrary` 此外可以用于映射其他可执行模块。  
  
 每个进程维护每个加载的库模块的引用计数。 此引用计数会递增每次`AfxLoadLibrary`称为，每次均递减`AfxFreeLibrary`调用。 当引用计数达到零时，将从调用进程的地址空间取消映射模块，并且句柄不再有效。  
  
 请务必使用`AfxLoadLibrary`和`AfxFreeLibrary`(而不是 Win32 函数**LoadLibrary**和**FreeLibrary**) 如果你的应用程序使用多个线程，并且它动态加载 MFC扩展 DLL。 使用`AfxLoadLibrary`和`AfxFreeLibrary`将确保在加载和卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。  
  
 使用`AfxLoadLibrary`在应用程序需要动态链接到 MFC; 的 DLL 版本的头文件`AfxLoadLibrary`，Afxdll_.h，才包含如果 MFC 链接到应用程序为 DLL。 这是设计使然因为你必须将链接到使用或创建 MFC 扩展 Dll 的 MFC 的 DLL 版本的不同而不同。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]  
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]  
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxdll_.h  
   
## <a name="afxmenutearoffmanager"></a> AfxMenuTearOffManager
指向全局[便捷菜单管理器](cmenutearoffmanager-class.md)。  
   
### <a name="syntax"></a>语法    
```  
CMenuTearOffManager* g_pTearOffMenuManager;  
```  
### <a name="requirements"></a>要求  
 **标头：** afxmenutearoffmanager.h  
   
### <a name="see-also"></a>请参阅     
 [CMenuTearOffManager 类](cmenutearoffmanager-class.md)
 
## <a name="afxmousemanager"></a>  AfxMouseManager
指向全局[鼠标管理器](cmousemanager-class.md)。  
   
### <a name="syntax"></a>语法  
  ```  
CMouseManager* afxMouseManager;  
```  
### <a name="requirements"></a>要求  
 **标头：** afxmousemanager.h  
   
### <a name="see-also"></a>请参阅  
 [CMouseManager 类](cmousemanager-class.md)
 

  
##  <a name="afxregisterclass"></a>  AfxRegisterClass  
 使用此函数在使用 MFC 的 DLL 中注册窗口类。  
  
```   
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass); 
```  
  
### <a name="parameters"></a>参数  
 *lpWndClass*  
 指向[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)结构，它包含有关要注册的窗口类信息。 此结构的详细信息，请参阅 Windows SDK。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果此类是已成功注册; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 如果使用此函数，则将在卸载 DLL 时自动取消注册类。  
  
 在非 DLL 版本中，`AfxRegisterClass`标识符定义为宏映射到 Windows 函数**RegisterClass**，因为在应用程序中注册的类会自动注销。 如果你使用`AfxRegisterClass`而不是**RegisterClass**，而无需在应用程序和 DLL 中进行更改，可以使用你的代码。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxregisterwndclass"></a>  AfxRegisterWndClass  
 允许您注册自己的窗口类。  
  
```  
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,  
    HCURSOR hCursor = 0,  
    HBRUSH hbrBackground = 0,  
    HICON hIcon = 0);  
```  
  
### <a name="parameters"></a>参数  
 *nClassStyle*  
 指定的 Windows 类样式或组合样式，通过使用位或创建 ( **&#124;**) 运算符，为窗口类。 有关类样式的列表，请参阅[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) Windows SDK 中的结构。 如果**NULL**，将设置的默认值，如下所示：  
  
-   将鼠标样式设置为**CS_DBLCLKS**，它会将双击消息到窗口过程当用户双击鼠标。  
  
-   将箭头光标样式设置为 Windows 标准**IDC_ARROW**。  
  
-   将背景画笔设置为**NULL**，因此窗口不会擦除其背景。  
  
-   将图标设置为标准的 Windows 徽标图标（飘扬的旗帜）。  
  
 `hCursor`  
 指定要在从窗口类创建的每个窗口中安装的光标资源的句柄。 如果你使用的默认**0**，您将获得标准**IDC_ARROW**光标。  
  
 *hbrBackground*  
 指定要在从窗口类创建的每个窗口中安装的画笔资源的句柄。 如果你使用的默认**0**，必须将**NULL**背景画笔，并且您的窗口将，默认情况下，不会擦除其背景处理时[WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055)。  
  
 `hIcon`  
 指定要在从窗口类创建的每个窗口中安装的图标资源的句柄。 如果你使用的默认**0**，您将获得标准的、 飘扬标志 Windows 徽标图标。  
  
### <a name="return-value"></a>返回值  
 包含类名的以 null 结尾的字符串。 你可以将传递到此类名称**创建**成员函数在`CWnd`或其他**CWnd-** 派生类，以创建窗口。 该名称由 Microsoft 基础类库生成。  
  
> [!NOTE]
>  返回值是指向静态缓冲区的指针。 若要保存此字符串，请将其分配到 `CString` 变量。  
  
### <a name="remarks"></a>备注  
 Microsoft 基础类库将自动为您注册若干标准窗口类。 如果要注册您自己的窗口类，则调用此函数。  
  
 由 `AfxRegisterWndClass` 为类注册的名称仅依赖于参数。 如果使用相同的参数调用 `AfxRegisterWndClass` 多次，它只会在首次调用时注册类。 如果使用相同的参数继续对 `AfxRegisterWndClass` 进行调用，则只会返回已注册的类名。  
  
 如果使用相同的参数为多个 CWnd 派生类调用 `AfxRegisterWndClass`，而不是为每个类获得单独的窗口类，则每个类都将共享同一窗口类。 这会导致问题，如果**CS_CLASSDC**使用类样式。 而不是多个**CS_CLASSDC**窗口类，你最终会得到一个**CS_CLASSDC**窗口类，并且使用类共享同一个域控制器的所有 c + + 窗口。 若要避免此问题，请调用[AfxRegisterClass](#afxregisterclass)以注册类。  
  
 请参阅技术说明[TN001： 窗口类注册](../../mfc/tn001-window-class-registration.md)有关详细信息窗口类注册和`AfxRegisterWndClass`函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxsetperuserregistration"></a>  AfxSetPerUserRegistration  
 设置是否应用程序将注册表访问重定向**HKEY_CURRENT_USER** ( **HKCU**) 节点。  
  
```  
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE` 指示注册表信息将定向至**HKCU**节点;`FALSE`指示，则应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** ( **HKCR**)。  
  
### <a name="remarks"></a>备注  

在 Windows Vista 中，应用程序访问通常使用注册表之前**HKEY_CLASSES_ROOT**节点。 但是，与 Windows Vista 或更高版本的操作系统，你必须运行应用程序在提升模式下写入**HKCR**。  
  
 此方法使你的应用程序能够读取和写入注册表，而无需通过将从注册表访问重定向在提升模式下运行**HKCR**到**HKCU**。 有关详细信息，请参阅[链接器属性页](../../ide/linker-property-pages.md)。  
  
 如果启用注册表重定向，框架将从访问重定向**HKCR**到**HKEY_CURRENT_USER\Software\Classes**。 仅 MFC 和 ATL 框架受重定向影响。  
  
 默认实现访问注册表项下的**HKCR**。  
  
### <a name="requirements"></a>要求  
  **标头**afxstat_.h    
  
##  <a name="afxsetresourcehandle"></a>  AfxSetResourceHandle  
 使用此函数可设置用来确定应用程序的默认资源的加载位置的 `HINSTANCE` 句柄。  
  
```  
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);  
```  
  
### <a name="parameters"></a>参数  
 `hInstResource`  
 从中加载应用程序的资源的 .EXE 或 .DLL 文件的实例或模块句柄。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  

## <a name="afxshellmanager"></a>  AfxShellManager
指向全局[shell 管理器](cshellmanager-class.md)。  
   
### <a name="syntax"></a>语法    
```  
CShellManager* afxShellManager;  
```  

### <a name="requirements"></a>要求  
 **标头：** afxshellmanager.h  
   
### <a name="see-also"></a>请参阅  
 [CShellManager 类](cshellmanager-class.md)
  
##  <a name="afxsocketinit"></a>  AfxSocketInit  
 在 `CWinApp::InitInstance` 重写中调用此函数可初始化 Windows 套接字。  
  
```  
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);  
```  
  
### <a name="parameters"></a>参数  
 `lpwsaData`  
 指向的指针[WSADATA](../../mfc/reference/wsadata-structure.md)结构。 如果 `lpwsaData` 不等于 `NULL`，则通过调用 `WSADATA` 填充 `WSAStartup` 结构的地址。 此函数还确保在应用程序终止前为您调用 `WSACleanup`。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。  
  
### <a name="requirements"></a>要求  
  **标头**afxsock.h  

## <a name="afxusertoolsmanager"></a>  AfxUserToolsManager
指向全局[用户工具管理器](cusertoolsmanager-class.md)。  
   
### <a name="syntax"></a>语法    
```  
CUserToolsManager* afxUserToolsManager;  
```  
   
### <a name="requirements"></a>要求  
 **标头：** afxusertoolsmanager.h  
   
### <a name="see-also"></a>请参阅  
 [CUserToolsManager 类](cusertoolsmanager-class.md)
 
  
##  <a name="afxwininit"></a>  AfxWinInit  
 调用此函数可通过 MFC 提供`WinMain`函数，作为的一部分[CWinApp](../../mfc/reference/cwinapp-class.md)基于 GUI 的应用程序，以初始化 MFC 的初始化。  
  
```  
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,  
    HINSTANCE hPrevInstance,  
    LPTSTR lpCmdLine,  
    int nCmdShow);  
```  
  
### <a name="parameters"></a>参数  
 `hInstance`  
 当前正在运行的模块的句柄。  
  
 *hPrevInstance*  
 应用程序的上一个实例句柄。 对于基于 Win32 的应用程序，此参数始终是**NULL**。  
  
 `lpCmdLine`  
 指向以 null 结尾的字符串指定命令行应用程序。  
  
 `nCmdShow`  
 指定将如何显示 GUI 应用程序的主窗口。  
  
### <a name="remarks"></a>备注  
 为控制台应用程序，其中不使用 MFC 提供`WinMain`函数，必须调用`AfxWinInit`直接以初始化 MFC。  
  
 如果调用`AfxWinInit`你自己，应声明的实例`CWinApp`类。 为控制台应用程序，你可以选择不派生您自己的类从`CWinApp`并改为使用的实例`CWinApp`直接。 这一技术是如果你决定将你的应用程序的所有功能的实现中相应**主要**。  
  
> [!NOTE]
>  当它为程序集创建激活上下文时，MFC 使用用户模块提供的清单资源。 激活上下文是在 `AfxWinInit` 中创建的。 有关详细信息，请参阅[MFC 模块状态中的激活上下文的支持](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]  

### <a name="requirements"></a>要求  
  **标头**afxwin.h  
    
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)   
 [CWinApp 类](../../mfc/reference/cwinapp-class.md)
