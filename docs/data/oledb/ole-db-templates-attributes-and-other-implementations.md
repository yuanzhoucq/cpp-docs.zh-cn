---
title: OLE DB 模板、特性和其他实现
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 722bfdf02dc89e061351fd2a87b5d019db10da6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209880"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>OLE DB 模板、特性和其他实现

## <a name="atl-ole-db-templates"></a>ATL OLE DB 模板

OLE DB 模板是 ATL （活动模板库）的一部分，通过提供实现许多常用 OLE DB 接口的类，使高性能 OLE DB 数据库技术更易于使用。 与此模板库一起提供了用于创建 OLE DB 入门应用程序的向导支持。

此模板库包含以下两个部分：

- **OLE DB 使用者模板**用于实现 OLE DB 客户端（使用者）应用程序。

- **OLE DB 提供程序模板**用于实现 OLE DB 服务器（提供程序）应用程序。

要使用 OLE DB 模板，应熟悉 C++ 模板、COM 和 OLE DB 接口。 如果你不熟悉 OLE DB，请参阅[OLE DB 程序员参考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)。

有关详细信息，可以：

- 阅读有关[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)或[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)的主题。

- 创建[OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer.md)或[OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)。

- 请参阅[OLE DB 使用者类](../../data/oledb/ole-db-consumer-templates-reference.md)或[OLE DB 提供程序类](../../data/oledb/ole-db-provider-templates-reference.md)的列表。

- 请参阅[OLE DB 模板](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)的列表示例。

- 请参阅[OLE DB 程序员参考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)（在 Windows SDK 中）。

## <a name="ole-db-attributes"></a>OLE DB 特性

[OLE DB 使用者属性](../../windows/ole-db-consumer-attributes.md)提供了一种简便的方法来创建 OLE DB 使用者。 OLE DB 属性基于[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-reference.md)插入代码，以创建工作 OLE DB 使用者和提供者。 如果需要指定属性不支持的功能，则可以将 OLE DB 模板与代码中的属性结合使用。

## <a name="mfc-ole-db-classes"></a>MFC OLE DB 类

MFC 库有一个类[COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)，用于显示控件中的数据库记录。 视图是直接连接到 `CRowset` 对象的窗体视图，并在对话框模板的控件中显示 `CRowset` 对象的字段。 它还提供了移动到第一条、下一条、上一条记录或最后一条记录的默认实现，以及用于更新当前视图上的记录的接口。 有关详细信息，请参阅 `COleDBRecordView`。

## <a name="ole-db-sdk-interfaces"></a>OLE DB SDK 接口

在 OLE DB 模板不支持 OLE DB 功能的情况下，你需要使用 OLE DB 接口。 有关详细信息，请参阅 Windows SDK 中的[OLE DB 程序员参考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)。

## <a name="see-also"></a>另请参阅

[OLE DB 编程](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)
