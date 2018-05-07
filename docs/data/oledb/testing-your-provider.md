---
title: 测试提供程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c35b1391e5b8cbfb073255b3680b0376d19ae040
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="testing-your-provider"></a>测试提供程序
发布提供程序之前，你应按所指示的顺序执行以下测试。 这些测试，请确保对大多数潜在用户正常运行的提供程序函数。  
  
1.  测试使用的提供程序[使用者](../../data/oledb/creating-an-ole-db-consumer.md)使用 OLE DB 使用者模板编写的应用程序。 测试使用者应涵盖提供程序 （即已添加或修改所有代码） 的所有功能的区域。  
  
2.  测试使用与 ADO 编写的使用者应用程序的提供程序。 大多数开发人员 （尤其是 Microsoft Visual Basic 和 C# Microsoft 的开发人员） 使用者应用程序使用 ADO 或 ADO.NET。 测试使用者应涵盖提供程序的所有功能的区域。 ADO 使用者应用程序的示例，请参阅[ADO 代码示例在 Microsoft Visual Basic](https://msdn.microsoft.com/en-us/library/ms807514.aspx)。  
  
3.  运行 OLE DB 一致性测试 （包括 ADO 一致性测试） 以确保你的提供商满足级别 0 标准 OLE DB 提供程序。 (有关级别 0 的说明，搜索"OLE DB 级别 0 一致性测试"在[OLE DB 程序员指南](http://go.microsoft.com/fwlink/p/?linkid=121548)。 数据访问 SDK 中的 Visual c + + 中附带了这些测试和关联的文档。 这些测试还有助于确保提供程序在被其他聚合时也运行[服务提供商](../../data/oledb/ole-db-resource-pooling-and-services.md)并且如果你修改或添加属性会特别有用。 有关一致性测试的详细信息，请参阅数据访问 sdk，它位于其中一个 Visual Studio Cd 上的自述文件。  
  
## <a name="see-also"></a>请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)