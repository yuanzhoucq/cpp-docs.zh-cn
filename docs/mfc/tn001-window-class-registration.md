---
title: "TN001：窗口类注册 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.registration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxRegisterClass 函数"
  - "TN001"
  - "WNDCLASS"
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# TN001：窗口类注册
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此注释说明注册 Microsoft Windows需要的[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)MFC 特定的例程。  MFC 使用特定 `WNDCLASS` 特性和窗口讨论。  
  
## 问题  
 [CWnd](../mfc/reference/cwnd-class.md) 对象的特性，类似于 Windows 中 `HWND` 句柄，在两个位置来存储：窗口对象和 `WNDCLASS`。  `WNDCLASS` 的名称传递给泛窗口创建函数，如参数中的 [CWnd::Create](../Topic/CWnd::Create.md) [CFrameWnd::Create](../Topic/CFrameWnd::Create.md) 和 `lpszClassName` 。  
  
 必须通过四种方式之一注册此 `WNDCLASS` :  
  
-   隐式使用 MFC 提供的 `WNDCLASS`。  
  
-   通过隐式 subclassing 窗口控件 \(或其他控件。\)  
  
-   显式调用 MFC [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 或[AfxRegisterClass](../Topic/AfxRegisterClass.md)。  
  
-   显式调用 Windows 例程[RegisterClass](http://msdn.microsoft.com/library/windows/desktop/ms633586)。  
  
## WNDCLASS 字段  
 `WNDCLASS` 结构包含描述一个窗口类的各字段。  下表演示字段并指定它们如何在 MFC 应用程序中使用：  
  
|字段|说明|  
|--------|--------|  
|`lpfnWndProc`|窗口进程，必须是 `AfxWndProc`|  
|`cbClsExtra`|不应使用 \(应为零\)|  
|`cbWndExtra`|不应使用 \(应为零\)|  
|`hInstance`|自动填充[AfxGetInstanceHandle](../Topic/AfxGetInstanceHandle.md)|  
|`hIcon`|框架窗口的图标，请参见下面|  
|`hCursor`|当鼠标悬停在窗口上时的游标，请参见下面|  
|`hbrBackground`|背景色，请参见下面|  
|`lpszMenuName`|不应使用（应为NULL）|  
|`lpszClassName`|类名，请参见下面|  
  
## 提供的 WNDCLASSes  
 MFC 早期版本 \(在 MFC 4.0之前\) ，提供多预定义 Windows 类。  默认情况下，这些窗口类不再提供。  应用程序应与相应参数的 `AfxRegisterWndClass`一起使用。  
  
 如果应用程序提供了一个资源，指定资源 ID \(例如，AFX\_IDI\_STD\_FRAME\)，MFC 将使用该资源。  否则将使用默认资源。  对于图标，使用标准应用程序图标，并且，对于光标，标准光标使用箭头。  
  
 两个图标支持一个文档类型的 MDI 应用程序：主应用程序的图标，图标式文档\/MDIChild 窗口中另一个图标。  对于不同图标的多文档类型，必须注册其他 `WNDCLASS`或者使用 [CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md) 函数。  
  
 `CFrameWnd::LoadFrame` 注册 `WNDCLASS` 将使用您指定图标的 ID，第一个参数和下列标准特性：  
  
-   类样式：CS\_DBLCLKS&#124;CS\_HREDRAW&#124;CS\_VREDRAW;  
  
-   图标 AFX\_IDI\_STD\_FRAME  
  
-   箭头光标。  
  
-   COLOR\_WINDOW 背景色  
  
 不使用背景色的值和 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) 光标的值，因为 `CMDIFrameWnd` 的工作区完全由**MDICLIENT** 窗口覆盖。  Microsoft 不鼓励 subclassing **MDICLIENT** 窗口，因此请使用颜色和标准光标类型，当可能时。  
  
## Subclassing 和控件创建超类  
 如果您的子类或超类 Windows 控制 \(例如，[CButton](../mfc/reference/cbutton-class.md)\) 而该类自动获取在控件的窗口实现中提供的 `WNDCLASS` 特性。  
  
## AfxRegisterWndClass 函数  
 MFC 提供注册一个窗口类的帮助器函数。  给定一组特性 \(窗口类样式、光标、背景画笔和图标\)，生成复合名，生成的 Windows 类被注册。  例如，  
  
```  
const char* AfxRegisterWndClass(UINT nClassStyle, HCURSOR hCursor, HBRUSH hbrBackground, HICON hIcon);  
```  
  
 此函数返回生成的注册一个窗口类名的一临时字符串。  有关函数的详细信息，请参阅[AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 。  
  
 返回字符串是临时指向静态字符串缓冲区的指针。  它是有效的直到下次调用 `AfxRegisterWndClass`。  如果要保存此字符串，请将它存储在 [CString](../atl-mfc-shared/using-cstring.md) 变量，如下例所示：  
  
```  
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);  
...  
CWnd* pWnd = new CWnd;  
pWnd->Create(strWndClass, ...);  
...  
```  
  
 `AfxRegisterWndClass` 将引发 [CResourceException](../mfc/reference/cresourceexception-class.md)，如果 Windows 类未能注册 \(由于参数错误，或者 Windows 内存不足\)。  
  
## RegisterClass 和 AfxRegisterClass 函数  
 如果希望执行相比 `AfxRegisterWndClass` 提供复杂的操作，您可以调用Windows API  `RegisterClass` 或 MFC Windows API 函数 `AfxRegisterClass`。  `CWnd`、[CFrameWnd](../mfc/reference/cframewnd-class.md) [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 和`Create` 函数采用一个 `lpszClassName` 字符串名称窗口类作为第一个参数。  可以使用任何已注册窗口类名，无论使用注册此提供程序的方法。  
  
 在 Win32 的 DLL，使用 `AfxRegisterClass` \(或 `AfxRegisterWndClass`\) 非常重要。  Win32 DLL 未自动注销由DLL注册的类，因此，您必须在DLL终止时显式地取消类 DLL。  使用 `RegisterClass` 而不是 `AfxRegisterClass` ，这为你自动处理。  `AfxRegisterClass` 保持由 DLL注册的唯一列表类并自动将其取消注册。  在 DLL 时使用 `RegisterClass`，您必须确保所有类为未注册的，在 DLL终止时 \(在[DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583) 函数中\)。  当另一客户端应用程序尝试使用 DLL 时，错误操作可能引起`RegisterClass`导致意外失败。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)