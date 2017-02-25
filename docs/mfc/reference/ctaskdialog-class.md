---
title: "CTaskDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTaskDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTaskDialog class"
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CTaskDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对象就象消息框，但在弹出对话框会显示附加信息传递给用户。  `CTaskDialog` 还包括集合功能的信息从用户。  
  
## 语法  
  
```  
class CTaskDialog : public CObject  
```  
  
## 成员  
  
### 构造函数  
  
|||  
|-|-|  
|[CTaskDialog::CTaskDialog](../Topic/CTaskDialog::CTaskDialog.md)|构造 `CTaskDialog` 对象。|  
  
### 方法  
  
|||  
|-|-|  
|[CTaskDialog::AddCommandControl](../Topic/CTaskDialog::AddCommandControl.md)|添加一个命令按钮控件。`CTaskDialog`。|  
|[CTaskDialog::AddRadioButton](../Topic/CTaskDialog::AddRadioButton.md)|添加一个单选按钮 `CTaskDialog`。|  
|[CTaskDialog::ClickCommandControl](../Topic/CTaskDialog::ClickCommandControl.md)|单击命令按钮控件或通用按钮程序模型。|  
|[CTaskDialog::ClickRadioButton](../Topic/CTaskDialog::ClickRadioButton.md)|单击单选按钮程序模型。|  
|[CTaskDialog::DoModal](../Topic/CTaskDialog::DoModal.md)|显示`CTaskDialog`。|  
|[CTaskDialog::GetCommonButtonCount](../Topic/CTaskDialog::GetCommonButtonCount.md)|检索可用常见的按钮数。|  
|[CTaskDialog::GetCommonButtonFlag](../Topic/CTaskDialog::GetCommonButtonFlag.md)|将标准Windows按钮为通用按钮类型与 `CTaskDialog` 选件类。|  
|[CTaskDialog::GetCommonButtonId](../Topic/CTaskDialog::GetCommonButtonId.md)|常见按钮类型的转换为与 `CTaskDialog` 选件类对标准Windows按钮。|  
|[CTaskDialog::GetOptions](../Topic/CTaskDialog::GetOptions.md)|返回此 `CTaskDialog`的可选标志。|  
|[CTaskDialog::GetSelectedCommandControlID](../Topic/CTaskDialog::GetSelectedCommandControlID.md)|返回选定的命令按钮控件。|  
|[CTaskDialog::GetSelectedRadioButtonID](../Topic/CTaskDialog::GetSelectedRadioButtonID.md)|返回选定的单选按钮。|  
|[CTaskDialog::GetVerificationCheckboxState](../Topic/CTaskDialog::GetVerificationCheckboxState.md)|检索验证复选框的状态。|  
|[CTaskDialog::IsCommandControlEnabled](../Topic/CTaskDialog::IsCommandControlEnabled.md)|确定命令按钮控件或通用按钮是否启用。|  
|[CTaskDialog::IsRadioButtonEnabled](../Topic/CTaskDialog::IsRadioButtonEnabled.md)|确定单选按钮是否启用。|  
|[CTaskDialog::IsSupported](../Topic/CTaskDialog::IsSupported.md)|确定正在运行应用程序的计算机是否支持 `CTaskDialog`。|  
|[CTaskDialog::LoadCommandControls](../Topic/CTaskDialog::LoadCommandControls.md)|添加命令按钮控件使用数据从字符串表。|  
|[CTaskDialog::LoadRadioButtons](../Topic/CTaskDialog::LoadRadioButtons.md)|添加单选按钮即可使用数据从字符串表。|  
|[CTaskDialog::NavigateTo](../Topic/CTaskDialog::NavigateTo.md)|调用焦点到另一 `CTaskDialog`。|  
|[CTaskDialog::OnCommandControlClick](../Topic/CTaskDialog::OnCommandControlClick.md)|当用户单击命令按钮控件时，框架调用此方法。|  
|[CTaskDialog::OnCreate](../Topic/CTaskDialog::OnCreate.md)|然后再创建 `CTaskDialog`后，框架调用此方法。|  
|[CTaskDialog::OnDestroy](../Topic/CTaskDialog::OnDestroy.md)|在它销毁 `CTaskDialog`之前，框架调用此方法。|  
|[CTaskDialog::OnExpandButtonClick](../Topic/CTaskDialog::OnExpandButtonClick.md)|当用户单击展开按钮时，框架调用此方法。|  
|[CTaskDialog::OnHelp](../Topic/CTaskDialog::OnHelp.md)|当用户请求帮助时，框架调用此方法。|  
|[CTaskDialog::OnHyperlinkClick](../Topic/CTaskDialog::OnHyperlinkClick.md)|当用户单击超链接时，框架调用此方法。|  
|[CTaskDialog::OnInit](../Topic/CTaskDialog::OnInit.md)|当 `CTaskDialog` 初始化时，框架调用此方法。|  
|[CTaskDialog::OnNavigatePage](../Topic/CTaskDialog::OnNavigatePage.md)|当用户移动焦点有关 `CTaskDialog`中的控件时，框架调用此方法。|  
|[CTaskDialog::OnRadioButtonClick](../Topic/CTaskDialog::OnRadioButtonClick.md)|当用户选择一个单选按钮控件时，框架调用此方法。|  
|[CTaskDialog::OnTimer](../Topic/CTaskDialog::OnTimer.md)|当计时器过期时，框架调用此方法。|  
|[CTaskDialog::OnVerificationCheckboxClick](../Topic/CTaskDialog::OnVerificationCheckboxClick.md)|当用户单击验证复选框时，框架调用此方法。|  
|[CTaskDialog::RemoveAllCommandControls](../Topic/CTaskDialog::RemoveAllCommandControls.md)|从 `CTaskDialog`移除所有命令控件。|  
|[CTaskDialog::RemoveAllRadioButtons](../Topic/CTaskDialog::RemoveAllRadioButtons.md)|从 `CTaskDialog`移除所有单选按钮。|  
|[CTaskDialog::SetCommandControlOptions](../Topic/CTaskDialog::SetCommandControlOptions.md)|更新在 `CTaskDialog`的命令按钮控件。|  
|[CTaskDialog::SetCommonButtonOptions](../Topic/CTaskDialog::SetCommonButtonOptions.md)|更新将启用的常见按钮的子集并需要UAC特权提升。|  
|[CTaskDialog::SetCommonButtons](../Topic/CTaskDialog::SetCommonButtons.md)|添加常见按钮。`CTaskDialog`。|  
|[CTaskDialog::SetContent](../Topic/CTaskDialog::SetContent.md)|更新 `CTaskDialog`的内容。|  
|[CTaskDialog::SetDefaultCommandControl](../Topic/CTaskDialog::SetDefaultCommandControl.md)|指定默认命令按钮控件。|  
|[CTaskDialog::SetDefaultRadioButton](../Topic/CTaskDialog::SetDefaultRadioButton.md)|指定默认单选按钮。|  
|[CTaskDialog::SetDialogWidth](../Topic/CTaskDialog::SetDialogWidth.md)|调整 `CTaskDialog`的宽度。|  
|[CTaskDialog::SetExpansionArea](../Topic/CTaskDialog::SetExpansionArea.md)|更新 `CTaskDialog`的展开区域。|  
|[CTaskDialog::SetFooterIcon](../Topic/CTaskDialog::SetFooterIcon.md)|更新 `CTaskDialog`的页脚图标。|  
|[CTaskDialog::SetFooterText](../Topic/CTaskDialog::SetFooterText.md)|更新在 `CTaskDialog`的页脚的文本。|  
|[CTaskDialog::SetMainIcon](../Topic/CTaskDialog::SetMainIcon.md)|更新 `CTaskDialog`的主要图标。|  
|[CTaskDialog::SetMainInstruction](../Topic/CTaskDialog::SetMainInstruction.md)|更新 `CTaskDialog`的主要命令。|  
|[CTaskDialog::SetOptions](../Topic/CTaskDialog::SetOptions.md)|配置 `CTaskDialog`的选项。|  
|[CTaskDialog::SetProgressBarMarquee](../Topic/CTaskDialog::SetProgressBarMarquee.md)|配置 `CTaskDialog` 的一个marquee栏并将其添加到对话框。|  
|[CTaskDialog::SetProgressBarPosition](../Topic/CTaskDialog::SetProgressBarPosition.md)|调整进度栏的位置。|  
|[CTaskDialog::SetProgressBarRange](../Topic/CTaskDialog::SetProgressBarRange.md)|调整进度栏的大小。|  
|[CTaskDialog::SetProgressBarState](../Topic/CTaskDialog::SetProgressBarState.md)|设置进度栏的状态并将其显示在 `CTaskDialog`。|  
|[CTaskDialog::SetRadioButtonOptions](../Topic/CTaskDialog::SetRadioButtonOptions.md)|启用或禁用单选按钮。|  
|[CTaskDialog::SetVerificationCheckbox](../Topic/CTaskDialog::SetVerificationCheckbox.md)|设置验证复选框中选中状态。|  
|[CTaskDialog::SetVerificationCheckboxText](../Topic/CTaskDialog::SetVerificationCheckboxText.md)|在验证复选框右侧的设置文本。|  
|[CTaskDialog::SetWindowTitle](../Topic/CTaskDialog::SetWindowTitle.md)|设置 `CTaskDialog`的标题。|  
|[CTaskDialog::ShowDialog](../Topic/CTaskDialog::ShowDialog.md)|创建并显示 `CTaskDialog`。|  
|[CTaskDialog::TaskDialogCallback](../Topic/CTaskDialog::TaskDialogCallback.md)|框架调用此响应各种Windows消息。|  
  
### 数据成员  
  
|||  
|-|-|  
|`m_aButtons`|`CTaskDialog`的命令按钮控件。|  
|`m_aRadioButtons`|`CTaskDialog`的单选按钮控件。|  
|`m_bVerified`|`TRUE` 指示验证复选框处于选中状态; `FALSE` 指示未启用。|  
|`m_footerIcon`|在 `CTaskDialog`的页脚的图标。|  
|`m_hWnd`|一个句柄 `CTaskDialog`的窗口。|  
|`m_mainIcon`|`CTaskDialog`的主要图标。|  
|`m_nButtonDisabled`|指示掩码哪些常见会禁用按钮。|  
|`m_nButtonElevation`|指示掩码哪些常见按钮需要UAC特权提升。|  
|`m_nButtonId`|选定的命令按钮控件的ID。|  
|`m_nCommonButton`|指示掩码哪些常见的按钮。`CTaskDialog`显示。|  
|`m_nDefaultCommandControl`|选中命令按钮控件的ID，当 `CTaskDialog` 显示。|  
|`m_nDefaultRadioButton`|选中单选按钮控件的ID，当 `CTaskDialog` 显示。|  
|`m_nFlags`|指示 `CTaskDialog`的选项掩码。|  
|`m_nProgressPos`|进度栏的当前位置。  该值必须介于 `m_nProgressRangeMin` 和 `m_nProgressRangeMax` 之间。|  
|`m_nProgressRangeMax`|进度栏的最大值。|  
|`m_nProgressRangeMin`|进度栏的最小值。|  
|`m_nProgressState`|进度栏的状态。  有关更多信息，请参见 [CTaskDialog::SetProgressBarState](../Topic/CTaskDialog::SetProgressBarState.md)。|  
|`m_nRadioId`|选定的单选按钮控件的ID。|  
|`m_nWidth`|`CTaskDialog` 的宽度（以像素为单位）。|  
|`m_strCollapse`|`CTaskDialog` 在展开框右侧显示的字符串，在展开的信息隐藏。|  
|`m_strContent`|`CTaskDialog`的内容字符串。|  
|`m_strExpand`|`CTaskDialog` 在展开框右侧显示的字符串，在展开的信息显示。|  
|`m_strFooter`|`CTaskDialog`的页脚。|  
|`m_strInformation`|`CTaskDialog`的扩展的信息。|  
|`m_strMainInstruction`|`CTaskDialog`的主要命令。|  
|`m_strTitle`|`CTaskDialog` 的标题。|  
|`m_strVerification`|`CTaskDialog` 在验证复选框右侧显示的字符串。|  
  
## 备注  
 `CTaskDialog` 选件类替换标准Windows消息框并具有其他功能\(例如收集来自用户的信息的新控件。  此选件类在 [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)]的MFC库中。  `CTaskDialog` 可用从开始 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  Windows的早期版本无法显示 `CTaskDialog` 对象。  使用 `CTaskDialog::IsSupported` 确定运行时当前用户是否可以显示任务对话框。  标准Windows消息框。[!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)]仍支持。  
  
 使用Unicode库时，因此，只有当您生成应用程序 `CTaskDialog` 可用。  
  
 `CTaskDialog` 有两种不同的构造函数。  构造函数可以指定两个命令按钮和更多六个普通按钮控件。  在创建 `CTaskDialog`后，可以添加更多命令按钮。  第二个构造函数不支持任何命令按钮，但是，您可以添加数量没有限制的普通按钮控件。  有关构造的更多信息，请参见 [CTaskDialog::CTaskDialog](../Topic/CTaskDialog::CTaskDialog.md)。  
  
 下图显示示例 `CTaskDialog` 说明中的某些位置控件。  
  
 ![CTaskDialog 示例](../../mfc/reference/media/ctaskdialogsample.png "CTaskDialogSample")  
CTaskDialog示例  
  
## 要求  
 **最少量必需的操作系统:** [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
 **标头:** afxtaskdialog.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [演练：向应用程序添加 CTaskDialog](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)