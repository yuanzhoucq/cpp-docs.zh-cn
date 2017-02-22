---
title: "CMFCButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCButton class"
  - "CMFCButton constructor"
  - "CMFCButton::CreateObject method"
  - "CMFCButton::DrawItem method"
  - "CMFCButton::OnDrawParentBackground method"
  - "CMFCButton::PreTranslateMessage method"
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# CMFCButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCButton` 选件类添加功能 [CButton](../../mfc/reference/cbutton-class.md) 选件类\(如\)对齐按钮文本，将按钮文本和图像，选择光标和指定工具提示。  
  
## 语法  
  
```  
class CMFCButton : public CButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCButton::CMFCButton`|默认构造函数。|  
|`CMFCButton::~CMFCButton`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCButton::CleanUp](../Topic/CMFCButton::CleanUp.md)|重置内部变量并释放分配的资源\(如图像、位图和图标。|  
|`CMFCButton::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|`CMFCButton::DrawItem`|调用由结构，在一个所有者描述的按钮的可视方面是已更改。  （重写 [CButton::DrawItem](../Topic/CButton::DrawItem.md)。）|  
|[CMFCButton::EnableFullTextTooltip](../Topic/CMFCButton::EnableFullTextTooltip.md)|指定是否显示工具提示的全文一种工具提示窗口的或文本的已截断的版本在一个小的工具提示窗口中。|  
|[CMFCButton::EnableMenuFont](../Topic/CMFCButton::EnableMenuFont.md)|指定按钮文本的字体是否与应用程序菜单字体。|  
|[CMFCButton::EnableWindowsTheming](../Topic/CMFCButton::EnableWindowsTheming.md)|指定按钮的边框样式是否符合当前Windows主题。|  
|`CMFCButton::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCButton::GetToolTipCtrl](../Topic/CMFCButton::GetToolTipCtrl.md)|返回对基础工具提示控件。|  
|[CMFCButton::IsAutoCheck](../Topic/CMFCButton::IsAutoCheck.md)|指示复选框或单选按钮是否是一个自动按钮。|  
|[CMFCButton::IsAutorepeatCommandMode](../Topic/CMFCButton::IsAutorepeatCommandMode.md)|指示按钮是否设置为自动重复模式。|  
|[CMFCButton::IsCheckBox](../Topic/CMFCButton::IsCheckBox.md)|指示按钮是否复选框按钮。|  
|[CMFCButton::IsChecked](../Topic/CMFCButton::IsChecked.md)|指示当前按钮是否已选中。|  
|[CMFCButton::IsHighlighted](../Topic/CMFCButton::IsHighlighted.md)|指示按钮是否显示。|  
|[CMFCButton::IsPressed](../Topic/CMFCButton::IsPressed.md)|指示按钮是否按并显示。|  
|[CMFCButton::IsPushed](../Topic/CMFCButton::IsPushed.md)|指示按钮是否按。|  
|[CMFCButton::IsRadioButton](../Topic/CMFCButton::IsRadioButton.md)|指示按钮是否是单选按钮。|  
|[CMFCButton::IsWindowsThemingEnabled](../Topic/CMFCButton::IsWindowsThemingEnabled.md)|指示按钮的边框样式是否符合当前Windows主题。|  
|`CMFCButton::OnDrawParentBackground`|在指定的区域绘制按钮的父的背景。  （重写 [AFX\_GLOBAL\_DATA::DrawParentBackground](../Topic/AFX_GLOBAL_DATA::DrawParentBackground.md)。）|  
|`CMFCButton::PreTranslateMessage`|在将调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows功能之前，将windows消息。  （重写 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。）|  
|[CMFCButton::SetAutorepeatMode](../Topic/CMFCButton::SetAutorepeatMode.md)|将按钮自动重复模式。|  
|[CMFCButton::SetCheckedImage](../Topic/CMFCButton::SetCheckedImage.md)|设置已检查的按钮的图像。|  
|[CMFCButton::SetFaceColor](../Topic/CMFCButton::SetFaceColor.md)|设置按钮文本的背景色。|  
|[CMFCButton::SetImage](../Topic/CMFCButton::SetImage.md)|将按钮的图像。|  
|[CMFCButton::SetMouseCursor](../Topic/CMFCButton::SetMouseCursor.md)|设置光标图像。|  
|[CMFCButton::SetMouseCursorHand](../Topic/CMFCButton::SetMouseCursorHand.md)|设置光标对现有量的图像。|  
|[CMFCButton::SetStdImage](../Topic/CMFCButton::SetStdImage.md)|使用一 `CMenuImages` 对象设置按钮图像。|  
|[CMFCButton::SetTextColor](../Topic/CMFCButton::SetTextColor.md)|设置按钮文本的颜色未选中的按钮。|  
|[CMFCButton::SetTextHotColor](../Topic/CMFCButton::SetTextHotColor.md)|设置按钮文本的选定颜色的按钮。|  
|[CMFCButton::SetTooltip](../Topic/CMFCButton::SetTooltip.md)|关联工具提示符按钮。|  
|[CMFCButton::SizeToContent](../Topic/CMFCButton::SizeToContent.md)|调整按钮包含其按钮文本和图像。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCButton::OnDraw](../Topic/CMFCButton::OnDraw.md)|调用由框架绘制按钮。|  
|[CMFCButton::OnDrawBorder](../Topic/CMFCButton::OnDrawBorder.md)|调用由结构分区按钮的边框。|  
|[CMFCButton::OnDrawFocusRect](../Topic/CMFCButton::OnDrawFocusRect.md)|调用由框架绘制按钮的焦点矩形。|  
|[CMFCButton::OnDrawText](../Topic/CMFCButton::OnDrawText.md)|调用由框架绘制按钮文本。|  
|[CMFCButton::OnFillBackground](../Topic/CMFCButton::OnFillBackground.md)|调用由框架绘制按钮文本的背景。|  
|[CMFCButton::SelectFont](../Topic/CMFCButton::SelectFont.md)|检索与指定的设备上下文的字体。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCButton::m\_bDrawFocus](../Topic/CMFCButton::m_bDrawFocus.md)|指示是否在按钮周围绘制焦点矩形。|  
|[CMFCButton::m\_bHighlightChecked](../Topic/CMFCButton::m_bHighlightChecked.md)|当光标悬停时，该值指示是否显示BS\_CHECKBOX\-style按。|  
|[CMFCButton::m\_bRightImage](../Topic/CMFCButton::m_bRightImage.md)|指示是否在按钮右边显示图像。|  
|[CMFCButton::m\_bTransparent](../Topic/CMFCButton::m_bTransparent.md)|指示按钮是否是透明的。|  
|[CMFCButton::m\_nAlignStyle](../Topic/CMFCButton::m_nAlignStyle.md)|指定按钮文本对齐方式。|  
|[CMFCButton::m\_nFlatStyle](../Topic/CMFCButton::m_nFlatStyle.md)|指定按钮的样式，如无边无际，平面，不稳定或三维。|  
  
## 备注  
 按钮的其他类型从 `CMFCButton` 选件类派生，例如 [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) 选件类，支持超链接和 `CMFCColorButton` 选件类，支持颜色选择器对话框。  
  
 `CMFCButton` 对象的样式可以是 *3D*，*平面*，*不稳定的* 或 *没有边框*。  按钮文本对齐，可以在左侧、顶部或按钮的中心。  在运行时，可以控制按钮是否显示文本、图像或文本和图像。  还可以指定特定光标图像显示，当光标悬停在按钮时。  
  
 使用 **MFC选件类向导** 工具和对话框模板，创建一个按钮控件直接在代码中，或。  如果直接创建一个按钮控件，请添加一个 `CMFCButton` 变量到您的应用程序，然后调用 `CMFCButton` 对象的构造函数和 `Create` 方法。  如果使用 **MFC选件类向导**，添加一个 `CButton` 变量到您的应用程序，从 `CButton` 然后将变量的类型。`CMFCButton`。  
  
 处理在对话框中应用程序的通知消息，请添加消息映射项和一个事件处理程序每个通知的。  `CMFCButton` 对象发送的通知是一样的。`CButton` 对象发送的小。  
  
## 示例  
 通过在 `CMFCButton` 选件类，中的各种方法下面的示例演示如何配置按钮的属性。  此示例是 [新的控件示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/CPP/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/CPP/cmfcbutton-class_2.cpp)]  
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/CPP/cmfcbutton-class_3.cpp)]  
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/CPP/cmfcbutton-class_4.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
## 要求  
 **标头:** afxbutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCLinkCtrl Class](../../mfc/reference/cmfclinkctrl-class.md)   
 [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md)   
 [CMFCMenuButton 类](../../mfc/reference/cmfcmenubutton-class.md)