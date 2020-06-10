---
title: 容器：客户端项通知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: 54b1b2a64685b00fb265e0f80c1f6ad878a7da85
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623016"
---
# <a name="containers-client-item-notifications"></a>容器：客户端项通知

本文介绍当服务器应用程序修改客户端应用程序的文档中的项时，MFC 框架调用的可重写函数。

[COleClientItem](reference/coleclientitem-class.md)定义了多个可重写的函数，这些函数用于响应来自组件应用程序的请求，该应用程序也称为 "服务器应用程序"。 这些可重写通常充当通知。 它们通知容器应用程序的各种事件，例如滚动、激活或位置更改，以及用户在编辑或操作该项时所做的更改。

此框架通过对的调用通知您的容器应用程序更改 `COleClientItem::OnChange` ，这是需要实现的可重写函数。 此受保护的函数接收两个参数。 第一个指定服务器更改项的原因：

|通知|含义|
|------------------|-------------|
|**OLE_CHANGED**|OLE 项的外观已更改。|
|**OLE_SAVED**|已保存 OLE 项。|
|**OLE_CLOSED**|OLE 项已关闭。|
|**OLE_RENAMED**|包含 OLE 项的服务器文档已被重命名。|
|**OLE_CHANGED_STATE**|OLE 项已从一种状态变为另一种状态。|
|**OLE_CHANGED_ASPECT**|OLE 项的绘制方位已由框架更改。|

这些值来自**OLE_NOTIFICATION**枚举，它是在 AFXOLE 中定义的。高.

此函数的第二个参数指定项如何更改或它所输入的状态：

|当第一个参数为|第二个参数|
|----------------------------|---------------------|
|**OLE_SAVED**或**OLE_CLOSED**|不使用。|
|**OLE_CHANGED**|指定已更改的 OLE 项的特性。|
|**OLE_CHANGED_STATE**|描述所输入的状态（*emptyState*、 *loadedState*、 *openState*、 *activeState*或*activeUIState*）。|

有关客户端项可以采用的状态的详细信息，请参阅[容器：客户端项状态](containers-client-item-states.md)。

`COleClientItem::OnGetItemPosition`当激活某项以进行就地编辑时，框架会调用。 实现对于支持就地编辑的应用程序是必需的。 MFC 应用程序向导提供了一个基本实现，该实现将项的坐标分配给 `CRect` 作为参数传递给的对象 `OnGetItemPosition` 。

如果在就地编辑过程中 OLE 项的位置或大小发生更改，则必须更新容器的有关项的位置和剪辑矩形的信息，并且服务器必须接收有关这些更改的信息。 框架 `COleClientItem::OnChangeItemPosition` 为此目的而调用。 MFC 应用程序向导提供了一个调用基类的函数的重写。 你应编辑应用程序向导为派生类编写的函数， `COleClientItem` 以使函数更新客户端项对象所保留的任何信息。

## <a name="see-also"></a>另请参阅

[容器](containers.md)<br/>
[容器：客户端项状态](containers-client-item-states.md)<br/>
[COleClientItem：： OnChangeItemPosition](reference/coleclientitem-class.md#onchangeitemposition)
