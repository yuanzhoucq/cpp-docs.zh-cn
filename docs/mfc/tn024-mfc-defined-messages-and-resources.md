---
title: TN024:定义的消息和资源
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 029177821d37d5d26abe0b39ea1581e8a5ad602b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306020"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024:定义的消息和资源

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

此说明描述的内部 Windows 消息和 MFC 使用的资源格式。 此信息的框架，实现进行说明，帮助您进行调试你的应用程序。 出于大胆，即使所有此类信息不受正式支持，您可使用其中某些信息的高级实现。

本说明包含 MFC 私有实现详细信息;所有内容在将来可能都会发生更改。 MFC 私有 Windows 消息在一个应用程序的作用域中具有意义，但会在将来更改以包含整个系统的消息。

范围的 MFC 私有 Windows 消息和资源类型中保留的"系统"范围设置放在一边通过 Microsoft Windows。 用于当前并非所有数字在范围内，并且，在将来，可能都使用的范围中的新数字。 当前使用的数字可能会发生更改。

MFC 私有 Windows 消息处于范围内 0x360 0x37F->。

MFC 私有资源类型处于范围内 0xF0-> 0xFF。

**MFC 私有 Windows 消息**

这些 Windows 消息，用来代替C++窗口对象之间需要比较松散耦合的虚函数和位置C++虚函数不会适当。

MFC 私有标头中声明这些私有 Windows 消息和关联的参数结构 AFXPRIV。H。 请注意，任何你包括此标头的代码可能依赖于未记录的行为并可能会中断在将来版本的 MFC。

在无需处理这些消息的一个极少数情况下，应使用 ON_MESSAGE 消息映射宏和处理泛型 LRESULT/WPARAM/LPARAM 格式中的消息。

**WM_QUERYAFXWNDPROC**

此消息发送到正在创建的窗口。 这作为确定如果 WndProc 是发送创建过程中非常早**AfxWndProc。AfxWndProc**返回 1。

|||
|-|-|
|wParam|未使用|
|lParam|未使用|
|返回|如果由处理 1 **AfxWndProc**|

**WM_SIZEPARENT**

发送此消息的框架窗口到其直接子级在调整大小过程 (`CFrameWnd::OnSize`调用`CFrameWnd::RecalcLayout`它调用`CWnd::RepositionBars`) 若要重新定位控件条涉及帧的方面。 AFX_SIZEPARENTPARAMS 结构包含用来调用父和 HDWP （这可能为 NULL） 的当前可用的客户端矩形`DeferWindowPos`尽量减少重新绘制。

|||
|-|-|
|wParam|未使用|
|lParam|AFX_SIZEPARENTPARAMS 结构的地址|
|返回|未使用 (0)|

忽略该消息指示，该窗口不参与布局。

**WM_SETMESSAGESTRING**

此消息发送到框架窗口询问它更新在状态栏中的消息行。 字符串 ID 或 LPCSTR 可以是指定 （而不是两者）。

|||
|-|-|
|wParam|字符串 ID （或零）|
|lParam|LPCSTR 字符串 （或 NULL）|
|返回|未使用 (0)|

**WM_IDLEUPDATECMDUI**

在空闲时间发送此消息来实现更新命令 UI 处理程序的空闲时间更新。 如果窗口 （通常控件条） 处理的消息，它将创建`CCmdUI`对象 （或派生类的对象） 并调用`CCmdUI::DoUpdate`为每个窗口中的"项"。 这反过来会检查命令处理程序链中的对象的 ON_UPDATE_COMMAND_UI 处理程序。

|||
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|未使用 (0)|
|返回|未使用 (0)|

*bDisableIfNoHandler*为非零值，若要禁用 UI 对象，如果没有 ON_UPDATE_COMMAND_UI 既不 ON_COMMAND 处理程序。

**WM_EXITHELPMODE**

此消息发布到`CFrameWnd`，若要退出上下文相关帮助模式。 收到此消息终止由启动模式循环`CFrameWnd::OnContextHelp`。

|||
|-|-|
|wParam|未使用 (0)|
|lParam|未使用 (0)|
|返回|未使用|

**WM_INITIALUPDATE**

此消息发送的文档模板到框架窗口的所有后代时是安全的程序来执行其初始更新。 它映射到调用`CView::OnInitialUpdate`，但可以使用其他`CWnd`-派生的类用于其他一次性更新。

|||
|-|-|
|wParam|未使用 (0)|
|lParam|未使用 (0)|
|返回|未使用 (0)|

**WM_RECALCPARENT**

视图到其父窗口发送此消息 (通过获得`GetParent`) 以强制布局重新计算 (通常情况下，将调用父`RecalcLayout`)。 这是 OLE 服务器应用程序中使用是所需的帧大小增大，这是因为该视图的总大小的增长。

如果父窗口处理此消息它应返回 TRUE，并且填充中使用的客户端区域的新大小的 lParam 传递 RECT。 使用此`CScrollView`能够正确处理滚动条 （然后在窗口时它们将被添加的外部位置） 的服务器对象时就地激活。

|||
|-|-|
|wParam|未使用 (0)|
|lParam|LPRECT rectClient 可能为 NULL|
|返回|如果新客户端矩形否则，返回 FALSE|

**WM_SIZECHILD**

此消息由发送`COleResizeBar`到它的所有者窗口 (通过`GetOwner`) 时在用户调整调整大小图柄大小调整条。 `COleIPFrameWnd` 通过尝试重新定位框架窗口，因为用户已请求来响应此消息。

新矩形工作区坐标中相对于包含大小调整条的框架窗口中提供指向在的 lParam。

|||
|-|-|
|wParam|未使用 (0)|
|lParam|LPRECT rectNew|
|返回|未使用 (0)|

**WM_DISABLEMODAL**

此消息发送到所有拥有的正在停用的框架窗口的弹出窗口。 框架窗口使用的结果来确定禁用弹出窗口。

您可以使用此弹出窗口中执行特殊处理，当帧进入模式状态或以防止某些弹出窗口被禁用。 工具提示使用此消息时框架窗口进入模式状态，例如销毁本身。

|||
|-|-|
|wParam|未使用 (0)|
|lParam|未使用 (0)|
|返回|为非零**不**禁用窗口，0 指示将禁用窗口|

**WM_FLOATSTATUS**

此消息发送到所有激活或停用的另一个顶级框架窗口框架时由框架窗口拥有的弹出窗口。 这由 MFS_SYNCACTIVE 中实现`CMiniFrameWnd`，以使这些弹出窗口激活与激活的顶级框架窗口同步。

|||
|-|-|
|wParam|是以下值之一：<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|未使用 (0)|

返回值应为非零如果 FS_SYNCACTIVE 是组和窗口使其激活与父框架。 `CMiniFrameWnd` 样式设置为 MFS_SYNCACTIVE 时返回非零值。

有关详细信息，请参阅的实现`CMiniFrameWnd`。

## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL

激活或停用在其"顶级组"窗口时，此消息是发送到顶级窗口。 如果它是一个顶级窗口 （任何父或所有者），或为属于此类窗口，窗口是顶级组的一部分。 此消息是在使用类似于 WM_ACTIVATEAPP，但情况属于不同的进程的 windows 中的工作原理混合 （在 OLE 应用程序中常见） 的单个窗口层次结构中。

## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_COMMANDHELP，WM_HELPHITTEST，WM_EXITHELPMODE

这些消息的上下文相关帮助实现中使用。 请参阅[技术说明 28](../mfc/tn028-context-sensitive-help-support.md)有关详细信息。

## <a name="mfc-private-resource-formats"></a>MFC 专用的资源格式

目前，MFC 定义两个专用的资源格式：RT_TOOLBAR 和 RT_DLGINIT。

## <a name="rttoolbar-resource-format"></a>RT_TOOLBAR 资源格式

默认的工具栏提供的应用程序向导基于 RT_TOOLBAR 自定义资源，MFC 4.0 中引入的。 您可以编辑此资源使用工具栏编辑器。

## <a name="rtdlginit-resource-format"></a>RT_DLGINIT 资源格式

一种 MFC 专用的资源格式用于存储额外对话框初始化信息。 这包括初始字符串存储在组合框中。 此资源的格式不是手动编辑，但在处理视觉对象C++。

VisualC++和此 RT_DLGINIT 资源无需使用 MFC 的相关的功能，由于没有 API 替代资源中使用的信息。 使用视觉对象C++使其更易于编写、 维护和转换你的应用程序从长远来看。

RT_DLGINIT 资源的基本结构是按如下所示：

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

重复的部分包含的控件 ID 向其发送消息，消息 # 发送 （普通的 Windows 消息） 和一种长度可变的数据。 Windows 邮件窗体中：

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

这是非常一般格式，允许任何 Windows 消息和数据内容。 视觉对象C++资源编辑器和 MFC 仅支持 Windows 消息的有限的子集：CB_ADDSTRING （数据是一个文本字符串） 的组合框的初始列表选项。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
