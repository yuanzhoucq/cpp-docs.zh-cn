---
title: "CMFCToolBarDateTimeCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "OnDrawOnCustomizeList"
  - "CMFCToolBarDateTimeCtrl::OnDraw"
  - "OnDraw"
  - "CMFCToolBarDateTimeCtrl.Serialize"
  - "CMFCToolBarDateTimeCtrl.OnSize"
  - "CMFCToolBarDateTimeCtrl.OnDrawOnCustomizeList"
  - "OnSize"
  - "OnCalculateSize"
  - "CMFCToolBarDateTimeCtrl"
  - "CMFCToolBarDateTimeCtrl::OnCalculateSize"
  - "SetStyle"
  - "CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList"
  - "CMFCToolBarDateTimeCtrl.OnDraw"
  - "CMFCToolBarDateTimeCtrl.SetStyle"
  - "CMFCToolBarDateTimeCtrl::SetStyle"
  - "CMFCToolBarDateTimeCtrl.OnCalculateSize"
  - "CMFCToolBarDateTimeCtrl::Serialize"
  - "CMFCToolBarDateTimeCtrl::OnSize"
  - "Serialize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarDateTimeCtrl class"
  - "OnCalculateSize method"
  - "OnDraw method"
  - "OnDrawOnCustomizeList method"
  - "OnSize method"
  - "Serialize method"
  - "SetStyle method"
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCToolBarDateTimeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一个包含日期和时间选择器控件的工具栏按钮。  
  
## 语法  
  
```  
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](../Topic/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl.md)|构造 `CMFCToolBarDateTimeCtrl` 对象。|  
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarDateTimeCtrl::CanBeStretched](../Topic/CMFCToolBarDateTimeCtrl::CanBeStretched.md)|指定用户是否在自定义过程中拉伸按钮。  （重写 [CMFCToolBarButton::CanBeStretched](../Topic/CMFCToolBarButton::CanBeStretched.md)。）|  
|[CMFCToolBarDateTimeCtrl::CopyFrom](../Topic/CMFCToolBarDateTimeCtrl::CopyFrom.md)|复制另一个工具栏按钮的属性设置为当前按钮。  （重写 [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md)。）|  
|`CMFCToolBarDateTimeCtrl::DuplicateData`|保留供将来使用。|  
|[CMFCToolBarButton::ExportToMenuButton](../Topic/CMFCToolBarButton::ExportToMenuButton.md)|复制从工具栏按钮文本添加到菜单。|  
|`CMFCToolBarDateTimeCtrl::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CMFCToolBarDateTimeCtrl::GetByCmd](../Topic/CMFCToolBarDateTimeCtrl::GetByCmd.md)|检索在具有指定的命令ID.的应用程序的第一 `CMFCToolBarDateTimeCtrl` 对象|  
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](../Topic/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl.md)|返回指向日期和时间选择器控件。|  
|[CMFCToolBarDateTimeCtrl::GetHwnd](../Topic/CMFCToolBarDateTimeCtrl::GetHwnd.md)|检索与工具栏按钮的窗口句柄。  （重写 [CMFCToolBarButton::GetHwnd](../Topic/CMFCToolBarButton::GetHwnd.md)。）|  
|`CMFCToolBarDateTimeCtrl::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCToolBarDateTimeCtrl::GetTime](../Topic/CMFCToolBarDateTimeCtrl::GetTime.md)|从日期和时间选择器控件在指定的 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) 结构获取选定的时间并将其放在|  
|[CMFCToolBarDateTimeCtrl::GetTimeAll](../Topic/CMFCToolBarDateTimeCtrl::GetTimeAll.md)|返回从具有指定的命令ID.的时间选择器控件按钮的所选时间|  
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](../Topic/CMFCToolBarDateTimeCtrl::HaveHotBorder.md)|确定按钮的边框是否显示，当用户选择按钮。  （重写 [CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md)。）|  
|[CMFCToolBarDateTimeCtrl::NotifyCommand](../Topic/CMFCToolBarDateTimeCtrl::NotifyCommand.md)|指定按钮是否处理 [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) 消息。  （重写 [CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md)。）|  
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](../Topic/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage.md)|调用由结构，当按钮添加到 **自定义** 对话框。  （重写 [CMFCToolBarButton::OnAddToCustomizePage](../Topic/CMFCToolBarButton::OnAddToCustomizePage.md)。）|  
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|调用由结构计算该按钮的大小指定的设备上下文和停靠状态的。  （重写 [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md)。）|  
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](../Topic/CMFCToolBarDateTimeCtrl::OnChangeParentWnd.md)|调用由结构，当按钮插入新工具栏。  （重写 [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md)。）|  
|[CMFCToolBarDateTimeCtrl::OnClick](../Topic/CMFCToolBarDateTimeCtrl::OnClick.md)|调用由结构，当用户单击控件。  （重写 [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)。）|  
|[CMFCToolBarDateTimeCtrl::OnCtlColor](../Topic/CMFCToolBarDateTimeCtrl::OnCtlColor.md)|调用由结构，当父工具栏处理 `WM_CTLCOLOR` 消息。  （重写 [CMFCToolBarButton::OnCtlColor](../Topic/CMFCToolBarButton::OnCtlColor.md)。）|  
|`CMFCToolBarDateTimeCtrl::OnDraw`|使用指定的样式和选项，调用由框架绘制按钮。  （重写 [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md)。）|  
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|调用由框架绘制在 **自定义** 对话框的 **命令** 窗格的按钮。  （重写 [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md)。）|  
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](../Topic/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged.md)|调用由框架，如果全局字体已更改。  （重写 [CMFCToolBarButton::OnGlobalFontsChanged](../Topic/CMFCToolBarButton::OnGlobalFontsChanged.md)。）|  
|[CMFCToolBarDateTimeCtrl::OnMove](../Topic/CMFCToolBarDateTimeCtrl::OnMove.md)|调用由结构，当父工具栏移动。  （重写 [CMFCToolBarButton::OnMove](../Topic/CMFCToolBarButton::OnMove.md)。）|  
|[CMFCToolBarDateTimeCtrl::OnShow](../Topic/CMFCToolBarDateTimeCtrl::OnShow.md)|调用由结构，当按钮变为可见或不可见。  （重写 [CMFCToolBarButton::OnShow](../Topic/CMFCToolBarButton::OnShow.md)。）|  
|`CMFCToolBarDateTimeCtrl::OnSize`|调用由结构，当父工具栏更改更改的按钮调整其大小或位置和此更改原因。  （重写 [CMFCToolBarButton::OnSize](../Topic/CMFCToolBarButton::OnSize.md)。）|  
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](../Topic/CMFCToolBarDateTimeCtrl::OnUpdateToolTip.md)|调用由结构，当父工具栏更新其工具提示文本。  （重写 [CMFCToolBarButton::OnUpdateToolTip](../Topic/CMFCToolBarButton::OnUpdateToolTip.md)。）|  
|`CMFCToolBarDateTimeCtrl::Serialize`|读取存档或写入的此对象到存档，\(重写 [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md)。）|  
|`CMFCToolBarDateTimeCtrl::SetStyle`|设置工具栏按钮的样式。  （重写 [CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md)。）|  
|[CMFCToolBarDateTimeCtrl::SetTime](../Topic/CMFCToolBarDateTimeCtrl::SetTime.md)|设置时间和日期时间选择器控件。|  
|[CMFCToolBarDateTimeCtrl::SetTimeAll](../Topic/CMFCToolBarDateTimeCtrl::SetTimeAll.md)|设置时间和日期在具有指定的命令ID.时间选择器控件的所有实例|  
  
## 备注  
 有关如何使用日期和时间选择器控件，请参见ToolbarDateTimePicker示例项目。  有关如何将控件添加到工具栏按钮的信息，请参见 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)  
  
## 要求  
 **标头:** afxtoolbardatetimectrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)