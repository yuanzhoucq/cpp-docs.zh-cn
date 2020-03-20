---
title: 测试提供程序
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: 722757b93d3423b02340c382b16e08a31626bc01
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544536"
---
# <a name="testing-your-provider"></a>测试提供程序

在发布提供程序之前，应按指示的顺序执行以下测试。 这些测试表明提供程序适用于大多数可能的用户。

1. 使用使用 OLE DB 使用者模板编写的使用[者](../../data/oledb/creating-an-ole-db-consumer.md)应用程序测试提供程序。 测试使用者应涵盖提供程序的所有功能区域（已添加或修改的所有代码）。

1. 使用用 ADO 编写的使用者应用程序测试提供程序。 大多数开发人员（特别是 Microsoft Visual Basic C#和 microsoft 开发人员）使用 ADO 或 ADO.NET 作为使用者应用程序。 测试使用者应涵盖提供商的所有功能区域。 有关 ADO 使用者应用程序的示例，请参阅[Microsoft Visual Basic 中的 Ado 代码示例](/previous-versions/ms807514(v=msdn.10))。

1. 运行 OLE DB 一致性测试（包括 ADO 一致性测试）以显示提供程序满足 OLE DB 提供程序的级别0标准。 （有关级别0的说明，请在[OLE DB 程序员指南](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)中搜索**OLE DB 级别0一致性测试**。 数据访问 SDK 中的视觉对象C++附带了这些测试和相关文档。 这些测试还有助于说明提供程序在由其他[服务提供程序](../../data/oledb/ole-db-resource-pooling-and-services.md)聚合时运行良好，并且在修改或添加属性时特别有用。 有关一致性测试的详细信息，请参阅数据访问 SDK 的自述文件，该文件位于某个 Visual Studio Cd 中。

## <a name="see-also"></a>另请参阅

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)