---
title: "CWnd 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWnd 类"
  - "window objects [C++]"
  - "windows [C++]"
ms.assetid: 49a832ee-bc34-4126-88b3-bc1d9974f6c4
caps.latest.revision: 27
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWnd 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Microsoft 基础类库中所有窗口类的基本功能。  
  
## 语法  
  
```  
class CWnd : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CWnd::CWnd](../Topic/CWnd::CWnd.md)|构造 `CWnd` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWnd::accDoDefaultAction](../Topic/CWnd::accDoDefaultAction.md)|由框架调用以执行对象的默认操作。|  
|[CWnd::accHitTest](../Topic/CWnd::accHitTest.md)|由框架调用以检索屏幕上给定点处的子元素或子对象。|  
|[CWnd::accLocation](../Topic/CWnd::accLocation.md)|由框架调用以检索指定对象的当前屏幕位置。|  
|[CWnd::accNavigate](../Topic/CWnd::accNavigate.md)|由框架调用以移到容器内的另一个用户界面元素，如果可能还检索对象。|  
|[CWnd::accSelect](../Topic/CWnd::accSelect.md)|由框架调用以修改选定内容或移动指定对象的键盘焦点。|  
|[CWnd::AnimateWindow](../Topic/CWnd::AnimateWindow.md)|对关联窗口对象进行动画处理。|  
|[CWnd::ArrangeIconicWindows](../Topic/CWnd::ArrangeIconicWindows.md)|排列所有最小化（图标）子窗口。|  
|[CWnd::Attach](../Topic/CWnd::Attach.md)|将 Windows 句柄附加到 `CWnd` 对象。|  
|[CWnd::BeginModalState](../Topic/CWnd::BeginModalState.md)|调用此成员函数以使框架窗口具有模式。|  
|[CWnd::BeginPaint](../Topic/CWnd::BeginPaint.md)|为进行绘制准备好 `CWnd`。|  
|[CWnd::BindDefaultProperty](../Topic/CWnd::BindDefaultProperty.md)|将调用对象的默认简单绑定属性（按照在类型库中进行的标记）绑定到与数据源控件关联的光标。|  
|[CWnd::BindProperty](../Topic/CWnd::BindProperty.md)|将数据绑定控件上的光标绑定属性绑定到数据源控件，并向 MFC 绑定管理器注册该关系。|  
|[CWnd::BringWindowToTop](../Topic/CWnd::BringWindowToTop.md)|将 `CWnd` 置于一堆重叠窗口的顶部。|  
|[CWnd::CalcWindowRect](../Topic/CWnd::CalcWindowRect.md)|调用以从客户端矩形计算窗口矩形。|  
|[CWnd::CancelToolTips](../Topic/CWnd::CancelToolTips.md)|禁用工具提示控件。|  
|[CWnd::CenterWindow](../Topic/CWnd::CenterWindow.md)|使窗口相对于其父级居中。|  
|[CWnd::ChangeClipboardChain](../Topic/CWnd::ChangeClipboardChain.md)|从剪贴板查看器链中移除 `CWnd`。|  
|[CWnd::CheckDlgButton](../Topic/CWnd::CheckDlgButton.md)|将复选标记置于按钮控件旁，或从按钮控件移除复选标记。|  
|[CWnd::CheckRadioButton](../Topic/CWnd::CheckRadioButton.md)|选中指定单选按钮，并从指定按钮组中的所有其他单选按钮移除复选标记。|  
|[CWnd::ChildWindowFromPoint](../Topic/CWnd::ChildWindowFromPoint.md)|确定哪些（如果有）子窗口包含指定点。|  
|[CWnd::ClientToScreen](../Topic/CWnd::ClientToScreen.md)|将显示中的给定点或矩形的客户端坐标转换为屏幕坐标。|  
|[CWnd::CloseWindow](../Topic/CWnd::CloseWindow.md)|最小化窗口。|  
|[CWnd::ContinueModal](../Topic/CWnd::ContinueModal.md)|继续窗口的模式状态。|  
|[CWnd::Create](../Topic/CWnd::Create.md)|创建并初始化与 `CWnd` 对象关联的子窗口。|  
|[CWnd::CreateAccessibleProxy](../Topic/CWnd::CreateAccessibleProxy.md)|为指定对象创建 Active Accessibility 代理服务器。|  
|[CWnd::CreateCaret](../Topic/CWnd::CreateCaret.md)|为系统插入符号创建新形状并获取插入符号的所有权。|  
|[CWnd::CreateControl](../Topic/CWnd::CreateControl.md)|创建在 MFC 程序中由 `CWnd` 对象表示的 ActiveX 控件。|  
|[CWnd::CreateEx](../Topic/CWnd::CreateEx.md)|创建 Windows 重叠、弹出或子窗口，并将它附加到 `CWnd` 对象。|  
|[CWnd::CreateGrayCaret](../Topic/CWnd::CreateGrayCaret.md)|为系统插入符号创建灰色块并获取插入符号的所有权。|  
|[CWnd::CreateSolidCaret](../Topic/CWnd::CreateSolidCaret.md)|为系统插入符号创建实心块并获取插入符号的所有权。|  
|[CWnd::DeleteTempMap](../Topic/CWnd::DeleteTempMap.md)|由 `CWinApp` 空闲时间处理程序自动调用，删除任何由 `FromHandle` 创建的临时 `CWnd` 对象。|  
|[CWnd::DestroyWindow](../Topic/CWnd::DestroyWindow.md)|销毁附加的 Windows 窗口。|  
|[CWnd::Detach](../Topic/CWnd::Detach.md)|从 `CWnd` 对象分离 Windows 句柄并返回该句柄。|  
|[CWnd::DlgDirList](../Topic/CWnd::DlgDirList.md)|使用文件或目录列表填充列表框。|  
|[CWnd::DlgDirListComboBox](../Topic/CWnd::DlgDirListComboBox.md)|使用文件或目录列表填充组合框的列表框。|  
|[CWnd::DlgDirSelect](../Topic/CWnd::DlgDirSelect.md)|从列表框检索当前所选内容。|  
|[CWnd::DlgDirSelectComboBox](../Topic/CWnd::DlgDirSelectComboBox.md)|从组合框的列表框检索当前所选内容。|  
|[CWnd::DragAcceptFiles](../Topic/CWnd::DragAcceptFiles.md)|指示窗口将接受拖动的文件。|  
|[CWnd::DragDetect](../Topic/CWnd::DragDetect.md)|捕获鼠标并跟踪其移动，直到用户释放左键、按 ESC 键或将鼠标移动到围绕指定点的拖动矩形外部。|  
|[CWnd::DrawAnimatedRects](../Topic/CWnd::DrawAnimatedRects.md)|绘制透明框架矩形并对它进行动画处理，以指示图标的打开或是窗口的最小化或最大化。|  
|[CWnd::DrawCaption](../Topic/CWnd::DrawCaption.md)|绘制标题。|  
|[CWnd::DrawMenuBar](../Topic/CWnd::DrawMenuBar.md)|重绘菜单栏。|  
|[CWnd::EnableActiveAccessibility](../Topic/CWnd::EnableActiveAccessibility.md)|启用用户定义的 `Active Accessibility` 函数。|  
|[CWnd::EnableDynamicLayout](../Topic/CWnd::EnableDynamicLayout.md)|使子窗口的位置和大小可以在用户调整窗口大小时动态调整。|  
|[CWnd::EnableD2DSupport](../Topic/CWnd::EnableD2DSupport.md)|启用或禁用窗口 `D2D` 支持。  在初始化主窗口之前调用此方法。|  
|[CWnd::EnableScrollBar](../Topic/CWnd::EnableScrollBar.md)|启用或禁用滚动条的一个或两个箭头。|  
|[CWnd::EnableScrollBarCtrl](../Topic/CWnd::EnableScrollBarCtrl.md)|启用或禁用同级滚动条控件。|  
|[CWnd::EnableToolTips](../Topic/CWnd::EnableToolTips.md)|启用工具提示控件。|  
|[CWnd::EnableTrackingToolTips](../Topic/CWnd::EnableTrackingToolTips.md)|在跟踪模式下启用工具提示控件。|  
|[CWnd::EnableWindow](../Topic/CWnd::EnableWindow.md)|启用或禁用鼠标和键盘输入。|  
|[CWnd::EndModalLoop](../Topic/CWnd::EndModalLoop.md)|启用窗口的模式状态。|  
|[CWnd::EndModalState](../Topic/CWnd::EndModalState.md)|调用此成员函数以将框架窗口从有模式更改为无模式。|  
|[CWnd::EndPaint](../Topic/CWnd::EndPaint.md)|标记绘制的末尾。|  
|[CWnd::ExecuteDlgInit](../Topic/CWnd::ExecuteDlgInit.md)|启动对话框资源。|  
|[CWnd::FilterToolTipMessage](../Topic/CWnd::FilterToolTipMessage.md)|检索与对话框中的控件关联的标题或文本。|  
|[CWnd::FindWindow](../Topic/CWnd::FindWindow.md)|返回由其窗口名和窗口类标识的窗口的句柄。|  
|[CWnd::FindWindowEx](../Topic/CWnd::FindWindowEx.md)|返回由其窗口名和窗口类标识的窗口的句柄。|  
|[CWnd::FlashWindow](../Topic/CWnd::FlashWindow.md)|使窗口闪烁一次。|  
|[CWnd::FlashWindowEx](../Topic/CWnd::FlashWindowEx.md)|使具有其他功能的窗口闪烁。|  
|[CWnd::FromHandle](../Topic/CWnd::FromHandle.md)|在提供了窗口的句柄时返回指向 `CWnd` 对象的指针。  如果 `CWnd` 对象未附加到该句柄，则会创建并附加一个临时 `CWnd` 对象。|  
|[CWnd::FromHandlePermanent](../Topic/CWnd::FromHandlePermanent.md)|在提供了窗口的句柄时返回指向 `CWnd` 对象的指针。  如果 `CWnd` 对象未附加到该句柄，则会创建并附加一个临时 `CWnd` 对象。|  
|[CWnd::get\_accChild](../Topic/CWnd::get_accChild.md)|由框架调用以检索指定子级的 `IDispatch` 接口地址。|  
|[CWnd::get\_accChildCount](../Topic/CWnd::get_accChildCount.md)|由框架调用调用以检索属于该对象的子级的个数。|  
|[CWnd::get\_accDefaultAction](../Topic/CWnd::get_accDefaultAction.md)|由框架调用以检索描述对象默认操作的字符串。|  
|[CWnd::get\_accDescription](../Topic/CWnd::get_accDescription.md)|由框架调用以检索描述指定对象的可视外观的字符串。|  
|[CWnd::get\_accFocus](../Topic/CWnd::get_accFocus.md)|由框架调用以检索具有键盘焦点的对象。|  
|[CWnd::get\_accHelp](../Topic/CWnd::get_accHelp.md)|由框架调用以检索对象的 **Help** 属性字符串。|  
|[CWnd::get\_accHelpTopic](../Topic/CWnd::get_accHelpTopic.md)|由框架调用以检索与指定对象关联的 `WinHelp` 文件的完整路径以及该文件内相应主题的标识符。|  
|[CWnd::get\_accKeyboardShortcut](../Topic/CWnd::get_accKeyboardShortcut.md)|由框架调用以检索指定对象的快捷键或访问键。|  
|[CWnd::get\_accName](../Topic/CWnd::get_accName.md)|由框架调用以检索指定对象的名称。|  
|[CWnd::get\_accParent](../Topic/CWnd::get_accParent.md)|由框架调用以检索对象父级的 `IDispatch` 接口。|  
|[CWnd::get\_accRole](../Topic/CWnd::get_accRole.md)|由框架调用以检索描述指定对象的角色的信息。|  
|[CWnd::get\_accSelection](../Topic/CWnd::get_accSelection.md)|由框架调用以检索该对象的选定子级。|  
|[CWnd::get\_accState](../Topic/CWnd::get_accState.md)|由框架调用以检索指定对象的当前状态。|  
|[CWnd::get\_accValue](../Topic/CWnd::get_accValue.md)|由框架调用以检索指定对象的值。|  
|[CWnd::GetActiveWindow](../Topic/CWnd::GetActiveWindow.md)|检索活动窗口。|  
|[CWnd::GetAncestor](../Topic/CWnd::GetAncestor.md)|检索指定窗口的上级先窗口对象。|  
|[CWnd::GetCapture](../Topic/CWnd::GetCapture.md)|检索具有鼠标捕获的 `CWnd`。|  
|[CWnd::GetCaretPos](../Topic/CWnd::GetCaretPos.md)|检索插入符号的当前位置的客户端坐标。|  
|[CWnd::GetCheckedRadioButton](../Topic/CWnd::GetCheckedRadioButton.md)|返回按钮中当前选中的单选按钮的 ID。|  
|[CWnd::GetClientRect](../Topic/CWnd::GetClientRect.md)|获取 `CWnd` 工作区的尺寸。|  
|[CWnd::GetClipboardOwner](../Topic/CWnd::GetClipboardOwner.md)|检索指向剪贴板当前所有者的指针。|  
|[CWnd::GetClipboardViewer](../Topic/CWnd::GetClipboardViewer.md)|检索指向剪贴板查看器链中第一个窗口的指针。|  
|[CWnd::GetControlUnknown](../Topic/CWnd::GetControlUnknown.md)|检索指向未知 ActiveX 控件的指针。|  
|[CWnd::GetDC](../Topic/CWnd::GetDC.md)|检索工作区的显示上下文。|  
|[CWnd::GetDCEx](../Topic/CWnd::GetDCEx.md)|检索工作区的显示上下文，并在绘制启用剪辑。|  
|[CWnd::GetDCRenderTarget](../Topic/CWnd::GetDCRenderTarget.md)|检索 `CWnd` 窗口的设备上下文 \(DC\) 呈现目标。|  
|[CWnd::GetDescendantWindow](../Topic/CWnd::GetDescendantWindow.md)|搜索所有子代窗口，并返回具有指定 ID 的窗口。|  
|[CWnd::GetDesktopWindow](../Topic/CWnd::GetDesktopWindow.md)|检索 Windows 桌面窗口。|  
|[CWnd::GetDlgCtrlID](../Topic/CWnd::GetDlgCtrlID.md)|如果 `CWnd` 是子窗口，则调用此函数会返回其 ID 值。|  
|[CWnd::GetDlgItem](../Topic/CWnd::GetDlgItem.md)|从指定对话框中检索具有指定 ID 的控件。|  
|[CWnd::GetDlgItemInt](../Topic/CWnd::GetDlgItemInt.md)|将给定对话框中控件的文本转换为整数值。|  
|[CWnd::GetDlgItemText](../Topic/CWnd::GetDlgItemText.md)|检索与控件关联的标题或文本。|  
|[CWnd::GetDSCCursor](../Topic/CWnd::GetDSCCursor.md)|检索指向由数据源控件的 DataSource、UserName、Password 和 SQL 属性定义的基础光标的指针。|  
|[CWnd::GetDynamicLayout](../Topic/CWnd::GetDynamicLayout.md)|检索指向动态布局管理器对象的指针。|  
|[CWnd::GetExStyle](../Topic/CWnd::GetExStyle.md)|返回窗口的扩展样式。|  
|[CWnd::GetFocus](../Topic/CWnd::GetFocus.md)|检索当前具有输入焦点的 `CWnd`。|  
|[CWnd::GetFont](../Topic/CWnd::GetFont.md)|检索当前字体。|  
|[CWnd::GetForegroundWindow](../Topic/CWnd::GetForegroundWindow.md)|返回指向前台窗口（用户当前正在使用的顶级窗口）的指针。|  
|[CWnd::GetIcon](../Topic/CWnd::GetIcon.md)|检索图标的句柄。|  
|[CWnd::GetLastActivePopup](../Topic/CWnd::GetLastActivePopup.md)|确定最近处于活动状态的由 `CWnd` 拥有的弹出窗口。|  
|[CWnd::GetLayeredWindowAttributes](../Topic/CWnd::GetLayeredWindowAttributes.md)|检索分层窗口的不透明度和透明度颜色键。|  
|[CWnd::GetMenu](../Topic/CWnd::GetMenu.md)|检索指向指定菜单的指针。|  
|[CWnd::GetNextDlgGroupItem](../Topic/CWnd::GetNextDlgGroupItem.md)|在控件组中搜索的下一个（或上一个）控件。|  
|[CWnd::GetNextDlgTabItem](../Topic/CWnd::GetNextDlgTabItem.md)|检索位于指定控件之后（或之前）的具有 [WS\_TABSTOP](../../mfc/reference/window-styles.md) 样式的第一个控件。|  
|[CWnd::GetNextWindow](../Topic/CWnd::GetNextWindow.md)|返回窗口管理器列表中的下一个（或上一个）窗口。|  
|[CWnd::GetOleControlSite](../Topic/CWnd::GetOleControlSite.md)|检索指定 ActiveX 控件的自定义站点。|  
|[CWnd::GetOpenClipboardWindow](../Topic/CWnd::GetOpenClipboardWindow.md)|检索指向当前打开剪贴板的窗口的指针。|  
|[CWnd::GetOwner](../Topic/CWnd::GetOwner.md)|检索指向 `CWnd` 所有者的指针。|  
|[CWnd::GetParent](../Topic/CWnd::GetParent.md)|检索 `CWnd` 的父窗口（如果有）。|  
|[CWnd::GetParentFrame](../Topic/CWnd::GetParentFrame.md)|检索 `CWnd` 对象的父框架窗口。|  
|[CWnd::GetParentOwner](../Topic/CWnd::GetParentOwner.md)|返回指向子窗口的父窗口的指针。|  
|[CWnd::GetProperty](../Topic/CWnd::GetProperty.md)|检索 ActiveX 控件属性。|  
|[CWnd::GetRenderTarget](../Topic/CWnd::GetRenderTarget.md)|获取与此窗口相关联的呈现目标。|  
|[CWnd::GetSafeHwnd](../Topic/CWnd::GetSafeHwnd.md)|返回 `m_hWnd`，如果 `this` 指针是 `NULL`，则返回 `NULL`。|  
|[CWnd::GetSafeOwner](../Topic/CWnd::GetSafeOwner.md)|检索给定窗口的安全所有者。|  
|[CWnd::GetScrollBarCtrl](../Topic/CWnd::GetScrollBarCtrl.md)|返回同级滚动条控件。|  
|[CWnd::GetScrollBarInfo](../Topic/CWnd::GetScrollBarInfo.md)|检索有关指定滚动条的信息。|  
|[CWnd::GetScrollInfo](../Topic/CWnd::GetScrollInfo.md)|检索 `SCROLLINFO` 结构维护的有关滚动条的信息。|  
|[CWnd::GetScrollLimit](../Topic/CWnd::GetScrollLimit.md)|检索滚动条的限制。|  
|[CWnd::GetScrollPos](../Topic/CWnd::GetScrollPos.md)|检索滚动框的当前位置。|  
|[CWnd::GetScrollRange](../Topic/CWnd::GetScrollRange.md)|复制给定滚动条的当前最小和最大滚动条位置。|  
|[CWnd::GetStyle](../Topic/CWnd::GetStyle.md)|返回当前窗口样式。|  
|[CWnd::GetSystemMenu](../Topic/CWnd::GetSystemMenu.md)|允许应用程序访问控件菜单以进行复制和修改。|  
|[CWnd::GetTitleBarInfo](../Topic/CWnd::GetTitleBarInfo.md)|检索有关指定标题栏的信息。|  
|[CWnd::GetTopLevelFrame](../Topic/CWnd::GetTopLevelFrame.md)|检索窗口的顶级框架窗口。|  
|[CWnd::GetTopLevelOwner](../Topic/CWnd::GetTopLevelOwner.md)|检索顶级窗口。|  
|[CWnd::GetTopLevelParent](../Topic/CWnd::GetTopLevelParent.md)|检索窗口的顶级父级。|  
|[CWnd::GetTopWindow](../Topic/CWnd::GetTopWindow.md)|返回属于 `CWnd` 的第一个子窗口。|  
|[CWnd::GetUpdateRect](../Topic/CWnd::GetUpdateRect.md)|检索完全包围 `CWnd` 更新区域的最小矩形的坐标。|  
|[CWnd::GetUpdateRgn](../Topic/CWnd::GetUpdateRgn.md)|检索 `CWnd` 更新区域。|  
|[CWnd::GetWindow](../Topic/CWnd::GetWindow.md)|返回与此窗口具有指定关系的窗口。|  
|[CWnd::GetWindowContextHelpId](../Topic/CWnd::GetWindowContextHelpId.md)|检索帮助上下文标识符。|  
|[CWnd::GetWindowDC](../Topic/CWnd::GetWindowDC.md)|检索整个窗口的显示上下文，包括标题栏、菜单和滚动条。|  
|[CWnd::GetWindowedChildCount](../Topic/CWnd::GetWindowedChildCount.md)|返回关联子窗口的数量。|  
|[CWnd::GetWindowInfo](../Topic/CWnd::GetWindowInfo.md)|返回有关窗口的信息。|  
|[CWnd::GetWindowlessChildCount](../Topic/CWnd::GetWindowlessChildCount.md)|返回关联无窗口子窗口的数量。|  
|[CWnd::GetWindowPlacement](../Topic/CWnd::GetWindowPlacement.md)|检索窗口的显示状态以及正常（已还原）、最小化和最大化位置。|  
|[CWnd::GetWindowRect](../Topic/CWnd::GetWindowRect.md)|获取 `CWnd` 的屏幕坐标。|  
|[CWnd::GetWindowRgn](../Topic/CWnd::GetWindowRgn.md)|检索窗口的窗口区域的副本。|  
|[CWnd::GetWindowText](../Topic/CWnd::GetWindowText.md)|返回窗口文本或标题（如果有）。|  
|[CWnd::GetWindowTextLength](../Topic/CWnd::GetWindowTextLength.md)|返回窗口文本或标题的长度。|  
|[CWnd::HideCaret](../Topic/CWnd::HideCaret.md)|通过从显示屏幕中移除来隐藏插入符号。|  
|[CWnd::HiliteMenuItem](../Topic/CWnd::HiliteMenuItem.md)|突出显示顶级（菜单栏）菜单项或从顶级（菜单栏）菜单项移除突出显示。|  
|[CWnd::HtmlHelp](../Topic/CWnd::HtmlHelp.md)|调用以启动 HTMLHelp 应用程序。|  
|[CWnd::Invalidate](../Topic/CWnd::Invalidate.md)|使整个工作区无效。|  
|[CWnd::InvalidateRect](../Topic/CWnd::InvalidateRect.md)|通过将给定矩形添加到当前更新区域，使该矩形内的工作区无效。|  
|[CWnd::InvalidateRgn](../Topic/CWnd::InvalidateRgn.md)|通过将给定区域添加到当前更新区域，使该区域内的工作区无效。|  
|[CWnd::InvokeHelper](../Topic/CWnd::InvokeHelper.md)|调用 ActiveX 控件方法或属性。|  
|[CWnd::IsChild](../Topic/CWnd::IsChild.md)|指示 `CWnd` 是否为指定窗口的子窗口或其他直接子代。|  
|[CWnd::IsD2DSupportEnabled](../Topic/CWnd::IsD2DSupportEnabled.md)|确定是否启用 `D2D` 支持。|  
|[CWnd::IsDialogMessage](../Topic/CWnd::IsDialogMessage.md)|确定给定消息是否用于无模式对话框，如果是，则处理它。|  
|[CWnd::IsDlgButtonChecked](../Topic/CWnd::IsDlgButtonChecked.md)|确定是否选中按钮控件。|  
|[CWnd::IsDynamicLayoutEnabled](../Topic/CWnd::IsDynamicLayoutEnabled.md)|确定是否在此窗口上启用动态布局。  如果启用动态布局，则子窗口的位置和大小可以在用户调整父窗口大小时进行更改。|  
|[CWnd::IsIconic](../Topic/CWnd::IsIconic.md)|确定 `CWnd` 是否进行最小化（图标化）。|  
|[CWnd::IsTouchWindow](../Topic/CWnd::IsTouchWindow.md)|指定 `CWnd` 是否具有触摸支持。|  
|[CWnd::IsWindowEnabled](../Topic/CWnd::IsWindowEnabled.md)|确定是否针对鼠标和键盘输入启用窗口。|  
|[CWnd::IsWindowVisible](../Topic/CWnd::IsWindowVisible.md)|确定窗口是否可见。|  
|[CWnd::IsZoomed](../Topic/CWnd::IsZoomed.md)|确定 `CWnd` 是否进行最大化。|  
|[CWnd::KillTimer](../Topic/CWnd::KillTimer.md)|终止系统计时器。|  
|[CWnd::LockWindowUpdate](../Topic/CWnd::LockWindowUpdate.md)|在给定窗口中禁用或重新启用绘制。|  
|[CWnd::MapWindowPoints](../Topic/CWnd::MapWindowPoints.md)|将一组点从 `CWnd` 的坐标空间转换（映射）到另一个窗口的坐标空间。|  
|[CWnd::MessageBox](../Topic/CWnd::MessageBox.md)|创建并显示包含应用程序提供的消息和标题的窗口。|  
|[CWnd::ModifyStyle](../Topic/CWnd::ModifyStyle.md)|修改当前窗口样式。|  
|[CWnd::ModifyStyleEx](../Topic/CWnd::ModifyStyleEx.md)|修改窗口的扩展样式。|  
|[CWnd::MoveWindow](../Topic/CWnd::MoveWindow.md)|更改 `CWnd` 的位置和尺寸。|  
|[CWnd::NotifyWinEvent](../Topic/CWnd::NotifyWinEvent.md)|向系统发出信号，指出发生了预定义事件。|  
|[CWnd::OnAmbientProperty](../Topic/CWnd::OnAmbientProperty.md)|实现环境属性值。|  
|[CWnd::OnDrawIconicThumbnailOrLivePreview](../Topic/CWnd::OnDrawIconicThumbnailOrLivePreview.md)|由框架在需要获取要在 Windows 7 选项卡缩略图上或客户端上（进行应用程序速览）显示的位图时进行调用。|  
|[CWnd::OnHelp](../Topic/CWnd::OnHelp.md)|处理应用程序中的 F1 帮助（使用当前上下文）。|  
|[CWnd::OnHelpFinder](../Topic/CWnd::OnHelpFinder.md)|处理 `ID_HELP_FINDER` 和 `ID_DEFAULT_HELP` 命令。|  
|[CWnd::OnHelpIndex](../Topic/CWnd::OnHelpIndex.md)|处理 `ID_HELP_INDEX` 命令，并提供默认帮助主题。|  
|[CWnd::OnHelpUsing](../Topic/CWnd::OnHelpUsing.md)|处理 `ID_HELP_USING` 命令。|  
|[CWnd::OnToolHitTest](../Topic/CWnd::OnToolHitTest.md)|确定点是否在指定工具的边框内并检索有关此工具的信息。|  
|[CWnd::OpenClipboard](../Topic/CWnd::OpenClipboard.md)|打开剪贴板。  其他应用程序将无法修改剪贴板，直到调用 Windows [CloseClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649035) 函数。|  
|[CWnd::PaintWindowlessControls](../Topic/CWnd::PaintWindowlessControls.md)|在控件容器上绘制无窗口控件。|  
|[CWnd::PostMessage](../Topic/CWnd::PostMessage.md)|将消息置于应用程序队列中，然后返回而不等待窗口处理该消息。|  
|[CWnd::PreCreateWindow](../Topic/CWnd::PreCreateWindow.md)|在创建附加到此 `CWnd` 对象的 Windows 窗口之前调用。|  
|[CWnd::PreSubclassWindow](../Topic/CWnd::PreSubclassWindow.md)|允许在调用 [SubclassWindow](../Topic/CWnd::SubclassWindow.md) 之前创建其他必要的子类。|  
|[CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)|由 `CWinApp` 用于在窗口消息调度到 `TranslateMessage` 和 `DispatchMessage` Windows 函数之前筛选它们。|  
|[CWnd::Print](../Topic/CWnd::Print.md)|在指定设备上下文中绘制当前窗口。|  
|[CWnd::PrintClient](../Topic/CWnd::PrintClient.md)|在指定设备上下文（通常是打印机设备上下文）中绘制任何窗口。|  
|[CWnd::PrintWindow](../Topic/CWnd::PrintWindow.md)|将可视窗口复制到指定设备上下文（通常是打印机设备上下文）。|  
|[CWnd::RedrawWindow](../Topic/CWnd::RedrawWindow.md)|更新工作区中的指定矩形或区域。|  
|[CWnd::RegisterTouchWindow](../Topic/CWnd::RegisterTouchWindow.md)|注册\/注销窗口 Windows 触摸支持。|  
|[CWnd::ReleaseDC](../Topic/CWnd::ReleaseDC.md)|释放客户端和窗口设备上下文，从而使它们可供其他应用程序使用。|  
|[CWnd::RepositionBars](../Topic/CWnd::RepositionBars.md)|在工作区中重新定位控件条。|  
|[CWnd::RunModalLoop](../Topic/CWnd::RunModalLoop.md)|为处于模式状态的窗口检索、转换或调度消息。|  
|[CWnd::ScreenToClient](../Topic/CWnd::ScreenToClient.md)|将显示中的给定点或矩形的屏幕坐标转换为客户端坐标。|  
|[CWnd::ScrollWindow](../Topic/CWnd::ScrollWindow.md)|滚动工作区的内容。|  
|[CWnd::ScrollWindowEx](../Topic/CWnd::ScrollWindowEx.md)|滚动工作区的内容。  类似于 `ScrollWindow`，不过具有附加功能。|  
|[CWnd::SendChildNotifyLastMsg](../Topic/CWnd::SendChildNotifyLastMsg.md)|从父窗口向子窗口提供通知消息，以便子窗口可以处理任务。|  
|[CWnd::SendDlgItemMessage](../Topic/CWnd::SendDlgItemMessage.md)|将消息发送到指定控件。|  
|[CWnd::SendMessage](../Topic/CWnd::SendMessage.md)|将消息发送到 `CWnd` 对象并且不返回，直到它处理了消息。|  
|[CWnd::SendMessageToDescendants](../Topic/CWnd::SendMessageToDescendants.md)|将消息发送到窗口的所有子代窗口。|  
|[CWnd::SendNotifyMessage](../Topic/CWnd::SendNotifyMessage.md)|将指定消息发送到窗口并尽快返回，具体取决于调用线程是否创建了窗口。|  
|[CWnd::SetActiveWindow](../Topic/CWnd::SetActiveWindow.md)|激活窗口。|  
|[CWnd::SetCapture](../Topic/CWnd::SetCapture.md)|使所有后续鼠标输入都发送到 `CWnd`。|  
|[CWnd::SetCaretPos](../Topic/CWnd::SetCaretPos.md)|将插入符号移动到指定位置。|  
|[CWnd::SetClipboardViewer](../Topic/CWnd::SetClipboardViewer.md)|将 `CWnd` 添加到每当剪贴板内容发生更改时便会收到通知的窗口的链。|  
|[CWnd::SetDlgCtrlID](../Topic/CWnd::SetDlgCtrlID.md)|为窗口（可以是任何子窗口，而不仅是对话框中的控件）设置窗口或控件 ID。|  
|[CWnd::SetDlgItemInt](../Topic/CWnd::SetDlgItemInt.md)|将控件的文本设置为表示整数值的字符串。|  
|[CWnd::SetDlgItemText](../Topic/CWnd::SetDlgItemText.md)|在指定对话框中设置控件的标题或文本。|  
|[CWnd::SetFocus](../Topic/CWnd::SetFocus.md)|声明输入焦点。|  
|[CWnd::SetFont](../Topic/CWnd::SetFont.md)|设置当前字体。|  
|[CWnd::SetForegroundWindow](../Topic/CWnd::SetForegroundWindow.md)|将创建窗口的线程置于前台，并激活窗口。|  
|[CWnd::SetIcon](../Topic/CWnd::SetIcon.md)|设置特定图标的句柄。|  
|[CWnd::SetLayeredWindowAttributes](../Topic/CWnd::SetLayeredWindowAttributes.md)|设置分层窗口的不透明度和透明度颜色键。|  
|[CWnd::SetMenu](../Topic/CWnd::SetMenu.md)|将菜单设置为指定菜单。|  
|[CWnd::SetOwner](../Topic/CWnd::SetOwner.md)|更改 `CWnd` 的所有者。|  
|[CWnd::SetParent](../Topic/CWnd::SetParent.md)|更改父窗口。|  
|[CWnd::SetProperty](../Topic/CWnd::SetProperty.md)|设置 ActiveX 控件属性。|  
|[CWnd::SetRedraw](../Topic/CWnd::SetRedraw.md)|允许重绘 `CWnd` 中的更改，或阻止重绘更改。|  
|[CWnd::SetScrollInfo](../Topic/CWnd::SetScrollInfo.md)|设置有关滚动条的信息。|  
|[CWnd::SetScrollPos](../Topic/CWnd::SetScrollPos.md)|设置滚动框的当前位置，并且（如果指定）重绘滚动条以反映新位置。|  
|[CWnd::SetScrollRange](../Topic/CWnd::SetScrollRange.md)|设置给定滚动条的最小和最大位置值。|  
|[CWnd::SetTimer](../Topic/CWnd::SetTimer.md)|安装在触发时发送 [WM\_TIMER](../Topic/CWnd::OnTimer.md) 消息的系统计时器。|  
|[CWnd::SetWindowContextHelpId](../Topic/CWnd::SetWindowContextHelpId.md)|设置帮助上下文标识符。|  
|[CWnd::SetWindowPlacement](../Topic/CWnd::SetWindowPlacement.md)|设置窗口的显示状态以及正常（已还原）、最小化和最大化位置。|  
|[CWnd::SetWindowPos](../Topic/CWnd::SetWindowPos.md)|更改子窗口、弹出窗口和顶级窗口的大小、位置和的顺序。|  
|[CWnd::SetWindowRgn](../Topic/CWnd::SetWindowRgn.md)|设置窗口的区域。|  
|[CWnd::SetWindowText](../Topic/CWnd::SetWindowText.md)|将窗口文本或标题（如果有）设置为指定文本。|  
|[CWnd::ShowCaret](../Topic/CWnd::ShowCaret.md)|在显示上插入符号的当前位置处显示插入符号。  显示之后，插入符号开始自动闪烁。|  
|[CWnd::ShowOwnedPopups](../Topic/CWnd::ShowOwnedPopups.md)|显示或隐藏窗口所拥有的所有弹出窗口。|  
|[CWnd::ShowScrollBar](../Topic/CWnd::ShowScrollBar.md)|显示或隐藏滚动条。|  
|[CWnd::ShowWindow](../Topic/CWnd::ShowWindow.md)|显示或隐藏窗口。|  
|[CWnd::SubclassDlgItem](../Topic/CWnd::SubclassDlgItem.md)|将 Windows 控件附加到 `CWnd` 对象，并使它通过 `CWnd` 的消息映射来路由消息。|  
|[CWnd::SubclassWindow](../Topic/CWnd::SubclassWindow.md)|将窗口附加到 `CWnd` 对象，并使它通过 `CWnd` 的消息映射来路由消息。|  
|[CWnd::UnlockWindowUpdate](../Topic/CWnd::UnlockWindowUpdate.md)|解锁使用 `CWnd::LockWindowUpdate` 锁定的窗口。|  
|[CWnd::UnsubclassWindow](../Topic/CWnd::UnsubclassWindow.md)|从 `CWnd` 对象分离窗口|  
|[CWnd::UpdateData](../Topic/CWnd::UpdateData.md)|从对话框初始化或检索数据。|  
|[CWnd::UpdateDialogControls](../Topic/CWnd::UpdateDialogControls.md)|调用以更新对话框按钮和其他控件的状态。|  
|[CWnd::UpdateLayeredWindow](../Topic/CWnd::UpdateLayeredWindow.md)|更新分层窗口的位置、大小、形状、内容和透明度。|  
|[CWnd::UpdateWindow](../Topic/CWnd::UpdateWindow.md)|更新工作区。|  
|[CWnd::ValidateRect](../Topic/CWnd::ValidateRect.md)|通过从当前更新区域移除给定矩形，来验证该矩形内的工作区。|  
|[CWnd::ValidateRgn](../Topic/CWnd::ValidateRgn.md)|通过从当前更新区域移除给定区域，来验证该区域内的工作区。|  
|[CWnd::WindowFromPoint](../Topic/CWnd::WindowFromPoint.md)|标识包含给定点的窗口。|  
|[CWnd::WinHelp](../Topic/CWnd::WinHelp.md)|调用以启动 WinHelp 应用程序。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CWnd::Default](../Topic/CWnd::Default.md)|调用默认窗口过程，该过程为应用程序不处理的任何窗口消息提供默认处理。|  
|[CWnd::DefWindowProc](../Topic/CWnd::DefWindowProc.md)|调用默认窗口过程，该过程为应用程序不处理的任何窗口消息提供默认处理。|  
|[CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md)|用于对话框数据交换和验证。  由 `UpdateData` 调用。|  
|[CWnd::GetCurrentMessage](../Topic/CWnd::GetCurrentMessage.md)|返回指向此窗口当前正在处理的消息的指针。  只应在处于 `On`*Message* 消息处理程序成员函数中时才进行调用。|  
|[CWnd::InitDynamicLayout](../Topic/CWnd::InitDynamicLayout.md)|由框架调用以初始化窗口的动态布局。|  
|[CWnd::LoadDynamicLayoutResource](../Topic/CWnd::LoadDynamicLayoutResource.md)|从资源文件加载动态布局信息。|  
|[CWnd::OnActivate](../Topic/CWnd::OnActivate.md)|当正在激活或停用 `CWnd` 时调用。|  
|[CWnd::OnActivateApp](../Topic/CWnd::OnActivateApp.md)|要激活或停用应用程序时调用。|  
|[CWnd::OnAppCommand](../Topic/CWnd::OnAppCommand.md)|当用户生成应用程序命令事件时调用。|  
|[CWnd::OnAskCbFormatName](../Topic/CWnd::OnAskCbFormatName.md)|由剪贴板查看器应用程序在剪贴板所有者显示剪贴板内容时调用。|  
|[CWnd::OnCancelMode](../Topic/CWnd::OnCancelMode.md)|调用以允许 `CWnd` 取消任何内部模式（如鼠标捕获）。|  
|[CWnd::OnCaptureChanged](../Topic/CWnd::OnCaptureChanged.md)|将消息发送到要失去鼠标捕获的窗口。|  
|[CWnd::OnChangeCbChain](../Topic/CWnd::OnChangeCbChain.md)|通知正在从链中移除指定窗口。|  
|[CWnd::OnChangeUIState](../Topic/CWnd::OnChangeUIState.md)|在应更改用户界面 \(UI\) 状态时调用。|  
|[CWnd::OnChar](../Topic/CWnd::OnChar.md)|当击键转换为非系统字符时调用。|  
|[CWnd::OnCharToItem](../Topic/CWnd::OnCharToItem.md)|由具有 [LBS\_WANTKEYBOARDINPUT](../../mfc/reference/list-box-styles.md) 样式的子列表框调用以响应 [WM\_CHAR](../Topic/CWnd::OnChar.md) 消息。|  
|[CWnd::OnChildActivate](../Topic/CWnd::OnChildActivate.md)|每当 `CWnd` 大小或位置更改或 `CWnd` 激活时，针对多文档界面 \(MDI\) 子窗口进行调用。|  
|[CWnd::OnChildNotify](../Topic/CWnd::OnChildNotify.md)|由父窗口调用以使通知控件有机会响应控件通知。|  
|[CWnd::OnClipboardUpdate](../Topic/CWnd::OnClipboardUpdate.md)|在剪贴板内容已更改时调用。|  
|[CWnd::OnClose](../Topic/CWnd::OnClose.md)|作为指示 `CWnd` 应关闭的信号进行调用。|  
|[CWnd::OnColorizationColorChanged](../Topic/CWnd::OnColorizationColorChanged.md)|在非工作区的呈现策略已更改时调用。|  
|[CWnd::OnCommand](../Topic/CWnd::OnCommand.md)|当用户选择命令时调用。|  
|[CWnd::OnCompacting](../Topic/CWnd::OnCompacting.md)|当 Windows 检测到系统内存不足时调用。|  
|[CWnd::OnCompareItem](../Topic/CWnd::OnCompareItem.md)|调用以确定新项在子所有者描述组合框或列表框中的相对位置。|  
|[CWnd::OnCompositionChanged](../Topic/CWnd::OnCompositionChanged.md)|在桌面窗口管理器 \(DWM\) 组合已启用或已禁用时针对所有顶级窗口进行调用。|  
|[CWnd::OnContextMenu](../Topic/CWnd::OnContextMenu.md)|当用户窗口中单击鼠标右键时调用。|  
|[CWnd::OnCopyData](../Topic/CWnd::OnCopyData.md)|将数据从一个应用程序复制到另一个应用程序。|  
|[CWnd::OnCreate](../Topic/CWnd::OnCreate.md)|在窗口创建过程中调用。|  
|[CWnd::OnCtlColor](../Topic/CWnd::OnCtlColor.md)|如果 `CWnd` 在要绘制控件时是控件的父级，则进行调用。|  
|[CWnd::OnDeadChar](../Topic/CWnd::OnDeadChar.md)|当击键转换为非系统语音符号字符（如重音字符）时调用。|  
|[CWnd::OnDeleteItem](../Topic/CWnd::OnDeleteItem.md)|当销毁所有者描述子列表框或组合框时，或是当从控件中移除项时调用。|  
|[CWnd::OnDestroy](../Topic/CWnd::OnDestroy.md)|当销毁 `CWnd` 时调用。|  
|[CWnd::OnDestroyClipboard](../Topic/CWnd::OnDestroyClipboard.md)|当通过调用 Windows [EmptyClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649037) 函数来清空剪贴板时调用。|  
|[CWnd::OnDeviceChange](../Topic/CWnd::OnDeviceChange.md)|向应用程序或设备驱动程序通知设备或计算机的硬件配置已更改。|  
|[CWnd::OnDevModeChange](../Topic/CWnd::OnDevModeChange.md)|当用户更改设备模式设置时针对所有顶级窗口进行调用。|  
|[CWnd::OnDrawClipboard](../Topic/CWnd::OnDrawClipboard.md)|当剪贴板内容已更改时调用。|  
|[CWnd::OnDrawItem](../Topic/CWnd::OnDrawItem.md)|当需要绘制所有者描述子按钮控件、组合框控件、列表框控件或菜单的可视方面时调用。|  
|[CWnd::OnDropFiles](../Topic/CWnd::OnDropFiles.md)|当用户在已将自己注册为拖放文件接收者的窗口上方释放鼠标左键时调用。|  
|[CWnd::OnEnable](../Topic/CWnd::OnEnable.md)|当启用或禁用 `CWnd` 时调用。|  
|[CWnd::OnEndSession](../Topic/CWnd::OnEndSession.md)|当会话结束时调用。|  
|[CWnd::OnEnterIdle](../Topic/CWnd::OnEnterIdle.md)|调用以向应用程序的主窗口过程通知模式对话框或菜单正在进入空闲状态。|  
|[CWnd::OnEnterMenuLoop](../Topic/CWnd::OnEnterMenuLoop.md)|当进入了菜单模式循环时调用。|  
|[CWnd::OnEnterSizeMove](../Topic/CWnd::OnEnterSizeMove.md)|在受影响的窗口进入移动或大小调整模式循环之后调用。|  
|[CWnd::OnEraseBkgnd](../Topic/CWnd::OnEraseBkgnd.md)|当窗口背景需要擦除时调用。|  
|[CWnd::OnExitMenuLoop](../Topic/CWnd::OnExitMenuLoop.md)|当退出了菜单模式循环时调用。|  
|[CWnd::OnExitSizeMove](../Topic/CWnd::OnExitSizeMove.md)|在受影响的窗口退出移动或大小调整模式循环之后调用。|  
|[CWnd::OnFontChange](../Topic/CWnd::OnFontChange.md)|当字体资源池更改时调用。|  
|[CWnd::OnGetDlgCode](../Topic/CWnd::OnGetDlgCode.md)|针对控件进行调用，以便控件可以自己处理箭头键和 TAB 键输入。|  
|[CWnd::OnGetMinMaxInfo](../Topic/CWnd::OnGetMinMaxInfo.md)|每当 Windows 需要知道最大化位置或尺寸或是最小或最大跟踪大小时调用。|  
|[CWnd::OnHelpInfo](../Topic/CWnd::OnHelpInfo.md)|当用户按 F1 键时，由框架调用。|  
|[CWnd::OnHotKey](../Topic/CWnd::OnHotKey.md)|当用户按系统范围热键时调用。|  
|[CWnd::OnHScroll](../Topic/CWnd::OnHScroll.md)|当用户单击 `CWnd` 的水平滚动条时调用。|  
|[CWnd::OnHScrollClipboard](../Topic/CWnd::OnHScrollClipboard.md)|当剪贴板所有者应滚动剪贴板图像、使相应部分失效以及更新滚动条值时调用。|  
|[CWnd::OnIconEraseBkgnd](../Topic/CWnd::OnIconEraseBkgnd.md)|当 `CWnd` 已最小化（图标化）并且必须在绘制图标之前填充图标背景时调用。|  
|[CWnd::OnInitMenu](../Topic/CWnd::OnInitMenu.md)|当菜单要成为活动状态时调用。|  
|[CWnd::OnInitMenuPopup](../Topic/CWnd::OnInitMenuPopup.md)|当弹出菜单要成为活动状态时调用。|  
|[CWnd::OnInputDeviceChange](../Topic/CWnd::OnInputDeviceChange.md)|当在系统中添加或移除 I\/O 设备时调用。|  
|[CWnd::OnInputLangChange](../Topic/CWnd::OnInputLangChange.md)|在应用程序的输入语言已更改之后调用。|  
|[CWnd::OnInputLangChangeRequest](../Topic/CWnd::OnInputLangChangeRequest.md)|当用户选择新输入语言时调用。|  
|[CWnd::OnKeyDown](../Topic/CWnd::OnKeyDown.md)|当按下非系统键时调用。|  
|[CWnd::OnKeyUp](../Topic/CWnd::OnKeyUp.md)|当释放非系统键时调用。|  
|[CWnd::OnKillFocus](../Topic/CWnd::OnKillFocus.md)|恰好在 `CWnd` 失去输入焦点之前调用。|  
|[CWnd::OnLButtonDblClk](../Topic/CWnd::OnLButtonDblClk.md)|当用户双击鼠标左键时调用。|  
|[CWnd::OnLButtonDown](../Topic/CWnd::OnLButtonDown.md)|当用户按下鼠标左键时调用。|  
|[CWnd::OnLButtonUp](../Topic/CWnd::OnLButtonUp.md)|当用户释放鼠标左键时调用。|  
|[CWnd::OnMButtonDblClk](../Topic/CWnd::OnMButtonDblClk.md)|当用户双击鼠标中键时调用。|  
|[CWnd::OnMButtonDown](../Topic/CWnd::OnMButtonDown.md)|当用户按下鼠标中键时调用。|  
|[CWnd::OnMButtonUp](../Topic/CWnd::OnMButtonUp.md)|当用户释放鼠标中键时调用。|  
|[CWnd::OnMDIActivate](../Topic/CWnd::OnMDIActivate.md)|当激活或停用 MDI 子窗口时调用。|  
|[CWnd::OnMeasureItem](../Topic/CWnd::OnMeasureItem.md)|创建控件时针对所有者描述子组合框、列表框或菜单项进行调用。  `CWnd` 向 Windows 通知控件的尺寸。|  
|[CWnd::OnMenuChar](../Topic/CWnd::OnMenuChar.md)|当用户按下不与当前菜单中任何预定义助记键匹配的菜单助记键字符时调用。|  
|[CWnd::OnMenuDrag](../Topic/CWnd::OnMenuDrag.md)|当用户开始拖动菜单项时调用。|  
|[CWnd::OnMenuGetObject](../Topic/CWnd::OnMenuGetObject.md)|当鼠标光标进入菜单项或从该项的中心移动到该项的顶部或底部时调用。|  
|[CWnd::OnMenuRButtonUp](../Topic/CWnd::OnMenuRButtonUp.md)|当光标位于菜单项上并且用户释放鼠标右键时调用。|  
|[CWnd::OnMenuSelect](../Topic/CWnd::OnMenuSelect.md)|当用户选择菜单项时调用。|  
|[CWnd::OnMouseActivate](../Topic/CWnd::OnMouseActivate.md)|当光标处于非活动窗口中并且用户按下鼠标按钮时调用。|  
|[CWnd::OnMouseHover](../Topic/CWnd::OnMouseHover.md)|当光标在先前 [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265) 调用中指定的时间段内悬停在窗口工作区上方时调用。|  
|[CWnd::OnMouseHWheel](../Topic/CWnd::OnMouseHWheel.md)|当前窗口由桌面窗口管理器 \(DWM\) 构造，并且该窗口已最大化时调用。|  
|[CWnd::OnMouseLeave](../Topic/CWnd::OnMouseLeave.md)|当光标离开在先前 [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265) 调用中指定的窗口工作区时调用。|  
|[CWnd::OnMouseMove](../Topic/CWnd::OnMouseMove.md)|当鼠标光标移动时调用。|  
|[CWnd::OnMouseWheel](../Topic/CWnd::OnMouseWheel.md)|当用户旋转鼠标滚轮时调用。  使用 Windows NT 4.0 消息处理。|  
|[CWnd::OnMove](../Topic/CWnd::OnMove.md)|在 `CWnd` 的位置已更改之后调用。|  
|[CWnd::OnMoving](../Topic/CWnd::OnMoving.md)|指示用户正在移动 `CWnd` 对象。|  
|[CWnd::OnNcActivate](../Topic/CWnd::OnNcActivate.md)|当需要更改非工作区以指示活动或非活动状态时调用。|  
|[CWnd::OnNcCalcSize](../Topic/CWnd::OnNcCalcSize.md)|当需要计算工作区的大小和位置时调用。|  
|[CWnd::OnNcCreate](../Topic/CWnd::OnNcCreate.md)|当创建工作区时在 [OnCreate](../Topic/CWnd::OnCreate.md) 之前调用。|  
|[CWnd::OnNcDestroy](../Topic/CWnd::OnNcDestroy.md)|当销毁非工作区时调用。|  
|[CWnd::OnNcHitTest](../Topic/CWnd::OnNcHitTest.md)|每当如果 `CWnd` 包含光标或使用 `SetCapture` 捕获了鼠标输入便移动鼠标时调用。|  
|[CWnd::OnNcLButtonDblClk](../Topic/CWnd::OnNcLButtonDblClk.md)|当用户在光标处于 `CWnd` 的非工作区期间双击鼠标左键时调用。|  
|[CWnd::OnNcLButtonDown](../Topic/CWnd::OnNcLButtonDown.md)|当用户在光标处于 `CWnd` 的非工作区期间按下鼠标左键时调用。|  
|[CWnd::OnNcLButtonUp](../Topic/CWnd::OnNcLButtonUp.md)|当用户在光标处于 `CWnd` 的非工作区期间释放鼠标左键时调用。|  
|[CWnd::OnNcMButtonDblClk](../Topic/CWnd::OnNcMButtonDblClk.md)|当用户在光标处于 `CWnd` 的非工作区期间双击鼠标中键时调用。|  
|[CWnd::OnNcMButtonDown](../Topic/CWnd::OnNcMButtonDown.md)|当用户在光标处于 `CWnd` 的非工作区期间按下鼠标中键时调用。|  
|[CWnd::OnNcMButtonUp](../Topic/CWnd::OnNcMButtonUp.md)|当用户在光标处于 `CWnd` 的非工作区期间释放鼠标中键时调用。|  
|[CWnd::OnNcMouseHover](../Topic/CWnd::OnNcMouseHover.md)|当光标在先前 [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265) 调用中指定的时间段内悬停在窗口非工作区上方时调用。|  
|[CWnd::OnNcMouseLeave](../Topic/CWnd::OnNcMouseLeave.md)|当光标离开在先前 [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265) 调用中指定的窗口非工作区时，框架调用此成员函数。|  
|[CWnd::OnNcMouseMove](../Topic/CWnd::OnNcMouseMove.md)|当在 `CWnd` 的非工作区中移动光标时调用。|  
|[CWnd::OnNcPaint](../Topic/CWnd::OnNcPaint.md)|当需要绘制非工作区时调用。|  
|[CWnd::OnNcRButtonDblClk](../Topic/CWnd::OnNcRButtonDblClk.md)|当用户在光标处于 `CWnd` 的非工作区期间双击鼠标右键时调用。|  
|[CWnd::OnNcRButtonDown](../Topic/CWnd::OnNcRButtonDown.md)|当用户在光标处于 `CWnd` 的非工作区期间按下鼠标右键时调用。|  
|[CWnd::OnNcRButtonUp](../Topic/CWnd::OnNcRButtonUp.md)|当用户在光标处于 `CWnd` 的非工作区期间释放鼠标右键时调用。|  
|[CWnd::OnNcRenderingChanged](../Topic/CWnd::OnNcRenderingChanged.md)|在非工作区的呈现策略已更改时调用。|  
|[CWnd::OnNcXButtonDblClk](../Topic/CWnd::OnNcXButtonDblClk.md)|当用户在光标位于窗口非工作区期间双击 XBUTTON1 或 XBUTTON2 时调用。|  
|[CWnd::OnNcXButtonDown](../Topic/CWnd::OnNcXButtonDown.md)|当用户在光标位于窗口非工作区期间按下鼠标的 XBUTTON1 或 XBUTTON2 时调用。|  
|[CWnd::OnNcXButtonUp](../Topic/CWnd::OnNcXButtonUp.md)|当用户在光标位于窗口非工作区期间释放鼠标的 XBUTTON1 或 XBUTTON2 时调用。|  
|[CWnd::OnNextMenu](../Topic/CWnd::OnNextMenu.md)|当使用向右或向左箭头键在菜单栏和系统菜单之间切换时调用。|  
|[CWnd::OnNotify](../Topic/CWnd::OnNotify.md)|由框架调用以通知父窗口，在其某个控件上发生事件或该控件需要信息。|  
|[CWnd::OnNotifyFormat](../Topic/CWnd::OnNotifyFormat.md)|调用以确定当前窗口是否接受 WM\_NOTIFY 通知消息中的 ANSI 或 Unicode 结构。|  
|[CWnd::OnPaint](../Topic/CWnd::OnPaint.md)|调用以重新绘制窗口的一部分。|  
|[CWnd::OnPaintClipboard](../Topic/CWnd::OnPaintClipboard.md)|当剪贴板查看器的工作区需要重新绘制时调用。|  
|[CWnd::OnPaletteChanged](../Topic/CWnd::OnPaletteChanged.md)|调用以允许使用调色板的窗口实现其逻辑调色板并更新其工作区。|  
|[CWnd::OnPaletteIsChanging](../Topic/CWnd::OnPaletteIsChanging.md)|当某个应用程序要实现其逻辑调色板时，通知其他应用程序。|  
|[CWnd::OnParentNotify](../Topic/CWnd::OnParentNotify.md)|当创建或销毁子窗口时，或是当用户在光标位于子窗口上方期间单击鼠标按钮时调用。|  
|[CWnd::OnPowerBroadcast](../Topic/CWnd::OnPowerBroadcast.md)|当电源管理事件发生时调用。|  
|[CWnd::OnQueryDragIcon](../Topic/CWnd::OnQueryDragIcon.md)|当用户要拖动最小化（图标化）的 `CWnd` 时调用。|  
|[CWnd::OnQueryEndSession](../Topic/CWnd::OnQueryEndSession.md)|当用户选择结束 Windows 会话时调用。|  
|[CWnd::OnQueryNewPalette](../Topic/CWnd::OnQueryNewPalette.md)|向 `CWnd` 告知它要接收输入焦点。|  
|[CWnd::OnQueryOpen](../Topic/CWnd::OnQueryOpen.md)|当 `CWnd` 是图标并且用户请求打开该图标时调用。|  
|[CWnd::OnQueryUIState](../Topic/CWnd::OnQueryUIState.md)|调用以检索窗口的用户界面 \(UI\) 状态。|  
|[CWnd::OnRawInput](../Topic/CWnd::OnRawInput.md)|当前窗口中获取原始输入时调用。|  
|[CWnd::OnRButtonDblClk](../Topic/CWnd::OnRButtonDblClk.md)|当用户双击鼠标右键时调用。|  
|[CWnd::OnRButtonDown](../Topic/CWnd::OnRButtonDown.md)|当用户按下鼠标右键时调用。|  
|[CWnd::OnRButtonUp](../Topic/CWnd::OnRButtonUp.md)|当用户释放鼠标右键时调用。|  
|[CWnd::OnRenderAllFormats](../Topic/CWnd::OnRenderAllFormats.md)|当所有者应用程序正在销毁并且需要呈现其所有格式时调用。|  
|[CWnd::OnRenderFormat](../Topic/CWnd::OnRenderFormat.md)|当需要呈现具有延迟呈现的特定格式时，针对剪贴板所有者进行调用。|  
|[CWnd::OnSessionChange](../Topic/CWnd::OnSessionChange.md)|调用以向应用程序通知会话状态已更改。|  
|[CWnd::OnSetCursor](../Topic/CWnd::OnSetCursor.md)|如果鼠标输入未捕获并且鼠标使光标在光标中移动，则调用。|  
|[CWnd::OnSetFocus](../Topic/CWnd::OnSetFocus.md)|在 `CWnd` 获取输入焦点之后调用。|  
|[CWnd::OnSettingChange](../Topic/CWnd::OnSettingChange.md)|当 Win32 `SystemParametersInfo` 函数更改系统范围设置时调用。|  
|[CWnd::OnShowWindow](../Topic/CWnd::OnShowWindow.md)|当 `CWnd` 要显示或隐藏时调用。|  
|[CWnd::OnSize](../Topic/CWnd::OnSize.md)|在 `CWnd` 的大小已更改之后调用。|  
|[CWnd::OnSizeClipboard](../Topic/CWnd::OnSizeClipboard.md)|当剪贴板查看器窗口工作区的大小已更改时调用。|  
|[CWnd::OnSizing](../Topic/CWnd::OnSizing.md)|指示用户正在调整矩形大小。|  
|[CWnd::OnSpoolerStatus](../Topic/CWnd::OnSpoolerStatus.md)|每当对打印管理器队列添加或移除作业时，从打印管理器调用。|  
|[CWnd::OnStyleChanged](../Topic/CWnd::OnStyleChanged.md)|指示 [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) Windows 函数已更改一个或多个窗口样式。|  
|[CWnd::OnStyleChanging](../Topic/CWnd::OnStyleChanging.md)|指示 [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) Windows 函数要更改一个或多个窗口样式。|  
|[CWnd::OnSysChar](../Topic/CWnd::OnSysChar.md)|当击键转换为系统字符时调用。|  
|[CWnd::OnSysColorChange](../Topic/CWnd::OnSysColorChange.md)|当在系统颜色设置中进行更改时，针对所有顶级窗口进行调用。|  
|[CWnd::OnSysCommand](../Topic/CWnd::OnSysCommand.md)|当用户从控件菜单中选择命令时，或是当用户选择最大化或最小化按钮时调用。|  
|[CWnd::OnSysDeadChar](../Topic/CWnd::OnSysDeadChar.md)|当击键转换为系统语音符号字符（如重音字符）时调用。|  
|[CWnd::OnSysKeyDown](../Topic/CWnd::OnSysKeyDown.md)|当用户按住 ALT 键，然后按下另一个键时调用。|  
|[CWnd::OnSysKeyUp](../Topic/CWnd::OnSysKeyUp.md)|当用户释放在按住 ALT 键的同时按下的键时调用。|  
|[CWnd::OnTCard](../Topic/CWnd::OnTCard.md)|当用户单击可创作的按钮时调用。|  
|[CWnd::OnTimeChange](../Topic/CWnd::OnTimeChange.md)|在系统时间更改之后针对所有顶级窗口进行调用。|  
|[CWnd::OnTimer](../Topic/CWnd::OnTimer.md)|在 [SetTimer](../Topic/CWnd::SetTimer.md) 中指定的每个间隔之后调用。|  
|[CWnd::OnTouchInput](../Topic/CWnd::OnTouchInput.md)|处理来自 Windows 触摸屏的单个输入。|  
|[CWnd::OnTouchInputs](../Topic/CWnd::OnTouchInputs.md)|处理来自 Windows 触摸屏的输入。|  
|[CWnd::OnUniChar](../Topic/CWnd::OnUniChar.md)|当按下键时调用。  即，当前窗口具有键盘焦点，并且 [WM\_KEYDOWN](http://msdn.microsoft.com/library/windows/desktop/ms646280) 消息由 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 函数进行转换。|  
|[CWnd::OnUnInitMenuPopup](../Topic/CWnd::OnUnInitMenuPopup.md)|在下拉菜单或子菜单已销毁时调用。|  
|[CWnd::OnUpdateUIState](../Topic/CWnd::OnUpdateUIState.md)|调用以更改指定窗口及其所有子窗口的用户界面 \(UI\) 状态。|  
|[CWnd::OnUserChanged](../Topic/CWnd::OnUserChanged.md)|在用户登录或注销之后调用。|  
|[CWnd::OnVKeyToItem](../Topic/CWnd::OnVKeyToItem.md)|由 `CWnd` 拥有的列表框调用以响应 [WM\_KEYDOWN](../Topic/CWnd::OnKeyDown.md) 消息。|  
|[CWnd::OnVScroll](../Topic/CWnd::OnVScroll.md)|当用户单击窗口的垂直滚动条时调用。|  
|[CWnd::OnVScrollClipboard](../Topic/CWnd::OnVScrollClipboard.md)|当所有者应滚动剪贴板图像、使相应部分失效以及更新滚动条值时调用。|  
|[CWnd::OnWindowPosChanged](../Topic/CWnd::OnWindowPosChanged.md)|当由于调用 [SetWindowPos](../Topic/CWnd::SetWindowPos.md) 或另一个窗口管理函数而更改了大小、位置或 Z 顺序时调用。|  
|[CWnd::OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md)|当由于调用 [SetWindowPos](../Topic/CWnd::SetWindowPos.md) 或另一个窗口管理函数而要更改大小、位置或 Z 顺序时调用。|  
|[CWnd::OnWinIniChange](../Topic/CWnd::OnWinIniChange.md)|在 Windows 初始化文件 \(WIN.INI\) 已更改之后对所有顶级窗口进行调用。|  
|[CWnd::OnWndMsg](../Topic/CWnd::OnWndMsg.md)|指示是否处理了 Windows 消息。|  
|[CWnd::OnXButtonDblClk](../Topic/CWnd::OnXButtonDblClk.md)|当用户在光标位于窗口工作区期间双击 XBUTTON1 或 XBUTTON2 时调用。|  
|[CWnd::OnXButtonDown](../Topic/CWnd::OnXButtonDown.md)|当用户在光标位于窗口工作区期间按下 XBUTTON1 或 XBUTTON2 时调用。|  
|[CWnd::OnXButtonUp](../Topic/CWnd::OnXButtonUp.md)|当用户在光标位于窗口工作区期间释放 XBUTTON1 或 XBUTTON2 时调用。|  
|[CWnd::PostNcDestroy](../Topic/CWnd::PostNcDestroy.md)|此虚函数在窗口已销毁之后由默认 [OnNcDestroy](../Topic/CWnd::OnNcDestroy.md) 函数调用。|  
|[CWnd::ReflectChildNotify](../Topic/CWnd::ReflectChildNotify.md)|将消息反射到其源的 Helper 函数。|  
|[CWnd::ReflectLastMsg](../Topic/CWnd::ReflectLastMsg.md)|将最后一个消息反射到子窗口。|  
|[CWnd::ResizeDynamicLayout](../Topic/CWnd::ResizeDynamicLayout.md)|如果对窗口启用了动态布局，则窗口大小更改以调整子窗口布局时会通过框架调用。|  
|[CWnd::WindowProc](../Topic/CWnd::WindowProc.md)|为 `CWnd` 提供窗口过程。  默认设置会通过消息映射调度消息。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CWnd::operator HWND](../Topic/CWnd::operator%20HWND.md)|调用以获取窗口的句柄。|  
|[CWnd::operator \!\=](../Topic/CWnd::operator%20!=.md)|确定窗口是否不与句柄为 [m\_hWnd](../Topic/CWnd::m_hWnd.md) 的窗口相同。|  
|[CWnd::operator \=\=](../Topic/CWnd::operator%20==.md)|确定窗口是否与句柄为 [m\_hWnd](../Topic/CWnd::m_hWnd.md) 的窗口相同。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CWnd::m\_hWnd](../Topic/CWnd::m_hWnd.md)|指示附加到此 `CWnd` 的 `HWND`。|  
  
## 备注  
 `CWnd` 对象与 Windows 窗口不同，但这两者紧密相关。  `CWnd` 对象由 `CWnd` 构造函数和析构函数进行创建或销毁。  另一方面，Windows 窗口是 Windows 内部的数据结构，由 **Create** 成员函数进行创建，并由 `CWnd` 虚拟析构函数进行销毁。  [DestroyWindow](../Topic/CWnd::DestroyWindow.md) 函数会销毁 Windows 窗口而不销毁对象。  
  
 `CWnd` 类和消息映射机制会隐藏 **WndProc** 函数。  传入的 Windows 通知消息会通过消息映射自动路由到正确的 **On***Message* `CWnd` 成员函数。  可重写 **On***Message* 成员函数以在派生类中处理成员的特定消息。  
  
 通过 `CWnd` 类还可以为应用程序创建 Windows 子窗口。  从 `CWnd` 派生类，然后将成员变量添加到派生类，以存储特定于应用程序的数据。  可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。  
  
 可采用两个步骤创建子窗口。  首先，调用构造函数 `CWnd` 以构造 `CWnd` 对象，然后调用 [Create](../Topic/CWnd::Create.md) 成员函数以创建子窗口，然后将它附加到 `CWnd` 对象。  
  
 当用户终止子窗口时，销毁 `CWnd` 对象，或调用 `DestroyWindow` 成员函数以移除窗口并销毁其数据结构。  
  
 在 Microsoft 基础类库中，从 `CWnd` 派生了更多类以提供特定窗口类型。  其中许多类（包括 [CFrameWnd](../../mfc/reference/cframewnd-class.md)、[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)、[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)、[CView](../../mfc/reference/cview-class.md) 和 [CDialog](../../mfc/reference/cdialog-class.md)）设计为可进一步派生。  派生自 `CWnd` 的控件类（如 [CButton](../../mfc/reference/cbutton-class.md)）可以直接使用，也可以用于进一步派生类。  
  
 有关使用 `CWnd` 的详细信息，请参阅[框架窗口](../../mfc/frame-windows.md)和[窗口对象](../../mfc/window-objects.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWnd`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)