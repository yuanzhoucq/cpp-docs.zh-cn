---
title: "CMultiDocTemplate Class | Microsoft Docs"
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
  - "CMultiDocTemplate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiDocTemplate class"
  - "MDI, 模板"
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMultiDocTemplate Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定义实现多文档界面\(MDI\)的文档模板。  
  
## 语法  
  
```  
  
class CMultiDocTemplate : public CDocTemplate  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMultiDocTemplate::CMultiDocTemplate](../Topic/CMultiDocTemplate::CMultiDocTemplate.md)|构造 `CMultiDocTemplate` 对象。|  
  
## 备注  
 MDI应用程序使用主框架窗口，当用户可以打开的工作区零个或多个文档框架窗口，其中显示每个文档。  有关MDI的详细说明，请参见*针对软件设计的 Windows 界面指南*。  
  
 文档模板定义了选件类中的三种类型的关系:  
  
-   文档选件类，则从 [CDocument](../../mfc/reference/cdocument-class.md)派生。  
  
-   视图选件类，显示从文档选件类的数据上面列出的。  可以从 [CView](../../mfc/reference/cview-class.md)、 `CScrollView`、 `CFormView`或 `CEditView`派生此选件类。  （可以直接还使用 `CEditView`。）  
  
-   框架窗口选件类，包含视图。  对于MDI文档模板，可以从 `CMDIChildWnd`派生此选件类，或者，如果不需要，自定义文档框架窗口的行为，则可以使用 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) 直接，而无需派生您的选件类。  
  
 MDI应用程序可以支持多个文档类型，并且文档不同的类型可以同时打开。  您的应用程序具有文档每个模板它所支持的文件类型。  例如，因此，如果您的MDI应用程序支持电子表格，并文本文档，应用程序有两 `CMultiDocTemplate` 对象。  
  
 当用户创建新文档时，应用程序使用文档模板。  如果应用程序支持多个文档类型，则框架在文件的对话框的列表获取支持的名称从文档模板中的文件类型并显示它们。  如果用户选择了一个文件类型，应用程序创建文档选件类对象、一框架窗口对象和一个视图对象并相互附加它们。  
  
 您不需要调用 `CMultiDocTemplate` 的任何成员函数除外构造函数。  内部结构处理 `CMultiDocTemplate` 对象。  
  
 有关 `CMultiDocTemplate`的更多信息，请参见 [文档模板，而且文档\/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CMultiDocTemplate`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CSingleDocTemplate Class](../../mfc/reference/csingledoctemplate-class.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)