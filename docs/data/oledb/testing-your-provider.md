---
title: 测试提供程序
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: ca1eaed3baf8e0ee4adad4968f7ecd176533ede3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430870"
---
# <a name="testing-your-provider"></a>测试提供程序

发布提供程序之前，您应指示的顺序执行以下测试。 这些测试，请确保对大多数潜在用户正常运行的提供程序函数。

1. 测试使用的提供程序[使用者](../../data/oledb/creating-an-ole-db-consumer.md)使用 OLE DB 使用者模板编写的应用程序。 测试使用者应涵盖你的提供商 （添加或修改的所有代码） 的所有功能区域。

1. 测试提供程序使用 ADO 编写的使用者应用程序。 大多数开发人员 （特别是 Microsoft Visual Basic 和 Microsoft C# 的开发人员） 的使用者应用程序使用 ADO 或 ADO.NET。 测试使用者应涵盖你的提供商的所有功能区域。 ADO 使用者应用程序的示例，请参阅[Microsoft Visual Basic 中的 ADO 代码示例](https://msdn.microsoft.com/library/ms807514.aspx)。

1. 运行 OLE DB 一致性测试 （包括 ADO 一致性测试） 以确保您的提供程序对 OLE DB 访问接口满足级别 0 标准。 (有关级别 0 的说明，搜索"OLE DB 级别 0 一致性测试"处[OLE DB 程序员指南](/previous-versions/windows/desktop/ms713643)。 Visual c + + 数据访问 SDK 中包含这些测试和相关的文档。 这些测试还有助于确保您的提供程序运行良好时由其他聚合[服务提供商](../../data/oledb/ole-db-resource-pooling-and-services.md)时特别有用，如果修改或添加属性。 有关符合性测试的详细信息，请参阅数据访问 sdk，位于其中一个 Visual Studio Cd 上的自述文件。

## <a name="see-also"></a>请参阅

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)