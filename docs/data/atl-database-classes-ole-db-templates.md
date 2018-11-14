---
title: ATL 数据库类（OLE DB 模板）
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: 4304c350ce6a9303a7542809fa85fb0cd2560031
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522062"
---
# <a name="atl-database-classes-ole-db-templates"></a>ATL 数据库类（OLE DB 模板）

Microsoft 提供了几个 OLE DB，一组提供对各种信息源和格式中的数据的统一访问的 COM 接口的实现。  OLE DB 正式不推荐使用;本文档适用于开发人员要保留旧代码。 新的应用程序应使用 ODBC 连接到 SQL 数据源。

OLE DB 模板是在 ATL 中使 OLE DB 数据库技术更易于使用，从而实现许多常用 OLE DB 接口的类的 c + + 模板。

此模板库包含两个部分：

- [OLE DB 使用者模板](../data/oledb/ole-db-consumer-templates-cpp.md)用于实现 OLE DB 客户端 （使用者） 应用程序。

- [OLE DB 提供程序模板](../data/oledb/ole-db-provider-templates-cpp.md)用于实现 OLE DB 服务器 （提供程序） 应用程序。

此外， [OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)提供方便地创建 OLE DB 使用者。 OLE DB 属性将插入基于 OLE DB 使用者模板来创建使用 OLE DB 使用者的代码。

请注意，MFC 库包含一个类[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)，在控件中显示数据库记录。 该视图是直接连接到的窗体视图`CRowset`对象，并显示字段的`CRowset`对话框模板的控件中的对象。

有关详细信息，请参阅[OLE DB 编程](../data/oledb/ole-db-programming.md)并[OLE DB 程序员指南](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)。

## <a name="see-also"></a>请参阅

[创建 OLE DB 使用者](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[创建 OLE DB 提供程序](../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB 使用者模板参考](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB 提供程序模板参考](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 模板示例](https://github.com/Microsoft/VCSamples)