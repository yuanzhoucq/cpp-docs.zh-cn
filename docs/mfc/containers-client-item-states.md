---
title: 容器： 客户端项状态 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5046ea7f3f3775cfe0009afe50f33a6ce6723cc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="containers-client-item-states"></a>容器：客户端项状态
此文章介绍了在其生存期内，通过传递客户端项的不同状态。  
  
 客户端项经过若干种状态，因为它是创建、 激活、 修改和保存。 每次项的状态发生更改，框架调用[COleClientItem::OnChange](../mfc/reference/coleclientitem-class.md#onchange)与`OLE_CHANGED_STATE`通知。 第二个参数是一个介于**COleClientItem::ItemState**枚举。 它可以是以下项之一：  
  
-   **COleClientItem::emptyState**  
  
-   **COleClientItem::loadedState**  
  
-   **COleClientItem::openState**  
  
-   **COleClientItem::activeState**  
  
-   **COleClientItem::activeUIState**  
  
 在空状态下，客户端项尚不完全项。 内存已分配，但它尚未已初始化 OLE 项的数据。 这是通过调用创建完毕后，客户端项处于的状态**新**但未经过通常分两步创建的第二步。  
  
 在第二个步骤中，通过调用执行`COleClientItem::CreateFromFile`或另一个 **CreateFrom * * * xxxx*函数，完全创建相应的项。 OLE 数据 （从文件或某些其他源，如剪贴板） 与`COleClientItem`-派生对象。 现在项处于加载状态。  
  
 当项具有已在服务器的窗口中打开而不是在容器的文档中的位置中打开时，它会处于打开 （或完全打开） 状态。 在此状态下，跨阴影通常绘制的表示形式来指明，在其他位置的项处于活动状态的容器的窗口中的项上。  
  
 当已就地激活项时，它将传递，通常仅简要，通过活动状态。 然后，它将输入 UI 活动状态，其菜单、 工具栏和与容器的其他用户界面组件，服务器已合并。 这些用户界面组件的状态区分 UI 活动状态从活动状态。 否则，活动状态类似于 UI 活动状态。 如果服务器支持撤消，则需要服务器来保留 OLE 项的撤消状态信息，直到它达到加载或打开状态。  
  
## <a name="see-also"></a>请参阅  
 [容器](../mfc/containers.md)   
 [激活](../mfc/activation-cpp.md)   
 [容器： 客户端项通知](../mfc/containers-client-item-notifications.md)   
 [跟踪器](../mfc/trackers.md)   
 [CRectTracker 类](../mfc/reference/crecttracker-class.md)
