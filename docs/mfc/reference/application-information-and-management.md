---
title: 应用程序信息和管理
description: 引用 Microsoft 基础类库（MFC）应用程序信息和管理功能。
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: c372f43bc5184349e70f29b6c0ae6a490f2102ed
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854538"
---
# <a name="application-information-and-management"></a>应用程序信息和管理

编写应用程序时，将创建单个[CWinApp](../../mfc/reference/cwinapp-class.md)派生对象。 有时，你可能想要从 `CWinApp`派生的对象之外获取有关此对象的信息。 或者你可能需要访问其他全局 "管理器" 对象。

Microsoft 基础类库提供了以下全局函数来帮助你完成这些任务：

## <a name="application-information-and-management-functions"></a>应用程序信息和管理功能

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|创建新线程。|
|[AfxContextMenuManager](#afxcontextmenumanager)|指向全局[上下文菜单管理器](ccontextmenumanager-class.md)的指针。|
|[AfxEndThread](#afxendthread)|终止当前线程。|
|[AfxFindResourceHandle](#afxfindresourcehandle)|遍历资源链，并按资源 ID 和资源类型查找特定资源。 |
|[AfxFreeLibrary](#afxfreelibrary)|递减已加载的动态链接库（DLL）模块的引用计数。 当引用计数达到零时，模块将被取消映射。|
|[AfxGetApp](#afxgetapp)|返回一个指向应用程序的单个 `CWinApp` 对象的指针。|
|[AfxGetAppName](#afxgetappname)|返回一个字符串，其中包含应用程序的名称。|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|返回表示应用程序的此实例的 HINSTANCE。|
|[AfxGetMainWnd](#afxgetmainwnd)|返回指向非 OLE 应用程序的当前 "主" 窗口或服务器应用程序的就地框架窗口的指针。|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|使用此函数可确定应用程序是否将注册表访问重定向到**HKEY_CURRENT_USER** （**HKCU**）节点。|
|[AfxGetResourceHandle](#afxgetresourcehandle)|将 HINSTANCE 返回到应用程序的默认资源的源。 使用直接访问应用程序的资源。|
|[AfxGetThread](#afxgetthread)|检索指向当前[CWinThread](../../mfc/reference/cwinthread-class.md)对象的指针。|
|[AfxInitRichEdit](#afxinitrichedit)|初始化应用程序的版本1.0 格式编辑控件。|
|[AfxInitRichEdit2](#afxinitrichedit2)|初始化应用程序的版本2.0 和更高版本的编辑控件。|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|确定给定窗口是否是扩展框架对象。|
|[AfxIsMFCToolBar](#afxismfctoolbar)|确定给定窗口是否为工具栏对象。|
|[AfxKeyboardManager](#afxkeyboardmanager)|指向全局[键盘管理器](ckeyboardmanager-class.md)的指针。|
|[AfxLoadLibrary](#afxloadlibrary)|映射 DLL 模块并返回一个句柄，该句柄可用于获取 DLL 函数的地址。|
|[AfxLoadLibraryEx](#afxloadlibraryex)|使用指定的选项映射 DLL 模块，并返回一个可用于获取 DLL 函数地址的句柄。|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|指向全局[撕开菜单管理器](cmenutearoffmanager-class.md)的指针。|
|[AfxMouseManager](#afxmousemanager)|指向全局[鼠标管理器](cmousemanager-class.md)的指针。|
|[AfxRegisterClass](#afxregisterclass)|在使用 MFC 的 DLL 中注册一个窗口类。|
|[AfxRegisterWndClass](#afxregisterwndclass)|注册 Windows 窗口类以对 MFC 自动注册的窗口类进行补充。|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|设置应用程序是否将注册表访问重定向到**HKEY_CURRENT_USER** （**HKCU**）节点。|
|[AfxSetResourceHandle](#afxsetresourcehandle)|设置 HINSTANCE 句柄，其中加载了应用程序的默认资源。|
|[AfxShellManager](#afxshellmanager)|指向全局[shell 管理器](cshellmanager-class.md)的指针。 |
|[AfxSocketInit](#afxsocketinit)|在 `CWinApp::InitInstance` 重写中调用以初始化 Windows 套接字。|
|[AfxUserToolsManager](#afxusertoolsmanager)|指向全局[用户工具管理器](cusertoolsmanager-class.md)的指针。|
|[AfxWinInit](#afxwininit)|由 MFC 提供的 `WinMain` 函数调用，作为基于 GUI 的应用程序的[CWinApp](../../mfc/reference/cwinapp-class.md)初始化的一部分，用于初始化 MFC。 必须直接为使用 MFC 的控制台应用程序调用。|

## <a name="afxbeginthread"></a>AfxBeginThread

调用此函数可创建新线程。

```cpp
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

### <a name="parameters"></a>parameters

*pfnThreadProc*\
指向工作线程的控制函数。 指针不能为 NULL。 必须按如下所示声明此函数：

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*\
派生自[CWinThread](../../mfc/reference/cwinthread-class.md)的对象的 RUNTIME_CLASS。

*pParam*\
要传递到控制函数的参数。

*nPriority*\
要为线程设置的优先级。 有关可用优先级的完整列表和说明，请参阅 Windows SDK 中的[参见 setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

*nStackSize*\
指定新线程堆栈的大小（以字节为单位）。 如果为0，则堆栈大小默认为与创建线程相同的堆栈大小。

*dwCreateFlags*\
指定控制线程创建的其他标志。 此标志可以包含以下两个值之一：

- CREATE_SUSPENDED 启动线程，该线程的挂起计数为1。 如果要在线程开始运行之前初始化 `CWinThread` 对象的任何成员数据，如[m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete)或派生类的任何成员，请使用 CREATE_SUSPENDED。 初始化完成后，请使用[CWinThread：： ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread)启动运行的线程。 调用 `CWinThread::ResumeThread` 之前，该线程不会执行。

- **0**创建后立即启动线程。

*lpSecurityAttrs*\
指向指定线程的安全属性的[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))结构。 如果为 NULL，则使用与创建线程相同的安全特性。 有关此结构的详细信息，请参阅 Windows SDK。

### <a name="return-value"></a>返回值

指向新创建的线程对象的指针; 如果发生失败，则为 NULL。

### <a name="remarks"></a>备注

第一种形式的 `AfxBeginThread` 创建工作线程。 第二个窗体创建一个线程，该线程可用作用户界面线程或工作线程。

`AfxBeginThread` 创建新的 `CWinThread` 对象，调用其[CreateThread](../../mfc/reference/cwinthread-class.md#createthread)函数以开始执行线程，并返回指向该线程的指针。 在整个过程中进行检查，以确保在创建过程中的任何部分都不会正确释放所有对象。 若要结束线程，请从线程内调用[AfxEndThread](#afxendthread) ，或从工作线程的控制函数返回。

应用程序必须启用多线程处理;否则，此函数将失败。 有关启用多线程处理的详细信息，请参阅[/md、/mt、/ld （使用运行时库）](../../build/reference/md-mt-ld-use-run-time-library.md)。

有关 `AfxBeginThread`的详细信息，请参阅文章[多线程处理：创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)和[多线程处理：创建用户界面线程](../../parallel/multithreading-creating-user-interface-threads.md)。

### <a name="example"></a>示例

请参阅[CSocket：： Attach](../../mfc/reference/csocket-class.md#attach)的示例。

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxcontextmenumanager"></a>AfxContextMenuManager

指向全局[上下文菜单管理器](ccontextmenumanager-class.md)的指针。

### <a name="syntax"></a>语法

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>要求

**标头：** afxcontextmenumanager

## <a name="afxendthread"></a>AfxEndThread

调用此函数可终止当前正在执行的线程。

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>parameters

*nExitCode*\
指定线程的退出代码。

*bDelete*\
从内存中删除线程对象。

### <a name="remarks"></a>备注

必须从要终止的线程中调用。

有关 `AfxEndThread`的详细信息，请参阅文章[多线程处理：终止线程](../../parallel/multithreading-terminating-threads.md)。

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle

使用 `AfxFindResourceHandle` 处理资源链并按资源 ID 和资源类型找到特定资源。

### <a name="syntax"></a>语法

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>parameters

*lpszName*\
指向包含资源 ID 的字符串的指针。
*lpszType*\
指向资源的类型的指针。 有关资源类型的列表，请参阅 Windows SDK 中的[system.windows.frameworkelement.findresource](/windows/win32/api/winbase/nf-winbase-findresourcea) 。

### <a name="return-value"></a>返回值

包含资源的模块的句柄。

### <a name="remarks"></a>备注

`AfxFindResourceHandle` 查找特定资源，并返回包含该资源的模块的句柄。 资源可能位于加载的任何 MFC 扩展 DLL 中。 `AfxFindResourceHandle` 将告知您哪个 DLL 包含该资源。

模块将按以下顺序进行搜索：

1. 主模块（如果它是 MFC 扩展 DLL）。

1. 非系统模块。

1. 语言特定的模块。

1. 主模块（如果它是系统 DLL）。

1. 系统模块。

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="afxfreelibrary"></a>AfxFreeLibrary

`AfxFreeLibrary` 和 `AfxLoadLibrary` 用于维护每个已加载库模块的引用计数。

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>parameters

*hInstLib*\
已加载库模块的句柄。 [AfxLoadLibrary](#afxloadlibrary)返回此句柄。

### <a name="return-value"></a>返回值

如果函数成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

`AfxFreeLibrary` 减少已加载动态链接库 (DLL) 模块的引用计数。 当引用计数达到零时，将从调用进程的地址空间取消映射模块，并且句柄不再有效。 每次调用 `AfxLoadLibrary` 时都会增加此引用计数。

在取消映射库模块之前，系统将使 DLL 从使用其的进程分离。 这样做会使 DLL 有机会清理为当前进程分配的资源。 在入口点函数返回之后，将从当前进程的地址空间移除库模板。

使用 `AfxLoadLibrary` 映射 DLL 模块。

如果你的应用程序使用多个线程，请确保使用 `AfxFreeLibrary` 和 `AfxLoadLibrary` （而不是 Win32 函数 `FreeLibrary` 和 `LoadLibrary`）。 使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` 确保加载并卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

### <a name="example"></a>示例

请参阅[AfxLoadLibrary](#afxloadlibrary)的示例。

### <a name="requirements"></a>要求

  **标头**afxdll_。h

## <a name="afxgetapp"></a>AfxGetApp

此函数返回的指针可用于访问应用程序信息，如主消息调度代码或最顶部的窗口。

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>返回值

指向应用程序的单个 `CWinApp` 对象的指针。

### <a name="remarks"></a>备注

如果此方法返回 NULL，则可能表示应用程序主窗口尚未完全初始化。 它也可能表示存在问题。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxgetappname"></a>AfxGetAppName

返回的字符串可用于诊断消息，或用作临时字符串名称的根。

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>返回值

包含应用程序名称的以 null 结尾的字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxgetinstancehandle"></a>AfxGetInstanceHandle

此函数使您能够检索当前应用程序的实例句柄。

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>返回值

应用程序的当前实例的 HINSTANCE。 如果从使用 MFC 的 USRDLL 版本链接的 DLL 中进行调用，则会返回 DLL 的 HINSTANCE。

### <a name="remarks"></a>备注

`AfxGetInstanceHandle` 总是返回可执行文件的 HINSTANCE （。EXE），除非它是从与 MFC 的 USRDLL 版本链接的 DLL 中调用的。 在这种情况下，它会将 HINSTANCE 返回到 DLL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxgetmainwnd"></a>AfxGetMainWnd

如果你的应用程序是 OLE 服务器，请调用此函数来检索指向应用程序活动主窗口的指针。 使用此结果而不是直接引用应用程序对象的[m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd)成员。

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>返回值

如果服务器具有一个在活动容器内就地活动的对象，则返回一个指向包含就地活动文档的框架窗口对象的指针。

如果容器中没有就地活动的对象，或者您的应用程序不是 OLE 服务器，则此函数将返回您的应用程序对象的*m_pMainWnd* 。

如果 `AfxGetMainWnd` 是从应用程序的主线程调用的，它将根据上述规则返回应用程序的主窗口。 如果该函数是从应用程序中的辅助线程调用的，它将返回与执行调用的线程关联的主窗口。

### <a name="remarks"></a>备注

如果你的应用程序不是 OLE 服务器，则调用此函数等效于直接引用应用程序对象的*m_pMainWnd*成员。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxgetperuserregistration"></a>AfxGetPerUserRegistration

使用此函数可确定应用程序是否将注册表访问重定向到**HKEY_CURRENT_USER** （**HKCU**）节点。

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>返回值

如果为 TRUE，则指示将注册表信息定向到 HKCU 节点。 FALSE 表示应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** （**HKCR**）。

### <a name="remarks"></a>备注

如果启用注册表重定向，框架会将访问从**HKCR**重定向到**HKEY_CURRENT_USER \software\classes**。 仅 MFC 和 ATL 框架受重定向影响。

若要更改应用程序是否重定向注册表访问，请使用[AfxSetPerUserRegistration](#afxsetperuserregistration)。

### <a name="requirements"></a>要求

  **标头**afxstat_。h

## <a name="afxgetresourcehandle"></a>AfxGetResourceHandle

使用此函数返回的 HINSTANCE 句柄可以直接访问应用程序的资源，例如，调用 Windows 函数 `FindResource`。

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>返回值

HINSTANCE 句柄，其中加载了应用程序的默认资源。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxgetthread"></a>AfxGetThread

调用此函数可获取指向[CWinThread](../../mfc/reference/cwinthread-class.md)对象的指针，该对象表示当前正在执行的线程。

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>返回值

指向当前执行线程的指针；否则为 NULL。

### <a name="remarks"></a>备注

必须从线程中调用。

> [!NOTE]
> 如果要从 Visual C++版本4.2、5.0 或6.0 迁移调用 `AfxGetThread` 的 MFC 项目，则 `AfxGetThread` 在未找到任何线程时调用[AfxGetApp](#afxgetapp) 。 在最新版本的编译器中，如果未找到任何线程，`AfxGetThread` 将返回 NULL。 如果需要应用程序线程，则必须调用 `AfxGetApp`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxinitrichedit"></a>AfxInitRichEdit

调用此函数可初始化应用程序的 rich edit 控件（版本1.0）。

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>备注

提供此函数是为了向后兼容。 新应用程序应使用[AfxInitRichEdit2](#afxinitrichedit2)。

`AfxInitRichEdit` 加载 RICHED32。用于初始化 rich edit 控件的1.0 版本的 DLL。 若要使用 rich edit 控件的2.0 和3.0 版本，请 RICHED20.DLL。需要加载 DLL。 它通过调用[AfxInitRichEdit2](#afxinitrichedit2)进行加载。

若要将现有视觉对象C++中的 rich edit 控件更新到版本2.0，请打开。RC 文件作为文本，将每个 rich edit 控件的类名从 "RICHEDIT" 更改为 "RichEdit20a"。 然后，将对 `AfxInitRichEdit` 的调用替换为 `AfxInitRichEdit2`。

如果尚未为进程初始化库，此函数还会初始化公共控制库。 如果直接在 MFC 应用程序中使用 rich edit 控件，请调用此函数以确保 MFC 正确地初始化了丰富的编辑控件运行时。 如果调用[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)、 [CRichEditView](../../mfc/reference/cricheditview-class.md)或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的 `Create` 方法，则通常不需要调用此函数，但在某些情况下，这可能是必需的。

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxinitrichedit2"></a>AfxInitRichEdit2

调用此函数为应用程序初始化 Rich Edit 控件（2.0 版和更高版本）。

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>备注

调用此函数以加载 RICHED20.DLL 并初始化 Rich Edit 控件 2.0 版。 如果调用[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)、 [CRichEditView](../../mfc/reference/cricheditview-class.md)或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的 `Create` 方法，则通常不需要调用此函数，但在某些情况下，这可能是必需的。

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxisextendedframeclass"></a>AfxIsExtendedFrameClass

确定给定窗口是否是扩展框架对象。

### <a name="syntax"></a>语法

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>parameters

*pWnd*\
中指向派生自 `CWnd`的对象的指针。

### <a name="return-value"></a>返回值

如果提供的窗口是扩展框架对象，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果*pWnd*从以下类之一派生，则此方法返回 TRUE：

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

此方法在你必须验证函数或方法参数是否是扩展框架窗口时很有用。

### <a name="requirements"></a>要求

**标头：** afxpriv.h

## <a name="afxismfctoolbar"></a>AfxIsMFCToolBar

确定给定窗口是否为工具栏对象。

### <a name="syntax"></a>语法

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>parameters

*pWnd*\
中指向派生自 `CWnd`的对象的指针。

### <a name="return-value"></a>返回值

如果提供的窗口为工具栏对象，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果*pWnd*派生自 `CMFCToolBar`，则此方法返回 `TRUE`。 此方法在您必须验证函数或方法参数是否是 `CMFCToolBar` 对象时很有用。

### <a name="requirements"></a>要求

**标头：** afxpriv.h

## <a name="afxkeyboardmanager"></a>AfxKeyboardManager

指向全局[键盘管理器](ckeyboardmanager-class.md)的指针。

### <a name="syntax"></a>语法

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>要求

**标头：** afxkeyboardmanager

## <a name="afxloadlibrary"></a>AfxLoadLibrary

使用 `AfxLoadLibrary` 映射 DLL 模块。

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>parameters

*lpszModuleName*\
指向以 null 结尾的字符串，该字符串包含模块的名称（。DLL 或。EXE 文件）。 指定的名称是模块的文件名。

如果字符串指定了一个路径，但该文件不在指定的目录中，则该函数将失败。

如果未指定路径并且省略了文件扩展名，则默认扩展名为。附加了 DLL。 但是，文件名字符串可包含尾随的点字符（.）来指示模块名称没有扩展名。 如果未指定路径，则该函数将使用[桌面应用程序的搜索顺序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications)。

### <a name="return-value"></a>返回值

如果函数成功，则返回值为模块的句柄。 如果失败，返回值为 NULL。

### <a name="remarks"></a>备注

它将返回一个句柄，该句柄可用于[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)以获取 DLL 函数的地址。 `AfxLoadLibrary` 还可用于映射其他可执行模块。

每个进程都维护每个已加载库模块的引用计数。 每次调用 `AfxLoadLibrary` 时，此引用计数会递增，每次调用 `AfxFreeLibrary` 时都将递增。 当引用计数达到零时，将从调用进程的地址空间取消映射模块，并且句柄不再有效。

如果应用程序使用多个线程，并且动态加载 MFC 扩展 DLL，请确保使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` （而不是 Win32 函数 `LoadLibrary` 和 `FreeLibrary`）。 使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` 可确保加载并卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

在应用程序中使用 `AfxLoadLibrary` 要求您动态链接到 MFC 的 DLL 版本。 仅当 MFC 作为 DLL 链接到应用程序时，才会包含 `AfxLoadLibrary`Afxdll_ .h 的标头文件。 此要求是设计使然，因为必须链接到 MFC 的 DLL 版本才能使用或创建 MFC 扩展 Dll。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>要求

  **标头**afxdll_。h

## <a name="afxloadlibraryex"></a>AfxLoadLibraryEx

使用 `AfxLoadLibraryEx` 映射 DLL 模块。

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>parameters

*lpFileName*\
指向以 null 结尾的字符串，该字符串包含模块的名称（。DLL 或。EXE 文件）。 指定的名称是模块的文件名。

如果字符串指定了一个路径，但该文件不在指定的目录中，则该函数将失败。

如果未指定路径并且省略了文件扩展名，则默认扩展名为。附加了 DLL。 但是，文件名字符串可包含尾随的点字符（.）来指示模块名称没有扩展名。 如果未指定路径，则该函数将使用[桌面应用程序的搜索顺序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications)。

*hFile*\
此参数留待将来使用。 它必须为 NULL。

*dwFlags*\
加载模块时要执行的操作。 如果未指定任何标志，则此函数的行为与 `AfxLoadLibrary` 函数相同。 [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)文档中介绍了此参数的可能值。

### <a name="return-value"></a>返回值

如果函数成功，则返回值为模块的句柄。 如果失败，返回值为 NULL。

### <a name="remarks"></a>备注

`AfxLoadLibraryEx` 返回一个句柄，该句柄可用于[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)以获取 DLL 函数的地址。 `AfxLoadLibraryEx` 还可用于映射其他可执行模块。

每个进程都维护每个已加载库模块的引用计数。 每次调用 `AfxLoadLibraryEx` 时，此引用计数会递增，每次调用 `AfxFreeLibrary` 时都将递增。 当引用计数达到零时，将从调用进程的地址空间取消映射模块，并且句柄不再有效。

如果应用程序使用多个线程并且动态加载 MFC 扩展 DLL，请确保使用 `AfxLoadLibraryEx` 和 `AfxFreeLibrary` （而不是 Win32 函数 `LoadLibraryEx` 和 `FreeLibrary`）。 使用 `AfxLoadLibraryEx` 和 `AfxFreeLibrary` 确保加载并卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

在应用程序中使用 `AfxLoadLibraryEx` 要求您动态链接到 MFC 的 DLL 版本。 仅当 MFC 作为 DLL 链接到应用程序时，才会包含 `AfxLoadLibraryEx`Afxdll_ .h 的标头文件。 此要求是设计使然，因为必须链接到 MFC 的 DLL 版本才能使用或创建 MFC 扩展 Dll。

### <a name="requirements"></a>要求

  **标头**afxdll_。h

## <a name="afxmenutearoffmanager"></a>AfxMenuTearOffManager

指向全局[撕开菜单管理器](cmenutearoffmanager-class.md)的指针。

### <a name="syntax"></a>语法

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>要求

**标头：** afxmenutearoffmanager

## <a name="afxmousemanager"></a>AfxMouseManager

指向全局[鼠标管理器](cmousemanager-class.md)的指针。

### <a name="syntax"></a>语法

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>要求

**标头：** afxmousemanager

## <a name="afxregisterclass"></a>AfxRegisterClass

使用此函数在使用 MFC 的 DLL 中注册窗口类。

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>parameters

*lpWndClass*\
指向[WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)结构的指针，该结构包含要注册的窗口类的相关信息。 有关此结构的详细信息，请参阅 Windows SDK。

### <a name="return-value"></a>返回值

如果类注册成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

如果使用此函数，则将在卸载 DLL 时自动取消注册类。

在非 DLL 生成中，`AfxRegisterClass` 标识符定义为映射到 Windows 函数 `RegisterClass`的宏，因为在应用程序中注册的类会自动取消注册。 如果使用 `AfxRegisterClass` 而不是 `RegisterClass`，则可以使用代码而无需在应用程序和 DLL 中进行更改。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxregisterwndclass"></a>AfxRegisterWndClass

允许您注册自己的窗口类。

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>parameters

*nClassStyle*\
指定窗口类的 Windows 类样式或样式组合，使用按位 "或" （ **&#124;** ）运算符创建。 有关类样式的列表，请参阅 Windows SDK 中的[WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)结构。 如果为 NULL，则默认值设置如下：

- 将鼠标样式设置为 CS_DBLCLKS，当用户双击鼠标时，它会将双击消息发送到窗口过程。

- 将箭头光标样式设置为 Windows 标准 IDC_ARROW。

- 将背景画笔设置为 NULL，使窗口不会擦除其背景。

- 将图标设置为标准的 Windows 徽标图标（飘扬的旗帜）。

*hCursor*\
指定要在从窗口类创建的每个窗口中安装的光标资源的句柄。 如果使用默认值**0**，您将获得标准 IDC_ARROW 游标。

*hbrBackground*\
指定要在从窗口类创建的每个窗口中安装的画笔资源的句柄。 如果使用默认值**0**，则将具有 NULL 背景画笔，默认情况下，在处理[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)时，窗口不会擦除其背景。

*hIcon*\
指定要在从窗口类创建的每个窗口中安装的图标资源的句柄。 如果使用默认值**0**，您将获得标准的飘扬-标记 Windows 徽标图标。

### <a name="return-value"></a>返回值

包含类名的以 null 结尾的字符串。 可以将此类名称传递到 `CWnd` 或其他**CWnd**派生类中的 `Create` 成员函数以创建窗口。 该名称由 Microsoft 基础类库生成。

> [!NOTE]
> 返回值是指向静态缓冲区的指针。 若要保存此字符串，请将其分配到 `CString` 变量。

### <a name="remarks"></a>备注

Microsoft 基础类库将自动为您注册若干标准窗口类。 如果要注册您自己的窗口类，则调用此函数。

由 `AfxRegisterWndClass` 为类注册的名称仅依赖于参数。 如果使用相同的参数调用 `AfxRegisterWndClass` 多次，它只会在首次调用时注册类。 以后调用具有相同参数的 `AfxRegisterWndClass` 将返回已注册的类名。

如果使用相同的参数为多个 CWnd 派生类调用 `AfxRegisterWndClass`，而不是为每个类获得单独的窗口类，则每个类都将共享同一窗口类。 如果使用 CS_CLASSDC 类样式，此共享可能会导致问题。 除了多个 CS_CLASSDC 窗口类，最终只需要一个 CS_CLASSDC 的窗口类。 使用C++该类的所有窗口共享同一 DC。 若要避免此问题，请调用[AfxRegisterClass](#afxregisterclass)来注册该类。

有关窗口类注册和 `AfxRegisterWndClass` 函数的详细信息，请参阅技术说明[TN001：窗口类注册](../../mfc/tn001-window-class-registration.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxsetperuserregistration"></a>AfxSetPerUserRegistration

设置应用程序是否将注册表访问重定向到**HKEY_CURRENT_USER** （**HKCU**）节点。

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>parameters

*bEnable*\
中如果为 TRUE，则指示将注册表信息定向到 HKCU 节点。 FALSE 表示应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** （**HKCR**）。

### <a name="remarks"></a>备注

在 Windows Vista 之前，访问注册表的应用程序通常使用**HKEY_CLASSES_ROOT**的节点。 但是，对于 Windows Vista 或更高版本的操作系统，必须在提升模式下运行应用程序才能写入 HKCR。

此方法使应用程序能够在不在提升模式下运行的情况下读取和写入注册表。 它的工作原理是将注册表访问从 HKCR 重定向到 HKCU。 有关详细信息，请参阅 [Linker Property Pages](../../build/reference/linker-property-pages.md)。

如果启用注册表重定向，框架会将访问从 HKCR 重定向到**HKEY_CURRENT_USER \software\classes**。 仅 MFC 和 ATL 框架受重定向影响。

默认实现访问 HKCR 下的注册表。

### <a name="requirements"></a>要求

  **标头**afxstat_。h

## <a name="afxsetresourcehandle"></a>AfxSetResourceHandle

使用此函数设置用于确定应用程序的默认资源加载位置的 HINSTANCE 句柄。

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>parameters

*hInstResource*\
从中加载应用程序的资源的 .EXE 或 .DLL 文件的实例或模块句柄。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="afxshellmanager"></a>AfxShellManager

指向全局[shell 管理器](cshellmanager-class.md)的指针。

### <a name="syntax"></a>语法

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>要求

**标头：** afxshellmanager

## <a name="afxsocketinit"></a>AfxSocketInit

在 `CWinApp::InitInstance` 重写中调用此函数可初始化 Windows 套接字。

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>parameters

*lpwsaData*\
指向[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)结构的指针。 如果*lpwsaData*不等于 NULL，则通过调用 `WSAStartup`来填充 `WSADATA` 结构的地址。 此函数还确保在应用程序终止前为您调用 `WSACleanup`。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。

### <a name="requirements"></a>要求

  **标头**afxsock

## <a name="afxusertoolsmanager"></a>AfxUserToolsManager

指向全局[用户工具管理器](cusertoolsmanager-class.md)的指针。

### <a name="syntax"></a>语法

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>要求

**标头：** afxusertoolsmanager

## <a name="afxwininit"></a>AfxWinInit

此函数由 MFC 提供的 `WinMain` 函数调用，作为基于 GUI 的应用程序的[CWinApp](../../mfc/reference/cwinapp-class.md)初始化的一部分，用于初始化 MFC。

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>parameters

*hInstance*\
当前正在运行的模块的句柄。

*hPrevInstance*\
应用程序的前一个实例的句柄。 对于基于 Win32 的应用程序，此参数始终为**NULL**。

*lpCmdLine*\
指向以 null 结尾的字符串，用于指定应用程序的命令行。

*nCmdShow*\
指定 GUI 应用程序的主窗口的显示方式。

### <a name="remarks"></a>备注

对于不使用 MFC 提供的 `WinMain` 函数的控制台应用程序，必须直接调用 `AfxWinInit` 以初始化 MFC。

如果自行调用 `AfxWinInit`，则应声明一个 `CWinApp` 类的实例。 对于控制台应用程序，你可以选择不从 `CWinApp` 派生你自己的类，而是直接使用 `CWinApp` 的实例。 如果你决定将应用程序的所有功能保留在**主**实现中，则此方法适用。

> [!NOTE]
> 当它为程序集创建激活上下文时，MFC 使用用户模块提供的清单资源。 激活上下文是在 `AfxWinInit` 中创建的。 有关详细信息，请参阅[MFC 模块状态中的激活上下文支持](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin。h

## <a name="see-also"></a>另请参阅

[宏和全局](mfc-macros-and-globals.md)\
[CWinApp 类](cwinapp-class.md)\
[CContextMenuManager 类](ccontextmenumanager-class.md)\
[CWnd 类](cwnd-class.md)\
[CFrameWndEx 类](cframewndex-class.md)\
[CMFCToolBar 类](cmfctoolbar-class.md)\
[CKeyboardManager 类](ckeyboardmanager-class.md)\
[CMenuTearOffManager 类](cmenutearoffmanager-class.md)\
[CMouseManager 类](cmousemanager-class.md)\
[CShellManager 类](cshellmanager-class.md)\
[CUserToolsManager 类](cusertoolsmanager-class.md)
