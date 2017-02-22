---
title: "CWinFormsDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinFormsDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinFormsDialog class"
  - "MFC [C++], Windows 窗体支持"
  - "Windows 窗体 [C++], MFC 支持"
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CWinFormsDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

承载一个Windows窗体用户控件的MFC对话框选件类的包装。  
  
## 语法  
  
```  
template <typename TManagedControl>  
class CWinFormsDialog :   
   public CDialog  
```  
  
#### 参数  
 `TManagedControl`  
 在MFC应用程序中显示的.NET Framework用户控件。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CWinFormsDialog::CWinFormsDialog](../Topic/CWinFormsDialog::CWinFormsDialog.md)|构造 `CWinFormsDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWinFormsDialog::GetControl](../Topic/CWinFormsDialog::GetControl.md)|检索对Windows窗体用户控件。|  
|[CWinFormsDialog::GetControlHandle](../Topic/CWinFormsDialog::GetControlHandle.md)|检索窗口句柄Windows窗体用户控件。|  
|[CWinFormsDialog::OnInitDialog](../Topic/CWinFormsDialog::OnInitDialog.md)|通过创建和承载此操作的一个Windows窗体用户控件初始化MFC对话框。|  
  
### 公共运算符  
  
|名称||  
|--------|-|  
|[CWinFormsDialog::operator \-\>](../Topic/CWinFormsDialog::operator%20-%3E.md)|替换在表达式中 [CWinFormsDialog::GetControl](../Topic/CWinFormsDialog::GetControl.md)。|  
|[CWinFormsDialog::operator TManagedControl^](../Topic/CWinFormsDialog::operator%20TManagedControl%5E.md)|在向Windows的引用窗体用户控件，将类型。|  
  
## 备注  
 `CWinFormsDialog` 是该MFC对话框的选件类\([CDialog](../../mfc/reference/cdialog-class.md)\)包装宿主Windows窗体\(<xref:System.Windows.Forms.UserControl>\)用户控件。  这使.NET Framework控件显示的是一个模式或无模式MFC对话框中。  
  
 有关使用Windows窗体的更多信息，请参见 [在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md) 和 [以 MFC 对话框的形式承载 Windows 窗体用户控件](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)。  
  
## 要求  
 **标头:** afxwinforms.h  
  
## 请参阅  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)