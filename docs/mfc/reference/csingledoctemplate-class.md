---
title: "CSingleDocTemplate Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSingleDocTemplate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSingleDocTemplate class"
  - "文档模板, single"
  - "单文档界面 (SDI), 应用程序"
  - "模板, SDI"
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CSingleDocTemplate Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定义实现单文档界面\(SDI\)的文档模板。  
  
## 语法  
  
```  
class CSingleDocTemplate : public CDocTemplate  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSingleDocTemplate::CSingleDocTemplate](../Topic/CSingleDocTemplate::CSingleDocTemplate.md)|构造 `CSingleDocTemplate` 对象。|  
  
## 备注  
 SDI应用程序使用主框架窗口显示文档;仅文档中一次是打开的。  
  
 文档模板定义选件类之间的三种类型的关系:  
  
-   文档选件类，则从 **CDocument**派生。  
  
-   视图选件类，显示从文档选件类的数据上面列出的。  可以从 `CView`、 `CScrollView`、 `CFormView`或 `CEditView`派生此选件类。  （可以直接还使用 `CEditView`。）  
  
-   框架窗口选件类，包含视图。  对于SDI文档模板，可以从 `CFrameWnd`派生类;此选件如果不需要自定义主框架窗口的行为，则可以使用 `CFrameWnd` 直接，而无需派生您的选件类。  
  
 SDI应用程序通常支持一个文档类型，因此，只有一 `CSingleDocTemplate` 对象。  仅文档中一次是打开的。  
  
 您不需要调用 `CSingleDocTemplate` 的任何成员函数除外构造函数。  内部结构处理 `CSingleDocTemplate` 对象。  
  
 有关使用 `CSingleDocTemplate`的更多信息，请参见 [文档模板，而且文档\/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CSingleDocTemplate`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC DOCKTOOL示例](../../top/visual-cpp-samples.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CMultiDocTemplate Class](../../mfc/reference/cmultidoctemplate-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)