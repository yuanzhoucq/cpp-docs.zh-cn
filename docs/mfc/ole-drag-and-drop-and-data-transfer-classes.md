---
title: OLE 拖放和数据传输类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: e30a358da55b29f9519bc1ab8ee5c93ada308d98
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284419"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>OLE 拖放和数据传输类

在 OLE 数据传输中使用这些类。 它们允许应用程序使用剪贴板或通过拖放之间传输数据。

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
控制从开始到结束拖放操作。 此类确定当拖动操作开始和结束的时候。 它还显示在拖放操作期间的游标的反馈。

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
在应用程序提供数据的数据传输时使用。 `COleDataSource` 可能会被视为面向对象的剪贴板对象。

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
表示拖放操作的目标。 一个`COleDropTarget`对象对应的窗口在屏幕上。 它确定是否接受拖放到它上面的任何数据，并实现实际删除操作。

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
作为接收方使用`COleDataSource`。 `COleDataObject` 对象提供对存储的数据访问`COleDataSource`对象。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)
