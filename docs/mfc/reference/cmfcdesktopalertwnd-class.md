---
title: "CMFCDesktopAlertWnd Class | Microsoft Docs"
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
  - "CMFCDesktopAlertWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDesktopAlertWnd class"
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDesktopAlertWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCDesktopAlertWnd` 选件类实现在屏幕上显示通知事件的用户无模式对话框的函数。  
  
## 语法  
  
```  
class CMFCDesktopAlertWnd : public CWnd  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md)|创建并初始化桌面通知窗口。|  
|[CMFCDesktopAlertWnd::GetAnimationSpeed](../Topic/CMFCDesktopAlertWnd::GetAnimationSpeed.md)|返回动画速度。|  
|[CMFCDesktopAlertWnd::GetAnimationType](../Topic/CMFCDesktopAlertWnd::GetAnimationType.md)|返回动画类型。|  
|[CMFCDesktopAlertWnd::GetAutoCloseTime](../Topic/CMFCDesktopAlertWnd::GetAutoCloseTime.md)|返回自动关闭时。|  
|[CMFCDesktopAlertWnd::GetCaptionHeight](../Topic/CMFCDesktopAlertWnd::GetCaptionHeight.md)|返回图例的高度。|  
|[CMFCDesktopAlertWnd::GetDialogSize](../Topic/CMFCDesktopAlertWnd::GetDialogSize.md)||  
|[CMFCDesktopAlertWnd::GetLastPos](../Topic/CMFCDesktopAlertWnd::GetLastPos.md)|返回桌面通知窗口的最后一个活动在屏幕上的位置。|  
|[CMFCDesktopAlertWnd::GetTransparency](../Topic/CMFCDesktopAlertWnd::GetTransparency.md)|返回透明度级别。|  
|[CMFCDesktopAlertWnd::HasSmallCaption](../Topic/CMFCDesktopAlertWnd::HasSmallCaption.md)|确定桌面通知窗口是否显示较小的说明。|  
|[CMFCDesktopAlertWnd::OnBeforeShow](../Topic/CMFCDesktopAlertWnd::OnBeforeShow.md)||  
|[CMFCDesktopAlertWnd::OnClickLinkButton](../Topic/CMFCDesktopAlertWnd::OnClickLinkButton.md)|调用由结构，当用户单击位于桌面通知菜单的链接按钮。|  
|[CMFCDesktopAlertWnd::OnCommand](../Topic/CMFCDesktopAlertWnd::OnCommand.md)|框架调用该成员函数，当用户选择一个项目从菜单中，那么，当子控件发送通知消息时，或者，在快捷键击键转换时。  （重写 [CWnd::OnCommand](../Topic/CWnd::OnCommand.md)。）|  
|[CMFCDesktopAlertWnd::OnDraw](../Topic/CMFCDesktopAlertWnd::OnDraw.md)||  
|[CMFCDesktopAlertWnd::ProcessCommand](../Topic/CMFCDesktopAlertWnd::ProcessCommand.md)||  
|[CMFCDesktopAlertWnd::SetAnimationSpeed](../Topic/CMFCDesktopAlertWnd::SetAnimationSpeed.md)|设置新动画速度。|  
|[CMFCDesktopAlertWnd::SetAnimationType](../Topic/CMFCDesktopAlertWnd::SetAnimationType.md)|设置动画类型。|  
|[CMFCDesktopAlertWnd::SetAutoCloseTime](../Topic/CMFCDesktopAlertWnd::SetAutoCloseTime.md)|设置自动关闭时。|  
|[CMFCDesktopAlertWnd::SetSmallCaption](../Topic/CMFCDesktopAlertWnd::SetSmallCaption.md)|在小和普通声明之间切换。|  
|[CMFCDesktopAlertWnd::SetTransparency](../Topic/CMFCDesktopAlertWnd::SetTransparency.md)|设置透明度级别。|  
  
## 备注  
 桌面通知窗口可以透明的，它可能带有动画效果，可能会消失\(在指定的时间的延迟后，或者当用户通过单击关闭"按钮关闭它时）。  
  
 桌面通知窗口还可以包含又包含一个图标、文本的默认对话框\(标签\)和一个链接。  或者，桌面通知窗口可以包含从应用程序资源的自定义对话框。  
  
 对两个步骤创建一个桌面通知窗口。  首先，调用构造函数构造 `CMFCDesktopAlertWnd` 对象。  接下来，调用 [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) 成员函数创建窗口并将其附加到 `CMFCDesktopAlertWnd` 对象。  
  
 `CMFCDesktopAlertWnd` 对象创建加载桌面通知窗口工作区的特定子对话框。  对话框拥有确定此的所有控件。  
  
 若要在弹出窗口的自定义对话框中，执行以下步骤:  
  
1.  从 `CMFCDesktopAlertDialog` 派生一个类。  
  
2.  创建子在对话框模板资源。  
  
3.  调用 [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) 使用对话框模板并指针的资源ID对于派生类的运行时选件类信息。  
  
4.  程序处理的自定义对话框直接来自承载的控件的所有通知或程序承载的控件来处理这些通知。  
  
 使用以下功能控制桌面通知窗口的行为:  
  
-   通过调用 [CMFCDesktopAlertWnd::SetAnimationType](../Topic/CMFCDesktopAlertWnd::SetAnimationType.md)设置动画类型。  有效的选项包括启动，将且不透明度?。  
  
-   通过调用 [CMFCDesktopAlertWnd::SetAnimationSpeed](../Topic/CMFCDesktopAlertWnd::SetAnimationSpeed.md)设置帧动画速度。  
  
-   通过调用 [CMFCDesktopAlertWnd::SetTransparency](../Topic/CMFCDesktopAlertWnd::SetTransparency.md)设置透明度级别。  
  
-   更改标题的大小到小通过调用 [CMFCDesktopAlertWnd::SetSmallCaption](../Topic/CMFCDesktopAlertWnd::SetSmallCaption.md)。  小的声明与高度约7像素。  
  
## 示例  
 下面的示例在 `CMFCDesktopAlertWnd` 选件类演示如何使用各种方案配置 `CMFCDesktopAlertWnd` 对象。  此示例演示如何设置动画类型，设置弹出窗口的透明度，指定警报窗口显示一个小的说明，并在警报窗口之前过去的自动结束的时间。  该示例还演示如何创建和初始化桌面通知窗口。  此代码段是 [桌面通知演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/CPP/cmfcdesktopalertwnd-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)  
  
## 要求  
 **标头:** afxDesktopAlertWnd.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWndInfo Class](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)