---
title: OLE DB 使用者属性C++ （COM）
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], database
- attributes [C++/CLI], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++/CLI]
- attributes [C++/CLI], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
ms.openlocfilehash: 67f58d6dd32360248c6437f66fa7042871bc4ea6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214660"
---
# <a name="ole-db-consumer-attributes"></a>OLE DB 使用者特性
OLE DB 使用者特性基于[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-reference.md)插入代码，以创建一个可执行任务（例如打开表、执行命令和访问数据）的工作 OLE DB 使用者。

|Attribute|说明|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|绑定行集中的列，并将其绑定到相应的访问器映射。|
|[db_column](db-column.md)|将指定列绑定到行集。|
|[db_command](db-command.md)|执行 OLE DB 命令。|
|[db_param](db-param.md)|将指定的成员变量与输入或输出参数关联。|
|[db_source](db-source.md)|通过提供程序创建和封装到数据源的连接。|
|[db_table](db-table.md)|打开 OLE DB 表。|

## <a name="see-also"></a>另请参阅

[按组分的特性](attributes-by-group.md)
