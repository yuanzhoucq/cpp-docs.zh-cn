---
title: 容器：客户端项状态
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 927211ccec35d8ec26e2f76b971c59b80248ab96
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625990"
---
# <a name="containers-client-item-states"></a>容器：客户端项状态

本文介绍客户端项目在其生存期内经历的不同状态。

当客户端项创建、激活、修改和保存时，它们会经历多个状态。 每次项的状态发生更改时，框架都将调用[COleClientItem：： OnChange](reference/coleclientitem-class.md#onchange)与**OLE_CHANGED_STATE**通知。 第二个参数是枚举中的一个值 `COleClientItem::ItemState` 。 该参数可以是下列值之一：

- *COleClientItem：： emptyState*

- *COleClientItem：： loadedState*

- *COleClientItem：： openState*

- *COleClientItem：： activeState*

- *COleClientItem：： activeUIState*

处于空状态时，客户端项尚未完全是项。 已为其分配内存，但尚未用 OLE 项的数据对其进行初始化。 这是客户端项在通过调用**new**创建，但尚未完成典型的两步创建的第二步时所处的状态。

在第二步中，通过调用 `COleClientItem::CreateFromFile` 或其他 `CreateFrom` *xxxx*函数执行，将完全创建项。 OLE 数据（来自文件或某些其他源，如剪贴板）已与 `COleClientItem` 派生对象相关联。 现在，该项处于已加载状态。

当项在服务器的窗口中打开而不是在容器文档中的位置打开时，它处于打开（或完全打开）状态。 在此状态下，通常会在容器窗口中项的表示形式上绘制交叉影线，以指示该项在其他地方处于活动状态。

就地激活项后，它通常只通过活动状态进行传递。 然后，它将进入 UI 活动状态，在该状态下，服务器已将其菜单、工具栏和其他用户界面组件与其容器的组件合并。 这些用户界面组件的状态将 UI 活动状态与活动状态区分开来。 否则，活动状态类似于 UI 活动状态。 如果服务器支持撤消，则服务器需要保留 OLE 项的撤消状态信息，直到它达到加载或打开状态。

## <a name="see-also"></a>另请参阅

[容器](containers.md)<br/>
[激活](activation-cpp.md)<br/>
[容器：客户端项通知](containers-client-item-notifications.md)<br/>
[跟踪](trackers.md)<br/>
[CRectTracker 类](reference/crecttracker-class.md)
