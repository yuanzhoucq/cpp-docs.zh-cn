---
title: OLE DB 消费属性 （C++ COM）
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], database
- attributes [C++/CLI], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++/CLI]
- attributes [C++/CLI], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
ms.openlocfilehash: a9147d80e87e23a754043a29eb3d15570e85aec0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377108"
---
# <a name="ole-db-consumer-attributes"></a>OLE DB 使用者特性

OLE DB 使用者属性基于[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-reference.md)注入代码，以创建一个工作中的 OLE DB 使用者，执行诸如打开表、执行命令和访问数据等任务。

|特性|描述|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|在行集中绑定列，并将它们绑定到相应的访问器映射。|
|[db_column](db-column.md)|将指定的列绑定到行集。|
|[db_command](db-command.md)|执行 OLE DB 命令。|
|[db_param](db-param.md)|将指定的成员变量与输入或输出参数关联。|
|[db_source](db-source.md)|通过提供程序创建和封装与数据源的连接。|
|[db_table](db-table.md)|打开 OLE 数据库表。|

## <a name="see-also"></a>另请参阅

[按组分的特性](attributes-by-group.md)
