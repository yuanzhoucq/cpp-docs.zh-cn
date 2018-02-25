---
title: "OLE DB 模板、 特性和其他实现 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: abdf0565db00b13c932366985c315c88d8d29f9e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>OLE DB 模板、特性和其他实现
## <a name="atl-ole-db-templates"></a>ATL OLE DB 模板  
 OLE DB 模板，这是 ATL （活动模板库） 的一部分，使高性能 OLE DB 数据库技术更轻松地通过提供实现许多常用 OLE DB 接口的类使用。 此模板以及库来自用于创建 OLE DB 初学者应用程序的向导支持。  
  
 此模板库包含两个部分：  
  
-   **OLE DB 使用者模板**用于实现 OLE DB 客户端 （使用者） 应用程序。  
  
-   **OLE DB 提供程序模板**用于实现的 OLE DB 服务器 （提供程序） 应用程序。  
  
 要使用 OLE DB 模板，应熟悉 C++ 模板、COM 和 OLE DB 接口。 如果你不熟悉 OLE DB，请参阅[OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)。  
  
 有关详细信息，你可以：  
  
-   有关阅读主题[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)或[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)。  
  
-   创建[OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer.md)或[OLE DB 访问接口](../../data/oledb/creating-an-ole-db-provider.md)。  
  
-   请参阅列表[OLE DB 使用者的类](../../data/oledb/ole-db-consumer-templates-reference.md)或[OLE DB 提供程序类](../../data/oledb/ole-db-provider-templates-reference.md)。  
  
-   请参阅列表[OLE DB 模板示例](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)。  
  
-   请参阅[OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)（在 Windows SDK)。  
  
## <a name="ole-db-attributes"></a>OLE DB 属性  
 [OLE DB 使用者特性](../../windows/ole-db-consumer-attributes.md)让你方便地创建 OLE DB 使用者。 OLE DB 属性将插入代码基于[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-reference.md)创建使用 OLE DB 使用者和提供程序。 如果你需要指定的特性不支持的功能，你可以在代码中与属性结合使用 OLE DB 模板。  
  
## <a name="mfc-ole-db-classes"></a>MFC OLE DB 类  
 MFC 库包含一个类， [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)，在控件中显示数据库记录。 视图是直接连接到窗体视图`CRowset`对象，并显示的字段`CRowset`对话框模板的控件中的对象。 它还会提供的默认实现，移动到第一个下, 一步上, 一个或最后一个记录和用于更新当前上视图的记录的接口。 有关详细信息，请参阅`COleDBRecordView`。  
  
## <a name="ole-db-sdk-interfaces"></a>OLE DB SDK 接口  
 在 OLE DB 模板不支持 OLE DB 功能的情况，你需要使用 OLE DB 接口本身。 有关详细信息，请参阅[OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)