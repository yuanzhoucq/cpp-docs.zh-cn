---
title: MEASUREITEMSTRUCT 结构
ms.date: 11/04/2016
f1_keywords:
- MEASUREITEMSTRUCT
helpviewer_keywords:
- MEASUREITEMSTRUCT structure [MFC]
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
ms.openlocfilehash: 3f541c30c484041d855807f220345d6863a780d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575030"
---
# <a name="measureitemstruct-structure"></a>MEASUREITEMSTRUCT 结构

`MEASUREITEMSTRUCT`结构通知 Windows 所有者描述的控件或菜单项的维数。

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

*CtlType*<br/>
包含控件类型。 控件类型的值如下所示：

- ODT_COMBOBOX 所有者描述的组合框

- ODT_LISTBOX 所有者描述列表框

- ODT_MENU 所有者描述菜单

*CtlID*<br/>
包含为组合框、 列表框或按钮的控件 ID。 此成员不适用于菜单。

*itemID*<br/>
包含一个菜单的菜单项 ID 或者用于高度可变的组合框或列表框的列表框项 ID。 此成员不用于固定高度组合框或列表框或按钮。

*itemWidth*<br/>
指定菜单项的宽度。 在消息中返回之前，所有者描述菜单项的所有者必须填写此成员。

*itemHeight*<br/>
指定列表框或菜单中的单个项的高度。 它将返回消息的所有者描述组合框中，所有者之前则列表框或菜单项必须填写此成员。 在列表框项的最大高度为 255。

*itemData*<br/>
对于组合框或列表框，此成员包含通过以下其中一项传递到列表框的值：

- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)

- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)

- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)

- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)

对于菜单，此成员包含通过以下其中一项传递到菜单的值：

- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)

- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)

- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)

这样，Windows，以便正确处理用户与控件交互。 无法填充中的适当成员`MEASUREITEMSTRUCT`结构将导致该控件的不正确的操作。

## <a name="requirements"></a>要求

**标头：** winuser.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)

