---
title: "CFontDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFontDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFontDialog class"
  - "对话框, 字体"
  - "字体"
  - "字体, 选择"
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
caps.latest.revision: 25
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFontDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以将字体选择对话框向应用程序中。  
  
## 语法  
  
```  
class CFontDialog : public CCommonDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFontDialog::CFontDialog](../Topic/CFontDialog::CFontDialog.md)|构造 `CFontDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFontDialog::DoModal](../Topic/CFontDialog::DoModal.md)|显示对话框以及允许用户进行选择。|  
|[CFontDialog::GetCharFormat](../Topic/CFontDialog::GetCharFormat.md)|检索选定的字体的字符格式。|  
|[CFontDialog::GetColor](../Topic/CFontDialog::GetColor.md)|返回选定的字体颜色。|  
|[CFontDialog::GetCurrentFont](../Topic/CFontDialog::GetCurrentFont.md)|分配当前选定的字体行为。`LOGFONT` 结构。|  
|[CFontDialog::GetFaceName](../Topic/CFontDialog::GetFaceName.md)|返回选定字体的文本名称。|  
|[CFontDialog::GetSize](../Topic/CFontDialog::GetSize.md)|返回选定的字体磅值。|  
|[CFontDialog::GetStyleName](../Topic/CFontDialog::GetStyleName.md)|返回选定的字体样式名称。|  
|[CFontDialog::GetWeight](../Topic/CFontDialog::GetWeight.md)|返回选定的字体权重。|  
|[CFontDialog::IsBold](../Topic/CFontDialog::IsBold.md)|确定字体是否为粗体。|  
|[CFontDialog::IsItalic](../Topic/CFontDialog::IsItalic.md)|确定字体是否为斜体。|  
|[CFontDialog::IsStrikeOut](../Topic/CFontDialog::IsStrikeOut.md)|确定字体是否显示带有删除线。|  
|[CFontDialog::IsUnderline](../Topic/CFontDialog::IsUnderline.md)|确定字体是否加下划线。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CFontDialog::m\_cf](../Topic/CFontDialog::m_cf.md)|用于的结构自定义 `CFontDialog` 对象。|  
  
## 备注  
 `CFontDialog` 对象是在该系统上当前安装字体列表的对话框。  用户可以选择特定字体从列表，因此，此选择然后报告回应用程序。  
  
 构造 `CFontDialog` 对象，使用提供的构造函数或派生新的子类和使用自定义构造函数。  
  
 在 `CFontDialog` 对象构造的，则可以使用 `m_cf` framework初始化控件值或状态在对话框中。  [m\_cf](../Topic/CFontDialog::m_cf.md) 机制是类型 [CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832)。  有关此结构的更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 在初始化对话框对象的控件之后，调用 `DoModal` 成员函数显示对话框并让用户选择字体。  `DoModal` 返回用户是否选择了“确定”\(**IDOK**\) 或移除 \(**IDCANCEL**\) 按钮。  
  
 如果 `DoModal` 返回 **IDOK**，您可以使用一个`CFontDialog`的成员函数由用户检索信息输入。  
  
 可以使用Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) 函数确定错误是否在对话框的初始化时生成并了解有关该错误。  有关此功能的更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `CFontDialog` 依赖于随Windows 3.1版和更高版本的COMMDLG.DLL文件。  
  
 若要自定义对话框，从 `CFontDialog`派生选件类，提供了一个自定义对话框模板，并将消息映射处理从扩展控件的通知消息。  应通过任何未处理的消息路由到基类。  
  
 挂钩函数不需要自定义。  
  
 有关使用 `CFontDialog`的更多信息，请参见 [用于通用对话框选件类](../../mfc/common-dialog-classes.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFontDialog`  
  
## 要求  
 **Header:** afxdlgs.h  
  
## 请参阅  
 [MFC示例HIERSVR](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)