---
title: OLE DB 使用者特性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], database
- attributes [C++], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++]
- attributes [C++], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2e9afcf3850d047452b201d9d1d84f1e0cf6cb4b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="ole-db-consumer-attributes"></a>OLE DB 使用者特性
OLE DB 使用者属性将插入代码中，基于[OLE DB 使用者模板](../data/oledb/ole-db-consumer-templates-reference.md)，若要创建使用 OLE DB 使用者执行任务，例如打开表，执行命令和访问数据。  
  
|特性|描述|  
|---------------|-----------------|  
|[db_accessor](../windows/db-accessor.md)|将列绑定在行集中，并将它们绑定到相应的访问器映射。|  
|[db_column](../windows/db-column.md)|将指定的列绑定到行集。|  
|[db_command](../windows/db-command.md)|执行的 OLE DB 命令。|  
|[db_param](../windows/db-param.md)|将指定的成员变量与一个输入或输出参数相关联。|  
|[db_source](../windows/db-source.md)|创建并封装的连接，通过提供商，与数据源。|  
|[db_table](../windows/db-table.md)|将打开一个 OLE DB 表。|  
  
## <a name="see-also"></a>请参阅  
 [按组分的特性](../windows/attributes-by-group.md)