---
title: "TN024：MFC 定义的消息和资源 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "消息 [C++], MFC"
  - "资源 [MFC]"
  - "TN024"
  - "Windows 消息 [C++], MFC 定义的"
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN024：MFC 定义的消息和资源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释说明 MFC 和资源格式使用的内部 Windows 消息。  此信息解释框架的实现以及帮助您调试的应用程序。  对于有，所有这些形，即使信息不受支持，您可以在高级实现重用此信息。  
  
 此注释包含私有 MFC 实现细节；所有内容将来可能会发生更改。  私有 MFC Windows 消息只具有含义在一个应用程序范围内，但以后更改包含系统级的消息。  
  
 范围私有 MFC Windows 消息和资源类型。Microsoft Windows 预留的保留“System”范围。  目前不使用范围中的所有数字，并且，可能在将来使用，在范围的新数目。  当前使用数可能更改。  
  
 私有 MFC Windows 消息在范围 0x360\-0x37F\>。  
  
 私有 MFC 资源类型在范围 0xF0\-0xFF\>。  
  
 **私有 MFC Windows 消息**  
  
 这些窗口消息在相对松散耦合。需要窗口对象之间的 C\+\+ 虚拟函数的位置使用，并且 .c. C\+\+ 虚拟函数不适当的位置。  
  
 这些窗口消息和私有参数关联结构在 MFC AFXPRIV.H 声明私有“标题”。  不将警告的任何代码包含此标题在 MFC 的未来版本可能依赖于未记录的行为，并且可能中断。  
  
 在极少数必要之时处理这些消息之一，则可以在泛型 LRESULT\/WPARAM\/LPARAM 格式应使用 `ON_MESSAGE` 宏和消息映射处理消息。  
  
 **WM\_QUERYAFXWNDPROC**  
  
 此信息发送来创建的窗口。  这很早在创建过程发送作为方法确定 WndProc 是 **AfxWndProc. AfxWndProc** 返回 1。  
  
|||  
|-|-|  
|wParam|未使用|  
|lParam|未使用|  
|返回|1，如果处理 **AfxWndProc**|  
  
 **WM\_SIZEPARENT**  
  
 此消息可由框架窗口发送给其直接子在调整句点 \(**CFrameWnd::OnSize** 调用 `CWnd::RepositionBars`\) 的 `CFrameWnd::RecalcLayout`。帧的一侧重新定位控件条。  **AFX\_SIZEPARENTPARAMS** 结构包含 NULL\) 可能调用 `DeferWindowPos` 将当前可用客户矩形绘制的 HDWP \(父和。  
  
|||  
|-|-|  
|wParam|未使用|  
|lParam|**AFX\_SIZEPARENTPARAMS** 结构的地址|  
|返回|没有使用 \(0\)|  
  
 忽略该消息指示窗口在不参与布局。  
  
 **WM\_SETMESSAGESTRING**  
  
 此信息在状态栏发送到框架窗口。请求它更新消息行。  字符串 ID LPCSTR \(或可以指定，而不要两者\)。  
  
|||  
|-|-|  
|wParam|字符串 ID \(或零个\)|  
|lParam|字符串 \(或 NULL\) LPCSTR|  
|返回|没有使用 \(0\)|  
  
 **WM\_IDLEUPDATECMDUI**  
  
 此信息在空闲时间时实现更新命令用户界面处理程序空闲时间更新。  如果窗口 \(通常为控制条\) 处理消息，则创建 `CCmdUI` 对象 \(或派生类的每个对象\) 调用 **CCmdUI::DoUpdate** 和“项”窗口。  这又会检查对象的 `ON_UPDATE_COMMAND_UI` 处理程序在命令处理程序的字符串。  
  
|||  
|-|-|  
|wParam|bDisableIfNoHandler BOOL|  
|lParam|没有使用 \(0\)|  
|返回|没有使用 \(0\)|  
  
 *bDisableIfNoHandler* 是非零禁用用户界面对象没有 `ON_UPDATE_COMMAND_UI` 和 `ON_COMMAND` 处理程序。  
  
 **WM\_EXITHELPMODE**  
  
 此消息。将退出到上下文相关帮助模式的 `CFrameWnd`。  此消息接收终止 **CFrameWnd::OnContextHelp.**模式启动的循环  
  
|||  
|-|-|  
|wParam|没有使用 \(0\)|  
|lParam|没有使用 \(0\)|  
|返回|未使用|  
  
 **WM\_INITIALUPDATE**  
  
 在执行其最初的更新之后，它们是安全的信息。本文档模板发送到框架窗口的所有子代。  映射到调用 `CView::OnInitialUpdate`，但可能在其他 `CWnd`\- 一次更新其他的派生类。  
  
|||  
|-|-|  
|wParam|没有使用 \(0\)|  
|lParam|没有使用 \(0\)|  
|返回|没有使用 \(0\)|  
  
 **WM\_RECALCPARENT**  
  
 该信息由视图发送到它的父窗口获取 \(通过 `GetParent`\) 强制重新布局 \(通常，父对象调用 `RecalcLayout`。\)  这在尺寸上增加的 OLE 服务器应用程序帧是必需的，原因在于视图的总大小增大。  
  
 如果父窗口处理此消息。应返回 true，并填充与新 lParam 传递和 POINT 则调整工作区。  这在 `CScrollView` 正确处理 \(位置然后滚动窗口的外部的，但添加\) 时，就地激活时的服务器对象。  
  
|||  
|-|-|  
|wParam|没有使用 \(0\)|  
|lParam|rectClient 的，可能 LPRECT NULL|  
|返回|true，如果矩形返回的新客户，否则为 false|  
  
 **WM\_SIZECHILD**  
  
 该信息由 `COleResizeBar` 发送到它的所有者窗口 \(通过 `GetOwner`\)，当用户调整大小的调整大小图柄时的调整条。  `COleIPFrameWnd` 响应此消息通过尝试重新定位框架窗口，用户请求。  
  
 新矩形命名工作区坐标中相对于包含调整条的框架窗口，点 lParam。  
  
|||  
|-|-|  
|wParam|没有使用 \(0\)|  
|lParam|LPRECT rectNew|  
|返回|没有使用 \(0\)|  
  
 **WM\_DISABLEMODAL**  
  
 此信息发送到框架窗口停用的拥有的所有弹出窗口。  框架窗口是否使用禁用结果确定弹出窗口。  
  
 在弹出窗口可以使用此执行特殊处理，在框架进入模式状态时防止某些或失败的弹出窗口。  工具提示使用自我销毁此消息，则框架窗口进入模式状态时，例如。  
  
|||  
|-|-|  
|wParam|没有使用 \(0\)|  
|lParam|没有使用 \(0\)|  
|返回|非零为 **NOT** 禁用窗口，0 指示窗口中禁用|  
  
 **WM\_FLOATSTATUS**  
  
 当帧，由另顶级框架窗口时，启用或停用此信息发送到框架窗口拥有的所有弹出窗口。  这是 **MFS\_SYNCACTIVE** 的实现用于 `CMiniFrameWnd`，从而保留这些弹出窗口中顶级激活与框架窗口激活的同步。  
  
|||  
|-|-|  
|wParam|为下列值之一：<br /><br /> **FS\_SHOW**<br /><br /> **FS\_HIDE**<br /><br /> **FS\_ACTIVATE**<br /><br /> **FS\_DEACTIVATE**<br /><br /> **FS\_ENABLEFS\_DISABLE**<br /><br /> **FS\_SYNCACTIVE**|  
|lParam|没有使用 \(0\)|  
  
 返回值应为非零，如果 **FS\_SYNCACTIVE** 集合，并 syncronizes 其窗口的父级框架的激活。  当样式设置为 **MFS\_SYNCACTIVE.**时，`CMiniFrameWnd` 返回非零  
  
 有关更多信息，请参见 `CMiniFrameWnd`的实现。  
  
## WM\_ACTIVATETOPLEVEL  
 当一窗口在其顶部“组”中激活或停用时，此信息发送到顶级窗口。  窗口是顶级组的一部分，如果是顶级窗口 \(没有父或所有者\)，则按此类窗口拥有。  此信息类似于在使用中属于不同进程的窗口中作为单一窗口层次结构进行的情况中 **WM\_ACTIVATEAPP,**，但工作 \(通用 OLE 在应用程序\)。  
  
## WM\_COMMANDHELP，WM\_HELPHITTEST，WM\_EXITHELPMODE  
 这些消息在上下文相关帮助实现的。   参考 [技术说明 28](../mfc/tn028-context-sensitive-help-support.md) 更多信息。  
  
## 私有 MFC 资源格式  
 目前，MFC 定义了两个私有资源格式：**RT\_TOOLBAR** 和 **RT\_DLGINIT**。  
  
## RT\_TOOLBAR 资源格式  
 AppWizard 提供的默认 **RT\_TOOLBAR** 工具栏根据自定义资源，在 MFC 4.0 中引入。  使用工具栏编辑器，可以编辑该资源。  
  
## RT\_DLGINIT 资源格式  
 一个私有 MFC 资源格式用于存储其他对话框的初始化信息。  在此组合框由存储初始字符串。  此资源格式并非旨在手动，但是由 Visual C\+\+ 编辑，处理。  
  
 因为有 API 替代使用资源，不需要此信息。Visual C\+\+ **RT\_DLGINIT** 和资源使用 MFC 相关功能。  使用 Visual C\+\+ 时更加容易编写，维护和从 \+ 长远 \+ 看转换应用程序。  
  
 **RT\_DLGINIT** 的基本资源结构如下所示：  
  
```  
+---------------+                    \  
| Control ID    |   UINT             |  
+---------------+                    |  
| Message #     |   UINT             |  
+---------------+                    |  
|length of data |   DWORD            |  
+---------------+                    |   Repeated  
|   Data        |   Variable Length  |   for each control  
|   ...         |   and Format       |   and message  
+---------------+                    /  
|     0         |   BYTE  
+---------------+  
```  
  
 一个重复的部分包含控件 ID 发送消息，消息为 \# 发送 \(普通窗口消息\) 和可变长度数据。  窗口发送窗体：  
  
```  
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);  
```  
  
 这会是一个非常常规格式，这允许任何窗口消息和数据内容。  Visual C\+\+ 资源编辑器仅和 MFC 支持有限部分 Windows 消息：初始列表选择的 CB\_ADDSTRING 组合框 \(数据是一个文本字符串。\)  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)