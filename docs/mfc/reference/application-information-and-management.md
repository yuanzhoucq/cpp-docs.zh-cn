---
title: 应用程序信息和管理
description: 引用 Microsoft 基础类库 （MFC） 应用程序信息和管理功能。
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: fc0b4b09f6c48da68bebe4a2825f49bcf6ab7e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372503"
---
# <a name="application-information-and-management"></a>应用程序信息和管理

编写应用程序时，将创建单个[CWinApp](../../mfc/reference/cwinapp-class.md)派生对象。 有时，您可能希望从`CWinApp`派生对象外部获取有关此对象的信息。 或者，您可能需要访问其他全局"管理器"对象。

Microsoft 基础类库提供以下全局函数，以帮助您完成以下任务：

## <a name="application-information-and-management-functions"></a>应用程序信息和管理功能

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|创建新线程。|
|[AfxContext菜单管理器](#afxcontextmenumanager)|指向全局[上下文菜单管理器的指针](ccontextmenumanager-class.md)。|
|[AfxEndThread](#afxendthread)|终止当前线程。|
|[AfxFindResourceHandle](#afxfindresourcehandle)|遍走资源链，按资源 ID 和资源类型定位特定资源。 |
|[AfxFreeLibrary](#afxfreelibrary)|删除加载的动态链接库 （DLL） 模块的引用计数。 当引用计数达到零时，模块将取消映射。|
|[AfxGetApp](#afxgetapp)|返回指向应用程序单个`CWinApp`对象的指针。|
|[AfxGetAppName](#afxgetappname)|返回包含应用程序名称的字符串。|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|返回表示应用程序此实例的 HINSTANCE。|
|[AfxGetMainWnd](#afxgetmainwnd)|返回指向非 OLE 应用程序的当前"主"窗口或服务器应用程序的就地帧窗口的指针。|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|使用此函数可确定应用程序是否重定向注册表访问**HKEY_CURRENT_USER** （**HKCU**） 节点。|
|[AfxGetResourceHandle](#afxgetresourcehandle)|将 HINSTANCE 返回到应用程序的默认资源的来源。 用于直接访问应用程序的资源。|
|[AfxGetThread](#afxgetthread)|检索指向当前[CWinThread](../../mfc/reference/cwinthread-class.md)对象的指针。|
|[AfxInitRichEdit](#afxinitrichedit)|初始化应用程序的版本 1.0 丰富的编辑控件。|
|[AfxInitRichEdit2](#afxinitrichedit2)|初始化版本 2.0 和更高版本的应用程序的丰富编辑控件。|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|确定给定窗口是否是扩展框架对象。|
|[AfxIsMFCToolBar](#afxismfctoolbar)|确定给定窗口是否为工具栏对象。|
|[Afx键盘管理器](#afxkeyboardmanager)|指向全局[键盘管理器的指针](ckeyboardmanager-class.md)。|
|[AfxLoadLibrary](#afxloadlibrary)|映射 DLL 模块并返回可用于获取 DLL 函数地址的句柄。|
|[AfxLoad图书馆Ex](#afxloadlibraryex)|使用指定的选项映射 DLL 模块，并返回可用于获取 DLL 函数地址的句柄。|
|[AfxMenutearoff管理器](#afxmenutearoffmanager)|指向全局[撕掉菜单管理器的指针](cmenutearoffmanager-class.md)。|
|[AfxMouse管理器](#afxmousemanager)|指向全局[鼠标管理器](cmousemanager-class.md)的指针。|
|[AfxRegisterClass](#afxregisterclass)|在使用 MFC 的 DLL 中注册窗口类。|
|[AfxRegisterWndClass](#afxregisterwndclass)|注册 Windows 窗口类以补充由 MFC 自动注册的类。|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|设置应用程序是否重定向注册表访问**HKEY_CURRENT_USER** （**HKCU**） 节点。|
|[AfxSetResourceHandle](#afxsetresourcehandle)|设置加载应用程序的默认资源的 HINSTANCE 句柄。|
|[AfxShell经理](#afxshellmanager)|指向全局[shell 管理器的指针](cshellmanager-class.md)。 |
|[AfxSocketInit](#afxsocketinit)|在`CWinApp::InitInstance`重写中调用以初始化 Windows 套接字。|
|[AfxUser工具管理器](#afxusertoolsmanager)|指向全局[用户工具管理器的指针](cusertoolsmanager-class.md)。|
|[AfxWinInit](#afxwininit)|由 MFC 提供的`WinMain`函数调用，作为基于 GUI 的应用程序的[CWinApp](../../mfc/reference/cwinapp-class.md)初始化的一部分，以初始化 MFC。 必须直接调用使用 MFC 的控制台应用程序。|

## <a name="afxbeginthread"></a><a name="afxbeginthread"></a>AfxBeginThread

调用此函数以创建新线程。

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

### <a name="parameters"></a>参数

*普芬线程普罗克*\
指向辅助线程的控制功能。 指针不能为 NULL。 此函数必须声明如下：

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThread 类*\
从[CWinThread](../../mfc/reference/cwinthread-class.md)派生的对象RUNTIME_CLASS 。

*pParam*\
要传递给控制函数的参数。

*n优先*\
要为线程设置的优先级。 有关可用优先级的完整列表和说明，请参阅 Windows SDK 中的[SetThreadPriority。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)

*nStackSize*\
指定新线程堆栈的大小（以字节为单位）。 如果为 0，堆栈大小默认与创建线程的大小堆栈相同。

*dwCreateFlags*\
指定控制创建线程的其他标志。 此标志可以包含两个值之一：

- CREATE_SUSPENDED 以 1 的挂起计数启动线程。 如果要在线程开始运行之前初始化`CWinThread`对象的任何成员数据（如[m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete)或派生类的任何成员，请使用CREATE_SUSPENDED。 初始化完成后，请使用[CWinThread：：resumeThread](../../mfc/reference/cwinthread-class.md#resumethread)开始线程运行。 在调用线程之前`CWinThread::ResumeThread`，线程不会执行。

- **0**创建后立即启动线程。

*lpSecurityAttrs*\
指向指定线程的安全属性[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))结构。 如果为 NULL，则使用与创建线程相同的安全属性。 有关此结构的详细信息，请参阅 Windows SDK。

### <a name="return-value"></a>返回值

指针指向新创建的线程对象，如果发生故障，则指向 NULL。

### <a name="remarks"></a>备注

创建辅助线程的第`AfxBeginThread`一种形式。 第二个窗体创建一个线程，该线程可用作用户界面线程或辅助线程。

`AfxBeginThread`创建一个新`CWinThread`对象，调用其[CreateThread](../../mfc/reference/cwinthread-class.md#createthread)函数以开始执行线程，并返回指向线程的指针。 在整个过程中进行检查，以确保在创建的任何部分失败时，所有对象都正确处理。 要结束线程，请从线程内调用[AfxEndThread，](#afxendthread)或从辅助线程的控制函数返回。

应用程序必须启用多线程;否则，此函数将失败。 有关启用多线程的详细信息，请参阅[/MD、/MT/LD（使用运行时库）。](../../build/reference/md-mt-ld-use-run-time-library.md)

有关 的详细信息`AfxBeginThread`，请参阅文章["多线程：创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)和[多线程：创建用户界面线程](../../parallel/multithreading-creating-user-interface-threads.md)"。

### <a name="example"></a>示例

请参阅[CSocket 的示例：附加](../../mfc/reference/csocket-class.md#attach)。

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxcontextmenumanager"></a><a name="afxcontextmenumanager"></a>AfxContext菜单管理器

指向全局[上下文菜单管理器的指针](ccontextmenumanager-class.md)。

### <a name="syntax"></a>语法

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>要求

**标题：** afxcontextmenumanager.h

## <a name="afxendthread"></a><a name="afxendthread"></a>AfxEndThread

调用此函数以终止当前正在执行的线程。

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>参数

*n退出代码*\
指定线程的退出代码。

*b 删除*\
从内存中删除线程对象。

### <a name="remarks"></a>备注

必须从线程内调用才能终止。

有关 的详细信息`AfxEndThread`，请参阅文章["多线程：终止线程](../../parallel/multithreading-terminating-threads.md)"。

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxfindresourcehandle"></a><a name="afxfindresourcehandle"></a>AfxFind资源句柄

使用 `AfxFindResourceHandle` 处理资源链并按资源 ID 和资源类型找到特定资源。

### <a name="syntax"></a>语法

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>参数

*lpsz名称*\
指向包含资源 ID 的字符串的指针。
*lpsz类型*\
指向资源的类型的指针。 有关资源类型的列表，请参阅在 Windows SDK 中[查找资源](/windows/win32/api/winbase/nf-winbase-findresourcea)。

### <a name="return-value"></a>返回值

包含资源的模块的句柄。

### <a name="remarks"></a>备注

`AfxFindResourceHandle`查找特定资源，并将句柄返回到包含资源的模块。 资源可能位于加载的任何 MFC 扩展 DLL 中。 `AfxFindResourceHandle` 将告知您哪个 DLL 包含该资源。

模块将按以下顺序进行搜索：

1. 主模块（如果是 MFC 扩展 DLL）。

1. 非系统模块。

1. 语言特定的模块。

1. 主模块，如果是系统 DLL。

1. 系统模块。

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="afxfreelibrary"></a><a name="afxfreelibrary"></a>Afx自由图书馆

`AfxFreeLibrary` 和 `AfxLoadLibrary` 用于维护每个已加载库模块的引用计数。

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>参数

*hInstLib*\
已加载库模块的句柄。 [AfxLoad库](#afxloadlibrary)返回此句柄。

### <a name="return-value"></a>返回值

如果函数成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

`AfxFreeLibrary` 减少已加载动态链接库 (DLL) 模块的引用计数。 当引用计数达到零时，将从调用进程的地址空间取消映射模块，并且句柄不再有效。 每次调用 `AfxLoadLibrary` 时都会增加此引用计数。

在取消映射库模块之前，系统将使 DLL 从使用其的进程分离。 这样做使 DLL 有机会清理为当前进程分配的资源。 在入口点函数返回之后，将从当前进程的地址空间移除库模板。

使用 `AfxLoadLibrary` 映射 DLL 模块。

如果应用程序使用多个`AfxFreeLibrary`线程`AfxLoadLibrary`，请确保使用 和 （而不是`FreeLibrary` `LoadLibrary`Win32 函数 和 ）。 使用`AfxLoadLibrary``AfxFreeLibrary`并确保在加载和卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

### <a name="example"></a>示例

请参阅[AfxLoadLibrary](#afxloadlibrary)的示例。

### <a name="requirements"></a>要求

  **标题**afxdll_.h

## <a name="afxgetapp"></a><a name="afxgetapp"></a>AfxGetApp

此函数返回的指针可用于访问应用程序信息，如主消息调度代码或最上面的窗口。

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>返回值

指向应用程序的单个`CWinApp`对象的指针。

### <a name="remarks"></a>备注

如果此方法返回 NULL，则可能表示应用程序主窗口尚未完全初始化。 它还可能表示存在问题。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxgetappname"></a><a name="afxgetappname"></a>AfxGetApp名称

返回的字符串可用于诊断消息，或用作临时字符串名称的根。

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>返回值

包含应用程序名称的以 null 结尾的字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxgetinstancehandle"></a><a name="afxgetinstancehandle"></a>AfxGetinstanceHandle

此函数使您能够检索当前应用程序的实例句柄。

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>返回值

应用程序的当前实例的 HINSTANCE。 如果从与 MFC USRDLL 版本链接的 DLL 内调用，则返回 DLL 的 HINSTANCE。

### <a name="remarks"></a>备注

`AfxGetInstanceHandle`始终返回可执行文件的 HINSTANCE （。EXE），除非是从与 MFC USRDLL 版本链接的 DLL 内调用的。 在这种情况下，它将 HINSTANCE 返回 DLL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxgetmainwnd"></a><a name="afxgetmainwnd"></a>阿FXGetMainwnd

如果应用程序是 OLE 服务器，请调用此函数以检索指向应用程序活动主窗口的指针。 使用此结果，而不是直接引用应用程序对象的[m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd)成员。

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>返回值

如果服务器具有在活动容器内处于活动状态的对象，则返回指向包含就地活动文档的框架窗口对象的指针。

如果容器内没有就地处于活动状态的对象，或者应用程序不是 OLE 服务器，则此函数将返回应用程序对象的*m_pMainWnd。*

如果 `AfxGetMainWnd` 是从应用程序的主线程调用的，它将根据上述规则返回应用程序的主窗口。 如果该函数是从应用程序中的辅助线程调用的，它将返回与执行调用的线程关联的主窗口。

### <a name="remarks"></a>备注

如果应用程序不是 OLE 服务器，则调用此函数等效于直接引用应用程序对象的*m_pMainWnd*成员。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxgetperuserregistration"></a><a name="afxgetperuserregistration"></a>AfxGetPer用户注册

使用此函数可确定应用程序是否重定向注册表访问**HKEY_CURRENT_USER** （**HKCU**） 节点。

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>返回值

TRUE 表示注册表信息定向到 HKCU 节点。 FALSE 指示应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** （**HKCR**）。

### <a name="remarks"></a>备注

如果启用注册表重定向，框架会将访问从**HKCR**重定向到**HKEY_CURRENT_USER_软件\类**。 仅 MFC 和 ATL 框架受重定向影响。

要更改应用程序是否重定向注册表访问，请使用[AfxSetPerUser 注册](#afxsetperuserregistration)。

### <a name="requirements"></a>要求

  **标题**afxstat_.h

## <a name="afxgetresourcehandle"></a><a name="afxgetresourcehandle"></a>AfxGet资源手柄

使用此函数返回的 HEXAMPLE 句柄直接访问应用程序的资源，例如，在调用 Windows 函数`FindResource`中。

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>返回值

加载应用程序的默认资源的 HINSTANCE 句柄。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxgetthread"></a><a name="afxgetthread"></a>AfxGetThread

调用此函数以获取指向表示当前正在执行的线程的[CWinThread](../../mfc/reference/cwinthread-class.md)对象的指针。

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>返回值

指向当前执行线程的指针；否则为 NULL。

### <a name="remarks"></a>备注

必须从线程内调用。

> [!NOTE]
> 如果要移植从 Visual C++ 版本`AfxGetThread`4.2、5.0 或 6.0 调用的`AfxGetThread`MFC 项目，则如果找不到线程，则调用[AfxGetApp。](#afxgetapp) 在编译器的较新版本中，如果未`AfxGetThread`找到线程，则返回 NULL。 如果需要应用程序线程，则必须调用 `AfxGetApp`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxinitrichedit"></a><a name="afxinitrichedit"></a>阿FXInitrichedit

调用此函数以初始化应用程序的富编辑控件（版本 1.0）。

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>备注

此功能用于向后兼容性。 新的应用程序应该使用[AfxInitrichedit2。](#afxinitrichedit2)

`AfxInitRichEdit`负载 RICHED32。DLL 用于初始化富编辑控件的版本 1.0。 要使用富编辑控件的 2.0 版和 3.0 版本，RICHED20。需要加载 DLL。 它加载通过调用[AfxInitRichEdit2。](#afxinitrichedit2)

要将现有 VisualC++ 应用程序中的丰富编辑控件更新到版本 2.0，请打开 。RC 文件作为文本，将每个富编辑控件的类名称从"RICHEDIT"更改为"RichEdit20a"。 然后将 调用`AfxInitRichEdit`替换为`AfxInitRichEdit2`。

如果尚未为进程初始化库，则此函数还会初始化公共控件库。 如果直接从 MFC 应用程序使用丰富的编辑控件，请调用此函数以确保 MFC 已正确初始化丰富的编辑控制运行时。 如果您调用`Create`[CRichEditCtrl、CRichEditView](../../mfc/reference/cricheditctrl-class.md)或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的方法，您通常不需要调用此函数，但在某些情况下可能有必要调用此函数。 [CRichEditView](../../mfc/reference/cricheditview-class.md)

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxinitrichedit2"></a><a name="afxinitrichedit2"></a>阿FXInitrichedit2

调用此函数为应用程序初始化 Rich Edit 控件（2.0 版和更高版本）。

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>备注

调用此函数以加载 RICHED20.DLL 并初始化 Rich Edit 控件 2.0 版。 如果您调用`Create`[CRichEditCtrl、CRichEditView](../../mfc/reference/cricheditctrl-class.md)或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的方法，您通常不需要调用此函数，但在某些情况下可能有必要调用此函数。 [CRichEditView](../../mfc/reference/cricheditview-class.md)

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxisextendedframeclass"></a><a name="afxisextendedframeclass"></a>AfxIs 扩展框架类

确定给定窗口是否是扩展框架对象。

### <a name="syntax"></a>语法

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>参数

*pwnd*\
[在]指向派生自`CWnd`的对象的指针。

### <a name="return-value"></a>返回值

如果提供的窗口是扩展帧对象，则为 TRUE;如果提供的窗口是扩展帧对象，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

如果*pWnd*派生自以下类之一，则此方法返回 TRUE：

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

此方法在你必须验证函数或方法参数是否是扩展框架窗口时很有用。

### <a name="requirements"></a>要求

**标头：** afxpriv.h

## <a name="afxismfctoolbar"></a><a name="afxismfctoolbar"></a>AfxIsMFCToolbar

确定给定窗口是否为工具栏对象。

### <a name="syntax"></a>语法

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*\
[在]指向派生自`CWnd`的对象的指针。

### <a name="return-value"></a>返回值

如果提供的窗口是工具栏对象，则为 TRUE;如果提供的窗口是工具栏对象，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

如果*pWnd*派生自`CMFCToolBar`，则此方法将返回`TRUE`。 此方法在您必须验证函数或方法参数是否是 `CMFCToolBar` 对象时很有用。

### <a name="requirements"></a>要求

**标头：** afxpriv.h

## <a name="afxkeyboardmanager"></a><a name="afxkeyboardmanager"></a>Afx键盘管理器

指向全局[键盘管理器的指针](ckeyboardmanager-class.md)。

### <a name="syntax"></a>语法

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>要求

**标题：** afx键盘管理器.h

## <a name="afxloadlibrary"></a><a name="afxloadlibrary"></a>AfxLoad库

使用 `AfxLoadLibrary` 映射 DLL 模块。

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>参数

*lpszModule 名称*\
指向包含模块名称的 null 端接字符串（或 。DLL 或 。EXE 文件）。 指定的名称是模块的文件名。

如果字符串指定路径，但文件在指定的目录中不存在，则函数将失败。

如果未指定路径，并且省略了文件名扩展名，则默认扩展名 。DLL 被追加。 但是，文件名字符串可以包含尾随点字符 （.）， 以指示模块名称没有扩展名。 当未指定路径时，该函数将使用[桌面应用程序的搜索顺序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications)。

### <a name="return-value"></a>返回值

如果函数成功，返回值是模块的句柄。 发生故障时，返回值为 NULL。

### <a name="remarks"></a>备注

它返回可在[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)中使用的句柄来获取 DLL 函数的地址。 `AfxLoadLibrary`还可用于映射其他可执行模块。

每个进程维护每个加载的库模块的引用计数。 每次`AfxLoadLibrary`调用时都会增加此引用计数，并且每次`AfxFreeLibrary`调用时都会递减。 当引用计数达到零时，将从调用进程的地址空间取消映射模块，并且句柄不再有效。

如果应用程序使用多个`AfxLoadLibrary`线程`AfxFreeLibrary`，并且它动态加载 MFC `LoadLibrary` `FreeLibrary`扩展 DLL，请确保使用 （而不是 Win32 函数和 ）。 使用`AfxLoadLibrary`并确保`AfxFreeLibrary`在加载和卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

在`AfxLoadLibrary`应用程序中使用需要您动态链接到 MFC 的 DLL 版本。 仅当 MFC`AfxLoadLibrary`以 DLL 身份链接到应用程序时，才会包含 的标头文件。Afxdll_.h。 此要求是设计原因，因为您必须链接到 MFC 的 DLL 版本才能使用或创建 MFC 扩展 DLL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>要求

  **标题**afxdll_.h

## <a name="afxloadlibraryex"></a><a name="afxloadlibraryex"></a>AfxLoad图书馆Ex

使用 `AfxLoadLibraryEx` 映射 DLL 模块。

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>参数

*lpFile名称*\
指向包含模块名称的 null 端接字符串（或 。DLL 或 。EXE 文件）。 指定的名称是模块的文件名。

如果字符串指定路径，但文件在指定的目录中不存在，则函数将失败。

如果未指定路径，并且省略了文件名扩展名，则默认扩展名 。DLL 被追加。 但是，文件名字符串可以包含尾随点字符 （.）， 以指示模块名称没有扩展名。 当未指定路径时，该函数将使用[桌面应用程序的搜索顺序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications)。

*hFile*\
此参数留待将来使用。 它必须为 NULL。

*dwFlags*\
加载模块时要执行的操作。 如果未指定标志，则此函数的行为与`AfxLoadLibrary`函数相同。 [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)文档中介绍了此参数的可能值。

### <a name="return-value"></a>返回值

如果函数成功，返回值是模块的句柄。 发生故障时，返回值为 NULL。

### <a name="remarks"></a>备注

`AfxLoadLibraryEx`返回可在[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)中使用的句柄来获取 DLL 函数的地址。 `AfxLoadLibraryEx`还可用于映射其他可执行模块。

每个进程维护每个加载的库模块的引用计数。 每次`AfxLoadLibraryEx`调用时都会增加此引用计数，并且每次`AfxFreeLibrary`调用时都会递减。 当引用计数达到零时，将从调用进程的地址空间取消映射模块，并且句柄不再有效。

如果应用程序使用多个`AfxLoadLibraryEx`线程`AfxFreeLibrary`，并且它动态加载 MFC `LoadLibraryEx` `FreeLibrary`扩展 DLL，请确保使用 （而不是 Win32 函数和 ）。 使用`AfxLoadLibraryEx``AfxFreeLibrary`并确保在加载和卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

在`AfxLoadLibraryEx`应用程序中使用需要您动态链接到 MFC 的 DLL 版本。 仅当 MFC`AfxLoadLibraryEx`以 DLL 身份链接到应用程序时，才会包含 的标头文件。Afxdll_.h。 此要求是设计原因，因为您必须链接到 MFC 的 DLL 版本才能使用或创建 MFC 扩展 DLL。

### <a name="requirements"></a>要求

  **标题**afxdll_.h

## <a name="afxmenutearoffmanager"></a><a name="afxmenutearoffmanager"></a>AfxMenutearoff管理器

指向全局[撕掉菜单管理器的指针](cmenutearoffmanager-class.md)。

### <a name="syntax"></a>语法

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>要求

**标题：** afxmenutearoff 管理器.h

## <a name="afxmousemanager"></a><a name="afxmousemanager"></a>AfxMouse管理器

指向全局[鼠标管理器](cmousemanager-class.md)的指针。

### <a name="syntax"></a>语法

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>要求

**标题：** afxmouse 管理器.h

## <a name="afxregisterclass"></a><a name="afxregisterclass"></a>Afx注册类

使用此函数在使用 MFC 的 DLL 中注册窗口类。

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>参数

*lpWndClass*\
指向[WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)结构的指针，其中包含有关要注册的窗口类的信息。 有关此结构的详细信息，请参阅 Windows SDK。

### <a name="return-value"></a>返回值

如果类注册成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

如果使用此函数，则将在卸载 DLL 时自动取消注册类。

在非 DLL 生成中`AfxRegisterClass`，标识符定义为映射到 Windows 函数`RegisterClass`的宏，因为在应用程序中注册的类将自动取消注册。 如果使用`AfxRegisterClass`而不是`RegisterClass`，则可以在应用程序和 DLL 中不使用更改即可使用代码。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxregisterwndclass"></a><a name="afxregisterwndclass"></a>Afx注册WndClass

允许您注册自己的窗口类。

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>参数

*nClassStyle*\
为窗口类指定使用位-OR** （&#124;**） 运算符创建的 Windows 类样式或样式组合。 有关类样式的列表，请参阅 Windows SDK 中的[WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)结构。 如果 NULL，则默认值设置如下：

- 将鼠标样式设置为 CS_DBLCLKS，当用户双击鼠标时，它会将双击消息发送到窗口过程。

- 将箭头光标样式设置为 Windows 标准 IDC_ARROW。

- 将背景画笔设置为 NULL，因此窗口不会擦除其背景。

- 将图标设置为标准的 Windows 徽标图标（飘扬的旗帜）。

*h光标*\
指定要在从窗口类创建的每个窗口中安装的光标资源的句柄。 如果使用默认值**0**，您将获得标准IDC_ARROW光标。

*hbr背景*\
指定要在从窗口类创建的每个窗口中安装的画笔资源的句柄。 如果使用默认值**0**，则具有 NULL 背景画笔，默认情况下，窗口在处理[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)时不会擦除其背景。

*hIcon*\
指定要在从窗口类创建的每个窗口中安装的图标资源的句柄。 如果使用默认值**0**，您将获得标准的"挥舞"标志 Windows 徽标图标。

### <a name="return-value"></a>返回值

包含类名的以 null 结尾的字符串。 您可以将此类名称传递给 中`Create``CWnd`的成员函数或其他**CWnd 派生**类以创建窗口。 该名称由 Microsoft 基础类库生成。

> [!NOTE]
> 返回值是指向静态缓冲区的指针。 若要保存此字符串，请将其分配到 `CString` 变量。

### <a name="remarks"></a>备注

Microsoft 基础类库将自动为您注册若干标准窗口类。 如果要注册您自己的窗口类，则调用此函数。

由 `AfxRegisterWndClass` 为类注册的名称仅依赖于参数。 如果使用相同的参数调用 `AfxRegisterWndClass` 多次，它只会在首次调用时注册类。 稍后调用`AfxRegisterWndClass`具有相同参数的调用将返回已注册的类名。

如果使用相同的参数为多个 CWnd 派生类调用 `AfxRegisterWndClass`，而不是为每个类获得单独的窗口类，则每个类都将共享同一窗口类。 如果使用CS_CLASSDC类样式，则此共享可能会导致问题。 您最终只能使用一个窗口类CS_CLASSDC而不是多个CS_CLASSDC窗口类。 使用该类的所有C++窗口共享同一个 DC。 为了避免此问题，请致电[AfxRegisterClass](#afxregisterclass)注册该类。

请参阅技术说明[TN001：窗口类注册](../../mfc/tn001-window-class-registration.md)，了解有关窗口类注册和`AfxRegisterWndClass`功能的详细信息。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxsetperuserregistration"></a><a name="afxsetperuserregistration"></a>AfxSetPer用户注册

设置应用程序是否重定向注册表访问**HKEY_CURRENT_USER** （**HKCU**） 节点。

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>参数

*b 启用*\
[在]TRUE 表示注册表信息定向到 HKCU 节点。 FALSE 指示应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** （**HKCR**）。

### <a name="remarks"></a>备注

在 Windows Vista 之前，访问注册表的应用程序通常使用**HKEY_CLASSES_ROOT**节点。 但是，使用 Windows Vista 或更高版本的操作系统，您必须以提升模式运行应用程序才能写入 HKCR。

此方法使应用程序能够读取和写入注册表，而无需在提升模式下运行。 它的工作原理是将注册处的注册存取从香港注册处转往香港联大。 有关详细信息，请参阅 [Linker Property Pages](../../build/reference/linker-property-pages.md)。

如果启用注册表重定向，框架会将访问从 HKCR 重定向到**HKEY_CURRENT_USER_软件\类**。 仅 MFC 和 ATL 框架受重定向影响。

默认实现访问 HKCR 下的注册表。

### <a name="requirements"></a>要求

  **标题**afxstat_.h

## <a name="afxsetresourcehandle"></a><a name="afxsetresourcehandle"></a>AfxSet资源句柄

使用此函数可以设置 HINSTANCE 句柄，确定应用程序的默认资源加载位置。

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>参数

*hInst资源*\
从中加载应用程序的资源的 .EXE 或 .DLL 文件的实例或模块句柄。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxshellmanager"></a><a name="afxshellmanager"></a>AfxShell经理

指向全局[shell 管理器的指针](cshellmanager-class.md)。

### <a name="syntax"></a>语法

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>要求

**标题：** afxshell管理器.h

## <a name="afxsocketinit"></a><a name="afxsocketinit"></a>阿FXSocketinit

在 `CWinApp::InitInstance` 重写中调用此函数可初始化 Windows 套接字。

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>参数

*lpwsaData*\
指向[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)结构的指针。 如果*lpwsaData*不等于 NULL，则`WSADATA`结构的地址将由调用`WSAStartup`填充。 此函数还确保在应用程序终止前为您调用 `WSACleanup`。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。

### <a name="requirements"></a>要求

  **头**afxsock.h

## <a name="afxusertoolsmanager"></a><a name="afxusertoolsmanager"></a>AfxUser工具管理器

指向全局[用户工具管理器的指针](cusertoolsmanager-class.md)。

### <a name="syntax"></a>语法

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>要求

**标题：** afxuser工具管理器.h

## <a name="afxwininit"></a><a name="afxwininit"></a>阿FXWininit

此函数由 MFC 提供的`WinMain`函数调用，作为基于 GUI 的应用程序的[CWinApp](../../mfc/reference/cwinapp-class.md)初始化的一部分，以初始化 MFC。

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>参数

*h实例*\
当前正在运行的模块的句柄。

*hPrev实例*\
应用程序前一个实例的句柄。 对于基于 Win32 的应用程序，此参数始终为**NULL**。

*lpCmdline*\
指向指定应用程序命令行的 null 端接字符串。

*nCmdShow*\
指定如何显示 GUI 应用程序的主窗口。

### <a name="remarks"></a>备注

对于不使用 MFC 提供的`WinMain`函数的控制台应用程序，必须直接调用`AfxWinInit`以初始化 MFC。

如果您称自己为类`AfxWinInit`，则应声明`CWinApp`类的实例。 对于控制台应用程序，您可以选择不派生`CWinApp`自己的类，而是直接使用 实例。 `CWinApp` 如果您决定在**main**的实现中保留应用程序的所有功能，则此技术是合适的。

> [!NOTE]
> 为程序集创建激活上下文时，MFC 将使用用户模块提供的清单资源。 激活上下文是在 `AfxWinInit` 中创建的。 有关详细信息，请参阅[MFC 模块状态中对激活上下文的支持](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="see-also"></a>另请参阅

[宏和全局](mfc-macros-and-globals.md)\
[CWinApp 类](cwinapp-class.md)\
[CContextMenuManager 类](ccontextmenumanager-class.md)\
[CWnd 类](cwnd-class.md)\
[CFramewndEx 类](cframewndex-class.md)\
[CMFCToolBar 类](cmfctoolbar-class.md)\
[键盘管理器类](ckeyboardmanager-class.md)\
[CMenuTearoff 经理类](cmenutearoffmanager-class.md)\
[鼠标管理器类](cmousemanager-class.md)\
[CShellManager 类](cshellmanager-class.md)\
[CUserToolsManager 类](cusertoolsmanager-class.md)
