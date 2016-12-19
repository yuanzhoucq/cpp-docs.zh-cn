---
title: "CMFCRibbonComboBox Class | Microsoft Docs"
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
  - "CMFCRibbonComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonComboBox class"
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
caps.latest.revision: 35
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonComboBox` 选件类实现可以添加到功能区栏、一个或功能区弹出菜单的组合框控件。  
  
## 语法  
  
```  
class CMFCRibbonComboBox : public CMFCRibbonEdit  
```  
  
## 成员  
  
### 构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonComboBox::CMFCRibbonComboBox](../Topic/CMFCRibbonComboBox::CMFCRibbonComboBox.md)|构造CMFCRibbonComboBox对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonComboBox::AddItem](../Topic/CMFCRibbonComboBox::AddItem.md)|追加一个项添加到列表框。|  
|[CMFCRibbonComboBox::DeleteItem](../Topic/CMFCRibbonComboBox::DeleteItem.md)|从列表框删除指定的项目。|  
|[CMFCRibbonComboBox::EnableDropDownListResize](../Topic/CMFCRibbonComboBox::EnableDropDownListResize.md)|指定列表框是否可以更改大小，则下拉。|  
|[CMFCRibbonComboBox::FindItem](../Topic/CMFCRibbonComboBox::FindItem.md)|返回第一项的索引在与指定字符串匹配的列表框中。|  
|[CMFCRibbonComboBox::GetCount](../Topic/CMFCRibbonComboBox::GetCount.md)|返回项的数目在列表框中。|  
|[CMFCRibbonComboBox::GetCurSel](../Topic/CMFCRibbonComboBox::GetCurSel.md)|获取当前选定项的索引在列表框中。|  
|[CMFCRibbonComboBox::GetDropDownHeight](../Topic/CMFCRibbonComboBox::GetDropDownHeight.md)|在列表框中删除处于按下状态时，获取列表框的高度。|  
|[CMFCRibbonComboBox::GetIntermediateSize](../Topic/CMFCRibbonComboBox::GetIntermediateSize.md)|返回组合框的大小显示在中间模式。|  
|[CMFCRibbonComboBox::GetItem](../Topic/CMFCRibbonComboBox::GetItem.md)|返回字符串与项目在列表框中指定的索引。|  
|[CMFCRibbonComboBox::GetItemData](../Topic/CMFCRibbonComboBox::GetItemData.md)|返回数据与项目在列表框中指定的索引。|  
|[CMFCRibbonComboBox::HasEditBox](../Topic/CMFCRibbonComboBox::HasEditBox.md)|指示控件是否包含一个编辑框。|  
|[CMFCRibbonComboBox::IsResizeDropDownList](../Topic/CMFCRibbonComboBox::IsResizeDropDownList.md)|指示列表框是否可调整大小。|  
|[CMFCRibbonComboBox::OnSelectItem](../Topic/CMFCRibbonComboBox::OnSelectItem.md)|调用由结构，当用户在列表框中选择一个项目。|  
|[CMFCRibbonComboBox::RemoveAllItems](../Topic/CMFCRibbonComboBox::RemoveAllItems.md)|从列表框删除所有项并清除编辑框。|  
|[CMFCRibbonComboBox::SelectItem](../Topic/CMFCRibbonComboBox::SelectItem.md)|在列表框中选择一个项目。|  
|[CMFCRibbonComboBox::SetDropDownHeight](../Topic/CMFCRibbonComboBox::SetDropDownHeight.md)|它放置处于按下状态时，将列表框的高度。|  
  
## 备注  
 功能区组合框包含列表框以及可由用户编辑的静态标签或标签。  您必须指定哪个类型需要，当您创建功能区组合框时。  
  
## 示例  
 下面的示例演示如何构造对象 `CMFCRibbonComboBox` 选件类，将项添加到组合框中，组合框中选择一个项目并添加一个组合框添加到面板。  
  
 [!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/CPP/cmfcribboncombobox-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
## 要求  
 **标头:** afxribboncombobox.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonEdit Class](../../mfc/reference/cmfcribbonedit-class.md)