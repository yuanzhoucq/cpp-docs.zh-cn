---
title: "CMFCShellListCtrl Class | Microsoft Docs"
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
  - "CMFCShellListCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCShellListCtrl class"
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCShellListCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCShellListCtrl` 选件类提供Windows列表控件的功能并通过包括能够展开它显示shell项列表。  
  
## 语法  
  
```  
class CMFCShellListCtrl : public CMFCListCtrl  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCShellListCtrl::DisplayFolder](../Topic/CMFCShellListCtrl::DisplayFolder.md)|公开给提供的文件夹包含的项列表。|  
|[CMFCShellListCtrl::DisplayParentFolder](../Topic/CMFCShellListCtrl::DisplayParentFolder.md)|显示在文件夹包含是当前显示的文件夹的父项的列表。|  
|[CMFCShellListCtrl::EnableShellContextMenu](../Topic/CMFCShellListCtrl::EnableShellContextMenu.md)|启用或禁用快捷菜单。|  
|[CMFCShellListCtrl::GetCurrentFolder](../Topic/CMFCShellListCtrl::GetCurrentFolder.md)|检索当前文件夹的路径。|  
|[CMFCShellListCtrl::GetCurrentFolderName](../Topic/CMFCShellListCtrl::GetCurrentFolderName.md)|检索当前文件夹的名称。|  
|[CMFCShellListCtrl::GetCurrentItemIdList](../Topic/CMFCShellListCtrl::GetCurrentItemIdList.md)|返回当前的PIDL列表控件项目。|  
|[CMFCShellListCtrl::GetCurrentShellFolder](../Topic/CMFCShellListCtrl::GetCurrentShellFolder.md)|返回指向当前Shell文件夹。|  
|[CMFCShellListCtrl::GetItemPath](../Topic/CMFCShellListCtrl::GetItemPath.md)|返回项目的文本路径。|  
|[CMFCShellListCtrl::GetItemTypes](../Topic/CMFCShellListCtrl::GetItemTypes.md)|返回由Shell列表控件显示的项类型。|  
|[CMFCShellListCtrl::IsDesktop](../Topic/CMFCShellListCtrl::IsDesktop.md)|检查当前选定的文件夹是否是桌面文件夹。|  
|[CMFCShellListCtrl::OnCompareItems](../Topic/CMFCShellListCtrl::OnCompareItems.md)|它比较两个项目时，框架调用此方法。  （重写 [CMFCListCtrl::OnCompareItems](../Topic/CMFCListCtrl::OnCompareItems.md)。）|  
|[CMFCShellListCtrl::OnFormatFileDate](../Topic/CMFCShellListCtrl::OnFormatFileDate.md)|调用，当框架检索列表控件显示的文件日期。|  
|[CMFCShellListCtrl::OnFormatFileSize](../Topic/CMFCShellListCtrl::OnFormatFileSize.md)|调用，当框架转换列表控件文件的大小。|  
|[CMFCShellListCtrl::OnGetItemIcon](../Topic/CMFCShellListCtrl::OnGetItemIcon.md)|调用，当框架检索列表控件项的图标。|  
|[CMFCShellListCtrl::OnGetItemText](../Topic/CMFCShellListCtrl::OnGetItemText.md)|调用，当框架转换列表项控件的文本。|  
|[CMFCShellListCtrl::OnSetColumns](../Topic/CMFCShellListCtrl::OnSetColumns.md)|调用由框架，它将列的名称。|  
|[CMFCShellListCtrl::Refresh](../Topic/CMFCShellListCtrl::Refresh.md)|刷新并重新绘制列表控件。|  
|[CMFCShellListCtrl::SetItemTypes](../Topic/CMFCShellListCtrl::SetItemTypes.md)|设置列表控件显示的项的类型。|  
  
## 备注  
 `CMFCShellListCtrl` 选件类通过使程序列出了Windows shell项扩展 [CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md) 的功能。  使用的显示格式是类似资源管理器窗口的列表视图。  
  
 [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) 对象可以与 `CMFCShellListCtrl` 对象创建完全资源管理器窗口。  然后，选择在 `CMFCShellTreeCtrl` 的项将导致 `CMFCShellListCtrl` 对象列表选定项的内容。  
  
## 示例  
 下面的示例演示如何创建 `CMFCShellListCtrl` 选件类的对象以及如何显示当前显示的文件夹的父文件夹。  此代码段是 [Explorer示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/CPP/cmfcshelllistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/CPP/cmfcshelllistctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/CPP/cmfcshelllistctrl-class_3.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
 [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)  
  
## 要求  
 **标头:** afxshelllistCtrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md)   
 [CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md)