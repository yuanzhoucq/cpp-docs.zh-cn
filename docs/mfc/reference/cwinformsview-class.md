---
title: "CWinFormsView Class | Microsoft Docs"
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
  - "CWinFormsView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinFormsView class"
  - "MFC [C++], Windows 窗体支持"
  - "Windows 窗体 [C++], MFC 支持"
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
caps.latest.revision: 26
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinFormsView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为承载Windows窗体控件提供通用功能作为MFC视图。  
  
## 语法  
  
```  
class CWinFormsView : public CView;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CWinFormsView::CWinFormsView](../Topic/CWinFormsView::CWinFormsView.md)|构造 `CWinFormsView` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWinFormsView::GetControl](../Topic/CWinFormsView::GetControl.md)|检索指向Windows窗体控件。|  
  
### 公共运算符  
  
|名称||  
|--------|-|  
|[CWinFormsView::operator Control^](../Topic/CWinFormsView::operator%20Control%5E.md)|转换类型，指向Windows窗体控件。|  
  
## 备注  
 MFC使用 `CWinFormsView` 选件类以承载在MFC视图中的一个.NET Framework Windows窗体控件。  该控件是本机视图的子视图MFC视图的整个工作区。  则结果将类似于 `CFormView` 视图，使您可以利用Windows窗体设计器和运行时创建丰富的基于窗体的视图。  
  
 有关使用Windows窗体的更多信息，请参见 [在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
> [!NOTE]
>  MFC Windows窗体集成只在与MFC的项目\(定义了AFXDLL\)的项动态链接。  
  
> [!NOTE]
>  CWinFormsView不支持MFC拆分窗口\([CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)）。  目前仅Windows窗体拆分控件\(<xref:System.Windows.Forms.Splitter>\)的支持。  
  
## 要求  
 **标头:** afxwinforms.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWinFormsControl Class](../../mfc/reference/cwinformscontrol-class.md)   
 [CWinFormsDialog Class](../../mfc/reference/cwinformsdialog-class.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)