---
title: "CPrintDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPrintDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrintDialog class"
  - "打印对话框"
  - "Print Setup dialog box"
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CPrintDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装Windows通用对话框提供的服务打印。  
  
## 语法  
  
```  
class CPrintDialog : public CCommonDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPrintDialog::CPrintDialog](../Topic/CPrintDialog::CPrintDialog.md)|构造 `CPrintDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPrintDialog::CreatePrinterDC](../Topic/CPrintDialog::CreatePrinterDC.md)|创建一个打印机上下文，而不显示打印对话框。|  
|[CPrintDialog::DoModal](../Topic/CPrintDialog::DoModal.md)|显示对话框以及允许用户进行选择。|  
|[CPrintDialog::GetCopies](../Topic/CPrintDialog::GetCopies.md)|检索请求的副本数。|  
|[CPrintDialog::GetDefaults](../Topic/CPrintDialog::GetDefaults.md)|检索设备默认值，而不显示对话框。|  
|[CPrintDialog::GetDeviceName](../Topic/CPrintDialog::GetDeviceName.md)|检索当前所选的打印机的名称。|  
|[CPrintDialog::GetDevMode](../Topic/CPrintDialog::GetDevMode.md)|检索 `DEVMODE` 结构。|  
|[CPrintDialog::GetDriverName](../Topic/CPrintDialog::GetDriverName.md)|检索当前所选的打印机驱动程序的名称。|  
|[CPrintDialog::GetFromPage](../Topic/CPrintDialog::GetFromPage.md)|检索打印范围的起始页。|  
|[CPrintDialog::GetPortName](../Topic/CPrintDialog::GetPortName.md)|检索当前所选的打印端口的名称。|  
|[CPrintDialog::GetPrinterDC](../Topic/CPrintDialog::GetPrinterDC.md)|检索处理打印机上下文。|  
|[CPrintDialog::GetToPage](../Topic/CPrintDialog::GetToPage.md)|检索打印大小的一侧页。|  
|[CPrintDialog::PrintAll](../Topic/CPrintDialog::PrintAll.md)|确定是否打印文档中的所有页。|  
|[CPrintDialog::PrintCollate](../Topic/CPrintDialog::PrintCollate.md)|确定排列的副本是否请求。|  
|[CPrintDialog::PrintRange](../Topic/CPrintDialog::PrintRange.md)|确定是否打印页的一个指定的范围。|  
|[CPrintDialog::PrintSelection](../Topic/CPrintDialog::PrintSelection.md)|确定是否只打印当前选定项。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPrintDialog::m\_pd](../Topic/CPrintDialog::m_pd.md)|用于的结构自定义 `CPrintDialog` 对象。|  
  
## 备注  
 常见的"打印"对话框提供了一种简单的方法实现打印和打印设置对话框的某些符合Windows标准。  
  
> [!NOTE]
>  `CPrintDialogEx` 选件类封装Windows 2000打印属性表提供的服务。  有关更多信息 [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) 请参见概述。  
  
 `CPrintDialog`的功能由该 [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)取代，旨在提供了一个通用对话框对打印设置和页面设置。  
  
 可以依赖于框架到的许多方面为您的应用程序晒印方法的句柄。  在这种情况下，框架自动显示打印的Windows通用对话框。  还可以使应用程序的框架处理打印，但重写具有自己的打印对话框的常见的"打印"对话框。  有关用于处理打印作业结构的更多信息，请参见文章 [打印](../../mfc/printing.md)。  
  
 如果希望应用程序处理打印，而无需结构的中，可以按原样使用 `CPrintDialog` 选件类使用提供的构造函数，也可从 `CPrintDialog` 和写入派生自己的对话框选件类构造函数以满足您的要求。  在任何情况下，因为它们是从选件类 `CCommonDialog`，派生这些对话框中的行为与标准MFC对话框。  
  
 使用 `CPrintDialog` 构造函数，若要使用 `CPrintDialog` 对象，请首先创建对象。  一旦对话框构造的，则可以设置或修改在 [m\_pd](../Topic/CPrintDialog::m_pd.md) 结构中的所有值初始化对话框的控件的值。  `m_pd` 机制是类型 [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)。  有关此结构的更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果您没有提供您在 `m_pd` 自己的处理 **hDevMode** 和 **hDevNames** 的成员，请务必调用这些句柄的Windows函数 **GlobalFree**，当处理对话框时。  在使用 `CWinApp::OnFilePrintSetup`中提供的机制的打印一组实现，您不必释放这些句柄。  句柄由 `CWinApp` 维护并在 `CWinApp` 析构函数中释放。  在使用独立时，的 `CPrintDialog` 释放这些仅处理是必需的。  
  
 在初始化对话框控件后，调用 `DoModal` 成员函数显示对话框并让用户选择打印选项。  `DoModal` 返回用户是否选择了“确定”\(**IDOK**\) 或移除 \(**IDCANCEL**\) 按钮。  
  
 如果 `DoModal` 返回 **IDOK**，您可以使用一个`CPrintDialog`的成员函数由用户检索信息输入。  
  
 `CPrintDialog::GetDefaults` 成员函数用于检索当前默认打印机很有用，而不显示对话框。  此成员函数不要求用户交互。  
  
 可以使用Windows **CommDlgExtendedError** 函数确定错误是否在对话框的初始化时生成并了解有关该错误。  有关此功能的更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `CPrintDialog` 依赖于随Windows 3.1版和更高版本的COMMDLG.DLL文件。  
  
 若要自定义对话框，从 `CPrintDialog`派生选件类，提供了一个自定义对话框模板，并将消息映射处理从扩展控件的通知消息。  应传递任何未处理的消息路由到基类。  挂钩函数不需要自定义。  
  
 若要以不同的方式处理同一消息基于对话框是否打印或打印设置，必须派生各对话框的选件类。  您还必须重写Windows **AttachOnSetup** 功能，处理新对话框的创建，打印时将按钮在打印对话框中选中。  
  
 有关使用 `CPrintDialog`的更多信息，请参见 [用于通用对话框选件类](../../mfc/common-dialog-classes.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialog`  
  
## 要求  
 **Header:** afxdlgs.h  
  
## 请参阅  
 [MFC示例DIBLOOK](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPrintInfo Structure](../../mfc/reference/cprintinfo-structure.md)