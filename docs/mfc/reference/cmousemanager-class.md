---
title: "CMouseManager Class | Microsoft Docs"
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
  - "CMouseManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMouseManager class"
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
caps.latest.revision: 26
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMouseManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允许用户关联查看不同的命令与特定 [CView](../../mfc/reference/cview-class.md) 对象，当用户双击于时。  
  
## 语法  
  
```  
class CMouseManager : public CObject  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMouseManager::AddView](../Topic/CMouseManager::AddView.md)|添加一 `CView` 对象到 **自定义项** 对话框。  **自定义项** 对话框允许用户关联使用每一个的命令列表的视图。|  
|[CMouseManager::GetViewDblClickCommand](../Topic/CMouseManager::GetViewDblClickCommand.md)|返回执行的命令，当用户双击外表中提供的视图中。|  
|[CMouseManager::GetViewIconId](../Topic/CMouseManager::GetViewIconId.md)|返回图标与提供的视图. ID|  
|[CMouseManager::GetViewIdByName](../Topic/CMouseManager::GetViewIdByName.md)|返回视图ID与提供的视图名称。|  
|[CMouseManager::GetViewNames](../Topic/CMouseManager::GetViewNames.md)|检索所有已添加的视图名称的列表。|  
|[CMouseManager::LoadState](../Topic/CMouseManager::LoadState.md)|从Windows注册表加载 `CMouseManager` 状态。|  
|[CMouseManager::SaveState](../Topic/CMouseManager::SaveState.md)|写入Windows注册表中 `CMouseManager` 状态。|  
|[CMouseManager::SetCommandForDblClk](../Topic/CMouseManager::SetCommandForDblClk.md)|关联所提供的命令和一个提供的视图。|  
  
## 备注  
 `CMouseManager` 选件类维护 `CView` 对象的集合。  每个视图确定所用的名称和由ID.  这些视图。**自定义项** 将显示对话框。  用户可以更改与所有视图。**自定义项** 对话框的命令。  当用户在该视图中，双击该关联的命令执行。  若要支持此从编码的角度讲，必须处理 `WM_LBUTTONDBLCLK` 消息并对代码的 [CWinAppEx::OnViewDoubleClick](../Topic/CWinAppEx::OnViewDoubleClick.md) 功能该 `CView` 对象的。  
  
 您不应该手动创建 `CMouseManager` 对象。  它将由应用程序框架创建。  当用户退出应用程序，还将自动销毁它。  获取对鼠标管理器的指针应用程序中，调用 [CWinAppEx::GetMouseManager](../Topic/CWinAppEx::GetMouseManager.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMouseManager](../../mfc/reference/cmousemanager-class.md)  
  
## 要求  
 **标头:** afxmousemanager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)