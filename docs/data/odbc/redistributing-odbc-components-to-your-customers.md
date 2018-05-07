---
title: 重新分发 ODBC 组件到你的客户 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e0427228b8fb3e852cf1d9ee66a10c9290b860b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="redistributing-odbc-components-to-your-customers"></a>为客户重新分发 ODBC 组件
如果你将 ODBC 管理员程序的功能合并到你的应用程序，则还必须分配到你的用户运行这些程序的文件。 这些 ODBC 文件驻留在 Visual c + + CD-ROM 的 \OS\System 目录。 Redistrb.wri 文件和许可协议位于同一目录中的包含你可以重新分发 ODBC 文件的列表。  
  
 请查阅你打算传送任何 ODBC 驱动程序的文档。 你需要确定哪些 Dll 和其他文件交付。 你还应阅读[到你的客户重新分发 ODBC 组件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)，其中解释了如何重新分发 ODBC 组件。  
  
 此外，你需要在大多数情况下包括其他文件。 Odbccr32.dll 是 ODBC 游标库。 此库提供 1 级驱动程序的向前和向后滚动功能。 它还提供了支持快照功能。 有关 ODBC 游标库的详细信息，请参阅[ODBC: ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
 以下主题提供有关使用 ODBC 数据库类使用的详细信息：  
  
-   [ODBC：ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
-   [ODBC：配置 ODBC 数据源](../../data/odbc/odbc-configuring-an-odbc-data-source.md)  
  
-   [ODBC：直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)  
  
## <a name="see-also"></a>请参阅  
 [ODBC 基础知识](../../data/odbc/odbc-basics.md)   
 [ODBC 管理器](../../data/odbc/odbc-administrator.md)