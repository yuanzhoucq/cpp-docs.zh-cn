---
title: "CPrintDialogEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPrintDialogEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrintDialogEx class"
  - "打印对话框"
  - "Print Setup dialog box"
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CPrintDialogEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装Windows 2000打印属性表提供的服务。  
  
## 语法  
  
```  
class CPrintDialogEx : public CCommonDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPrintDialogEx::CPrintDialogEx](../Topic/CPrintDialogEx::CPrintDialogEx.md)|构造 `CPrintDialogEx` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPrintDialogEx::CreatePrinterDC](../Topic/CPrintDialogEx::CreatePrinterDC.md)|创建一个打印机上下文，而不显示打印对话框。|  
|[CPrintDialogEx::DoModal](../Topic/CPrintDialogEx::DoModal.md)|显示对话框以及允许用户进行选择。|  
|[CPrintDialogEx::GetCopies](../Topic/CPrintDialogEx::GetCopies.md)|检索请求的副本数。|  
|[CPrintDialogEx::GetDefaults](../Topic/CPrintDialogEx::GetDefaults.md)|检索设备默认值，而不显示对话框。|  
|[CPrintDialogEx::GetDeviceName](../Topic/CPrintDialogEx::GetDeviceName.md)|检索当前所选的打印机的名称。|  
|[CPrintDialogEx::GetDevMode](../Topic/CPrintDialogEx::GetDevMode.md)|检索 `DEVMODE` 结构。|  
|[CPrintDialogEx::GetDriverName](../Topic/CPrintDialogEx::GetDriverName.md)|检索SYSTEM中定义的打印机设备驱动程序的名称。|  
|[CPrintDialogEx::GetPortName](../Topic/CPrintDialogEx::GetPortName.md)|检索当前所选的打印端口的名称。|  
|[CPrintDialogEx::GetPrinterDC](../Topic/CPrintDialogEx::GetPrinterDC.md)|检索处理打印机上下文。|  
|[CPrintDialogEx::PrintAll](../Topic/CPrintDialogEx::PrintAll.md)|确定是否打印文档中的所有页。|  
|[CPrintDialogEx::PrintCollate](../Topic/CPrintDialogEx::PrintCollate.md)|确定排列的副本是否请求。|  
|[CPrintDialogEx::PrintCurrentPage](../Topic/CPrintDialogEx::PrintCurrentPage.md)|确定是否打印文档的当前页面。|  
|[CPrintDialogEx::PrintRange](../Topic/CPrintDialogEx::PrintRange.md)|确定是否打印页的一个指定的范围。|  
|[CPrintDialogEx::PrintSelection](../Topic/CPrintDialogEx::PrintSelection.md)|确定是否只打印当前选定项。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPrintDialogEx::m\_pdex](../Topic/CPrintDialogEx::m_pdex.md)|用于的结构自定义 `CPrintDialogEx` 对象。|  
  
## 备注  
 可以依赖于框架到的许多方面为您的应用程序晒印方法的句柄。  有关用于处理打印作业结构的更多信息，请参见文章 [打印](../../mfc/printing.md)。  
  
 如果希望应用程序处理打印，而无需结构的中，可以按原样使用 `CPrintDialogEx` 选件类使用提供的构造函数，也可从 `CPrintDialogEx` 和写入派生自己的对话框选件类构造函数以满足您的要求。  在任何情况下，因为它们是从选件类 `CCommonDialog`，派生这些对话框中的行为与标准MFC对话框。  
  
 使用 `CPrintDialogEx` 构造函数，若要使用 `CPrintDialogEx` 对象，请首先创建对象。  一旦对话框构造的，则可以设置或修改在 [m\_pdex](../Topic/CPrintDialogEx::m_pdex.md) 结构中的所有值初始化对话框的控件的值。  `m_pdex` 机制是类型 [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844)。  有关此结构的更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果您没有提供您在 `m_pdex` 自己的处理 **hDevMode** 和 **hDevNames** 的成员，请务必调用这些句柄的Windows函数 **GlobalFree**，当处理对话框时。  
  
 在初始化对话框控件后，调用 `DoModal` 成员函数显示对话框并让用户选择打印选项。  当 `DoModal` 返回时，可以确定用户是否选择了"，应用或取消按钮。  
  
 如果用户按已在就绪，可以使用`CPrintDialogEx`的成员函数由用户检索信息输入。  
  
 `CPrintDialogEx::GetDefaults` 成员函数用于检索当前默认打印机很有用，而不显示对话框。  此方法不需要用户交互。  
  
 可以使用Windows **CommDlgExtendedError** 函数确定错误是否在对话框的初始化时生成并了解有关该错误。  有关此功能的更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关使用 `CPrintDialogEx`的更多信息，请参见 [用于通用对话框选件类](../../mfc/common-dialog-classes.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `IObjectWithSite`  
  
 `IPrintDialogCallback`  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialogEx`  
  
## 要求  
 **Header:** afxdlgs.h  
  
## 请参阅  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPrintInfo Structure](../../mfc/reference/cprintinfo-structure.md)