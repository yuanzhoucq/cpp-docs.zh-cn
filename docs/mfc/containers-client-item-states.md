---
title: 容器：客户端项状态
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 866aa6f2265abe671ce0028e3be5f1c8ee1762a8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575339"
---
# <a name="containers-client-item-states"></a>容器：客户端项状态

本文介绍了在其生存期内，通过传递客户端项的不同状态。

客户端项经过若干种状态，因为它的创建、 激活、 修改和保存。 每次项的状态更改，框架将调用[COleClientItem::OnChange](../mfc/reference/coleclientitem-class.md#onchange)与**OLE_CHANGED_STATE**通知。 第二个参数是一个介于`COleClientItem::ItemState`枚举。 它可以是以下值之一：

- *COleClientItem::emptyState*

- *COleClientItem::loadedState*

- *COleClientItem::openState*

- *COleClientItem::activeState*

- *COleClientItem::activeUIState*

在空状态下，客户端项不是尚未完全项。 已分配内存，但它具有尚未初始化 OLE 项的数据。 这是通过调用创建完毕后，客户端项处于的状态**新**但尚未进行通常分两步创建的第二个步骤。

在第二个步骤中，通过调用执行`COleClientItem::CreateFromFile`或其他`CreateFrom` *xxxx*函数，完全创建项。 OLE 数据 （从文件或某些其他源，如剪贴板） 相关联`COleClientItem`-派生的对象。 现在该项处于加载状态。

当项具有已在服务器的窗口中打开而不是在容器的文档中的位置中打开时，则处于打开 （或完全打开） 状态。 在此状态下，跨阴影通常是上绘制指示的其他位置项处于活动状态的容器的窗口中项的表示形式。

当已就地激活了某个项时，该测试通过，通常仅简单地说，通过活动状态。 然后进入 UI 活动状态，该服务器已合并其菜单、 工具栏和与这些容器的其他用户界面组件。 这些用户界面组件存在用于区分 UI 活动状态从活动状态。 否则，活动状态类似于 UI 活动状态。 如果服务器支持撤消，则需要保留 OLE 项的撤消状态信息，直到达到加载或打开状态服务器。

## <a name="see-also"></a>请参阅

[容器](../mfc/containers.md)<br/>
[激活](../mfc/activation-cpp.md)<br/>
[容器：客户端项通知](../mfc/containers-client-item-notifications.md)<br/>
[跟踪器](../mfc/trackers.md)<br/>
[CRectTracker 类](../mfc/reference/crecttracker-class.md)
