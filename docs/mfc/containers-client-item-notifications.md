---
title: 容器：客户端项通知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: b59ba84c27d9ed4c964bd308cf69f9f729eb3c39
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528890"
---
# <a name="containers-client-item-notifications"></a>容器：客户端项通知

本文介绍 MFC 框架在服务器应用程序修改客户端应用程序的文档中的项时调用的可重写函数。

[COleClientItem](../mfc/reference/coleclientitem-class.md)组件应用程序，这也称为服务器应用程序的请求响应中定义多个调用的可重写函数。 这些可重写通常充当通知。 它们通知各种事件，如滚动，激活或更改的位置，以及编辑或其他操纵项时用户所做的更改的容器应用程序。

该框架会通知容器应用程序的更改通过调用`COleClientItem::OnChange`，其实现是必需的可重写函数。 此受保护的函数接收两个参数。 第一个指定服务器发生更改的项的原因：

|通知|含义|
|------------------|-------------|
|**OLE_CHANGED**|OLE 项的外观已更改。|
|**OLE_SAVED**|已保存的 OLE 项。|
|**OLE_CLOSED**|OLE 项已关闭。|
|**OLE_RENAMED**|已重命名包含 OLE 项的服务器文档。|
|**OLE_CHANGED_STATE**|OLE 项已从一个状态更改为另一个。|
|**OLE_CHANGED_ASPECT**|OLE 项的绘制方面已更改的框架。|

这些值取自**OLE_NOTIFICATION** AFXOLE 中定义的枚举。H.

此函数的第二个参数指定项已发生更改或给定的状态：

|当第一个参数是|第二个参数|
|----------------------------|---------------------|
|**OLE_SAVED**或**OLE_CLOSED**|不使用。|
|**OLE_CHANGED**|指定的 OLE 项的已更改的方面。|
|**OLE_CHANGED_STATE**|描述要进入的状态 (*emptyState*， *loadedState*， *openState*， *activeState*，或*activeUIState*)。|

有关可以假定客户端项状态的详细信息，请参阅[容器： 客户端项状态](../mfc/containers-client-item-states.md)。

框架将调用`COleClientItem::OnGetItemPosition`项以进行就地编辑激活的时。 需要支持进行就地编辑的应用程序实现。 MFC 应用程序向导提供了一个基本实现，将分配到的项目的坐标`CRect`作为参数传递的对象`OnGetItemPosition`。

如果 OLE 项的位置或大小在就地编辑期间发生更改，必须更新项的位置和剪辑矩形的容器的信息和服务器必须接收有关更改的信息。 框架将调用`COleClientItem::OnChangeItemPosition`实现此目的。 MFC 应用程序向导提供了一个替代以调用基类的函数。 应编辑应用程序向导为编写的函数在`COleClientItem`-派生的类，以便该函数更新保留的客户端项对象的任何信息。

## <a name="see-also"></a>请参阅

[容器](../mfc/containers.md)<br/>
[容器：客户端项状态](../mfc/containers-client-item-states.md)<br/>
[COleClientItem::OnChangeItemPosition](../mfc/reference/coleclientitem-class.md#onchangeitemposition)

