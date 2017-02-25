---
title: "容器：客户端项通知 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "通知, 容器客户端项"
  - "OLE 容器, 客户端项通知"
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 容器：客户端项通知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文讨论 MFC 框架调用的可重写的函数在服务器应用修改在客户端应用程序中的文档项时。  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md) 定义调用响应从组件应用程序的请求，也称为服务器应用程序的若干可重写的函数。  这些 overridables 通常用作通知。  他们通知容器应用程序各种事件，如滚动、激活或位置的更改，该，而更改用户进行，在编辑操作或项。  
  
 框架通过调用 `COleClientItem::OnChange`，需要实现的可重写的函数通知更改容器应用程序。  此保护的函数接收两个参数。  第一指定服务器更改项的原因：  
  
|通知|含义|  
|--------|--------|  
|`OLE_CHANGED`|OLE 项的外观将随之更改。|  
|`OLE_SAVED`|OLE 项保存。|  
|`OLE_CLOSED`|OLE 项关闭。|  
|**OLE\_RENAMED**|包含 OLE 项的服务器文档已重命名。|  
|`OLE_CHANGED_STATE`|OLE 项从一个状态更改为另一个架构。|  
|**OLE\_CHANGED\_ASPECT**|OLE 项的绘制特性由框架更改。|  
  
 这些值是从 **OLE\_NOTIFICATION** 枚举，在 AFXOLE.H. 定义。  
  
 对此函数的第二个参数指定这些项以及如何更改其状态。已输入：  
  
|当第一个参数为|第二个参数|  
|-------------|-----------|  
|`OLE_SAVED` 或 `OLE_CLOSED`|没有使用。|  
|`OLE_CHANGED`|指定将 OLE 项的特性。|  
|`OLE_CHANGED_STATE`|介绍状态进入 \(`emptyState`、**loadedState**、`openState`、`activeState`或 `activeUIState`\)。|  
  
 有关客户项可以采用的状态的更多信息，请参见 [容器：客户端状态项](../mfc/containers-client-item-states.md)。  
  
 当项为就地激活编辑时，框架调用 `COleClientItem::OnGetItemPosition`。  为就地编辑实现支持的应用程序是必需的。  MFC 应用程序向导提供的基本实现，分配项的坐标为 `CRect` 对象作为参数传递给 `OnGetItemPosition`。  
  
 就地，则在编辑过程一个 OLE 项的位置或大小更改，必须更新有关项的矩形剪辑和位置的容器信息，服务器必须获得有关更改的信息。  框架因此调用 `COleClientItem::OnChangeItemPosition`。  MFC 应用程序向导提供调用基类中函数的重写。  应编辑应用程序向导为 `COleClientItem`派生类编写的函数，使该函数更新客户项对象保留的所有信息。  
  
## 请参阅  
 [容器](../mfc/containers.md)   
 [容器：客户端项状态](../mfc/containers-client-item-states.md)   
 [COleClientItem::OnChangeItemPosition](../Topic/COleClientItem::OnChangeItemPosition.md)