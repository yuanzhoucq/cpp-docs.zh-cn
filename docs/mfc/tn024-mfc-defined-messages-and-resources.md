---
title: TN024：MFC 定义的消息和资源
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 24bcacd46b839babe9c9c89facb1cc56d18c0ee5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370356"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024：MFC 定义的消息和资源

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明描述了 MFC 使用的内部 Windows 消息和资源格式。 此信息解释了框架的实现，并将帮助您调试应用程序。 对于冒险者，即使所有这些信息被正式不支持，您也可能将其中一些信息用于高级实现。

本说明包含 MFC 私有实现详细信息;所有内容将来都可能发生变化。 MFC 专用 Windows 消息仅在一个应用程序的范围内有意义，但将来将更改为包含系统范围的消息。

MFC 专用 Windows 消息和资源类型的范围位于 Microsoft Windows 预留的"系统"范围内。 目前，并非所有范围中的数字都使用，并且将来可以使用范围中的新数字。 可能更改当前使用的数字。

MFC 专用 Windows 消息的范围为 0x360->0x37F。

MFC 专用资源类型在 0xF0->0xFF 范围内。

**MFC 专用窗口消息**

这些 Windows 消息用于代替C++虚拟函数，其中窗口对象之间需要相对松散的耦合，并且C++虚拟函数不合适。

这些专用 Windows 消息和相关参数结构在 MFC 专用标头"AFXPRIV"中声明。H.. 请注意，包含此标头的任何代码都可能依赖于未记录的行为，并且可能会在未来版本的 MFC 中中断。

在极少数情况下需要处理这些消息之一，应使用ON_MESSAGE消息映射宏，并使用泛型 LRESULT/WPARAM/LPARAM 格式处理消息。

**WM_QUERYAFXWNDPROC**

此消息将发送到正在创建的窗口。 这在创建过程的早期发送，作为确定 WndProc 是否为**AfxWndProc 的方法。AfxWndProc**返回 1。

|||
|-|-|
|wParam|未使用|
|lParam|未使用|
|返回|1 如果由**AfxWndProc**处理|

**WM_SIZEPARENT**

在调整大小（`CFrameWnd::OnSize`调用`CFrameWnd::RecalcLayout``CWnd::RepositionBars`调用）以重新定位框架一侧周围的控制栏时，此消息通过帧窗口发送到其直接子级。 AFX_SIZEPARENTPARAMS结构包含父项的当前可用客户端矩形和 HDWP（可能是 NULL），用于调用`DeferWindowPos`该矩形可最大限度地减少重新绘制。

|||
|-|-|
|wParam|未使用|
|lParam|AFX_SIZEPARENTPARAMS结构的地址|
|返回|未使用 （0）|

忽略该消息表示窗口不参与布局。

**WM_SETMESSAGESTRING**

此消息将发送到帧窗口，要求其更新状态栏中的消息行。 可以指定字符串 ID 或 LPCSTR（但不能同时指定这两者）。

|||
|-|-|
|wParam|字符串 ID（或零）|
|lParam|字符串的 LPCSTR（或 NULL）|
|返回|未使用 （0）|

**WM_IDLEUPDATECMDUI**

此消息在空闲时间发送，以实现更新命令 UI 处理程序的空闲时间更新。 如果窗口（通常是控件栏）处理消息，它将创建一个`CCmdUI`对象（或派生类的对象），并调用`CCmdUI::DoUpdate`窗口中的每个"项"。 这将检查命令处理程序链中对象的ON_UPDATE_COMMAND_UI处理程序。

|||
|-|-|
|wParam|BOOL bDisableifNoHandler|
|lParam|未使用 （0）|
|返回|未使用 （0）|

*bDisableIfNoHandler*是非零禁用 UI 对象，如果没有ON_UPDATE_COMMAND_UI也没有ON_COMMAND处理程序。

**WM_EXITHELPMODE**

此消息将发布到退出`CFrameWnd`上下文敏感帮助模式的。 此消息的接收终止由 启动`CFrameWnd::OnContextHelp`的模式循环。

|||
|-|-|
|wParam|未使用 （0）|
|lParam|未使用 （0）|
|返回|未使用|

**WM_INITIALUPDATE**

当文档模板可以安全地执行初始更新时，此消息由文档模板发送给框架窗口的所有后代。 它映射到调用，`CView::OnInitialUpdate`但可用于其他`CWnd`派生类进行其他单次更新。

|||
|-|-|
|wParam|未使用 （0）|
|lParam|未使用 （0）|
|返回|未使用 （0）|

**WM_RECALCPARENT**

此消息由视图发送到其父窗口（通过`GetParent`获得）以强制重新计算布局（通常，父级将调用`RecalcLayout`）。 这在 OLE 服务器应用程序中使用，其中帧的大小需要随着视图的总大小的增长而增大。

如果父窗口处理此消息，则应返回 TRUE，并将在 lParam 中传递的 RECT 与工作区的新大小填充。 当服务器对象就`CScrollView`地激活时，这用于正确处理滚动条（然后放在窗口外部时）。

|||
|-|-|
|wParam|未使用 （0）|
|lParam|LPRECT 整流客户，可能是 NULL|
|返回|如果返回了新的客户端矩形，则为 TRUE，否则为 FALSE|

**WM_SIZECHILD**

当用户调整具有调整大小`COleResizeBar`的控点的大小时，`GetOwner`此消息将发送到其所有者窗口（通过 ）。 `COleIPFrameWnd`通过尝试根据用户请求重新定位帧窗口来响应此消息。

新矩形位于客户端坐标中，相对于包含调整大小的条形的帧窗口，由 lParam 指向。

|||
|-|-|
|wParam|未使用 （0）|
|lParam|LPRECT 重新|
|返回|未使用 （0）|

**WM_DISABLEMODAL**

此消息将发送到正在停用的帧窗口拥有的所有弹出窗口。 帧窗口使用结果来确定是否禁用弹出窗口。

当帧进入模态状态时，可以使用它在弹出窗口中执行特殊处理，或防止某些弹出窗口被禁用。 例如，工具提示使用此消息在帧窗口进入模态状态时自行销毁。

|||
|-|-|
|wParam|未使用 （0）|
|lParam|未使用 （0）|
|返回|非零到**不**禁用窗口，0 表示窗口将被禁用|

**WM_FLOATSTATUS**

当帧被另一个顶级框架窗口激活或停用时，此消息将发送到帧窗口拥有的所有弹出窗口。 这在 中`CMiniFrameWnd`实现MFS_SYNCACTIVE用于保持这些弹出窗口的激活与顶层框架窗口的激活同步。

|||
|-|-|
|wParam|是以下值之一：<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|未使用 （0）|

如果设置了FS_SYNCACTIVE并且窗口将其激活与父帧同步，则返回值应为非零。 `CMiniFrameWnd`当样式设置为MFS_SYNCACTIVE时，返回非零。

有关详细信息，请参阅 的`CMiniFrameWnd`实现。

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

当"顶级组"中的窗口被激活或停用时，此消息将发送到顶级窗口。 如果窗口是顶级窗口（没有父窗口或所有者），或者由此类窗口拥有，则窗口是顶级组的一部分。 此消息与WM_ACTIVATEAPP类似，但在属于不同进程的窗口混合在单个窗口层次结构中（在 OLE 应用程序中很常见）的情况下，则适用于此消息。

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP，WM_HELPHITTEST，WM_EXITHELPMODE

这些消息用于实现上下文相关的帮助。 有关详细信息，请参阅[技术说明 28。](../mfc/tn028-context-sensitive-help-support.md)

## <a name="mfc-private-resource-formats"></a>MFC 私有资源格式

目前，MFC 定义了两种私有资源格式：RT_TOOLBAR和RT_DLGINIT。

## <a name="rt_toolbar-resource-format"></a>RT_TOOLBAR资源格式

AppWizard 提供的默认工具栏基于 RT_TOOLBAR自定义资源，该资源在 MFC 4.0 中引入。 您可以使用工具栏编辑器编辑此资源。

## <a name="rt_dlginit-resource-format"></a>RT_DLGINIT资源格式

一种 MFC 专用资源格式用于存储额外的对话框初始化信息。 这包括存储在组合框中的初始字符串。 此资源的格式不是设计为手动编辑，而是由 Visual C++处理。

可视化C++和此RT_DLGINIT资源不需要使用 MFC 的相关功能，因为使用资源中的信息有 API 替代方法。 使用 Visual C++可以简化应用程序的长期编写、维护和翻译。

RT_DLGINIT资源的基本结构如下：

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

重复部分包含要将消息发送到的控制 ID、要发送的消息 +（普通 Windows 消息）和可变数据长度。 Windows 消息以以下形式发送：

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

这是一种非常通用的格式，允许任何 Windows 消息和数据内容。 Visual C++资源编辑器和 MFC 仅支持有限的 Windows 消息子集：CB_ADDSTRING组合框的初始列表选择（数据是文本字符串）。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
