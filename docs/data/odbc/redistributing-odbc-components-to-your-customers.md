---
title: 重新分发 ODBC 组件到客户 |Microsoft Docs
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
ms.openlocfilehash: 737343a57a852e8bd6a11116fa0d123502208b88
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079825"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>为客户重新分发 ODBC 组件

如果将 ODBC 管理器程序的功能合并到应用程序，您必须还将分发到你的用户运行这些程序的文件。 这些 ODBC 文件驻留在 Visual c + + CD-ROM 的 \OS\System 目录。 Redistrb.wri 文件和许可协议的相同目录中包含你可以重新分发 ODBC 文件的列表。  
  
请查阅你打算发布的任何 ODBC 驱动程序的文档。 您需要确定哪些 Dll 和其他文件交付。 此外应阅读[为客户重新分发 ODBC 组件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)，该文介绍了如何重新分发 ODBC 组件。  
  
此外，您需要在大多数情况下包含一个其他文件。 Odbccr32.dll 是 ODBC 游标库。 此库提供 1 级驱动程序的向前和向后滚动功能。 它还提供了支持快照功能。 有关 ODBC 游标库的详细信息，请参阅[ODBC: ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
以下主题提供有关使用 ODBC 数据库类使用的详细信息：  
  
- [ODBC：ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
- [ODBC：配置 ODBC 数据源](../../data/odbc/odbc-configuring-an-odbc-data-source.md)  
  
- [ODBC：直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)  
  
## <a name="see-also"></a>请参阅  

[ODBC 基础](../../data/odbc/odbc-basics.md)<br/>
[ODBC 管理器](../../data/odbc/odbc-administrator.md)