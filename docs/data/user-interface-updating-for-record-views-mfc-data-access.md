---
title: 记录视图的用户界面更新（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
ms.openlocfilehash: de94b28e713459edfd63aff832caecc7ea49ca33
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023355"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>记录视图的用户界面更新（MFC 数据访问）

`CRecordView` 提供了默认用户界面更新处理程序为导航命令。 这些处理程序自动启用和禁用用户界面对象 — 菜单项和工具栏按钮。 应用程序向导提供标准菜单并选择**可停靠工具栏**选项，一组工具栏按钮的命令。 如果使用 `CRecordView` 创建记录视图类，建议将类似的用户界面对象添加到应用程序。

### <a name="to-create-menu-resources-with-the-menu-editor"></a>若要使用菜单编辑器创建菜单资源

1. 有关如何使用信息引用[菜单编辑器](../windows/menu-editor.md)，使用相同的四个命令创建您自己的菜单。

#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>若要使用图形编辑器创建工具栏按钮

1. 有关如何使用信息引用[工具栏编辑器](../windows/toolbar-editor.md)，编辑工具栏资源以便为记录导航命令添加工具栏按钮。

## <a name="see-also"></a>请参阅

[支持在记录视图中导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[使用记录视图](../data/using-a-record-view-mfc-data-access.md)