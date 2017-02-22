---
title: "CMDITabInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMDITabInfo"
  - "CMDITabInfo.CMDITabInfo"
  - "CMDITabInfo::CMDITabInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDITabInfo class"
  - "CMDITabInfo class, 构造函数"
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
caps.latest.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 39
---
# CMDITabInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMDITabInfo` 选件类用于将参数传递到 [CMDIFrameWndEx::EnableMDITabbedGroups](../Topic/CMDIFrameWndEx::EnableMDITabbedGroups.md) 方法。  此选件类的成员控件支持MDI选项卡式组行为。  
  
## 语法  
  
```  
class CMDITabInfo   
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMDITabInfo::CMDITabInfo`|默认构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMDITabInfo::Serialize](../Topic/CMDITabInfo::Serialize.md)|读取或写入此对象从或对存档。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMDITabInfo::m\_bActiveTabCloseButton;](../Topic/CMDITabInfo::m_bActiveTabCloseButton;.md)|指定 **关闭** 按钮是否在活动选项卡上的标签中显示。|  
|[CMDITabInfo::m\_bAutoColor](../Topic/CMDITabInfo::m_bAutoColor.md)|指定是否在MDI选项。|  
|[CMDITabInfo::m\_bDocumentMenu](../Topic/CMDITabInfo::m_bDocumentMenu.md)|指定选项卡组是否显示的弹出菜单列出打开文档或显示滚动按钮。|  
|[CMDITabInfo::m\_bEnableTabSwap](../Topic/CMDITabInfo::m_bEnableTabSwap.md)|指定用户是否可以通过拖动交换选项的位置。|  
|[CMDITabInfo::m\_bFlatFrame](../Topic/CMDITabInfo::m_bFlatFrame.md)|指定选项是否具有简单的帧。|  
|[CMDITabInfo::m\_bTabCloseButton](../Topic/CMDITabInfo::m_bTabCloseButton.md)|指定每个选项卡标签是否显示 **关闭** 按钮。|  
|[CMDITabInfo::m\_bTabCustomTooltips](../Topic/CMDITabInfo::m_bTabCustomTooltips.md)|指定自定义工具提示是否启用。|  
|[CMDITabInfo::m\_bTabIcons](../Topic/CMDITabInfo::m_bTabIcons.md)|指定是否显示在MDI选项的图标。|  
|[CMDITabInfo::m\_nTabBorderSize](../Topic/CMDITabInfo::m_nTabBorderSize.md)|指定每个可选窗口的边框大小。|  
|[CMDITabInfo::m\_style](../Topic/CMDITabInfo::m_style.md)|指定选项卡标签的样式。|  
|[CMDITabInfo::m\_tabLocation](../Topic/CMDITabInfo::m_tabLocation.md)|指定选项卡标签是否位于顶部或页面底部。|  
  
## 备注  
 此选件类指定framework创建MDI选项卡组的参数。  
  
## 示例  
 下面的示例演示如何设置各种成员变量的值。`CMDITabInfo` 选件类的。  
  
 [!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/CPP/cmditabinfo-class_1.cpp)]  
  
## 继承层次结构  
 [CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)  
  
## 要求  
 **标头:** afxmdiclientareawnd.h  
  
## 请参阅  
 [CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)   
 [MDI 选项卡式组](../../mfc/mdi-tabbed-groups.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)