---
title: "MEASUREITEMSTRUCT 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MEASUREITEMSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MEASUREITEMSTRUCT 结构"
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# MEASUREITEMSTRUCT 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`MEASUREITEMSTRUCT` 结构通知窗口的所有者描述的控件或菜单项的大小。  
  
## 语法  
  
```  
  
      typedef struct tagMEASUREITEMSTRUCT {  
   UINT CtlType;  
   UINT CtlID;  
   UINT itemID;  
   UINT itemWidth;  
   UINT itemHeight;  
   DWORD itemData  
} MEASUREITEMSTRUCT;  
```  
  
#### 参数  
 `CtlType`  
 包含控件类型。  控件类型的值如下所示：  
  
-   所有者描述**ODT\_COMBOBOX** 组合框  
  
-   所有者描述列表框**ODT\_LISTBOX**  
  
-   所有者描述**ODT\_MENU** 菜单  
  
 `CtlID`  
 包含组合框、列表框或按钮的控件 ID。  此成员对于菜单使用。  
  
 `itemID`  
 包含菜单的项目标识或变量高度组合框或列表框的列表框项 ID。  此成员不用于固定高度的组合框或列表框，或者为按钮。  
  
 *itemWidth*  
 指定菜单项的宽度。  则从返回消息之前，所有者描述菜单项的所有者必须填充该成员。  
  
 *itemHeight*  
 在列表框或下拉菜单指定单个项的高度。  在从消息之前返回，所有者描述组合框、列表框或菜单项的所有者必须填写此成员。  列表框项的最大事高度为 255。  
  
 `itemData`  
 对于组合框或列表框，此成员包含传递到下面列表框之一：  
  
-   [CComboBox::AddString](../Topic/CComboBox::AddString.md)  
  
-   [CComboBox::InsertString](../Topic/CComboBox::InsertString.md)  
  
-   [CListBox::AddString](../Topic/CListBox::AddString.md)  
  
-   [CListBox::InsertString](../Topic/CListBox::InsertString.md)  
  
 对于菜单，该成员包含传递到菜单下列操作之一：  
  
-   [CMenu::AppendMenu](../Topic/CMenu::AppendMenu.md)  
  
-   [CMenu::InsertMenu](../Topic/CMenu::InsertMenu.md)  
  
-   [CMenu::ModifyMenu](../Topic/CMenu::ModifyMenu.md)  
  
 这允许窗口正确处理与控件的交互。  未完成 `MEASUREITEMSTRUCT` 结构的相应成员会导致控件的不正确的操作。  
  
## 要求  
 **页眉：** 指令  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnMeasureItem](../Topic/CWnd::OnMeasureItem.md)