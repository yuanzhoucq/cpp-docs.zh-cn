---
title: "TN028：区分上下文的帮助支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.help"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "区分上下文的帮助, MFC 应用程序"
  - "资源标识符, 区分上下文的帮助"
  - "TN028"
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# TN028：区分上下文的帮助支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此注释该描述分配的帮助上下文 ID 和其他帮助规则问题。  上下文要求支持相关帮助可在 Visual C\+\+ 编译器的帮助。  
  
> [!NOTE]
>  除实现使用 WinHelp 的上下文相关帮助，使用 HTML 以外的 MFC 支持也帮助。  有关本支持和编程的 HTML 帮助的更多信息，请参见 [HTML 帮助：程序的上下文相关的帮助](../mfc/html-help-context-sensitive-help-for-your-programs.md)。  
  
## 支持类型的帮助  
 在 Windows 应用程序的上下文相关帮助实现的两种类型。  第一，称为“F1 帮助”中启动 WinHelp 使用基于当前活动的对象的相应的上下文。  第二个是“F1 Shift\+”模式。  在此模式下，将鼠标光标更改帮助光标和用户而单击对象。  此时，WinHelp 启动提供用户单击对象的帮助。  
  
 Microsoft 基础类 \(MFC\) 帮助实现这两种形式。  此外，框架支持简单的帮助，命令帮助索引和使用帮助。  
  
## 帮助文件  
 Microsoft 基础类具有一个帮助文件。  帮助文件必须具有名称和路径并应用程序相同。  例如，在中，如果可执行文件是 C:\\MyApplication\\MyHelp.exe 帮助文件必须是 C:\\MyApplication\\MyHelp.hlp.  通过 [CWinApp Class](../mfc/reference/cwinapp-class.md)的 `m_pszHelpFilePath` 成员变量设置的路径。  
  
## 帮助上下文大小  
 MFC 的默认实现需要程序遵循关于帮助上下文 ID 分配的一些规则。  这些规则是范围 ID 分配到特定控件。  通过提供各种帮助关联的成员函数不同的实现重写这些规则。  
  
```  
0x00000000 - 0x0000FFFF : user defined  
0x00010000 - 0x0001FFFF : commands (menus/command buttons)  
   0x00010000 + ID_  
   (note: 0x18000-> 0x1FFFF is the practical range since command IDs are >=0x8000)  
0x00020000 - 0x0002FFFF : windows and dialogs  
   0x00020000 + IDR_  
   (note: 0x20000-> 0x27FFF is the practical range since IDRs are <= 0x7FFF)  
0x00030000 - 0x0003FFFF : error messages (based on error string ID)  
   0x00030000 + IDP_  
0x00040000 - 0x0004FFFF : special purpose (non-client areas)  
   0x00040000 + HitTest area  
0x00050000 - 0x0005FFFF : controls (those that are not commands)  
   0x00040000 + IDW_  
```  
  
## 简单的“帮助”命令  
 包含由 Microsoft 基础类实现的简单命令帮助：  
  
-   按 [CWinApp::OnHelpIndex](../Topic/CWinApp::OnHelpIndex.md)实现的 ID\_HELP\_INDEX  
  
-   按 [CWinApp::OnHelpUsing](../Topic/CWinApp::OnHelpUsing.md)实现的 ID\_HELP\_USING  
  
 第一命令演示应用程序的帮助索引。  第二个示例演示在使用 WinHelp 程序的用户帮助。  
  
## 上下文相关帮助\(F1 Help\)  
 F1 键通常转换为具有 ID `ID_HELP` 的命令的快捷键。放在主窗口的快捷键对应表。  `ID_HELP` 命令可能用 ID `ID_HELP` 的按钮还在生成主窗口或对话框。  
  
 无论 `ID_HELP` 如何生成常规的路由命令，则为命令，直到到达命令处理程序。  有关 MFC 命令传送结构的更多信息，请参见 [技术说明 21](../mfc/tn021-command-and-message-routing.md)。  如果应用程序已启用的帮助，则 `ID_HELP` 命令将已被 [CWinApp::OnHelp](../Topic/CWinApp::OnHelp.md)处理。  Application 对象收到帮助消息正确然后路由命令。  因为默认路由命令用于确定最特定的上下文，不够的这是必需的。  
  
 `CWinApp::OnHelp` 尝试启动按下面的顺序 WinHelp:  
  
1.  检查使用 `AfxMessageBox` 活动调用的帮助 ID.  如果消息框处于活动状态，WinHelp 启动与上下文相应于该消息框。  
  
2.  WM\_COMMANDHELP 信息发送到活动窗口。  如果该窗口不响应通过启动 WinHelp，同一信息并发送到该窗口的上级，直到处理消息或当前窗口是顶级窗口。  
  
3.  发送 ID\_DEFAULT\_HELP 命令向主窗口。  这称为默认帮助。  此命令映射通常为 `CWinApp::OnHelpIndex`。  
  
 全局重写默认 ID 基数值 \(即 0x10000 命令的资源的 0x20000 如和对话框\)，应用程序应将 [CWinApp::WinHelp](../Topic/CWinApp::WinHelp.md)。  
  
 若要重写此功能和帮助上下文确定的方法，您应处理 WM\_COMMANDHELP 消息。  您与框架提供可提供希望更具体的帮助，路由，因为它仅访问相同深度与当前 MDI 子窗口。  可能还需要提供更具体的帮助为特定窗口或对话框，可以根据该对象当前内部状态或在对话框内的活动控件。  
  
## WM\_COMMANDHELP  
  
```  
  
afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)  
```  
  
 WM\_COMMANDHELP 是活动窗口收到的私有 MFC Windows 消息，同时帮助请求时。  当窗口收到此消息时，它可以调用使用与窗口的内部状态执行上下文的 `CWinApp::WinHelp`。  
  
 `lParam`  
 包含当前可用的帮助上下文。  如果不确定，其`lParam` 为零帮助上下文。  `OnCommandHelp` 的实现。`lParam` 使用的上下文确定 ID 不同的上下文也可以传递到 `CWinApp::WinHelp`。  
  
 `wParam`  
 使用和不为零。  
  
 如果 `OnCommandHelp` 函数调用 `CWinApp::WinHelp`，它将返回 `TRUE`。  返回 `TRUE` 停止此命令传送到其他类以及其他窗口。  
  
## 帮助模式 \(Shift\+F1 帮助\)  
 这是第二个窗体上下文相关的帮助。  通常，此模式将输入按 SHIFT\+F1 或通过菜单或工具栏。  它实现为命令 \(**ID\_CONTEXT\_HELP**\)。  消息筛选器挂钩不用于将此命令，在模式对话框或菜单为活动时，此命令才可用，因此用户在执行应用程序的主消息泵时 \(`CWinApp::Run`\)。  
  
 在输入此模式后，鼠标光标帮助显示在所有区域，应用，即使应用程序通常显示为该区域的光标 \(如在 Windows 周围的大小调整边框\)。  用户可以使用鼠标或键盘选择命令。  而不是执行命令，该命令的帮助显示。  此外，用户可以单击屏幕上的可视化对象，如工具栏上的按钮，而且，用于帮助为该对象中显示。  `CWinApp::OnContextHelp`帮助提供此模式。  
  
 在循环中执行，所有类型是停用，除键访问菜单的。  此外，命令转换通过 `PreTranslateMessage` 执行仍允许用户按快捷键以及获得该命令的帮助。  
  
 如果特定转换或在 SHIFT\+F1 帮助模式期间，出现在不应出现的 `PreTranslateMessage` 操作函数，您应在执行这些操作之前检查 `CWinApp` 的 `m_bHelpMode` 成员。  例如 `PreTranslateMessage` 的 `CDialog` 实现在调用 `IsDialogMessage`之前检查此。  在 SHIFT\+F1 模式下，这会禁用“对话框在无模式的对话框的导航”键。  此外，此循环内，`CWinApp::OnIdle` 仍调用。  
  
 如果用户从菜单中选择菜单命令，它将被处理为该命令的帮助 \(通过 **WM\_COMMANDHELP**，请参见下文\)。  如果用户单击应用程序窗口中可见区域，用于确定将与是否为非单击或客户端的单击。  `OnContextHelp` 句柄映射到客户的非工作单击自动单击。  如果它是客户单击它，然后将 **WM\_HELPHITTEST** 添加到单击的窗口。  如果该窗口返回一个非零值，则该值使用作为上下文。  如果返回零，`OnContextHelp` 尝试窗口 \(父和失败时，其父，等等\)。  如果帮助上下文都无法确定，默认会发送 **ID\_DEFAULT\_HELP** 命令向主窗口 \(通常为\)，则映射到 `CWinApp::OnHelpIndex`。  
  
## WM\_HELPHITTEST  
  
```  
  
afx_msg LRESULT CWnd::OnHelpHitTest(  
WPARAM, LPARAM lParam)  
```  
  
 **WM\_HELPHITTEST** 是在 SHIFT\+F1 帮助模式期间单击活动的窗口收到的私有 MFC Windows 消息。  当窗口收到此消息时，它返回一帮助 ID WinHelp 供使用。  
  
 lParam LOWORD \(\)  
 包含相对于鼠标单击窗口工作区的 X 轴设备坐标。  
  
 HIWORD lParam \(\)  
 Y 轴包含坐标。  
  
 `wParam`  
 使用和不为零。  如果返回值不为零，WinHelp 调用该上下文。  如果返回值为零，父窗口对于帮助查询。  
  
 在许多情况下，您可以利用您可能已经具有进行命中测试代码。  用于处理 **WM\_HELPHITTEST** 消息的示例参见 **CToolBar::OnHelpHitTest** 的实现 \(代码利用了按钮上和工具提示使用执行命中测试的代码。\) `CControlBar`。  
  
## MFC 应用程序向导支持和 MAKEHM  
 MFC 应用程序向导创建必要的文件生成帮助文件 \(.cnt 和 .hpj 文件\)。  它还包括被 Microsoft Help 编译器接受的预 .rtf 文件。  许多主题完成，但一些可能需要对特定的应用程序进行修改。  
  
 “Help”映射文件的自动创建调用由 MAKEHM 的实用工具支持。  MAKEHM 实用工具可以将应用程序的文件 RESOURCE.H 到帮助映射文件。  例如：  
  
```  
#define IDD_MY_DIALOG   2000  
#define ID_MY_COMMAND   150  
```  
  
 将转换为：  
  
```  
HIDD_MY_DIALOG    0x207d0  
HID_MY_COMMAND    0x10096  
```  
  
 此格式是使用帮助编译器的功能兼容，映射上下文 ID \(右侧的数字\) 的主题的名称 \(在左侧的符号\)。  
  
 MAKEHM 的源代码可在编程实用工具示例 [MAKEHM](../top/visual-cpp-samples.md)的 MFC。  
  
## 添加帮助支持在运行" MFC 应用程序向导后  
 的最佳方法将帮助添加到应用程序会检查在 MFC 应用程序向导的高级功能页面“区分上下文的帮助”选项在创建应用程序。  这样一来 MFC 应用程序向导自动将必要的消息映射项。`CWinApp`\- 对支持有助于的派生类。  
  
## 消息框上的帮助  
 消息框上的帮助 \(有时称为警报\) 通过 `AfxMessageBox` 的 `MessageBox` 函数，它使用 Windows API 的换行支持。  
  
 具有 `AfxMessageBox`，一个用于字符串 ID 的使用和其他的两个版本使用。字符串指针 \(`LPCSTR`\):  
  
```  
int AFXAPI AfxMessageBox(LPCSTR lpszText, UINT nType, UINT nIDHelp);  
int AFXAPI AfxMessageBox(UINT nIDPrompt, UINT nType, UINT nIDHelp);  
```  
  
 在这两种情况下，有帮助选项 ID.  
  
 在第一种情况 nIDHelp，默认的为 0，而指示此消息的帮助。  如果用户按 F1，在 \(例如消息为活动时，用户不会获取帮助 \(即使应用程序支持帮助\)。  如果这不需要的，应该为 nIDHelp 提供帮助 ID。  
  
 在第二种情况下，nIDHelp 的默认值是 \-1，指示帮助 ID 与 nIDPrompt。  帮助会起作用，只有当应用程序帮助启用，当然\)。  应为 nIDHelp 提供 0，如果希望消息没有帮助支持。  如果不希望 nIDPrompt 消息是启用的帮助，但希望不同的帮助 ID，请为 nIDHelp 提供正值与 nIDPrompt 不同。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)