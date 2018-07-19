---
title: 将弹出菜单连接到你的应用程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pop-up menus, connecting to applications
- context menus, connecting to applications
- menus, pop-up
- shortcut menus, connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 533fc4eea9299d51183a91febb371ff8142e0a7b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879524"
---
# <a name="connecting-a-pop-up-menu-to-your-application"></a>将弹出菜单连接到应用程序
### <a name="to-connect-a-pop-up-menu-to-your-application"></a>将弹出菜单连接到应用程序  
  
1.  添加的消息处理程序 WM_CONTEXTMENU （例如） 所示。 有关详细信息，请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。  
  
2.  将以下代码添加到消息处理程序：  
  
    ```  
    CMenu menu;  
    VERIFY(menu.LoadMenu(IDR_MENU1));  
    CMenu* pPopup = menu.GetSubMenu(0);  
    ASSERT(pPopup != NULL);  
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());  
    ```  
  
    > [!NOTE]
    >  [CPoint](../atl-mfc-shared/reference/cpoint-class.md) **传递的消息处理程序位于屏幕坐标。**  
  

  
 **要求**  
  
 MFC  
  
## <a name="see-also"></a>请参阅  
 [创建弹出菜单](../windows/creating-pop-up-menus.md)   
 [菜单编辑器](../windows/menu-editor.md)   
