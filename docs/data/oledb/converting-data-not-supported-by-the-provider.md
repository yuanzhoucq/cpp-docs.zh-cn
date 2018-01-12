---
title: "将数据提供程序不支持转换 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 438d75ad3a36c82c4f9389d4c9b65d677603f6c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="converting-data-not-supported-by-the-provider"></a>转换不受提供程序支持的数据
当使用者请求提供程序不支持的数据类型时，OLE DB 提供程序模板的代码`IRowsetImpl::GetData`调用 Msdadc.dll 要转换的数据类型。  
  
 如果实现类似的界面`IRowsetChange`需要数据转换，您可以调用 Msdaenum.dll 来执行转换。 使用`GetData`在 Atldb.h，作为示例中定义。  
  
## <a name="see-also"></a>请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)