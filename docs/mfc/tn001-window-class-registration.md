---
title: TN001:窗口类注册
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: 68c851ae6a6b1b8578df90e2618f257122797aa5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306259"
---
# <a name="tn001-window-class-registration"></a>TN001:窗口类注册

此注释描述 MFC 例程，注册这两个特殊[WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa)es 所需的 Microsoft Windows。 特定`WNDCLASS`讨论 MFC 和 Windows 使用的属性。

## <a name="the-problem"></a>问题

特性[CWnd](../mfc/reference/cwnd-class.md)对象，如`HWND`处理在 Windows 中，将存储在两个位置： 窗口对象和`WNDCLASS`。 名称`WNDCLASS`传递给常规窗口创建函数如[cwnd:: Create](../mfc/reference/cwnd-class.md#create)并[CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create)中*lpszClassName*参数。

这`WNDCLASS`必须通过四种方式之一注册：

- 通过使用 MFC 提供隐式`WNDCLASS`。

- 隐式通过子类化 Windows 控件 （或某些其他控件）。

- 通过调用 MFC 显式[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)或[AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass)。

- 显式通过调用 Windows 例程[RegisterClass](/windows/desktop/api/winuser/nf-winuser-registerclassa)。

## <a name="wndclass-fields"></a>WNDCLASS 字段

`WNDCLASS`结构包括描述的窗口类的各个字段。 下表显示的字段，并指定如何在 MFC 应用程序中使用：

|字段|描述|
|-----------|-----------------|
|*lpfnWndProc*|窗口进程必须是 `AfxWndProc`|
|*cbClsExtra*|未使用 （应为零）|
|*cbWndExtra*|未使用 （应为零）|
|*hInstance*|自动填充[AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|请参阅下面的框架窗口的图标|
|*hCursor*|游标鼠标时通过窗口中，请参阅下文|
|*hbrBackground*|背景色，请参阅下文|
|*lpszMenuName*|未使用 （应为 NULL）|
|*lpszClassName*|类名，请参阅下文|

## <a name="provided-wndclasses"></a>提供 WNDCLASSes

早期版本的 MFC （在 MFC 4.0)，提供多个预定义的窗口类。 默认情况下不再提供这些窗口类。 应用程序应使用`AfxRegisterWndClass`使用适当的参数。

如果应用程序提供了具有指定的资源 ID (例如，AFX_IDI_STD_FRAME) 的资源，MFC 将使用该资源。 否则，它将使用默认的资源。 对于图标，则使用标准的应用程序图标，并对于游标，使用标准箭头光标。

这两个图标支持具有单个文档类型的 MDI 应用程序： 主应用程序的一个图标，图标文档/MDIChild windows 的其他图标。 对于使用不同的图标的多个文档类型，必须注册附加`WNDCLASS`es 或使用[CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)函数。

`CFrameWnd::LoadFrame` 将注册`WNDCLASS`使用图标 ID 指定为第一个参数，以下标准属性：

- 类样式：CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;

- icon AFX_IDI_STD_FRAME

- 箭头光标

- COLOR_WINDOW 背景色

背景色和光标的值[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)以来的工作区不使用`CMDIFrameWnd`完全受**MDICLIENT**窗口。 Microsoft 不鼓励子类化**MDICLIENT**窗口，因此使用标准颜色和游标类型在可能的情况。

## <a name="subclassing-and-superclassing-controls"></a>子类化和创建超类的控件

如果您子类或超类 Windows 控制 (例如， [CButton](../mfc/reference/cbutton-class.md)) 然后，您的类自动获取`WNDCLASS`该控件的 Windows 实现中提供的属性。

## <a name="the-afxregisterwndclass-function"></a>AfxRegisterWndClass 函数

MFC 提供了用于注册窗口类的一个帮助程序函数。 给定一组属性 （窗口类样式、 光标、 背景画笔和图标），将生成一个综合的名称，并且生成的窗口类注册。 例如，应用于对象的

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

此函数返回临时生成的已注册的窗口类名称的字符串。 有关此函数的详细信息，请参阅[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)。

返回的字符串是指向静态字符串缓冲区的临时。 在下一步调用之前都有效`AfxRegisterWndClass`。 如果你想要保留围绕此字符串，将其存储在[CString](../atl-mfc-shared/using-cstring.md)变量，如本例所示：

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass` 将引发[CResourceException](../mfc/reference/cresourceexception-class.md)如果窗口类注册失败 （由于错误的参数，或 Windows 内存不足）。

## <a name="the-registerclass-and-afxregisterclass-functions"></a>RegisterClass 和 AfxRegisterClass 函数

如果你想要执行的任何内容更加复杂比什么`AfxRegisterWndClass`提供，可以调用 Windows API`RegisterClass`或 MFC 函数`AfxRegisterClass`。 `CWnd`， [CFrameWnd](../mfc/reference/cframewnd-class.md)并[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create`函数采用*lpszClassName*窗口类的第一个参数的字符串名称。 可以使用任何已注册的窗口类名称，而不考虑用来将其注册的方法。

务必使用`AfxRegisterClass`(或`AfxRegisterWndClass`) 上 Win32 DLL 中。 Win32 不会自动注销已注册的 dll，因此终止 DLL 时必须显式取消注册类的类。 通过使用`AfxRegisterClass`而不是`RegisterClass`为您自动处理。 `AfxRegisterClass` 维护一系列的唯一类注册的 DLL 和将自动注销 DLL 终止时。 当你使用`RegisterClass`在一个 DLL，您必须确保 DLL 终止时的情况下，所有类都都可以取消注册 (在你[DllMain](/windows/desktop/Dlls/dllmain)函数)。 如果不这样做可能会导致`RegisterClass`另一个客户端应用程序尝试使用您的 DLL 时意外失败。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
