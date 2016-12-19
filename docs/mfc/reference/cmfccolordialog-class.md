---
title: "CMFCColorDialog Class | Microsoft Docs"
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
  - "CMFCColorDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorDialog class"
  - "CMFCColorDialog::m_bIsMyPalette data member"
  - "CMFCColorDialog::m_bPickerMode data member"
  - "CMFCColorDialog::m_btnColorSelect data member"
  - "CMFCColorDialog::m_CurrentColor data member"
  - "CMFCColorDialog::m_hcurPicker data member"
  - "CMFCColorDialog::m_NewColor data member"
  - "CMFCColorDialog::m_pColourSheetOne data member"
  - "CMFCColorDialog::m_pColourSheetTwo data member"
  - "CMFCColorDialog::m_pPalette data member"
  - "CMFCColorDialog::m_pPropSheet data member"
  - "CMFCColorDialog::m_wndColors data member"
  - "CMFCColorDialog::m_wndStaticPlaceHolder data member"
  - "CMFCColorDialog::PreTranslateMessage method"
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCColorDialog` 选件类表示颜色选择对话框。  
  
## 语法  
  
```  
class CMFCColorDialog : public CDialogEx  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorDialog::CMFCColorDialog](../Topic/CMFCColorDialog::CMFCColorDialog.md)|构造 `CMFCColorDialog` 对象。|  
|`CMFCColorDialog::~CMFCColorDialog`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorDialog::GetColor](../Topic/CMFCColorDialog::GetColor.md)|返回当前选定的颜色。|  
|[CMFCColorDialog::GetPalette](../Topic/CMFCColorDialog::GetPalette.md)|返回调色板。|  
|`CMFCColorDialog::PreTranslateMessage`|在将调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows功能之前，将windows消息。  有关语法和更多信息，请参见 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。  （重写 `CDialogEx::PreTranslateMessage`。）|  
|[CMFCColorDialog::RebuildPalette](../Topic/CMFCColorDialog::RebuildPalette.md)|从系统调色板派生一个调色板。|  
|[CMFCColorDialog::SetCurrentColor](../Topic/CMFCColorDialog::SetCurrentColor.md)|将当前选定的颜色。|  
|[CMFCColorDialog::SetNewColor](../Topic/CMFCColorDialog::SetNewColor.md)|设置颜色最等效具有指定的RGB值。|  
|[CMFCColorDialog::SetPageOne](../Topic/CMFCColorDialog::SetPageOne.md)|对于第一属性页中选择一个RGB值。|  
|[CMFCColorDialog::SetPageTwo](../Topic/CMFCColorDialog::SetPageTwo.md)|对于第二属性页中选择一个RGB值。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|`m_bIsMyPalette`|`TRUE`，如果颜色选择对话框使用自己的调色板或 `FALSE`，如果对话框使用在 `CMFCColorDialog` 构造函数中指定了一个调色板。|  
|`m_bPickerMode`|`TRUE`，当用户选择一种颜色从选择对话框时;否则，`FALSE`。|  
|`m_btnColorSelect`|用户选择的颜色按钮。|  
|`m_CurrentColor`|当前选定的颜色。|  
|`m_hcurPicker`|用于选择颜色的光标。|  
|`m_NewColor`|所选定的颜色，可以永久选中或还原为原始颜色。|  
|`m_pColourSheetOne`|为颜色选择属性表的第一个属性页的指针。|  
|`m_pColourSheetTwo`|为颜色选择属性表的第二个特性页的指针。|  
|`m_pPalette`|当前逻辑调色板。|  
|`m_pPropSheet`|对属性表的指针颜色选择对话框的。|  
|`m_wndColors`|颜色选取器控件对象。|  
|`m_wndStaticPlaceHolder`|是颜色选取器属性表的占位符的静态控件。|  
  
## 备注  
 颜色选择对话框中显示为带有两页的一个属性表。  在第一页，则选择一个标准颜色从系统调色板;在第二页上，选择自定义颜色。  
  
 可以使用在堆栈上的 `CMFCColorDialog` 对象并调用 `DoModal`，可以将初始颜色作为参数传递给 `CMFCColorDialog` 构造函数。  颜色选择对话框然后创建用于处理的多 [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md) 对象每个调色板。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## 示例  
 通过在 `CMFCColorDialog` 选件类，中的各种方法下面的示例演示如何配置颜色对话框。  此示例演示如何设置当前和对话框的新颜色以及如何设置为选定颜色的红色，绿色和蓝色分量在颜色对话框的两个属性页。  此示例是 [新的控件示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/CPP/cmfccolordialog-class_1.cpp)]  
  
## 要求  
 **标头:** afxcolordialog.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md)