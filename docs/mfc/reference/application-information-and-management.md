---
title: 应用程序信息和管理
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: c1e742d3320dae4140cc4886c47d34dbe9b6071f
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178338"
---
# <a name="application-information-and-management"></a>应用程序信息和管理

当您编写的应用程序时，创建单个[CWinApp](../../mfc/reference/cwinapp-class.md)-派生的对象。 有时，可能想要获取有关从外部此对象的信息`CWinApp`-派生的对象。 或者，您可能需要与其他全局"mananger"对象的访问。

Microsoft 基础类库提供了以下全局函数，以帮助您完成这些任务：

### <a name="application-information-and-management-functions"></a>应用程序信息和管理功能

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|创建一个新线程。|
|[AfxContextMenuManager](#afxcontextmenumanager)|指向全局[上下文菜单管理器](ccontextmenumanager-class.md)。|
|[AfxEndThread](#afxendthread)|终止当前线程。|
|[AfxFindResourceHandle](#afxfindresourcehandle)|指导资源链并查找特定资源的资源 ID 和资源类型。 |
|[AfxFreeLibrary](#afxfreelibrary)|递减引用计数的已加载的动态链接库 (DLL) 模块中;当引用计数达到零时，该模块未映射。|
|[AfxGetApp](#afxgetapp)|返回一个指向应用程序的单个`CWinApp`对象。|
|[AfxGetAppName](#afxgetappname)|返回一个字符串，包含应用程序的名称。|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|返回表示此实例的应用程序的 HINSTANCE。|
|[AfxGetMainWnd](#afxgetmainwnd)|返回指向当前"main"窗口的非 OLE 应用程序或服务器应用程序的就地框架窗口的指针。|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|使用此函数可确定应用程序是否将注册表访问重定向**HKEY_CURRENT_USER** ( **HKCU**) 节点。|
|[AfxGetResourceHandle](#afxgetresourcehandle)|返回到应用程序的默认资源源 HINSTANCE。 用于直接访问应用程序的资源。|
|[AfxGetThread](#afxgetthread)|检索指向当前[CWinThread](../../mfc/reference/cwinthread-class.md)对象。|
|[AfxInitRichEdit](#afxinitrichedit)|初始化 1.0 rich edit 控件的应用程序的版本。|
|[AfxInitRichEdit2](#afxinitrichedit2)|初始化 2.0 及更高版本的 rich edit 控件的应用程序的版本。|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|确定给定窗口是否是扩展框架对象。|
|[AfxIsMFCToolBar](#afxismfctoolbar)|确定给定窗口是否为工具栏对象。|
|[AfxKeyboardManager](#afxkeyboardmanager)|指向全局[键盘管理器](ckeyboardmanager-class.md)。|
|[AfxLoadLibrary](#afxloadlibrary)|映射 DLL 模块，并返回一个句柄，可用于获取 DLL 函数的地址。|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|指向全局[tearoff 菜单管理器](cmenutearoffmanager-class.md)。|
|[AfxMouseManager](#afxmousemanager)|指向全局[鼠标管理器](cmousemanager-class.md)。|
|[AfxRegisterClass](#afxregisterclass)|在使用 MFC 的 DLL 中注册窗口类。|
|[AfxRegisterWndClass](#afxregisterwndclass)|注册来补充这些由 MFC 自动注册的 Windows 窗口类。|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|设置是否在应用程序将注册表访问重定向**HKEY_CURRENT_USER** ( **HKCU**) 节点。|
|[AfxSetResourceHandle](#afxsetresourcehandle)|设置的默认资源的应用程序的加载位置的 HINSTANCE 句柄。|
|[AfxShellManager](#afxshellmanager)|指向全局[shell 管理器](cshellmanager-class.md)。 |
|[AfxSocketInit](#afxsocketinit)|在中称为`CWinApp::InitInstance`替代，以便初始化 Windows 套接字。|
|[AfxUserToolsManager](#afxusertoolsmanager)|指向全局[用户工具管理器](cusertoolsmanager-class.md)。|
|[AfxWinInit](#afxwininit)|由 MFC 提供调用`WinMain`函数，作为的一部分[CWinApp](../../mfc/reference/cwinapp-class.md)的基于 GUI 的应用程序，以初始化 MFC 的初始化。 必须为使用 MFC 的控制台应用程序直接调用。|

##  <a name="afxbeginthread"></a>  AfxBeginThread

调用此函数可创建一个新线程。

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

*pfnThreadProc*<br/>
指向工作线程的控件函数。 不能为 NULL。 必须按如下所示声明此函数：

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*<br/>
对象的 RUNTIME_CLASS 派生自[CWinThread](../../mfc/reference/cwinthread-class.md)。

*pParam*<br/>
参数要传递到控制函数的参数中的函数声明中所示*pfnThreadProc*。

*nPriority*<br/>
所需的线程优先级。 有关完整列表和可用优先级的说明，请参阅[SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) Windows SDK 中。

*nStackSize*<br/>
以字节为单位的新线程的堆栈中指定的大小。 如果为 0，堆栈大小默认为同一个与创建线程堆栈大小。

*dwCreateFlags*<br/>
指定一个额外的标记的线程的创建操作进行控制。 此标志可以包含两个值之一：

- CREATE_SUSPENDED 开始挂起计数为 1 的线程。 如果你想要初始化的任何成员数据，请使用 CREATE_SUSPENDED`CWinThread`对象，例如[m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete)或派生类中之前在线程开始运行, 的任何成员。 你的初始化完成后，使用[cwinthread:: Resumethread](../../mfc/reference/cwinthread-class.md#resumethread)开始运行的线程。 在线程不会执行直到`CWinThread::ResumeThread`调用。

- **0**创建后立即启动线程。

*lpSecurityAttrs*<br/>
指向[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)结构，它指定线程的安全属性。 如果为 NULL，则将使用与创建线程相同的安全属性。 此结构的详细信息，请参阅 Windows SDK。

### <a name="return-value"></a>返回值

指向新创建的线程对象，或者如果发生故障，则为 NULL 指针。

### <a name="remarks"></a>备注

第一种形式`AfxBeginThread`创建工作线程。 第二个窗体作为用户界面线程或工作线程创建可以为提供服务的线程。

`AfxBeginThread` 创建一个新`CWinThread`对象，调用其[CreateThread](../../mfc/reference/cwinthread-class.md#createthread)函数开始执行线程，并将指针返回到线程。 整个过程进行检查以确保所有对象都都已解除分配正确应创建的任何部分出现故障。 若要结束该线程，请调用[AfxEndThread](#afxendthread)从中的线程或从工作线程控制函数返回。

多线程处理必须启用该应用程序。否则，此函数将失败。 有关启用多线程处理的详细信息，请参阅[/MD、 /MT、 /LD （使用运行时库）](../../build/reference/md-mt-ld-use-run-time-library.md)下*Visual c + + 编译器选项*。

有关详细信息`AfxBeginThread`，请参阅文章[多线程处理：创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)和[多线程处理：创建用户界面线程](../../parallel/multithreading-creating-user-interface-threads.md)。

### <a name="example"></a>示例

有关示例，请参阅[csocket:: Attach](../../mfc/reference/csocket-class.md#attach)。

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

*nExitCode*<br/>
指定线程的退出代码。

*bDelete*<br/>
从内存中删除线程对象。

### <a name="remarks"></a>备注

必须从调用的线程终止内。

有关详细信息`AfxEndThread`，请参阅文章[多线程处理：终止线程](../../parallel/multithreading-terminating-threads.md)。

### <a name="requirements"></a>要求

  **标头**afxwin.h

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
使用 `AfxFindResourceHandle` 处理资源链并按资源 ID 和资源类型找到特定资源。

### <a name="syntax"></a>语法

```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>参数

*lpszName*<br/>
指向包含资源 ID 的字符串的指针。
*lpszType*<br/>
指向资源的类型的指针。 资源类型的列表，请参阅[FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) Windows SDK 中。

### <a name="return-value"></a>返回值

包含资源的模块的句柄。

### <a name="remarks"></a>备注

`AfxFindResourceHandle` 查找特定资源并返回包含该资源的模块的句柄。 该资源可能在任何 MFC 扩展 DLL 已加载。 `AfxFindResourceHandle` 将告知您哪个 DLL 包含该资源。

模块将按以下顺序进行搜索：

1. 主模块 （如果它是 MFC 扩展 DLL）。

1. 非系统模块。

1. 语言特定的模块。

1. 主模块（如果它是系统 DLL）。

1. 系统模块。

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

*hInstLib*<br/>
已加载库模块的句柄。 [AfxLoadLibrary](#afxloadlibrary)返回此句柄。

### <a name="return-value"></a>返回值

如果函数成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

`AfxFreeLibrary` 减少已加载动态链接库 (DLL) 模块的引用计数。 当引用计数达到零时，将从调用进程的地址空间取消映射模块，并且句柄不再有效。 每次调用 `AfxLoadLibrary` 时都会增加此引用计数。

在取消映射库模块之前，系统将使 DLL 从使用其的进程分离。 为此，为 DLL 提供机会清理代表当前进程分配的资源。 在入口点函数返回之后，将从当前进程的地址空间移除库模板。

使用 `AfxLoadLibrary` 映射 DLL 模块。

请务必使用`AfxFreeLibrary`并`AfxLoadLibrary`(而不是 Win32 函数`FreeLibrary`和`LoadLibrary`) 如果你的应用程序使用多个线程。 使用`AfxLoadLibrary`和`AfxFreeLibrary`确保 MFC 扩展 DLL 加载和卸载不会损坏全局 MFC 状态时执行的启动和关闭代码。

### <a name="example"></a>示例

有关示例，请参阅[AfxLoadLibrary](#afxloadlibrary)。

### <a name="requirements"></a>要求

  **标头**afxdll_.h

##  <a name="afxgetapp"></a>  AfxGetApp

此函数返回的指针可用于访问应用程序信息，例如主消息调度代码或最顶层窗口。

```
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>返回值

指向单个`CWinApp`应用程序的对象。

### <a name="remarks"></a>备注

如果此方法返回 NULL，则可能表示，应用程序主窗口具有尚未完全初始化。 它还可能表示存在问题。

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

与当前实例的应用程序的 HINSTANCE。 如果从内部与 MFC 的 USRDLL 版本链接的 DLL 调用，则返回对 DLL HINSTANCE。

### <a name="remarks"></a>备注

`AfxGetInstanceHandle` 始终返回可执行文件的 HINSTANCE (。EXE) 除非调用内，否则与 MFC 的 USRDLL 版本链接 DLL。 在这种情况下，它返回 HINSTANCE 到 DLL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin.h

##  <a name="afxgetmainwnd"></a>  AfxGetMainWnd

如果你的应用程序是 OLE 服务器，调用此函数可检索到的应用程序而不是直接引用的活动主窗口的指针[m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd)应用程序对象的成员。

```
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>返回值

如果服务器具有在容器内处于就地活动状态的对象，并且此容器处于活动状态，此函数将返回一个指针，该指针指向包含就地活动文档的框架窗口对象。

如果没有为容器内的处于就地活动状态的对象，或者你的应用程序不是 OLE 服务器，此函数仅返回*m_pMainWnd*的应用程序对象。

如果 `AfxGetMainWnd` 是从应用程序的主线程调用的，它将根据上述规则返回应用程序的主窗口。 如果该函数是从应用程序中的辅助线程调用的，它将返回与执行调用的线程关联的主窗口。

### <a name="remarks"></a>备注

如果你的应用程序不是 OLE 服务器，则调用此函数等同于直接引用*m_pMainWnd*应用程序对象的成员。

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

TRUE 表示注册表信息将定向到的 HKCU 节点;FALSE 表示应用程序将注册表信息写入到默认的节点。 默认的节点是**HKEY_CLASSES_ROOT** ( **HKCR**)。

### <a name="remarks"></a>备注

如果启用注册表重定向，则框架会将访问权限**HKCR**到**HKEY_CURRENT_USER\Software\Classes**。 仅 MFC 和 ATL 框架受重定向影响。

若要更改是否在应用程序将重定向注册表访问权限，请使用[AfxSetPerUserRegistration](#afxsetperuserregistration)。

### <a name="requirements"></a>要求

  **标头**afxstat_.h

##  <a name="afxgetresourcehandle"></a>  AfxGetResourceHandle

使用 HINSTANCE 处理返回的此函数可直接访问应用程序的资源，在调用 Windows 函数`FindResource`。

```
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>返回值

默认资源的应用程序的加载位置 HINSTANCE 句柄。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin.h

##  <a name="afxgetthread"></a>  AfxGetThread

调用此函数可获取一个指向[CWinThread](../../mfc/reference/cwinthread-class.md)对象，表示当前正在执行的线程。

```
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>返回值

指向当前正在执行的线程;否则为，为 NULL。

### <a name="remarks"></a>备注

必须从所需线程内部调用。

> [!NOTE]
>  如果要将迁移 MFC 项目调用`AfxGetThread`Visual c + + 版本 4.2、 5.0 或 6.0 中，从`AfxGetThread`调用[AfxGetApp](#afxgetapp)如果未找到线程时。 在较新版本的编译器，`AfxGetThread`如果未找到线程时，则返回 NULL。 如果需要应用程序线程，则必须调用 `AfxGetApp`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin.h

##  <a name="afxinitrichedit"></a>  AfxInitRichEdit

调用此函数可初始化 rich edit 控件 （版本 1.0） 的应用程序。

```
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>备注

提供此函数是为了向后兼容性。 新的应用程序应使用[AfxInitRichEdit2](#afxinitrichedit2)。

`AfxInitRichEdit` 加载 RICHED32。若要初始化 rich edit 控件的 1.0 版的 DLL。 若要使用版本 2.0 和 3.0 rich edit 控件，RICHED20。需要加载 DLL。 这通过调用来实现[AfxInitRichEdit2](#afxinitrichedit2)。

若要更新到版本 2.0 的现有 Visual c + + 应用程序中的格式文本编辑控件，请打开。RC 文件作为文本，更改每个格式文本编辑控件从"RICHEDIT"到"RichEdit20a"的类名。 然后将为调用`AfxInitRichEdit`与`AfxInitRichEdit2`。

此函数还可以初始化公共控件库，如果库尚未初始化的进程。 如果你直接从 MFC 应用程序使用 rich edit 控件，则应调用此函数可确保 MFC 程序正确初始化格式文本编辑控件运行时。 如果调用的 Create 方法[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)， [CRichEditView](../../mfc/reference/cricheditview-class.md)，或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，通常无需调用此函数，但在某些情况下可能会必需。

### <a name="requirements"></a>要求

  **标头**afxwin.h

##  <a name="afxinitrichedit2"></a>  AfxInitRichEdit2

调用此函数为应用程序初始化 Rich Edit 控件（2.0 版和更高版本）。

```
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>备注

调用此函数以加载 RICHED20.DLL 并初始化 Rich Edit 控件 2.0 版。 如果调用的 Create 方法[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)， [CRichEditView](../../mfc/reference/cricheditview-class.md)，或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，通常无需调用此函数，但在某些情况下可能会必需。

### <a name="requirements"></a>要求

  **标头**afxwin.h

  ## <a name="afxisextendedframeclass"></a>  AfxIsExtendedFrameClass
确定给定窗口是否是扩展框架对象。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>参数

*pWnd*<br/>
[in]指向派生自的对象的指针`CWnd`。

### <a name="return-value"></a>返回值

如果提供的窗口是扩展的框架对象; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法返回 TRUE，如果*pWnd*派生以下类之一：

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

此方法在你必须验证函数或方法参数是否是扩展框架窗口时很有用。

### <a name="requirements"></a>要求

**标头：** afxpriv.h

### <a name="see-also"></a>请参阅

[CWnd 类](cwnd-class.md)<br/>
[CFrameWndEx 类](cframewndex-class.md)

## <a name="afxismfctoolbar"></a> AfxIsMFCToolBar

确定给定窗口是否为工具栏对象。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
[in]指向派生自的对象的指针`CWnd`。

### <a name="return-value"></a>返回值

如果提供的窗口为工具栏对象; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法返回`TRUE`如果*pWnd*派生自`CMFCToolBar`。 此方法在您必须验证函数或方法参数是否是 `CMFCToolBar` 对象时很有用。

### <a name="requirements"></a>要求

**标头：** afxpriv.h

### <a name="see-also"></a>请参阅

[CWnd 类](cwnd-class.md)<br/>
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

[宏、 全局函数和全局变量](mfc-macros-and-globals.md)<br/>
[CKeyboardManager 类](ckeyboardmanager-class.md)

##  <a name="afxloadlibrary"></a>  AfxLoadLibrary

使用 `AfxLoadLibrary` 映射 DLL 模块。

```
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>参数

*lpszModuleName*<br/>
指向以 null 结尾的字符串，其中包含的模块的名称 (任一。DLL 或。EXE 文件）。 指定的名称是该模块的文件名。

如果该字符串指定的路径，但该文件不存在指定的目录中，函数将失败。

如果未指定路径和文件扩展名省略，默认扩展插件。追加 DLL。 但是，文件名字符串可以不包含尾随点字符 （.） 来指示模块名称包含任何扩展。 时未指定路径，该函数搜索的文件按以下顺序：

- 加载应用程序目录。

- 当前目录中。

- **Windows 95/98:** Windows 系统目录。 **Windows NT:** 32 位 Windows 系统目录。 此目录的名称是 SYSTEM32。

- **Windows NT:** 16 位 Windows 系统目录。 获取此目录的路径没有 Win32 函数，但它会搜索。 此目录的名称是系统。

- Windows 目录中。

- PATH 环境变量中列出的目录。

### <a name="return-value"></a>返回值

如果函数成功，返回值是模块的句柄。 如果函数失败，返回值为 NULL。

### <a name="remarks"></a>备注

它将返回一个句柄，可在[GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress)获取 DLL 函数的地址。 `AfxLoadLibrary` 此外可以用于映射其他可执行模块。

每个进程维护每个已加载的库模块引用的计数。 此引用计数会在每次递增`AfxLoadLibrary`称为，将减少每次`AfxFreeLibrary`调用。 当引用计数达到零时，将从调用进程的地址空间取消映射模块，并且句柄不再有效。

请务必使用`AfxLoadLibrary`并`AfxFreeLibrary`(而不是 Win32 函数`LoadLibrary`和`FreeLibrary`) 如果你的应用程序使用多个线程和动态加载的 MFC 扩展 DLL。 使用`AfxLoadLibrary`和`AfxFreeLibrary`也可确保在加载和卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

使用`AfxLoadLibrary`在应用程序要求您动态链接到 MFC; 的 DLL 版本的标头文件`AfxLoadLibrary`，Afxdll_.h，才包括当 MFC 已链接到 dll 的应用程序。 这是特意设计因为您必须链接到使用或创建 MFC 扩展 Dll 的 MFC 的 DLL 版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>要求

  **标头**afxdll_.h

## <a name="afxmenutearoffmanager"></a> AfxMenuTearOffManager

指向全局[tearoff 菜单管理器](cmenutearoffmanager-class.md)。

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

*lpWndClass*<br/>
指向[WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa)结构，它包含有关要注册的窗口类信息。 此结构的详细信息，请参阅 Windows SDK。

### <a name="return-value"></a>返回值

如果已成功注册的类; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

如果使用此函数，则将在卸载 DLL 时自动取消注册类。

在非 DLL 版本中，`AfxRegisterClass`标识符定义为宏映射到 Windows 函数`RegisterClass`，因为应用程序中注册的类会自动注销。 如果您使用`AfxRegisterClass`而不是`RegisterClass`，可以使用你的代码而无需更改应用程序中并在 DLL 中。

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

*nClassStyle*<br/>
指定的 Windows 类样式或样式，使用按位或创建的组合 ( **&#124;**) 运算符，窗口类。 有关类样式的列表，请参阅[WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) Windows SDK 中的结构。 如果为 NULL，则将按如下所示设置默认值：

- 将鼠标样式设置为 CS_DBLCLKS，它会将双击消息到窗口过程当用户双击鼠标。

- 设置为 Windows 标准 IDC_ARROW 的箭头光标样式。

- 设置为 NULL，背景画笔，因此窗口不会擦除其背景。

- 将图标设置为标准的 Windows 徽标图标（飘扬的旗帜）。

*hCursor*<br/>
指定要在从窗口类创建的每个窗口中安装的光标资源的句柄。 如果使用默认值为**0**，将显示标准的 IDC_ARROW 光标。

*hbrBackground*<br/>
指定要在从窗口类创建的每个窗口中安装的画笔资源的句柄。 如果使用默认值为**0**，将拥有 NULL 背景画笔，并且您的窗口，默认情况下，不会擦除其背景处理时[WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd)。

*hIcon*<br/>
指定要在从窗口类创建的每个窗口中安装的图标资源的句柄。 如果使用默认值为**0**，您将获得标准的飘扬标志 Windows 徽标图标。

### <a name="return-value"></a>返回值

包含类名的以 null 结尾的字符串。 可以将传递到此类名`Create`中的成员函数`CWnd`或其他**CWnd-** 派生类，以创建窗口。 该名称由 Microsoft 基础类库生成。

> [!NOTE]
>  返回值是指向静态缓冲区的指针。 若要保存此字符串，请将其分配到 `CString` 变量。

### <a name="remarks"></a>备注

Microsoft 基础类库将自动为您注册若干标准窗口类。 如果要注册您自己的窗口类，则调用此函数。

由 `AfxRegisterWndClass` 为类注册的名称仅依赖于参数。 如果使用相同的参数调用 `AfxRegisterWndClass` 多次，它只会在首次调用时注册类。 如果使用相同的参数继续对 `AfxRegisterWndClass` 进行调用，则只会返回已注册的类名。

如果使用相同的参数为多个 CWnd 派生类调用 `AfxRegisterWndClass`，而不是为每个类获得单独的窗口类，则每个类都将共享同一窗口类。 如果使用 CS_CLASSDC 类样式，这会导致问题。 而不是多个 CS_CLASSDC 窗口类，您最终得到一个 CS_CLASSDC 窗口类，并使用该类共享同一个域控制器的所有 c + + 窗口。 若要避免此问题，请调用[AfxRegisterClass](#afxregisterclass)以注册类。

请参阅技术说明[TN001:窗口类注册](../../mfc/tn001-window-class-registration.md)有关详细信息窗口类注册和`AfxRegisterWndClass`函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin.h

##  <a name="afxsetperuserregistration"></a>  AfxSetPerUserRegistration

设置是否在应用程序将注册表访问重定向**HKEY_CURRENT_USER** ( **HKCU**) 节点。

```
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
[in]TRUE 表示注册表信息将定向到的 HKCU 节点;FALSE 表示应用程序将注册表信息写入到默认的节点。 默认的节点是**HKEY_CLASSES_ROOT** ( **HKCR**)。

### <a name="remarks"></a>备注

Windows Vista，访问注册表，通常可用的应用程序之前**HKEY_CLASSES_ROOT**节点。 但是，与 Windows Vista 或更高版本的操作系统，必须在提升模式下将 HKCR 写入运行应用程序。

此方法使应用程序可以读取和写入注册表，而无需通过将从 HKCR 到 HKCU 注册表访问重定向在提升模式下运行。 有关详细信息，请参阅 [Linker Property Pages](../../ide/linker-property-pages.md)。

如果启用注册表重定向，则框架会将访问从到的 HKCR **HKEY_CURRENT_USER\Software\Classes**。 仅 MFC 和 ATL 框架受重定向影响。

默认实现访问 HKCR 下的注册表。

### <a name="requirements"></a>要求

  **标头**afxstat_.h

##  <a name="afxsetresourcehandle"></a>  AfxSetResourceHandle

使用此函数设置确定的默认资源的应用程序的加载位置的 HINSTANCE 句柄。

```
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>参数

*hInstResource*<br/>
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

*lpwsaData*<br/>
一个指向[WSADATA](/windows/desktop/api/winsock2/ns-winsock2-wsadata)结构。 如果*lpwsaData*不等于 NULL，然后的地址`WSADATA`结构填充通过调用`WSAStartup`。 此函数还确保在应用程序终止前为您调用 `WSACleanup`。

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

MFC 提供调用此函数`WinMain`函数，作为的一部分[CWinApp](../../mfc/reference/cwinapp-class.md)的基于 GUI 的应用程序，以初始化 MFC 的初始化。

```
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>参数

*hInstance*<br/>
当前正在运行的模块的句柄。

*hPrevInstance*<br/>
应用程序的前一个实例句柄。 为基于 Win32 的应用程序，此参数始终是**NULL**。

*lpCmdLine*<br/>
指向一个以 null 结尾的字符串，指定命令行应用程序。

*nCmdShow*<br/>
指定将如何显示 GUI 应用程序的主窗口。

### <a name="remarks"></a>备注

为控制台应用程序，其中不使用 MFC 提供`WinMain`函数，必须调用`AfxWinInit`直接以初始化 MFC。

如果您调用`AfxWinInit`自己，应声明的实例`CWinApp`类。 为控制台应用程序，您可能选择不派生您自己的类从`CWinApp`改为使用的实例和`CWinApp`直接。 此技术是如果决定将您的应用程序的所有功能的实现中相应**主要**。

> [!NOTE]
>  当它创建激活上下文的程序集时，MFC 使用用户模块提供的清单资源。 激活上下文是在 `AfxWinInit` 中创建的。 有关详细信息，请参阅[支持 MFC 模块状态中的激活上下文](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CWinApp 类](../../mfc/reference/cwinapp-class.md)
