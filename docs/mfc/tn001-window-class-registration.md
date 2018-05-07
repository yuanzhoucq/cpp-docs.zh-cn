---
title: TN001： 窗口类注册 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.registration
dev_langs:
- C++
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 245ffcb66223813c7146c50c964cd97203ed8d53
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="tn001-window-class-registration"></a>TN001：窗口类注册
本说明介绍注册这两个特殊的 MFC 例程[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)es 所需的 Microsoft Windows。 特定`WNDCLASS`讨论使用 MFC 和 Windows 的属性。  
  
## <a name="the-problem"></a>问题  
 属性[CWnd](../mfc/reference/cwnd-class.md)对象，如`HWND`处理在 Windows 中，在两个位置存储： 窗口对象和`WNDCLASS`。 名称`WNDCLASS`传递给常规窗口创建函数如[cwnd:: Create](../mfc/reference/cwnd-class.md#create)和[CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create)中`lpszClassName`参数。  
  
 这`WNDCLASS`必须注册通过四个方法之一：  
  
-   隐式通过使用提供的 MFC `WNDCLASS`。  
  
-   隐式通过子类化 Windows 控件 （或一些其他控件）。  
  
-   通过显式调用 MFC [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)或[AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass)。  
  
-   显式通过调用 Windows 例程[RegisterClass](http://msdn.microsoft.com/library/windows/desktop/ms633586)。  
  
## <a name="wndclass-fields"></a>WNDCLASS 字段  
 `WNDCLASS`结构包含描述窗口类的各个字段。 下表显示的字段，并指定如何使用 MFC 应用程序中：  
  
|字段|描述|  
|-----------|-----------------|  
|`lpfnWndProc`|窗口过程，必须是 `AfxWndProc`|  
|`cbClsExtra`|未使用 （应为零）|  
|`cbWndExtra`|未使用 （应为零）|  
|`hInstance`|使用自动填充[AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|  
|`hIcon`|图标的框架窗口，请参阅下文|  
|`hCursor`|下面提供了窗口，上方时鼠标光标|  
|`hbrBackground`|背景色，请参阅下文|  
|`lpszMenuName`|未使用 （应为 NULL）|  
|`lpszClassName`|类名，请参阅下文|  
  
## <a name="provided-wndclasses"></a>提供 WNDCLASSes  
 早期版本的 MFC （之前 MFC 4.0)，提供多个预定义的窗口类。 默认情况下不再提供这些窗口类。 应用程序应使用`AfxRegisterWndClass`结合适当的参数。  
  
 如果应用程序提供了具有指定的资源 ID (例如，AFX_IDI_STD_FRAME) 的资源，MFC 将使用该资源。 否则，它将使用默认的资源。 图标，则使用标准应用程序图标，并对于游标，使用标准箭头光标。  
  
 两个图标支持具有单个文档类型的 MDI 应用程序： 对于主应用程序的一个图标，图标的文档 MDIChild windows 的其他图标。 对于使用不同的图标的多个文档类型，必须注册附加`WNDCLASS`es 或使用[CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)函数。  
  
 `CFrameWnd::LoadFrame` 将注册`WNDCLASS`使用你指定为第一个参数以及下列标准属性的图标 ID:  
  
-   类样式： CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;  
  
-   图标 AFX_IDI_STD_FRAME  
  
-   箭头光标  
  
-   COLOR_WINDOW 背景色  
  
 背景色和光标的值[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)未使用的工作区以来`CMDIFrameWnd`被完全覆盖**MDICLIENT**窗口。 Microsoft 不鼓励子类化**MDICLIENT**窗口，因此使用标准颜色和尽可能的游标类型。  
  
## <a name="subclassing-and-superclassing-controls"></a>子类化和创建超类控件  
 如果你子类或超类 Windows 控件 (例如， [CButton](../mfc/reference/cbutton-class.md)) 然后，你的类自动获取`WNDCLASS`提供在 Windows 中执行该控件的属性。  
  
## <a name="the-afxregisterwndclass-function"></a>AfxRegisterWndClass 函数  
 MFC 提供的帮助器函数注册窗口类。 给定的一组特性 （窗口类样式、 光标、 背景画笔和图标），将生成一个综合的名称，并且生成的窗口类注册。 例如，应用于对象的  
  
```  
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```  
  
 此函数返回临时生成的已注册的窗口类名称的字符串。 有关此函数的详细信息，请参阅[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)。  
  
 返回的字符串是指向静态字符串缓冲区的临时指针。 下一个调用之前都有效`AfxRegisterWndClass`。 如果你想要保留围绕此字符串，将其存储在[CString](../atl-mfc-shared/using-cstring.md)变量，如此示例所示：  
  
```  
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...  
CWnd* pWnd = new CWnd;  
pWnd->Create(strWndClass, ...);

...  
```  
  
 `AfxRegisterWndClass` 将引发[CResourceException](../mfc/reference/cresourceexception-class.md)如果窗口类注册失败 （由于错误的参数，或 Windows 内存不足）。  
  
## <a name="the-registerclass-and-afxregisterclass-functions"></a>RegisterClass 和 AfxRegisterClass 函数  
 如果你想要执行的任何内容更完善比`AfxRegisterWndClass`提供，你可以调用 Windows API`RegisterClass`或 MFC 函数`AfxRegisterClass`。 `CWnd`， [CFrameWnd](../mfc/reference/cframewnd-class.md)和[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create`函数采用`lpszClassName`窗口类作为第一个参数的字符串名称。 你可以使用任何已注册的窗口类名称，而不考虑用来将其注册的方法。  
  
 务必使用`AfxRegisterClass`(或`AfxRegisterWndClass`) 在 Win32 DLL 中。 Win32 自动注销注册的一个 DLL，以便该 DLL 而终止时，必须显式注销类的类。 通过使用`AfxRegisterClass`而不是`RegisterClass`这会为你自动处理。 `AfxRegisterClass` 维护的唯一类的列表由您的 DLL 注册和将自动注销该 DLL 终止时。 当你使用`RegisterClass`在 DLL，你必须确保该 DLL 而终止时的情况下，所有类都都可以取消注册 (在你[DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583)函数)。 如果不这样做可能会导致`RegisterClass`另一个客户端应用程序尝试使用您的 DLL 时意外失败。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

