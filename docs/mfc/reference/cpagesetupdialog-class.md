---
title: "CPageSetupDialog Class | Microsoft Docs"
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
  - "CPageSetupDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPageSetupDialog class"
  - "OLE Page Setup dialog box"
  - "页设置"
  - "“页设置”对话框"
  - "Print Setup dialog box"
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
caps.latest.revision: 24
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPageSetupDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装具有的通用OLE页面设置对话框用于设置和修改的打印边距附加支持的Windows提供的服务。  
  
## 语法  
  
```  
class CPageSetupDialog : public CCommonDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPageSetupDialog::CPageSetupDialog](../Topic/CPageSetupDialog::CPageSetupDialog.md)|构造 `CPageSetupDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPageSetupDialog::CreatePrinterDC](../Topic/CPageSetupDialog::CreatePrinterDC.md)|创建打印的设备上下文。|  
|[CPageSetupDialog::DoModal](../Topic/CPageSetupDialog::DoModal.md)|显示对话框以及允许用户进行选择。|  
|[CPageSetupDialog::GetDeviceName](../Topic/CPageSetupDialog::GetDeviceName.md)|返回打印机的设备名称。|  
|[CPageSetupDialog::GetDevMode](../Topic/CPageSetupDialog::GetDevMode.md)|返回打印机的当前 `DEVMODE`。|  
|[CPageSetupDialog::GetDriverName](../Topic/CPageSetupDialog::GetDriverName.md)|返回要使用的驱动器。|  
|[CPageSetupDialog::GetMargins](../Topic/CPageSetupDialog::GetMargins.md)|返回打印机的当前边距设置。|  
|[CPageSetupDialog::GetPaperSize](../Topic/CPageSetupDialog::GetPaperSize.md)|返回打印机的页面大小。|  
|[CPageSetupDialog::GetPortName](../Topic/CPageSetupDialog::GetPortName.md)|返回输出端口的名称。|  
|[CPageSetupDialog::OnDrawPage](../Topic/CPageSetupDialog::OnDrawPage.md)|调用框架呈现打印的页的屏幕图像。|  
|[CPageSetupDialog::PreDrawPage](../Topic/CPageSetupDialog::PreDrawPage.md)|调用由框架在呈现打印的页的屏幕之前。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPageSetupDialog::m\_psd](../Topic/CPageSetupDialog::m_psd.md)|用于的结构自定义 `CPageSetupDialog` 对象。|  
  
## 备注  
 此选件类旨在取代打印设置对话框。  
  
 使用 `CPageSetupDialog` 构造函数，若要使用 `CPageSetupDialog` 对象，请首先创建对象。  一旦对话框构造的，则可以设置或修改在 `m_psd` 数据成员的所有值初始化对话框的控件的值。  [m\_psd](../Topic/CPageSetupDialog::m_psd.md) 机制是类型 **PAGESETUPDLG**。  
  
 在初始化对话框控件后，调用 `DoModal` 成员函数显示对话框并让用户选择打印选项。  `DoModal` 返回用户是否选择了“确定”\(**IDOK**\) 或移除 \(**IDCANCEL**\) 按钮。  
  
 如果 `DoModal` 返回 **IDOK**，可以使用多个`CPageSetupDialog`的成员函数或访问 `m_psd` 数据成员，由用户检索信息输入。  
  
> [!NOTE]
>  在通用OLE页面设置对话框关闭后，用户所做的任何更改将不会由框架保存。  将由应用程序从此对话框中的所有值到一个永久位置，例如应用程序的文档或应用程序选件类的成员。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPageSetupDialog`  
  
## 要求  
 **Header:** afxdlgs.h  
  
## 请参阅  
 [MFC示例WORDPAD](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)