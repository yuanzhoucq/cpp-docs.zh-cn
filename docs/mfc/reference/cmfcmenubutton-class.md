---
title: "CMFCMenuButton 类 | Microsoft Docs"
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
  - "CMFCMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCMenuButton 类"
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
caps.latest.revision: 32
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCMenuButton 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

显示一个弹出菜单和报告用户选择菜单的按钮。  
  
## 语法  
  
```  
class CMFCMenuButton : public CMFCButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CMFCMenuButton::CMFCMenuButton](../Topic/CMFCMenuButton::CMFCMenuButton.md)|构造 `CMFCMenuButton` 对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CMFCMenuButton::PreTranslateMessage](../Topic/CMFCMenuButton::PreTranslateMessage.md)|调用由框架将窗口消息，在计划之前它们。  \(重写 `CMFCButton::PreTranslateMessage`。\)|  
|[CMFCMenuButton::SizeToContent](../Topic/CMFCMenuButton::SizeToContent.md)|基于其文本和图像大小更改按钮的大小。|  
  
### 数据成员  
  
|名称|描述|  
|--------|--------|  
|[CMFCMenuButton::m\_bOSMenu](../Topic/CMFCMenuButton::m_bOSMenu.md)|指定是否显示默认值系统弹出菜单或使用 [CContextMenuManager::TrackPopupMenu](../Topic/CContextMenuManager::TrackPopupMenu.md)。|  
|[CMFCMenuButton::m\_bRightArrow](../Topic/CMFCMenuButton::m_bRightArrow.md)|指定弹出菜单是否在下将显示或在按钮右侧。|  
|[CMFCMenuButton::m\_bStayPressed](../Topic/CMFCMenuButton::m_bStayPressed.md)|指定菜单按钮是否更改其状态时，在用户松开按钮之后。|  
|[CMFCMenuButton::m\_hMenu](../Topic/CMFCMenuButton::m_hMenu.md)|附加 windows 菜单的句柄。|  
|[CMFCMenuButton::m\_nMenuResult](../Topic/CMFCMenuButton::m_nMenuResult.md)|指示的标识符哪个项目用户从弹出菜单中选择。|  
  
## 备注  
 从 [CButton Class](../../mfc/reference/cbutton-class.md)，反过来，派生的 `CMFCMenuButton` 选件类从 [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md) 派生。  因此，可以在代码中使用 `CMFCMenuButton` 您将使用 `CButton`的方法相同。  
  
 当您创建 `CMFCMenuButton`时，可以在处理必须传递到关联的弹出菜单。  接下来，请调用函数 `CMFCMenuButton::SizeToContent`。  `CMFCMenuButton::SizeToContent` 检查按钮大小足以包含即指向位置弹出窗口将显示\)，下面或在按钮右侧的箭头。  
  
## 示例  
 下面的示例演示如何设置菜单的处理附加到按钮，根据其文本和图像大小调整按钮，并将由框架显示的弹出菜单。  此代码段是 [新的控件示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/CPP/cmfcmenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/CPP/cmfcmenubutton-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)  
  
## 要求  
 **标头：** afxmenubutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md)