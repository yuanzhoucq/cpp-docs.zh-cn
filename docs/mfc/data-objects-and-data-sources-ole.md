---
title: 数据对象和数据源 (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
ms.openlocfilehash: dfe400dddfecce3e52337f7f449e975dff2ca83e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616221"
---
# <a name="data-objects-and-data-sources-ole"></a>数据对象和数据源 (OLE)

在使用剪贴板或拖放操作执行数据传输时，数据将具有一个源和一个目标。 一个应用程序提供数据以进行复制，另一个应用程序接受该数据以进行粘贴。 传输的每一端均需要对同一数据执行不同的操作以使传输成功。 Microsoft 基础类 (MFC) 库提供表示此传输的每一端的两个类：

- 数据源（由 `COleDataSource` 对象实现）表示数据传输的源端。 在将数据复制到剪贴板或在提供数据以进行拖放操作时，源应用程序就会创建数据源。

- 数据对象（由 `COleDataObject` 对象实现）表示数据传输的目标端。 当目标应用程序中放入了数据或目标应用程序要求从剪贴板执行粘贴操作时，就会创建数据对象。

以下文章说明了如何在应用程序中使用数据对象和数据源。 此信息适用于容器和服务器应用程序，因为二者都可能被要求复制并粘贴数据。

- [数据对象和数据源：创建和销毁](data-objects-and-data-sources-creation-and-destruction.md)

- [数据对象和数据源：操作](data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>本节内容

[拖放](drag-and-drop-ole.md)

[剪贴板](clipboard.md)

## <a name="see-also"></a>另请参阅

[OLE](ole-in-mfc.md)<br/>
[COleDataObject 类](reference/coledataobject-class.md)<br/>
[COleDataSource 类](reference/coledatasource-class.md)
