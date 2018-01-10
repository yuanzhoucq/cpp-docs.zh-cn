---
title: "MEASUREITEMSTRUCT 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MEASUREITEMSTRUCT
dev_langs: C++
helpviewer_keywords: MEASUREITEMSTRUCT structure [MFC]
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ce5221943ba1591a01ddebe2c261e4197fa18501
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="measureitemstruct-structure"></a>MEASUREITEMSTRUCT 结构
`MEASUREITEMSTRUCT`结构通知 Windows 所有者绘制的控件或菜单项的维数。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `CtlType`  
 包含控件类型。 控件类型的值如下所示：  
  
- **ODT_COMBOBOX**所有者描述组合框  
  
- **ODT_LISTBOX**所有者描述列表框  
  
- **ODT_MENU**所有者描述菜单  
  
 `CtlID`  
 包含组合框、 列表框中或按钮的控件的 ID。 此成员不适用于菜单。  
  
 `itemID`  
 包含一个菜单的菜单项 ID 或高度可变的组合框或列表框的列表框项 ID。 此成员不用于高度固定的组合框或列表框中，或一个按钮。  
  
 *itemWidth*  
 指定菜单项的宽度。 返回从消息之前，所有者绘制菜单项的所有者必须填写此成员。  
  
 *itemHeight*  
 指定列表框或菜单中的单个项的高度。 它返回的消息，所有者描述组合框的所有者中之前则列表框或菜单项必须填写此成员。 列表框项的最大高度为 255。  
  
 `itemData`  
 对于组合框或列表框，此成员包含通过以下其中一项传递到列表框的值：  
  
- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)  
  
- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)  
  
- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)  
  
- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)  
  
 对于菜单，此成员包含通过以下其中一项传递到菜单的值：  
  
- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)  
  
- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)  
  
- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)  
  
 这允许 Windows 正确地处理用户与控件交互。 未能填写中的正确成员`MEASUREITEMSTRUCT`结构将导致不正确的操作的控件。  
  
## <a name="requirements"></a>惠?  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)

