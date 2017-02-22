---
title: "CBaseTabbedPane 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBaseTabbedPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBaseTabbedPane 类"
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CBaseTabbedPane 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

扩展 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 的功能支持选项卡式窗口中创建。  
  
## 语法  
  
```  
class CBaseTabbedPane : public CDockablePane  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|`CBaseTabbedPane::CBaseTabbedPane`|默认构造函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CBaseTabbedPane::AddTab](../Topic/CBaseTabbedPane::AddTab.md)|添加新的选项卡到一个选项卡式窗格。|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../Topic/CBaseTabbedPane::AllowDestroyEmptyTabbedPane.md)|指定是否可以销毁一个空选项卡式窗格。|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](../Topic/CBaseTabbedPane::ApplyRestoredTabInfo.md)|适用于制表符设置，从该注册表加载，一个选项卡式窗格。|  
|[CBaseTabbedPane::CanFloat](../Topic/CBaseTabbedPane::CanFloat.md)|确定窗格是否可以浮动。  \(重写 [CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md)。\)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](../Topic/CBaseTabbedPane::CanSetCaptionTextToTabName.md)|确定选项卡式窗格中声明是否应显示文本的并且有效选项相同。|  
|[CBaseTabbedPane::ConvertToTabbedDocument](../Topic/CBaseTabbedPane::ConvertToTabbedDocument.md)|\(重写 [CDockablePane::ConvertToTabbedDocument](../Topic/CDockablePane::ConvertToTabbedDocument.md)。\)|  
|[CBaseTabbedPane::DetachPane](../Topic/CBaseTabbedPane::DetachPane.md)|将一个或多个停靠窗格为选项卡式 MDI 文档。|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](../Topic/CBaseTabbedPane::EnableSetCaptionTextToTabName.md)|启用或禁用选项卡式窗格中提供了在活动选项卡上的标签文本同步标题文本。|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](../Topic/CBaseTabbedPane::FillDefaultTabsOrderArray.md)|还原内部 tab 键顺序为默认状态。|  
|[CBaseTabbedPane::FindBarByTabNumber](../Topic/CBaseTabbedPane::FindBarByTabNumber.md)|返回位于选项的窗格，如果选项卡由从零开始的索引选项时确定的。|  
|||  
|[CBaseTabbedPane::FindPaneByID](../Topic/CBaseTabbedPane::FindPaneByID.md)|返回由窗格 ID. 确定的窗格|  
|[CBaseTabbedPane::FloatTab](../Topic/CBaseTabbedPane::FloatTab.md)|只有 \+ 当窗格当前位于一个可拆的选项，浮动窗格中，但。|  
|[CBaseTabbedPane::GetDefaultTabsOrder](../Topic/CBaseTabbedPane::GetDefaultTabsOrder.md)|返回选项默认值顺序在窗格中。|  
|[CBaseTabbedPane::GetFirstVisibleTab](../Topic/CBaseTabbedPane::GetFirstVisibleTab.md)|检索指向第一个突出显示的选项。|  
|[CBaseTabbedPane::GetMinSize](../Topic/CBaseTabbedPane::GetMinSize.md)|检索窗格的最小值允许的范围。  \(重写 [CPane::GetMinSize](../Topic/CPane::GetMinSize.md)。\)|  
|[CBaseTabbedPane::GetPaneIcon](../Topic/CBaseTabbedPane::GetPaneIcon.md)|返回的句柄窗格图标。  \(重写 [CBasePane::GetPaneIcon](../Topic/CBasePane::GetPaneIcon.md)。\)|  
|[CBaseTabbedPane::GetPaneList](../Topic/CBaseTabbedPane::GetPaneList.md)|返回在选项卡式窗格包含窗格的列表。|  
|[CBaseTabbedPane::GetTabArea](../Topic/CBaseTabbedPane::GetTabArea.md)|返回顶部和底部选项区域的边框。|  
|[CBaseTabbedPane::GetTabsNum](../Topic/CBaseTabbedPane::GetTabsNum.md)|返回计数。可选窗口的选项卡。|  
|[CBaseTabbedPane::GetUnderlyingWindow](../Topic/CBaseTabbedPane::GetUnderlyingWindow.md)|获取基础 \(包装\) 选项窗口。|  
|[CBaseTabbedPane::GetVisibleTabsNum](../Topic/CBaseTabbedPane::GetVisibleTabsNum.md)|返回计数将显示选项。|  
|[CBaseTabbedPane::HasAutoHideMode](../Topic/CBaseTabbedPane::HasAutoHideMode.md)|确定选项卡式窗格是否可以切换到自动隐藏模式。|  
|[CBaseTabbedPane::IsHideSingleTab](../Topic/CBaseTabbedPane::IsHideSingleTab.md)|确定选项卡式窗格是否为隐藏的，如果只有一个将显示选项卡。|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|使用在内部在序列化时。|  
|[CBaseTabbedPane::RecalcLayout](../Topic/CBaseTabbedPane::RecalcLayout.md)|计算窗格的格式信息。  \(重写 [CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md)。\)|  
|[CBaseTabbedPane::RemovePane](../Topic/CBaseTabbedPane::RemovePane.md)|从选项卡式窗格中移除窗格。|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|使用在内部在序列化时。|  
|`CBaseTabbedPane::Serialize`|\(重写 [CDockablePane::Serialize](http://msdn.microsoft.com/zh-cn/09787e59-e446-4e76-894b-206d303dcfd6)。\)|  
|`CBaseTabbedPane::SerializeTabWindow`|使用在内部在序列化时。|  
|[CBaseTabbedPane::SetAutoDestroy](../Topic/CBaseTabbedPane::SetAutoDestroy.md)|确定是否将自动销毁选项卡式控制条。|  
|[CBaseTabbedPane::SetAutoHideMode](../Topic/CBaseTabbedPane::SetAutoHideMode.md)|切换显示在中的和自动隐藏模式之间的停靠窗格。  \(重写 [CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md)。\)|  
|[CBaseTabbedPane::ShowTab](../Topic/CBaseTabbedPane::ShowTab.md)|显示或隐藏选项。|  
  
## 备注  
 此选件类是一个抽象类，且无法实例化。  它实现到所有类型的选项卡式窗格共有的服务。  
  
 目前，库包括两派生的选项卡式窗格选件类：[CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md) 和 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 `CBaseTabbedPane` 对象包装的指针 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md) 对象。  [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md) 然后变为选项卡式窗格的子窗口。  
  
 有关如何创建选项卡式窗格的更多信息，请参见 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)、[CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md)和 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
## 要求  
 **标头：** afxBaseTabbedPane.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)