---
title: "容器：客户端项状态 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "客户端项和 OLE 容器"
  - "生存期, 生命周期状态和 OLE 容器客户端项"
  - "OLE 容器, 客户端项状态"
  - "states, OLE 容器客户端项"
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 容器：客户端项状态
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明客户项在其生存传递的不同状态。  
  
 在创建的，则激活，修改，并将其保存项，客户通过若干状态。  每次项的状态转换，框架调用的 `OLE_CHANGED_STATE` 通知的 [COleClientItem::OnChange](../Topic/COleClientItem::OnChange.md)。  第二个参数是从 **COleClientItem::ItemState** 枚举的值。  它可以为下列之一：  
  
-   **COleClientItem::emptyState**  
  
-   **COleClientItem::loadedState**  
  
-   **COleClientItem::openState**  
  
-   **COleClientItem::activeState**  
  
-   **COleClientItem::activeUIState**  
  
 在空状态项，客户端不完全是项。  内存为其分配，但是，它未初始化与 OLE 项的数据。  这就是客户端中的项的状态在通过指向，但尚未进行典型的两步创建的第二步的 **new** 的调用创建。  
  
 在第二个步骤中，可以通过调用 `COleClientItem::CreateFromFile` 或其他*xxxx***CreateFrom**函数，项完全创建。  OLE 数据 \(来自文件或其他源，例如剪贴板\) 与 `COleClientItem`派生的对象。  现在项在加载状态。  
  
 当项在服务器的文档容器窗口就地在中打开。而不是打开，则在打开 \(或完全打开状态\)。  在此状态中，跨阴影线通常通过绘制项的表示在容器的窗口指示项是其他地方的活动。  
  
 当项时，它激活就地，通常只简单，通过活动状态。  随后访问 UI 活动状态中，服务器将其菜单、工具栏和其他用户界面具有这些组件的容器。  这些用户界面组件出现与活动状态区分使用 UI 活动状态。  否则，活动状态类似于 UI 活动状态。  如果服务器需要服务器支持保留撤消 OLE 项的撤消状态信息，直到其达到加载或打开状态。  
  
## 请参阅  
 [容器](../mfc/containers.md)   
 [激活](../mfc/activation-cpp.md)   
 [容器：客户端项通知](../mfc/containers-client-item-notifications.md)   
 [跟踪器](../mfc/trackers.md)   
 [CRectTracker Class](../mfc/reference/crecttracker-class.md)