---
title: 'TN024: MFC 定义的消息和资源 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4dd403693dd860966cfcca42eacc909b01eb513b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024：MFC 定义的消息和资源
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 本说明介绍的内部 Windows 消息和 MFC 使用的资源格式。 此信息对实现进行说明的框架，并将帮助你调试你的应用程序。 对于谨慎，即使所有此类信息不正式支持，你可能使用此信息的某些高级实现。  
  
 本说明包含 MFC 私有实现详细信息。所有内容在将来可能都会进行更改。 MFC 私有 Windows 消息在一个应用程序的作用域中具有意义，但将在将来更改以包含整个系统消息。  
  
 范围的 MFC 私有 Windows 消息和资源类型是保留的"系统"范围中留出受 Microsoft Windows。 使用范围中的当前并非所有数字，并且，在将来，可能会都使用的范围中的新数字。 当前所用的数字可能会发生更改。  
  
 MFC 私有 Windows 消息都在范围之内 0x360 0x37F->。  
  
 MFC 私有资源类型都在范围之内 0xF0-> 0xFF。  
  
 **MFC 私有 Windows 消息**  
  
 这些 Windows 消息用于代替 c + + 虚函数相对松散耦合要求的位置之间窗口对象，其中的 c + + 虚函数将不适用。  
  
 MFC 私有标头中声明这些私有 Windows 消息和关联的参数结构 AFXPRIV。H。 发出警告的任何代码，其中包含此标头可能依赖于未记录的行为和都可能中断在将来版本的 MFC。  
  
 在无需处理这些消息之一的极少数情况下，你应使用`ON_MESSAGE`消息映射宏和处理中的泛型 LRESULT/WPARAM/LPARAM 格式的消息。  
  
 **WM_QUERYAFXWNDPROC**  
  
 此消息发送到正在创建的窗口。 发送此消息在创建过程的非常早期作为确定如果 WndProc 方法**AfxWndProc。AfxWndProc**返回 1。  
  
|||  
|-|-|  
|wParam|未使用|  
|lParam|未使用|  
|返回|如果处理 1 **AfxWndProc**|  
  
 **WM_SIZEPARENT**  
  
 此消息由发送框架窗口到其直接子项在调整大小时 (**CFrameWnd::OnSize**调用`CFrameWnd::RecalcLayout`哪些调用`CWnd::RepositionBars`) 若要重新定位控件条周围的框架的端。 **AFX_SIZEPARENTPARAMS**结构包含用于调用父和 HDWP （它可能是 NULL） 的当前可用的客户端矩形`DeferWindowPos`尽量减少重新绘制。  
  
|||  
|-|-|  
|wParam|未使用|  
|lParam|地址**AFX_SIZEPARENTPARAMS**结构|  
|返回|未使用 (0)|  
  
 忽略该消息指示窗口不带布局中的一部分。  
  
 **WM_SETMESSAGESTRING**  
  
 此消息发送到框架窗口，以使其更新状态栏中的消息行。 字符串 ID 或 LPCSTR 可以是指定 （但不是能同时）。  
  
|||  
|-|-|  
|wParam|字符串 ID （或零）|  
|lParam|LPCSTR 字符串 （或 NULL）|  
|返回|未使用 (0)|  
  
 **WM_IDLEUPDATECMDUI**  
  
 在空闲时间发送此消息实现更新命令 UI 处理程序的空闲时间更新。 如果窗口 （通常控件条） 处理的消息，它将创建`CCmdUI`对象 （或派生类的对象） 并调用**CCmdUI::DoUpdate**为每个窗口中的"项目"。 这反过来将检查`ON_UPDATE_COMMAND_UI`处理程序命令处理程序链中的对象。  
  
|||  
|-|-|  
|wParam|BOOL bDisableIfNoHandler|  
|lParam|未使用 (0)|  
|返回|未使用 (0)|  
  
 *bDisableIfNoHandler*不为零可禁用用户界面对象，如果既无`ON_UPDATE_COMMAND_UI`也不`ON_COMMAND`处理程序。  
  
 **WM_EXITHELPMODE**  
  
 此消息发布到`CFrameWnd`，若要退出上下文相关帮助模式。 收到此消息终止通过启动模式循环**CFrameWnd::OnContextHelp。**  
  
|||  
|-|-|  
|wParam|未使用 (0)|  
|lParam|未使用 (0)|  
|返回|未使用|  
  
 **WM_INITIALUPDATE**  
  
 任务要执行其初始更新安全时，此消息是由文档模板发送到框架窗口的所有后代中。 它映射到调用`CView::OnInitialUpdate`但可在其他`CWnd`-派生其他单步更新的类。  
  
|||  
|-|-|  
|wParam|未使用 (0)|  
|lParam|未使用 (0)|  
|返回|未使用 (0)|  
  
 **WM_RECALCPARENT**  
  
 此消息由视图发送到其父窗口 (通过获取`GetParent`) 若要强制布局进行计算后 (通常情况下，将调用父`RecalcLayout`)。 这是 OLE 服务器应用程序中使用其所在的帧增大随着视图的总大小的增长所需。  
  
 如果父窗口处理此消息它应返回 TRUE，并且填充在与客户端区域的新大小 lParam 中传递的矩形。 这在中使用`CScrollView`能够正确处理滚动条 （然后在窗口时它们将被添加外部位置） 的服务器对象时就地激活。  
  
|||  
|-|-|  
|wParam|未使用 (0)|  
|lParam|LPRECT rectClient 可能为 NULL|  
|返回|如果新的客户端矩形返回，则 FALSE 否则|  
  
 **WM_SIZECHILD**  
  
 此消息由发送`COleResizeBar`到其所有者窗口 (通过`GetOwner`) 当用户调整大小时重设大小句柄的大小调整栏。 `COleIPFrameWnd` 尝试重新定位框架窗口，如用户已请求的响应此消息。  
  
 新添加的矩形，其中包含的调整大小栏中，与框架窗口相对的客户端坐标中给定是 lParam 指向。  
  
|||  
|-|-|  
|wParam|未使用 (0)|  
|lParam|LPRECT rectNew|  
|返回|未使用 (0)|  
  
 **WM_DISABLEMODAL**  
  
 此消息发送到所有拥有的正在停用的框架窗口的弹出窗口。 框架窗口使用结果来确定禁用弹出窗口。  
  
 你可以使用这在弹出窗口中执行特殊处理，当帧进入模式状态，或以防止获取禁用某些弹出窗口。 工具提示将此消息时框架窗口会将进入模式状态，例如销毁本身。  
  
|||  
|-|-|  
|wParam|未使用 (0)|  
|lParam|未使用 (0)|  
|返回|非零到**不**禁用窗口，0 表示窗口将被禁用|  
  
 **WM_FLOATSTATUS**  
  
 此消息发送到所有拥有的框架窗口时激活或停用另一个顶级框架窗口框架的弹出窗口。 实现使用此**MFS_SYNCACTIVE**中`CMiniFrameWnd`，以使这些弹出式窗口激活与顶部级别框架窗口的激活同步。  
  
|||  
|-|-|  
|wParam|是以下值之一：<br /><br /> **FS_SHOW**<br /><br /> **FS_HIDE**<br /><br /> **FS_ACTIVATE**<br /><br /> **FS_DEACTIVATE**<br /><br /> **FS_ENABLEFS_DISABLE**<br /><br /> **FS_SYNCACTIVE**|  
|lParam|未使用 (0)|  
  
 返回值应为非零如果**FS_SYNCACTIVE**是组和窗口使其与父帧的激活。 `CMiniFrameWnd` 返回非零值时的样式设置为**MFS_SYNCACTIVE。**  
  
 有关详细信息，请参阅的实现`CMiniFrameWnd`。  
  
## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL  
 当激活或停用在其"顶级组"窗口时，此消息是发送到顶级窗口。 如果这是一个顶级窗口 （没有父或所有者），或属于这样一个窗口，窗口将是顶级组的一部分。 此消息是在使用类似**WM_ACTIVATEAPP，**但可在属于不同的进程的 windows （常见 OLE 应用程序中） 的单个窗口层次结构中的混合其中的情况下。  
  
## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_COMMANDHELP，WM_HELPHITTEST，WM_EXITHELPMODE  
 这些消息的上下文相关帮助实现中使用。 请参阅[技术注意 28](../mfc/tn028-context-sensitive-help-support.md)有关详细信息。  
  
## <a name="mfc-private-resource-formats"></a>MFC 私有资源格式  
 目前，MFC 定义两种专用的资源格式： **RT_TOOLBAR**和**RT_DLGINIT**。  
  
## <a name="rttoolbar-resource-format"></a>RT_TOOLBAR 资源格式  
 默认的工具栏由 AppWizard 提供基于**RT_TOOLBAR** MFC 4.0 中引入的自定义资源。 你可以编辑使用工具栏编辑器此资源。  
  
## <a name="rtdlginit-resource-format"></a>RT_DLGINIT 资源格式  
 一个 MFC 专用的资源格式用于存储额外对话框初始化信息。 这包括存储在一个组合框的初始字符串。 此资源的格式不是手动进行编辑，但由 Visual c + +。  
  
 Visual c + +，这**RT_DLGINIT**资源不需要使用 MFC 的相关的功能，因为不存在的资源使用信息 API 替代方法。 使用 Visual c + +，使得可以更轻松地编写、 维护和转换从长远来看，你的应用程序。  
  
 基本结构**RT_DLGINIT**资源是，如下所示：  
  
```  
+---------------+    \  
| Control ID    |   UINT             |  
+---------------+    |  
| Message #     |   UINT             |  
+---------------+    |  
|length of data |   DWORD            |  
+---------------+    |   Repeated  
|   Data        |   Variable Length  |   for each control  
|   ...         |   and Format       |   and message  
+---------------+    /  
|     0         |   BYTE  
+---------------+  
```  
  
 重复的部分包含的控件 ID 向其发送消息，消息 # 发送 （正常的 Windows 消息） 和可变长度的数据。 窗体中发送的 Windows 消息：  
  
```  
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```  
  
 这是一个非常一般的格式，允许任何 Windows 消息和数据内容。 在 Visual c + + 资源编辑器和 MFC 仅支持 Windows 消息的有限的子集： CB_ADDSTRING （数据是一个文本字符串） 的组合框的初始列表选项。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

