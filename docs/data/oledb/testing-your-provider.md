---
title: "测试提供程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供程序, 测试"
  - "测试提供程序"
  - "测试, OLE DB 提供程序"
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 测试提供程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在发布提供程序之前，应该按指示的顺序执行以下测试。  这些测试确保提供程序对大多数潜在的用户都可以正常运行。  
  
1.  使用以 OLE DB 使用者模板编写的[使用者](../../data/oledb/creating-an-ole-db-consumer.md)应用程序测试提供程序。  测试使用者应包括提供程序的所有功能区域（已添加或修改的所有代码）。  
  
2.  用以 ADO 编写的使用者应用程序来测试提供程序。  大多数开发人员（尤其是 Microsoft Visual Basic 和 Microsoft C\# 开发人员）对使用者应用程序使用 ADO 或 ADO.NET。  测试使用者应包括提供程序的所有功能区域。  有关 ADO 使用者应用程序的示例，请参见 [Microsoft Visual Basic 中的 ADO 代码示例](https://msdn.microsoft.com/en-us/library/ms807514.aspx)。  
  
3.  运行 OLE DB 一致性测试（包括 ADO 一致性测试），确保提供程序符合 OLE DB 提供程序的级别 0 标准。\(有关级别的说明 0，“OLE DB 级别 0 一致性测试”[OLE DB 程序员的指南。](http://go.microsoft.com/fwlink/?LinkId=121548)。的搜索。  这些测试和关联文档与 Visual C\+\+ 一起包括在 Data Access SDK 中。  这些测试也有助于确保提供程序在被其他[服务提供程序](../../data/oledb/ole-db-resource-pooling-and-services.md)聚合时运行良好，并且对修改或添加属性特别有用。  有关一致性测试的更多信息，请参见 Data Access SDK 的自述文件，该文件位于其中一张 Visual Studio 光盘上。  
  
## 请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)