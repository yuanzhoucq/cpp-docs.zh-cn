---
title: 记录视图 （MFC 数据访问） 的用户界面更新 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1227ba1fe0a14af7013109b336d1d60eda41137e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105811"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>记录视图的用户界面更新（MFC 数据访问）
`CRecordView` 提供了默认用户界面更新处理程序为导航命令。 这些处理程序自动启用和禁用用户界面对象 — 菜单项和工具栏按钮。 应用程序向导提供标准菜单并且，如果你选择**可停靠工具栏**选项，一组的所有命令的工具栏按钮。 如果使用 `CRecordView` 创建记录视图类，建议将类似的用户界面对象添加到应用程序。  
  
### <a name="to-create-menu-resources-with-the-menu-editor"></a>若要使用菜单编辑器创建菜单资源  
  
1.  有关使用的信息引用[菜单编辑器](../windows/menu-editor.md)，使用相同的四个命令创建您自己的菜单。  
  
#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>若要使用图形编辑器创建工具栏按钮  
  
1.  有关使用的信息引用[工具栏编辑器](../windows/toolbar-editor.md)，编辑工具栏资源以便为记录导航命令添加工具栏按钮。  
  
## <a name="see-also"></a>请参阅  
 [支持在记录视图中导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)   
 [使用记录视图](../data/using-a-record-view-mfc-data-access.md)