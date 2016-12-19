---
title: "CColorDialog Class | Microsoft Docs"
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
  - "CColorDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CColorDialog class"
  - "颜色, 对话框"
  - "对话框, 颜色"
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
caps.latest.revision: 25
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CColorDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允许将颜色选择对话框向应用程序中。  
  
## 语法  
  
```  
class CColorDialog : public CCommonDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CColorDialog::CColorDialog](../Topic/CColorDialog::CColorDialog.md)|构造 `CColorDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CColorDialog::DoModal](../Topic/CColorDialog::DoModal.md)|显示颜色对话框以及允许用户进行选择。|  
|[CColorDialog::GetColor](../Topic/CColorDialog::GetColor.md)|返回包含选定颜色的值 **COLORREF** 结构。|  
|[CColorDialog::GetSavedCustomColors](../Topic/CColorDialog::GetSavedCustomColors.md)|检索用户创建的自定义颜色。|  
|[CColorDialog::SetCurrentColor](../Topic/CColorDialog::SetCurrentColor.md)|强制当前颜色选择到指定的颜色。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CColorDialog::OnColorOK](../Topic/CColorDialog::OnColorOK.md)|验证颜色的重写联接对话框。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CColorDialog::m\_cc](../Topic/CColorDialog::m_cc.md)|用于的结构自定义对话框的设置。|  
  
## 备注  
 `CColorDialog` 对象是具有用于显示系统定义颜色的列表的对话框。  用户可以从列表中选择或创建特殊颜色，然后报告回应用程序，当对话框退出时。  
  
 构造 `CColorDialog` 对象，使用提供的构造函数或派生新选件类和使用自定义构造函数。  
  
 一旦对话框构造的，则可以设置或修改在[m\_cc](../Topic/CColorDialog::m_cc.md) 结构中的所有值初始化对话框的控件的值。  `m_cc` 机制是类型 [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)。  
  
 在初始化对话框的控件之后，调用 `DoModal` 成员函数显示对话框并让用户选择颜色。  `DoModal` 返回好的对话框\(**IDOK**\)或cancel \(**IDCANCEL**\)按钮的用户的选择。  
  
 如果 `DoModal` 返回 **IDOK**，您可以使用一个`CColorDialog`的成员函数由用户检索信息输入。  
  
 可以使用Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) 函数确定错误是否在对话框的初始化时生成并了解有关该错误。  
  
 `CColorDialog` 依赖于随Windows 3.1版和更高版本的COMMDLG.DLL文件。  
  
 若要自定义对话框，从 `CColorDialog`派生选件类，提供了一个自定义对话框模板，并将消息映射处理从扩展控件的通知消息。  应通过任何未处理的消息路由到基类。  
  
 挂钩函数不需要自定义。  
  
> [!NOTE]
>  在这些安装，如果使用框架进行其他 `CDialog` 对象灰色，`CColorDialog` 对象不会显示与具有灰色背景。  
  
 有关使用 `CColorDialog`的更多信息，请参见 [用于通用对话框选件类](../../mfc/common-dialog-classes.md)  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CColorDialog`  
  
## 要求  
 **Header:** afxdlgs.h  
  
## 请参阅  
 [MFC MDI示例](../../top/visual-cpp-samples.md)   
 [MFC示例DRAWCLI](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)