---
title: "组合框样式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBS_LOWERCASE
- CBS_SORT
- CBS_OWNERDRAWVARIABLE
- CBS_OEMCONVERT
- CBS_AUTOHSCROLL
- CBS_NOINTEGRALHEIGHT
- CBS_SIMPLE
- CBS_DROPDOWNLIST
- CBS_DROPDOWN
- CBS_UPPERCASE
- CBS_HASSTRINGS
- CBS_DISABLENOSCROLL
- CBS_OWNERDRAWFIXED
dev_langs:
- C++
helpviewer_keywords:
- CBS_OWNERDRAWVARIABLE constant [MFC]
- CBS_NOINTEGRALHEIGHT constant [MFC]
- CBS_SIMPLE constant [MFC]
- CBS_AUTOHSCROLL constant [MFC]
- CBS_OEMCONVERT constant [MFC]
- CBS_DISABLENOSCROLL constant [MFC]
- CBS_HASSTRINGS constant [MFC]
- CBS_LOWERCASE constant [MFC]
- CBS_SORT constant [MFC]
- CBS_DROPDOWN constant [MFC]
- CBS_OWNERDRAWFIXED constant [MFC]
- combo boxes [MFC], styles
- CBS_UPPERCASE constant [MFC]
- CBS_DROPDOWNLIST constant
ms.assetid: d21a5023-e6a2-495b-a6bd-010a515cbc63
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 52cfd21df2f0f72da10589745fb3a8be3e0b24e1
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="combo-box-styles"></a>组合框样式
以下组合框样式在 MFC 中可用。  
  
-   **CBS_AUTOHSCROLL** 当用户在行尾键入字符时，使编辑控件中的文本自动滚动到右侧。 如果未设置此样式，则仅允许矩形边界内的文本。  
  
-   **CBS_DISABLENOSCROLL** 当列表框未包含足够的项而不需要滚动时，将显示一个禁用的垂直滚动条。 如果不使用此样式，则当列表框未包含足够的项时，将会隐藏滚动条。  
  
-   **CBS_DROPDOWN** 类似于 **CBS_SIMPLE**，只不过只有当用户选择编辑控件旁的图标时，才会显示该列表框。  
  
-   **CBS_DROPDOWNLIST** 类似于 **CBS_DROPDOWN**，只不过编辑控件被替换为一个在列表框中显示当前选择的静态文本项。  
  
-   **CBS_HASSTRINGS** 所有者描述的组合框包含由字符串组成的项。 组合框维护字符串的内存和指针，以便应用程序可使用 `GetText` 成员函数检索特定项的文本。  
  
-   **CBS_LOWERCASE** 将选择字段和列表中的所有文本转换为小写。  
  
-   **CBS_NOINTEGRALHEIGHT** 指定组合框的大小正是应用程序创建此组合框时指定的大小。 通常，Windows 会调整组合框的大小，以使组合框不会仅显示部分项。  
  
-   **CBS_OEMCONVERT** 在组合框编辑控件中输入的文本将从 ANSI 字符集转换为 OEM 字符集，然后重新转换为 ANSI。 这可确保当应用程序调用 `AnsiToOem` Windows 函数将组合框中的 ANSI 字符串转换为 OEM 字符时，能正确进行字符转换。 此样式最适用于包含文件名的组合框，且仅适用于使用 **CBS_SIMPLE** 或 **CBS_DROPDOWN** 样式创建的组合框。  
  
-   **CBS_OWNERDRAWFIXED** 列表框的所有者负责绘制其内容；列表框中的项的高度相同。  
  
-   **CBS_OWNERDRAWVARIABLE** 列表框的所有者负责绘制其内容；列表框中的项的高度不同。  
  
-   **CBS_SIMPLE** 始终显示列表框。 列表框中的当前选择显示在编辑控件中。  
  
-   **CBS_SORT** 对输入到列表框的字符串进行自动排序。  
  
-   **CBS_UPPERCASE** 将选择字段和列表中的所有文本转换为大写。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CComboBox::Create](ccombobox class.md # ccombobox__create   




