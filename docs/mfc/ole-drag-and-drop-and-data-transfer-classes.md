---
title: OLE 拖放和数据传输类
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: 530b1772dfb623689facd5b14eebe9ed1eacd4fd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624147"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>OLE 拖放和数据传输类

这些类用于 OLE 数据传输。 它们允许使用剪贴板或通过拖放方式在应用程序之间传输数据。

[COleDropSource](reference/coledropsource-class.md)<br/>
控制从开始到完成的拖放操作。 此类确定拖动操作的开始时间和结束时间。 它还在拖放操作过程中显示游标反馈。

[COleDataSource](reference/coledatasource-class.md)<br/>
当应用程序为数据传输提供数据时使用。 `COleDataSource`可作为面向对象的剪贴板对象查看。

[COleDropTarget](reference/coledroptarget-class.md)<br/>
表示拖放操作的目标。 `COleDropTarget`对象对应于屏幕上的一个窗口。 它确定是否接受拖放到它上面的任何数据，并实现实际的删除操作。

[COleDataObject](reference/coledataobject-class.md)<br/>
用作的接收方 `COleDataSource` 。 `COleDataObject`对象提供对对象存储的数据的访问 `COleDataSource` 。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
