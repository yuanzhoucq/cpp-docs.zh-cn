---
title: OLE DB 使用者特性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], database
- attributes [C++/CLI], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++/CLI]
- attributes [C++/CLI], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07b129e2810b7b1310eb8988ca60fbd6e5dcad5a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391914"
---
# <a name="ole-db-consumer-attributes"></a>OLE DB 使用者特性
OLE DB 使用者特性注入代码中，基于[OLE DB 使用者模板](../data/oledb/ole-db-consumer-templates-reference.md)，若要创建使用 OLE DB 使用者执行任务，例如打开表执行命令和访问数据。
  
|特性|描述|
|---------------|-----------------|
|[db_accessor](../windows/db-accessor.md)|绑定行集中的列，并将它们绑定到相应的访问器映射。|
|[db_column](../windows/db-column.md)|将指定的列绑定到行集。|
|[db_command](../windows/db-command.md)|执行 OLE DB 命令。|
|[db_param](../windows/db-param.md)|将指定的成员变量与输入或输出参数相关联。|
|[db_source](../windows/db-source.md)|创建并封装到数据源的提供程序通过建立的连接。|
|[db_table](../windows/db-table.md)|将打开一个 OLE DB 表。|
  
## <a name="see-also"></a>请参阅

[按组分的特性](../windows/attributes-by-group.md)