---
title: "CMFCToolBarComboBoxButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarComboBoxButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarComboBoxButton class"
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCToolBarComboBoxButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一个包含组合框控件的工具栏按钮\([CComboBox Class](../../mfc/reference/ccombobox-class.md)）。  
  
## 语法  
  
```  
class CMFCToolBarComboBoxButton : public CMFCToolBarButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](../Topic/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton.md)|构造 `CMFCToolBarComboBoxButton`。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarComboBoxButton::AddItem](../Topic/CMFCToolBarComboBoxButton::AddItem.md)|向组合框的末尾列出。|  
|[CMFCToolBarComboBoxButton::AddSortedItem](../Topic/CMFCToolBarComboBoxButton::AddSortedItem.md)|向组合框列表。  项的顺序在列表中由 `Compare`指定。|  
|[CMFCToolBarComboBoxButton::Compare](../Topic/CMFCToolBarComboBoxButton::Compare.md)|比较两个项目。  调用排序 `AddSortedItems` 添加到组合框的项列表。|  
|[CMFCToolBarComboBoxButton::CreateEdit](../Topic/CMFCToolBarComboBoxButton::CreateEdit.md)|创建新组合框按钮的编辑控件。|  
|[CMFCToolBarComboBoxButton::DeleteItem](../Topic/CMFCToolBarComboBoxButton::DeleteItem.md)|从组合框中删除项列表。|  
|[CMFCToolBarComboBoxButton::FindItem](../Topic/CMFCToolBarComboBoxButton::FindItem.md)|返回包含指定字符串项的索引。|  
|[CMFCToolBarComboBoxButton::GetByCmd](../Topic/CMFCToolBarComboBoxButton::GetByCmd.md)|返回指向具有指定的命令ID.的组合框按钮|  
|[CMFCToolBarComboBoxButton::GetComboBox](../Topic/CMFCToolBarComboBoxButton::GetComboBox.md)|返回指向在组合框按钮嵌入的组合框控件。|  
|[CMFCToolBarComboBoxButton::GetCount](../Topic/CMFCToolBarComboBoxButton::GetCount.md)|返回的项数。组合框的列表。|  
|[CMFCToolBarComboBoxButton::GetCountAll](../Topic/CMFCToolBarComboBoxButton::GetCountAll.md)|查找具有指定的命令ID.的组合框按钮  返回的项数。组合框中显示该按钮。|  
|[CMFCToolBarComboBoxButton::GetCurSel](../Topic/CMFCToolBarComboBoxButton::GetCurSel.md)|返回选定项的索引在组合框的列表。|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](../Topic/CMFCToolBarComboBoxButton::GetCurSelAll.md)|查找具有指定的命令ID的组合框按钮，并返回选定项的索引在组合框中显示该按钮。|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](../Topic/CMFCToolBarComboBoxButton::GetEditCtrl.md)|返回指向在组合框按钮嵌入的编辑控件。|  
|[CMFCToolBarComboBoxButton::GetItem](../Topic/CMFCToolBarComboBoxButton::GetItem.md)|返回与在组合框中指定的索引列表的字符串。|  
|[CMFCToolBarComboBoxButton::GetItemAll](../Topic/CMFCToolBarComboBoxButton::GetItemAll.md)|查找具有指定的命令ID的组合框按钮，并返回与组合框的索引列表该按钮的字符串。|  
|[CMFCToolBarComboBoxButton::GetItemData](../Topic/CMFCToolBarComboBoxButton::GetItemData.md)|返回与在组合框中指定的索引列表的32位值。|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](../Topic/CMFCToolBarComboBoxButton::GetItemDataAll.md)|查找具有指定的命令ID的组合框按钮，并返回与组合框的索引列表该按钮的32位值。|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](../Topic/CMFCToolBarComboBoxButton::GetItemDataPtrAll.md)|查找具有指定的命令ID.的组合框按钮  检索关联在组合框的索引列表该按钮，并返回该32位值为指针的32位值。|  
|[CMFCToolBarComboBoxButton::GetText](../Topic/CMFCToolBarComboBoxButton::GetText.md)|返回从组合框中编辑控件的文本。|  
|[CMFCToolBarComboBoxButton::GetTextAll](../Topic/CMFCToolBarComboBoxButton::GetTextAll.md)|查找具有指定的命令ID的组合框按钮，并返回文本从该按钮编辑控件。|  
|[CMFCToolBarComboBoxButton::IsCenterVert](../Topic/CMFCToolBarComboBoxButton::IsCenterVert.md)|识别应用程序中的组合框按钮是否居中对齐或工具栏的顶部。|  
|[CMFCToolBarComboBoxButton::IsFlatMode](../Topic/CMFCToolBarComboBoxButton::IsFlatMode.md)|识别应用程序中的组合框按钮是否具有简单的外观。|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](../Topic/CMFCToolBarComboBoxButton::RemoveAllItems.md)|从列表框中移除所有项和组合框的编辑控件。|  
|[CMFCToolBarComboBoxButton::SelectItem](../Topic/CMFCToolBarComboBoxButton::SelectItem.md)|根据索引、32位值或字符串组合框中选择一个项目中，并通知选定内容的组合框控件。|  
|[CMFCToolBarComboBoxButton::SelectItemAll](../Topic/CMFCToolBarComboBoxButton::SelectItemAll.md)|查找具有指定的命令ID.的组合框按钮  调用 `SelectItem` 根据字符串、索引或32位值组合框中选择一个项目该按钮。|  
|[CMFCToolBarComboBoxButton::SetCenterVert](../Topic/CMFCToolBarComboBoxButton::SetCenterVert.md)|指定在应用程序的组合框按钮是垂直中居中对齐或工具栏的顶部。|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](../Topic/CMFCToolBarComboBoxButton::SetDropDownHeight.md)|设置高度下拉式列表框。|  
|[CMFCToolBarComboBoxButton::SetFlatMode](../Topic/CMFCToolBarComboBoxButton::SetFlatMode.md)|指定在应用程序的组合框按钮是否具有简单的外观。|  
  
## 备注  
 若要将某个组合框按钮添加到工具栏，请执行以下步骤:  
  
 1.  保留虚拟资源ID在父工具栏资源的按钮。  
  
 2.  构造 `CMFCToolBarComboBoxButton` 对象。  
  
 3.  使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)，在处理 `AFX_WM_RESETTOOLBAR` 消息的消息处理程序，请在新的组合框按钮替换虚假的按钮。  
  
 有关更多信息，请参见 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  有关组合框工具栏按钮的示例，请参见示例项目VisualStudioDemo。  
  
## 示例  
 下面的示例在 `CMFCToolBarComboBoxButton` 选件类演示如何使用各种方法。  此示例演示如何启用编辑和组合框，设置组合框按钮的垂直位置在应用程序中，将列表框的高度，则放置处于按下状态时，设置组合框按钮的平面样式外观在应用程序，并在组合框按钮的编辑框的文本。  此代码段是 [Visual Studio演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/CPP/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/CPP/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## 要求  
 **标头:** afxtoolbarcomboboxbutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)