---
title: "IView Interface | Microsoft Docs"
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
  - "IView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IView class"
  - "views [MFC]"
  - "视图, 类"
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
caps.latest.revision: 23
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IView Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

执行 [CWinFormsView](../../mfc/reference/cwinformsview-class.md) 使用视图通知发送到托管控件的方法。  
  
## 语法  
  
```  
interface class IView  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IView::OnActivateView](../Topic/IView::OnActivateView.md)|调用由MFC激活时，视图或停用。|  
|[IView::OnInitialUpdate](../Topic/IView::OnInitialUpdate.md)|调用由框架，该视图首先附加到文档后，但，该视图最初显示之前。|  
|[IView::OnUpdate](../Topic/IView::OnUpdate.md)|调用由MFC，该视图的文档之后修改的;此功能允许视图更新其显示反映修改。|  
  
## 备注  
 `IView` 执行 `CWinFormsView` 使用向前常见视图通知给承载的托管控件的方法。  这些是 [OnInitialUpdate](../Topic/IView::OnInitialUpdate.md)、 [OnUpdate](../Topic/IView::OnUpdate.md) 和 [OnActivateView](../Topic/IView::OnActivateView.md)。  
  
 `IView` 类似于 [CView](../../mfc/reference/cview-class.md)，但是，仅使用具有管理视图和控件。  
  
 有关使用Windows窗体的更多信息，请参见 [在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
## 要求  
 标头:afxwinforms.h \(定义程序集中atlmfc \\ lib \\ mfcmifc80.dll\)  
  
## 请参阅  
 [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)