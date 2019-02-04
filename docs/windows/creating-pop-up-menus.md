---
title: 创建弹出菜单 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
ms.openlocfilehash: cf2e3578f49cb6b4af8797052273211f699a6b4f
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702825"
---
# <a name="creating-pop-up-menus-c"></a>创建弹出菜单 （c + +）

[弹出菜单](../mfc/menus-mfc.md) 显示常用命令。 它们对指针的位置可以区分上下文。 在应用程序中使用弹出菜单需要先生成菜单，然后将菜单连接到应用程序代码。

创建菜单资源后，应用程序代码需要加载该菜单资源并使用[TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu)才会显示该菜单。 一旦用户通过选择之外，解除了弹出菜单，或选择一个命令，该函数将返回。 如果用户选择一个命令，该命令消息将被发送到传递了其句柄的窗口。

## <a name="to-create-a-pop-up-menu"></a>创建弹出菜单

1. 使用空标题（不提供[标题](../windows/creating-a-menu.md) ） **创建菜单**。

1. [将菜单命令添加到新菜单](../windows/adding-commands-to-a-menu.md)。 将移动到空白菜单标题下的第一个菜单命令 (临时标题显示`Type Here`)。 键入 **标题** 和任何其他信息。

   对弹出菜单中的任何其他菜单命令重复此过程。

1. 保存菜单资源。

## <a name="to-connect-a-pop-up-menu-to-your-application"></a>将弹出菜单连接到应用程序

1. （例如） 添加 WM_CONTEXTMENU 消息处理程序。 有关详细信息，请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。

1. 将以下代码添加到消息处理程序：

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md)传递的消息处理程序是屏幕坐标。

   > [!NOTE]
   > 弹出菜单连接到你的应用程序需要 MFC。

## <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>以弹出菜单方式查看菜单资源

通常情况下，当您在中工作**菜单**编辑器中，菜单资源显示为菜单栏。 但是，你可能拥有在程序运行时添加到应用程序菜单栏的菜单资源。

右键单击该菜单，然后选择**以弹出方式查看**从快捷菜单。

   此选项只是查看首选项，并且不会修改你的菜单。

   > [!NOTE]
   > 若要改回菜单栏视图，请单击**以弹出方式查看**再次 （它将删除复选标记，并返回菜单栏视图）。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[菜单编辑器](../windows/menu-editor.md)
