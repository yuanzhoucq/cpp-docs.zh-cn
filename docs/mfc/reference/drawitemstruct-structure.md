---
title: DRAWITEMSTRUCT 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DRAWITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DRAWITEMSTRUCT structure [MFC]
ms.assetid: ba9ef1d4-aebb-45e9-b956-4b81a02e50f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff4596a52170d0c6d197a0bda431963b5f0e9344
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120927"
---
# <a name="drawitemstruct-structure"></a>DRAWITEMSTRUCT 结构
`DRAWITEMSTRUCT` 结构提供有关所有者窗口必须确定如何绘制所有者描述的控件或菜单项的信息。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagDRAWITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    UINT itemAction;  
    UINT itemState;  
    HWND hwndItem;  
    HDC hDC;  
    RECT rcItem;  
    DWORD itemData;  
} DRAWITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>参数  
 *CtlType*  
 控件类型。 控件类型的值如下所示：  
  
- ODT_BUTTON 所有者描述的按钮  
  
- ODT_COMBOBOX 所有者描述的组合框  
  
- ODT_LISTBOX 所有者描述的列表框  
  
- ODT_MENU 所有者描述的菜单  
  
- ODT_LISTVIEW 列表视图控件  
  
- ODT_STATIC 所有者描述的静态控件  
  
- ODT_TAB 选项卡控件  
  
 *CtlID*  
 组合框、列表框或按钮的控件 ID。 此成员不适用于菜单。  
  
 *itemID*  
 菜单的菜单项 ID 或者列表框或组合框中的项的索引。 对于空列表框或组合框中，此成员是负值，它允许应用程序指定的坐标处绘制聚焦`rcItem`即使控件中没有的项的成员。 因此用户可看到列表框或组合框中是否有输入焦点。 中的位的设置`itemAction`成员确定是否要像列表框或组合框具有输入焦点绘制矩形。  
  
 *ItemAction*  
 定义所需的绘制操作。 这将是以下一个或多个位：  
  
- ODA_DRAWENTIRE 时需要绘制整个控件设置此位。  
  
- ODA_FOCUS 当控件获得或失去输入的焦点时，将设置此位。 `itemState`成员应检查以确定是否在控件有焦点。  
  
- ODA_SELECT 仅选择状态发生更改时，将设置此位。 `itemState`成员应检查以确定新的选择状态。  
  
 *ItemState*  
 当前绘图操作发生后，请指定该项的可视状态。 也就是说，如果菜单项将为灰显，状态标志 ODS_GRAYED 将设置。 新标志如下所示：  
  
- ODS_CHECKED 要检查菜单项时，将设置此位。 此位仅适用于菜单。  
  
- ODS_DISABLED 如果项是要绘制为禁用，将设置此位。  
  
- 如果项目具有输入焦点，则设置 ODS_FOCUS 此位。  
  
- ODS_GRAYED 当项将为灰显，才设置此位。 此位仅适用于菜单。  
  
- ODS_SELECTED 如果选择项的状态，将设置此位。  
  
- ODS_COMBOBOXEDIT 绘图发生在 ownerdrawn 组合框选择字段 （编辑控件）。  
  
- ODS_DEFAULT 项是默认项。  
  
 *hwndItem*  
 指定组合框、列表框和按钮的控件的窗口句柄。 指定包含项的菜单的菜单 (HMENU) 的句柄。  
  
 *hDC*  
 标识设备上下文。 在控件上执行绘制操作时，必须使用此设备上下文。  
  
 *rcItem*  
 通过指定的设备上下文中的矩形*hDC*定义要绘制的控件的边界的成员。 Windows 会自动剪裁所有者在设备上下文中绘制的关于组合框、列表框和按钮的任何内容，但它不会剪切菜单项。 当绘制菜单项，所有者必须不描述由定义的矩形边界之外`rcItem`成员。  
  
 *itemData*  
 对于组合框或列表框，此成员包含通过以下其中一项传递到列表框的值：  
  
- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)  
  
- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)  
  
- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)  
  
- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)  
  
 对于菜单，此成员包含通过以下其中一项传递到菜单的值：  
  
- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)  
  
- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)  
  
- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)  
  
## <a name="remarks"></a>备注  
 所有者描述控件或菜单项的所有者窗口接收指向此结构用作*lParam* WM_DRAWITEM 消息参数。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

