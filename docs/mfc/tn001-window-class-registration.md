---
title: TN001：窗口类注册
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: 95e35ddd6f55c955bc2adb7b4db2460ae84a6dc7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513545"
---
# <a name="tn001-window-class-registration"></a>TN001：窗口类注册

此注释描述了用于注册 Microsoft Windows 所需的特殊[WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)的 MFC 例程。 讨论`WNDCLASS` MFC 和 Windows 使用的特定属性。

## <a name="the-problem"></a>问题

[CWnd](../mfc/reference/cwnd-class.md)对象的特性（如`HWND` Windows 中的句柄）存储在两个位置： `WNDCLASS`窗口对象和。 的`WNDCLASS`名称将传递给常规窗口创建功能，如[CWnd：： create](../mfc/reference/cwnd-class.md#create)和[CFrameWnd：： create](../mfc/reference/cframewnd-class.md#create) in *lpszClassName*参数。

这`WNDCLASS`必须通过以下四种方式之一进行注册：

- 通过使用提供`WNDCLASS`的 MFC 隐式。

- 通过对 Windows 控件（或某个其他控件）的子类进行隐式。

- 通过调用 MFC [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)或[AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass)显式调用。

- 通过调用 Windows 例程[RegisterClass](/windows/win32/api/winuser/nf-winuser-registerclassw)显式调用。

## <a name="wndclass-fields"></a>WNDCLASS 字段

`WNDCLASS`结构由描述窗口类的各种字段组成。 下表显示了这些字段，并指定了这些字段在 MFC 应用程序中的使用方式：

|字段|描述|
|-----------|-----------------|
|*lpfnWndProc*|窗口进程，必须是`AfxWndProc`|
|*cbClsExtra*|未使用（应为零）|
|*cbWndExtra*|未使用（应为零）|
|*hInstance*|自动填充[AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|框架窗口图标，请参阅下文|
|*hCursor*|鼠标位于窗口上方时的光标，请参阅下面的|
|*hbrBackground*|背景色，请参阅下文|
|*lpszMenuName*|未使用（应为 NULL）|
|*lpszClassName*|类名称，请参阅下文|

## <a name="provided-wndclasses"></a>提供 WNDCLASSes

MFC 的早期版本（在 MFC 4.0 之前）提供了几个预定义的窗口类。 默认情况下不再提供这些窗口类。 应用程序应`AfxRegisterWndClass`使用相应的参数。

如果应用程序提供具有指定资源 ID 的资源（例如，AFX_IDI_STD_FRAME），则 MFC 将使用该资源。 否则，它将使用默认资源。 对于图标，使用标准应用程序图标，对于光标，使用标准箭头光标。

两个图标支持具有单个文档类型的 MDI 应用程序：一个应用于主应用程序的图标，另一个图标用于图标 document/MDIChild windows。 对于具有不同图标的多个文档类型，必须注册`WNDCLASS`其他 es 或使用[CFrameWnd：： LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)函数。

`CFrameWnd::LoadFrame`将`WNDCLASS`使用您指定的图标 ID 作为第一个参数和以下标准属性注册：

- 类样式：CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;

- 图标 AFX_IDI_STD_FRAME

- 箭头光标

- COLOR_WINDOW 背景色

不会使用[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)的背景色和光标值，因为`CMDIFrameWnd` **MDICLIENT**窗口完全涵盖了的工作区。 Microsoft 不鼓励为**MDICLIENT**窗口使用子类，因此尽可能使用标准颜色和光标类型。

## <a name="subclassing-and-superclassing-controls"></a>子类化控件和 Superclassing 控件

如果对 windows 控件（例如， [CButton](../mfc/reference/cbutton-class.md)）使用子类或超类，则类会自动获取`WNDCLASS`该控件的 windows 实现中提供的属性。

## <a name="the-afxregisterwndclass-function"></a>AfxRegisterWndClass 函数

MFC 提供了用于注册窗口类的 helper 函数。 给定一组属性（窗口类样式、光标、背景画笔和图标），生成一个综合名称并注册生成的窗口类。 例如，应用于对象的

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

此函数返回生成的已注册窗口类名的临时字符串。 有关此函数的详细信息，请参阅[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)。

返回的字符串是指向静态字符串缓冲区的临时指针。 直到下一次调用`AfxRegisterWndClass`时，它才有效。 如果要保留此字符串，请将其存储在[CString](../atl-mfc-shared/using-cstring.md)变量中，如以下示例中所示：

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass`如果窗口类注册失败（由于参数错误或 Windows 内存不足），则将引发[CResourceException](../mfc/reference/cresourceexception-class.md) 。

## <a name="the-registerclass-and-afxregisterclass-functions"></a>RegisterClass 和 AfxRegisterClass 函数

如果要执行比`AfxRegisterWndClass`提供的功能更复杂的操作，可以调用 Windows API `RegisterClass`或 MFC 函数`AfxRegisterClass`。 `CWnd`   、[CFrameWnd](../mfc/reference/cframewnd-class.md) 和[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)`Create`函数采用 *lpszClassName* 字符串名称作为第一个参数的窗口类。 你可以使用任何已注册的窗口类名称，无论你使用哪种方法来注册它。

在 Win32 上，在`AfxRegisterClass` DLL 中`AfxRegisterWndClass`使用（或）很重要。 Win32 不会自动取消注册由 DLL 注册的类，因此当 DLL 终止时，必须显式取消注册类。 通过使用`AfxRegisterClass` `RegisterClass`而不是，自动处理。 `AfxRegisterClass`维护由您的 DLL 注册的唯一类的列表，并在 DLL 终止时自动将其注销。 在 dll 中`RegisterClass`使用时，必须确保在 dll 终止时（在[DllMain](/windows/win32/Dlls/dllmain)函数中）注销所有类。 否则，在其他客户端`RegisterClass`应用程序尝试使用您的 DLL 时，可能会意外失败。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
