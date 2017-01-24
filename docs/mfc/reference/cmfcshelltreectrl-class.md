---
title: "CMFCShellTreeCtrl Class | Microsoft Docs"
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
  - "CMFCShellTreeCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCShellTreeCtrl class"
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCShellTreeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCShellTreeCtrl` 选件类通过显示Shell项目层次结构扩展 [CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md) 功能。  
  
## 语法  
  
```  
class CMFCShellTreeCtrl : public CTreeCtrl  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCShellTreeCtrl::EnableShellContextMenu](../Topic/CMFCShellTreeCtrl::EnableShellContextMenu.md)|启用或禁用快捷菜单。|  
|[CMFCShellTreeCtrl::GetFlags](../Topic/CMFCShellTreeCtrl::GetFlags.md)|返回传递给 [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)标志的组合。|  
|[CMFCShellTreeCtrl::GetItemPath](../Topic/CMFCShellTreeCtrl::GetItemPath.md)|检索的路径项目。|  
|[CMFCShellTreeCtrl::GetRelatedList](../Topic/CMFCShellTreeCtrl::GetRelatedList.md)|返回指向与此 `CMFCShellTreeCtrl` 对象一起使用来创建类似于资源管理器窗口的 [CMFCShellListCtrl Class](../../mfc/reference/cmfcshelllistctrl-class.md) 对象。|  
|[CMFCShellTreeCtrl::OnChildNotify](../Topic/CMFCShellTreeCtrl::OnChildNotify.md)|此成员函数由此窗口的父窗口调用，在收到应用于此窗口的通知消息时返回。  （重写 [CWnd::OnChildNotify](../Topic/CWnd::OnChildNotify.md)。）|  
|[CMFCShellTreeCtrl::OnGetItemIcon](../Topic/CMFCShellTreeCtrl::OnGetItemIcon.md)||  
|[CMFCShellTreeCtrl::OnGetItemText](../Topic/CMFCShellTreeCtrl::OnGetItemText.md)||  
|[CMFCShellTreeCtrl::Refresh](../Topic/CMFCShellTreeCtrl::Refresh.md)|刷新并重新绘制当前 `CMFCShellTreeCtrl` 对象。|  
|[CMFCShellTreeCtrl::SelectPath](../Topic/CMFCShellTreeCtrl::SelectPath.md)|选择基于所提供的PIDL或字符串路径的相应树控件项目。|  
|[CMFCShellTreeCtrl::SetFlags](../Topic/CMFCShellTreeCtrl::SetFlags.md)|设置标志筛选树上下文\(类似于 `IShellFolder::EnumObjects`使用的标志）。|  
|[CMFCShellTreeCtrl::SetRelatedList](../Topic/CMFCShellTreeCtrl::SetRelatedList.md)|将当前 `CMFCShellTreeCtrl` 对象和 `CMFCShellListCtrl` 对象之间的关系。|  
  
## 备注  
 此选件类通过使程序\(包括Windows Shell项目在树扩展 `CTreeCtrl` 选件类。  此选件类可以与 `CMFCShellListCtrl` 对象创建完全资源管理器窗口。  然后，选择在树中的一个项目将显示在关联的Windows Shell项列表。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CTreeCtrl](../../mfc/reference/ctreectrl-class.md)  
  
 [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)  
  
## 要求  
 **标头:** afxshelltreeCtrl.h  
  
## 示例  
 下面的示例演示如何创建 `CMFCShellTreeCtrl` 选件类的对象。  此代码段是 [Explorer示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/CPP/cmfcshelltreectrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/CPP/cmfcshelltreectrl-class_2.cpp)]  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)   
 [CMFCShellListCtrl Class](../../mfc/reference/cmfcshelllistctrl-class.md)