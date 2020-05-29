---
title: 记录视图的用户界面更新（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
ms.openlocfilehash: 9bfb907d21c928c605b304c595acb834d0046e35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209048"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>记录视图的用户界面更新（MFC 数据访问）

`CRecordView` 提供导航命令的默认用户界面更新处理程序。 这些处理程序自动启用和禁用用户界面对象 — 菜单项和工具栏按钮。 应用程序向导提供标准菜单，如果选择 "可**停靠工具栏**" 选项，则为命令提供一组工具栏按钮。 如果使用 `CRecordView` 创建记录视图类，建议将类似的用户界面对象添加到应用程序。

### <a name="to-create-menu-resources-with-the-menu-editor"></a>若要使用菜单编辑器创建菜单资源

1. 参考有关使用[菜单编辑器](../windows/menu-editor.md)的信息，使用相同的四个命令创建自己的菜单。

#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>若要使用图形编辑器创建工具栏按钮

1. 有关使用[工具栏编辑器](../windows/toolbar-editor.md)的信息，请编辑工具栏资源，为记录导航命令添加工具栏按钮。

## <a name="see-also"></a>另请参阅

[支持在记录视图中导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[使用记录视图](../data/using-a-record-view-mfc-data-access.md)
