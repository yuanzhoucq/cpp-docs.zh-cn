---
title: "CMFCCaptionBar 类 | Microsoft Docs"
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
  - "CMFCCaptionBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCCaptionBar 类"
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
caps.latest.revision: 28
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCCaptionBar 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCCaptionBar` 对象是可显示三个元素的控制条：按钮、文本标签和位图。  它可以一次只显示每个类型的组件。  您可以对齐每个元素到控件的左边缘或右边缘或为中心。  还可将简单列表或三维样式应用于标题栏的顶部和底部边界。  
  
## 语法  
  
```  
class CMFCCaptionBar : public CPane  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CMFCCaptionBar::Create](../Topic/CMFCCaptionBar::Create.md)|创建标题栏控件并将它附加到 `CMFCCaptionBar`对象。|  
|[CMFCCaptionBar::DoesAllowDynInsertBefore](../Topic/CMFCCaptionBar::DoesAllowDynInsertBefore.md)|指示另一个窗格是否可以动态插入标题栏上与其父框架。  \(重写 [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)。\)|  
|[CMFCCaptionBar::EnableButton](../Topic/CMFCCaptionBar::EnableButton.md)|启用或禁用标题栏上的按钮。|  
|[CMFCCaptionBar::GetAlignment](../Topic/CMFCCaptionBar::GetAlignment.md)|返回指定元素的对齐方式。|  
|[CMFCCaptionBar::GetBorderSize](../Topic/CMFCCaptionBar::GetBorderSize.md)|返回标题栏的边框大小。|  
|[CMFCCaptionBar::GetButtonRect](../Topic/CMFCCaptionBar::GetButtonRect.md)|检索按钮的边框标题栏上的。|  
|[CMFCCaptionBar::GetMargin](../Topic/CMFCCaptionBar::GetMargin.md)|返回标题栏元素的边缘和标题栏控件的边缘之间的距离。|  
|[CMFCCaptionBar::IsMessageBarMode](../Topic/CMFCCaptionBar::IsMessageBarMode.md)|指定标题栏是否在消息条模式。|  
|[CMFCCaptionBar::RemoveBitmap](../Topic/CMFCCaptionBar::RemoveBitmap.md)|从标题栏移除位图图像。|  
|[CMFCCaptionBar::RemoveButton](../Topic/CMFCCaptionBar::RemoveButton.md)|从标题栏移除按钮。|  
|[CMFCCaptionBar::RemoveIcon](../Topic/CMFCCaptionBar::RemoveIcon.md)|从标题栏移除图标。|  
|[CMFCCaptionBar::RemoveText](../Topic/CMFCCaptionBar::RemoveText.md)|从标题栏移除文本标签。|  
|[CMFCCaptionBar::SetBitmap](../Topic/CMFCCaptionBar::SetBitmap.md)|设置标题栏的位图图像。|  
|[CMFCCaptionBar::SetBorderSize](../Topic/CMFCCaptionBar::SetBorderSize.md)|设置标题栏的边框大小。|  
|[CMFCCaptionBar::SetButton](../Topic/CMFCCaptionBar::SetButton.md)|设置标题栏中的按钮。|  
|[CMFCCaptionBar::SetButtonPressed](../Topic/CMFCCaptionBar::SetButtonPressed.md)|指定按钮仍是否按下了。|  
|[CMFCCaptionBar::SetButtonToolTip](../Topic/CMFCCaptionBar::SetButtonToolTip.md)|设置按钮的工具提示。|  
|[CMFCCaptionBar::SetFlatBorder](../Topic/CMFCCaptionBar::SetFlatBorder.md)|设置标题栏的边框样式。|  
|[CMFCCaptionBar::SetIcon](../Topic/CMFCCaptionBar::SetIcon.md)|设置标题栏的图标。|  
|[CMFCCaptionBar::SetImageToolTip](../Topic/CMFCCaptionBar::SetImageToolTip.md)|设置图像的工具提示标题栏的。|  
|[CMFCCaptionBar::SetMargin](../Topic/CMFCCaptionBar::SetMargin.md)|设置标题栏元素的边缘和标题栏控件的边缘之间的距离。|  
|[CMFCCaptionBar::SetText](../Topic/CMFCCaptionBar::SetText.md)|设置标题栏的文本标签。|  
  
### 受保护的方法  
  
|名称|描述|  
|--------|--------|  
|[CMFCCaptionBar::OnDrawBackground](../Topic/CMFCCaptionBar::OnDrawBackground.md)|调用 framework 加载标题栏的背景。|  
|[CMFCCaptionBar::OnDrawBorder](../Topic/CMFCCaptionBar::OnDrawBorder.md)|调用由结构分区标题栏的边框。|  
|[CMFCCaptionBar::OnDrawButton](../Topic/CMFCCaptionBar::OnDrawButton.md)|调用由框架绘制标题栏按钮。|  
|[CMFCCaptionBar::OnDrawImage](../Topic/CMFCCaptionBar::OnDrawImage.md)|调用由框架绘制标题栏图像。|  
|[CMFCCaptionBar::OnDrawText](../Topic/CMFCCaptionBar::OnDrawText.md)|调用由框架绘制标题栏文本。|  
  
### 数据成员  
  
|名称|描述|  
|--------|--------|  
|[CMFCCaptionBar::m\_clrBarBackground](../Topic/CMFCCaptionBar::m_clrBarBackground.md)|标题栏的背景色。|  
|[CMFCCaptionBar::m\_clrBarBorder](../Topic/CMFCCaptionBar::m_clrBarBorder.md)|标题栏的边框的颜色。|  
|[CMFCCaptionBar::m\_clrBarText](../Topic/CMFCCaptionBar::m_clrBarText.md)|标题栏文本的颜色。|  
  
## 备注  
 若要创建标题栏，请执行以下步骤：  
  
1.  构造 `CMFCCaptionBar` 对象。  通常，您需要添加标题栏到框架窗口选件类。  
  
2.  调用 [CMFCCaptionBar::Create](../Topic/CMFCCaptionBar::Create.md) 方法创建标题栏控件并将其附加到 `CMFCCaptionBar` 对象。  
  
3.  调用 [CMFCCaptionBar::SetButton](../Topic/CMFCCaptionBar::SetButton.md)、[CMFCCaptionBar::SetText](../Topic/CMFCCaptionBar::SetText.md)、[CMFCCaptionBar::SetIcon](../Topic/CMFCCaptionBar::SetIcon.md)和 [CMFCCaptionBar::SetBitmap](../Topic/CMFCCaptionBar::SetBitmap.md) 设置标题栏元素。  
  
 将按钮元素时，必须将命令 ID。按钮。  当用户单击按钮时，标题栏路由具有此 ID 到父框架窗口的 `WM_COMMAND` 消息。  
  
 标题栏在消息条模式下也可能适用，模拟消息条出现在 Microsoft Office 2007 应用程序。  在条消息模式下，标题栏显示位图、消息（通常会打开对话框的按钮）。可以将工具提示到位图。  
  
 若要启动消息条模式，请调用 [CMFCCaptionBar::Create](../Topic/CMFCCaptionBar::Create.md) 并将第四个参数 \(bIsMessageBarMode\) 到 `TRUE`。  
  
## 示例  
 下面的示例在 `CMFCCaptionBar` 选件类演示如何使用各种方法。  此示例演示如何创建标题栏控件，设置标题栏的三维边框，设置距离，以像素为单位，在标题栏元素的边缘和标题栏控件的边缘之间，设置标题栏的按钮，将按钮的工具提示，设置标题栏的文本标签，设置标题栏的位图图像，并设置图像的工具提示在标题栏。  此代码段是 [MS 办公室 2007 中演示的示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/CPP/cmfccaptionbar-class_1.h)]  
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/CPP/cmfccaptionbar-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)  
  
## 要求  
 **标头：** afxcaptionbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)