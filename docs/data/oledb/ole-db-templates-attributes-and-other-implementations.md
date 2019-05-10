---
title: OLE DB 模板、特性和其他实现
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 0e6b5dbc97f6a7bea1df342d6a792ea43907ca33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283819"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>OLE DB 模板、特性和其他实现

## <a name="atl-ole-db-templates"></a>ATL OLE DB 模板

OLE DB 模板，都是 ATL （动态模板库） 的一部分，使高性能 OLE DB 数据库技术更易于使用，从而实现许多常用 OLE DB 接口的类。 此模板以及库提供用于创建 OLE DB 初学者应用程序向导支持。

此模板库包含两个部分：

- **OLE DB 使用者模板**用于实现 OLE DB 客户端 （使用者） 应用程序。

- **OLE DB 提供程序模板**用于实现 OLE DB 服务器 （提供程序） 应用程序。

要使用 OLE DB 模板，应熟悉 C++ 模板、COM 和 OLE DB 接口。 如果您不熟悉 OLE DB，请参阅[OLE DB 程序员参考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)。

有关详细信息，你可以：

- 阅读有关主题[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)或[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)。

- 创建[OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer.md)或[OLE DB 访问接口](../../data/oledb/creating-an-ole-db-provider.md)。

- 请参阅的列表[OLE DB 使用者类](../../data/oledb/ole-db-consumer-templates-reference.md)或[OLE DB 提供程序类](../../data/oledb/ole-db-provider-templates-reference.md)。

- 请参阅的列表[OLE DB 模板示例](https://github.com/Microsoft/VCSamples)。

- 请参阅[OLE DB 程序员参考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)（在 Windows SDK 中)。

## <a name="ole-db-attributes"></a>OLE DB 属性

[OLE DB 使用者特性](../../windows/ole-db-consumer-attributes.md)提供方便地创建 OLE DB 使用者。 OLE DB 属性将插入基于代码[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-reference.md)若要创建使用 OLE DB 使用者和提供程序。 如果你需要指定不支持属性的功能，可以使用 OLE DB 模板与特性一起使用，在代码中。

## <a name="mfc-ole-db-classes"></a>MFC OLE DB 类

MFC 库包含一个类， [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)，在控件中显示数据库记录。 该视图是直接连接到的窗体视图`CRowset`对象，并显示字段的`CRowset`对话框模板的控件中的对象。 它还会提供默认实现将移到第一个下, 一步上, 一个，或最后一个记录和更新当前在视图上的记录的接口。 有关详细信息，请参阅 `COleDBRecordView`。

## <a name="ole-db-sdk-interfaces"></a>OLE DB SDK 接口

在其中 OLE DB 模板不支持 OLE DB 功能的情况下，您需要使用 OLE DB 接口本身。 有关详细信息，请参阅[OLE DB 程序员参考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)Windows SDK 中。

## <a name="see-also"></a>请参阅

[OLE DB 编程](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)