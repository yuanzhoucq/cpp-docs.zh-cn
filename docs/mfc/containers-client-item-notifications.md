---
title: 容器： 客户端项通知 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2255f28c1250096bfbeb1a9365c57f78e17e20d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="containers-client-item-notifications"></a>容器：客户端项通知
本文讨论 MFC 框架在服务器应用程序修改客户端应用程序的文档中的项时调用的可重写函数。  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md)定义多个调用的可重写函数以响应从组件应用程序，这也称为服务器应用程序的请求。 这些可重写通常充当通知。 它们通知容器应用程序的各种事件，如滚动、 激活或者更改位置，以及用户编辑或否则操作项时所做的更改。  
  
 框架通知容器应用程序的更改通过调用`COleClientItem::OnChange`，其实是必需的可重写函数。 此受保护的函数接收两个自变量。 第一个参数指定的服务器被更改项的原因：  
  
|通知|含义|  
|------------------|-------------|  
|`OLE_CHANGED`|OLE 项的外观已更改。|  
|`OLE_SAVED`|已保存的 OLE 项。|  
|`OLE_CLOSED`|OLE 项已关闭。|  
|**OLE_RENAMED**|已重命名包含 OLE 项的服务器文档。|  
|`OLE_CHANGED_STATE`|OLE 项已从一个状态更改为另一个。|  
|**OLE_CHANGED_ASPECT**|OLE 项的绘图方面已由框架。|  
  
 这些值是从**OLE_NOTIFICATION** AFXOLE 中定义的枚举。H。  
  
 此函数的第二个参数指定项的更改方式或给定的状态：  
  
|当第一个参数是|第二个参数|  
|----------------------------|---------------------|  
|`OLE_SAVED` 或 `OLE_CLOSED`|未使用。|  
|`OLE_CHANGED`|指定已更改的 OLE 项的方面。|  
|`OLE_CHANGED_STATE`|描述输入的状态 (`emptyState`， **loadedState**， `openState`， `activeState`，或`activeUIState`)。|  
  
 有关可以假定客户端项状态的详细信息，请参阅[容器： 客户端项状态](../mfc/containers-client-item-states.md)。  
  
 框架调用`COleClientItem::OnGetItemPosition`时激活某个项时正在进行就地编辑。 支持就地编辑应用程序，需要实现。 MFC 应用程序向导提供基本实现，它将分配到的项的坐标`CRect`作为的自变量传递的对象`OnGetItemPosition`。  
  
 如果 OLE 项的位置或大小发生更改的就地编辑过程，必须更新有关项的位置和剪辑矩形的容器的信息，并且服务器必须接收的更改信息。 框架调用`COleClientItem::OnChangeItemPosition`为此目的。 MFC 应用程序向导提供调用基类的函数的替代。 你应编辑应用程序向导为编写的函数你`COleClientItem`-派生类，以使该函数更新你的客户端项对象保留的任何信息。  
  
## <a name="see-also"></a>请参阅  
 [容器](../mfc/containers.md)   
 [容器： 客户端项状态](../mfc/containers-client-item-states.md)   
 [COleClientItem::OnChangeItemPosition](../mfc/reference/coleclientitem-class.md#onchangeitemposition)

