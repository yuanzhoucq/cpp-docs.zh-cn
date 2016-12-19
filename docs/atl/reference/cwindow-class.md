---
title: "CWindow Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CWindow"
  - "ATL::CWindow"
  - "CWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWindow class"
ms.assetid: fefa00c8-f053-4bcf-87bc-dc84f5386683
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWindow Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类用于操作窗口的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CWindow  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CWindow::CWindow](../Topic/CWindow::CWindow.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWindow::ArrangeIconicWindows](../Topic/CWindow::ArrangeIconicWindows.md)|让所有最小化的子窗口。|  
|[CWindow::Attach](../Topic/CWindow::Attach.md)|附加到windows `CWindow` 对象。|  
|[CWindow::BeginPaint](../Topic/CWindow::BeginPaint.md)|窗口用于绘制准备。|  
|[CWindow::BringWindowToTop](../Topic/CWindow::BringWindowToTop.md)|对Z顺序的顶部显示窗口。|  
|[CWindow::CenterWindow](../Topic/CWindow::CenterWindow.md)|焦点窗口特定窗口。|  
|[CWindow::ChangeClipboardChain](../Topic/CWindow::ChangeClipboardChain.md)|从剪贴板查看程序链中移除窗口。|  
|[CWindow::CheckDlgButton](../Topic/CWindow::CheckDlgButton.md)|更改用于指定按钮的复选状态。|  
|[CWindow::CheckRadioButton](../Topic/CWindow::CheckRadioButton.md)|检查指定的单选按钮。|  
|[CWindow::ChildWindowFromPoint](../Topic/CWindow::ChildWindowFromPoint.md)|检索包含窗口指定点的子级。|  
|[CWindow::ChildWindowFromPointEx](../Topic/CWindow::ChildWindowFromPointEx.md)|检索窗口包含指定点子级的特定类型。|  
|[CWindow::ClientToScreen](../Topic/CWindow::ClientToScreen.md)|转换为屏幕坐标的工作区坐标。|  
|[CWindow::Create](../Topic/CWindow::Create.md)|创建一个窗口。|  
|[CWindow::CreateCaret](../Topic/CWindow::CreateCaret.md)|创建系统插入符号的新形状。|  
|[CWindow::CreateGrayCaret](../Topic/CWindow::CreateGrayCaret.md)|创建系统插入符号的灰色矩形。|  
|[CWindow::CreateSolidCaret](../Topic/CWindow::CreateSolidCaret.md)|创建系统插入符号的一个矩形。|  
|[CWindow::DeferWindowPos](../Topic/CWindow::DeferWindowPos.md)|更新指定的窗口中指定了多个窗口位置结构。|  
|[CWindow::DestroyWindow](../Topic/CWindow::DestroyWindow.md)|销毁窗口与 `CWindow` 对象。|  
|[CWindow::Detach](../Topic/CWindow::Detach.md)|分离 `CWindow` 对象的窗口。|  
|[CWindow::DlgDirList](../Topic/CWindow::DlgDirList.md)|用与指定的路径或文件名的所有文件的名称填充列表框。|  
|[CWindow::DlgDirListComboBox](../Topic/CWindow::DlgDirListComboBox.md)|用与指定的路径或文件名的所有文件的名称填充组合框。|  
|[CWindow::DlgDirSelect](../Topic/CWindow::DlgDirSelect.md)|从列表框检索当前选择。|  
|[CWindow::DlgDirSelectComboBox](../Topic/CWindow::DlgDirSelectComboBox.md)|从组合框检索当前选择。|  
|[CWindow::DragAcceptFiles](../Topic/CWindow::DragAcceptFiles.md)|寄存器"窗口是否接受被拖动的文件。|  
|[CWindow::DrawMenuBar](../Topic/CWindow::DrawMenuBar.md)|重绘窗口菜单栏。|  
|[CWindow::EnableScrollBar](../Topic/CWindow::EnableScrollBar.md)|启用或禁用滚动条箭头。|  
|[CWindow::EnableWindow](../Topic/CWindow::EnableWindow.md)|启用或禁用输入。|  
|[CWindow::EndPaint](../Topic/CWindow::EndPaint.md)|标记绘制的结尾。|  
|[CWindow::FlashWindow](../Topic/CWindow::FlashWindow.md)|一个闪烁窗口。|  
|[CWindow::GetClientRect](../Topic/CWindow::GetClientRect.md)|检索工作区的坐标。|  
|[CWindow::GetDC](../Topic/CWindow::GetDC.md)|检索工作区的设备上下文。|  
|[CWindow::GetDCEx](../Topic/CWindow::GetDCEx.md)|检索工作区的设备上下文并允许剪辑选项。|  
|[CWindow::GetDescendantWindow](../Topic/CWindow::GetDescendantWindow.md)|检索指定的子代窗口。|  
|[CWindow::GetDlgControl](../Topic/CWindow::GetDlgControl.md)|检索在指定的控件的接口。|  
|[CWindow::GetDlgCtrlID](../Topic/CWindow::GetDlgCtrlID.md)|检索窗口的标识符\(仅适用于子窗口）。|  
|[CWindow::GetDlgHost](../Topic/CWindow::GetDlgHost.md)|检索对接口为ATL控件宿主容器的指针。|  
|[CWindow::GetDlgItem](../Topic/CWindow::GetDlgItem.md)|检索指定的子窗口。|  
|[CWindow::GetDlgItemInt](../Topic/CWindow::GetDlgItemInt.md)|将控件的文本为整数。|  
|[CWindow::GetDlgItemText](../Topic/CWindow::GetDlgItemText.md)|检索控件的文本。|  
|[CWindow::GetExStyle](../Topic/CWindow::GetExStyle.md)|检索扩展的窗口样式。|  
|[CWindow::GetFont](../Topic/CWindow::GetFont.md)|检索窗口的当前字体。|  
|[CWindow::GetHotKey](../Topic/CWindow::GetHotKey.md)|确定快捷键与窗口。|  
|[CWindow::GetIcon](../Topic/CWindow::GetIcon.md)|检索窗口的大图标或小图标。|  
|[CWindow::GetLastActivePopup](../Topic/CWindow::GetLastActivePopup.md)|检索最近活动的弹出窗口。|  
|[CWindow::GetMenu](../Topic/CWindow::GetMenu.md)|检索windows菜单。|  
|[CWindow::GetNextDlgGroupItem](../Topic/CWindow::GetNextDlgGroupItem.md)|在一组控件中检索上个月或下一个控件。|  
|[CWindow::GetNextDlgTabItem](../Topic/CWindow::GetNextDlgTabItem.md)|检索将一个或下一个控件 **WS\_TABSTOP** 样式。|  
|[CWindow::GetParent](../Topic/CWindow::GetParent.md)|检索直接父窗口。|  
|[CWindow::GetScrollInfo](../Topic/CWindow::GetScrollInfo.md)|检索滚动条的参数。|  
|[CWindow::GetScrollPos](../Topic/CWindow::GetScrollPos.md)|检索滚动框的位置。|  
|[CWindow::GetScrollRange](../Topic/CWindow::GetScrollRange.md)|检索滚动条范围。|  
|[CWindow::GetStyle](../Topic/CWindow::GetStyle.md)|检索窗口样式。|  
|[CWindow::GetSystemMenu](../Topic/CWindow::GetSystemMenu.md)|创建系统菜单的副本中进行修改。|  
|[CWindow::GetTopLevelParent](../Topic/CWindow::GetTopLevelParent.md)|检索顶级父或所有者窗口。|  
|[CWindow::GetTopLevelWindow](../Topic/CWindow::GetTopLevelWindow.md)|检索顶级所有者窗口。|  
|[CWindow::GetTopWindow](../Topic/CWindow::GetTopWindow.md)|检索顶级子窗口。|  
|[CWindow::GetUpdateRect](../Topic/CWindow::GetUpdateRect.md)|检索完全封闭更新区域最小矩形的坐标。|  
|[CWindow::GetUpdateRgn](../Topic/CWindow::GetUpdateRgn.md)|检索已更新区域并将其复制到指定的范围。|  
|[CWindow::GetWindow](../Topic/CWindow::GetWindow.md)|检索指定的窗口。|  
|[CWindow::GetWindowContextHelpId](../Topic/CWindow::GetWindowContextHelpId.md)|检索窗口的帮助上下文标识符。|  
|[CWindow::GetWindowDC](../Topic/CWindow::GetWindowDC.md)|检索整个窗口的设备上下文。|  
|[CWindow::GetWindowLong](../Topic/CWindow::GetWindowLong.md)|检索32位值在指定的偏移量额外的windows内存中。|  
|[CWindow::GetWindowLongPtr](../Topic/CWindow::GetWindowLongPtr.md)|检索有关指定窗口的信息，包括值在指定的偏移量额外的windows内存中。|  
|[CWindow::GetWindowPlacement](../Topic/CWindow::GetWindowPlacement.md)|检索显示状态和位置。|  
|[CWindow::GetWindowProcessID](../Topic/CWindow::GetWindowProcessID.md)|检索创建窗口操作的标识符。|  
|[CWindow::GetWindowRect](../Topic/CWindow::GetWindowRect.md)|检索窗口的限制的大小。|  
|[CWindow::GetWindowRgn](../Topic/CWindow::GetWindowRgn.md)|获取窗口的窗口区域的副本。|  
|[CWindow::GetWindowText](../Topic/CWindow::GetWindowText.md)|检索窗口的文本。|  
|[CWindow::GetWindowTextLength](../Topic/CWindow::GetWindowTextLength.md)|检索窗口的文本的长度。|  
|[CWindow::GetWindowThreadID](../Topic/CWindow::GetWindowThreadID.md)|检索创建指定线程的窗口的标识符。|  
|[CWindow::GetWindowWord](../Topic/CWindow::GetWindowWord.md)|检索16位值在指定的偏移量额外的windows内存中。|  
|[CWindow::GotoDlgCtrl](../Topic/CWindow::GotoDlgCtrl.md)|设置键盘焦点设置在对话框的控件。|  
|[CWindow::HideCaret](../Topic/CWindow::HideCaret.md)|隐藏系统插入符号。|  
|[CWindow::HiliteMenuItem](../Topic/CWindow::HiliteMenuItem.md)|突出显示或从顶级菜单项移除突出显示。|  
|[CWindow::Invalidate](../Topic/CWindow::Invalidate.md)|无效的整个工作区。|  
|[CWindow::InvalidateRect](../Topic/CWindow::InvalidateRect.md)|无效在指定的矩形内的工作区。|  
|[CWindow::InvalidateRgn](../Topic/CWindow::InvalidateRgn.md)|无效在指定范围内的工作区。|  
|[CWindow::IsChild](../Topic/CWindow::IsChild.md)|确定指定的窗口是否为子窗口。|  
|[CWindow::IsDialogMessage](../Topic/CWindow::IsDialogMessage.md)|确定消息是否能指定的对话框使用。|  
|[CWindow::IsDlgButtonChecked](../Topic/CWindow::IsDlgButtonChecked.md)|确定按钮的复选状态。|  
|[CWindow::IsIconic](../Topic/CWindow::IsIconic.md)|确定是否窗口最小化。|  
|[CWindow::IsParentDialog](../Topic/CWindow::IsParentDialog.md)|确定控件的父窗口是否为对话框窗口。|  
|[CWindow::IsWindow](../Topic/CWindow::IsWindow.md)|确定指定的窗口句柄是否标识现有的窗口。|  
|[CWindow::IsWindowEnabled](../Topic/CWindow::IsWindowEnabled.md)|确定窗口是否为输入启用。|  
|[CWindow::IsWindowUnicode](../Topic/CWindow::IsWindowUnicode.md)|确定指定的窗口是否为本机Unicode窗口。|  
|[CWindow::IsWindowVisible](../Topic/CWindow::IsWindowVisible.md)|确定窗口的可见性状态。|  
|[CWindow::IsZoomed](../Topic/CWindow::IsZoomed.md)|确定窗口是否被最大化。|  
|[CWindow::KillTimer](../Topic/CWindow::KillTimer.md)|销毁一个计时器事件。|  
|[CWindow::LockWindowUpdate](../Topic/CWindow::LockWindowUpdate.md)|禁用或启用窗口中的绘图。|  
|[CWindow::MapWindowPoints](../Topic/CWindow::MapWindowPoints.md)|将设置从窗口的坐标空间指向另一个窗口坐标空间。|  
|[CWindow::MessageBox](../Topic/CWindow::MessageBox.md)|显示消息框。|  
|[CWindow::ModifyStyle](../Topic/CWindow::ModifyStyle.md)|修改窗口样式。|  
|[CWindow::ModifyStyleEx](../Topic/CWindow::ModifyStyleEx.md)|修改扩展窗口样式。|  
|[CWindow::MoveWindow](../Topic/CWindow::MoveWindow.md)|更改窗口的大小和位置。|  
|[CWindow::NextDlgCtrl](../Topic/CWindow::NextDlgCtrl.md)|设置键盘焦点设置在对话框的下一个控件。|  
|[CWindow::OpenClipboard](../Topic/CWindow::OpenClipboard.md)|打开剪贴板。|  
|[CWindow::PostMessage](../Topic/CWindow::PostMessage.md)|在消息队列将消息与创建窗口的线程。  返回，而不等待线程处理消息。|  
|[CWindow::PrevDlgCtrl](../Topic/CWindow::PrevDlgCtrl.md)|设置键盘焦点设置在对话框中的上一个控件。|  
|[CWindow::Print](../Topic/CWindow::Print.md)|请求窗口在指定的设备上下文绘制。|  
|[CWindow::PrintClient](../Topic/CWindow::PrintClient.md)|请求窗口的工作区在指定的设备上下文绘制。|  
|[CWindow::RedrawWindow](../Topic/CWindow::RedrawWindow.md)|更新一个指定的矩形或区域在工作区。|  
|[CWindow::ReleaseDC](../Topic/CWindow::ReleaseDC.md)|释放设备上下文。|  
|[CWindow::ResizeClient](../Topic/CWindow::ResizeClient.md)|调整窗口的大小。|  
|[CWindow::ScreenToClient](../Topic/CWindow::ScreenToClient.md)|转换为工作区坐标的屏幕坐标。|  
|[CWindow::ScrollWindow](../Topic/CWindow::ScrollWindow.md)|将指定的工作区。|  
|[CWindow::ScrollWindowEx](../Topic/CWindow::ScrollWindowEx.md)|将与附加的功能指定的工作区。|  
|[CWindow::SendDlgItemMessage](../Topic/CWindow::SendDlgItemMessage.md)|将消息发送到控件。|  
|[CWindow::SendMessage](../Topic/CWindow::SendMessage.md)|将消息发送到窗口，并返回，直到窗口过程处理消息。|  
|[CWindow::SendMessageToDescendants](../Topic/CWindow::SendMessageToDescendants.md)|将消息发送到指定的子代窗口。|  
|[CWindow::SendNotifyMessage](../Topic/CWindow::SendNotifyMessage.md)|将消息发送到窗口。  如果窗口是由调用的线程创建的，`SendNotifyMessage` 不返回，直到窗口过程处理消息。  否则，则立即返回。|  
|[CWindow::SetActiveWindow](../Topic/CWindow::SetActiveWindow.md)|窗口被激活。|  
|[CWindow::SetCapture](../Topic/CWindow::SetCapture.md)|发送输入的所有后续鼠标到窗口。|  
|[CWindow::SetClipboardViewer](../Topic/CWindow::SetClipboardViewer.md)|添加到windows剪贴板查看程序链。|  
|[CWindow::SetDlgCtrlID](../Topic/CWindow::SetDlgCtrlID.md)|更改窗口的标识符。|  
|[CWindow::SetDlgItemInt](../Topic/CWindow::SetDlgItemInt.md)|更改控件的文本为整数值的字符串表示形式。|  
|[CWindow::SetDlgItemText](../Topic/CWindow::SetDlgItemText.md)|更改控件的文本。|  
|[CWindow::SetFocus](../Topic/CWindow::SetFocus.md)|输入焦点设置到窗口。|  
|[CWindow::SetFont](../Topic/CWindow::SetFont.md)|更改窗口的当前字体。|  
|[CWindow::SetHotKey](../Topic/CWindow::SetHotKey.md)|将一个快捷键与窗口。|  
|[CWindow::SetIcon](../Topic/CWindow::SetIcon.md)|更改窗口的大图标或小图标。|  
|[CWindow::SetMenu](../Topic/CWindow::SetMenu.md)|更改窗口的当前菜单。|  
|[CWindow::SetParent](../Topic/CWindow::SetParent.md)|更改父窗口。|  
|[CWindow::SetRedraw](../Topic/CWindow::SetRedraw.md)|设置或清除重绘标志。|  
|[CWindow::SetScrollInfo](../Topic/CWindow::SetScrollInfo.md)|将滚动条的参数。|  
|[CWindow::SetScrollPos](../Topic/CWindow::SetScrollPos.md)|更改滚动框的位置。|  
|[CWindow::SetScrollRange](../Topic/CWindow::SetScrollRange.md)|更改滚动条范围。|  
|[CWindow::SetTimer](../Topic/CWindow::SetTimer.md)|创建一个计时器事件。|  
|[CWindow::SetWindowContextHelpId](../Topic/CWindow::SetWindowContextHelpId.md)|设置窗口的帮助上下文标识符。|  
|[CWindow::SetWindowLong](../Topic/CWindow::SetWindowLong.md)|将32位值在指定的偏移量额外的windows内存中。|  
|[CWindow::SetWindowLongPtr](../Topic/CWindow::SetWindowLongPtr.md)|更改用于指定窗口的属性，并将值在额外的windows内存中指定的偏移量。|  
|[CWindow::SetWindowPlacement](../Topic/CWindow::SetWindowPlacement.md)|设置显示状态和位置。|  
|[CWindow::SetWindowPos](../Topic/CWindow::SetWindowPos.md)|设置大小、位置和Z顺序。|  
|[CWindow::SetWindowRgn](../Topic/CWindow::SetWindowRgn.md)|设置窗口的windows区域。|  
|[CWindow::SetWindowText](../Topic/CWindow::SetWindowText.md)|更改窗口的文本。|  
|[CWindow::SetWindowWord](../Topic/CWindow::SetWindowWord.md)|将16位值在指定的偏移量额外的windows内存中。|  
|[CWindow::ShowCaret](../Topic/CWindow::ShowCaret.md)|显示系统插入符号。|  
|[CWindow::ShowOwnedPopups](../Topic/CWindow::ShowOwnedPopups.md)|显示或隐藏窗口拥有的弹出窗口。|  
|[CWindow::ShowScrollBar](../Topic/CWindow::ShowScrollBar.md)|显示或隐藏滚动条。|  
|[CWindow::ShowWindow](../Topic/CWindow::ShowWindow.md)|设置窗口中显示状态。|  
|[CWindow::ShowWindowAsync](../Topic/CWindow::ShowWindowAsync.md)|设置不同的线程创建的窗口中显示状态。|  
|[CWindow::UpdateWindow](../Topic/CWindow::UpdateWindow.md)|更新工作区。|  
|[CWindow::ValidateRect](../Topic/CWindow::ValidateRect.md)|验证在指定的矩形内的工作区。|  
|[CWindow::ValidateRgn](../Topic/CWindow::ValidateRgn.md)|验证在指定范围内的工作区。|  
|[CWindow::WinHelp](../Topic/CWindow::WinHelp.md)|启动Windows帮助。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CWindow::operator HWND](../Topic/CWindow::operator%20HWND.md)|转换为 `HWND`的 `CWindow` 对象。|  
|[CWindow::operator \=](../Topic/CWindow::operator%20=.md)|分配 `HWND` 到 `CWindow` 对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CWindow::m\_hWnd](../Topic/CWindow::m_hWnd.md)|窗口的句柄与 `CWindow` 对象。|  
|[CWindow::rcDefault](../Topic/CWindow::rcDefault.md)|包含默认窗口大小。|  
  
## 备注  
 `CWindow` 用于操作在ATL的窗口提供基本功能。  许多 `CWindow` 方法之一个Win32 API函数。  例如，请比较 `CWindow::ShowWindow` 和 `ShowWindow`的原型:  
  
|CWindow方法|Win32函数|  
|---------------|-------------|  
|**BOOL ShowWindow\( int**  `nCmdShow`\);|**BOOL ShowWindow\( HWND**  `hWnd` **, int**  `nCmdShow`\);|  
  
 `CWindow::ShowWindow` 通过 `CWindow::m_hWnd` 调用Win32函数 `ShowWindow` 作为第一个参数。  直接包装一个Win32函数的每个 `CWindow` 方法通过 `m_hWnd` 成员;因此，许多 `CWindow` 文档将介绍 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
> [!NOTE]
>  并非每个与窗口相关的Win32函数由 `CWindow`，包装，并不是每个 `CWindow` 方法包装一个Win32函数。  
  
 `CWindow::m_hWnd` 存储标识一个窗口的 `HWND`。  `HWND` 附加到对象，则:  
  
-   指定 `HWND` 在`CWindow`的构造函数。  
  
-   调用 `CWindow::Attach`。  
  
-   使用`CWindow`的 **operator \=**。  
  
-   创建或使用以下选件类之一的窗口 `CWindow`从派生的子类:  
  
     [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 允许您创建新窗口或子类现有的窗口。  
  
     [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 实现在其他对象中包含的窗口。  可以创建新窗口或子类现有的窗口。  
  
     [CDialogImpl](../../atl/reference/cdialogimpl-class.md) 允许您创建模式或无模式对话框。  
  
 有关窗口的更多信息，请参见 [Windows](http://msdn.microsoft.com/library/windows/desktop/ms632595) 及随后的主题。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  有关使用窗口的更多信息在ATL，请参见文章 [ATL窗口选件类](../../atl/atl-window-classes.md)。  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)