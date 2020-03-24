---
title: 数据成员属性（C++ COM）
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- data members [C++], attributes
- data members [C++]
ms.assetid: 95b2397d-1daf-4ae4-8cd0-06956d005b13
ms.openlocfilehash: f23ca0963c63212ea2a8a70362b8e76fa0819fc7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214872"
---
# <a name="data-member-attributes"></a>数据成员特性

以下属性适用于类、组件类或接口中的数据成员。

|Attribute|说明|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|将参与基于 `IAccessor`的绑定 `db_column` 特性组合在一起。|
|[db_column](db-column.md)|将指定列绑定到行集。|
|[db_command](db-command.md)|创建 OLE DB 命令。|
|[db_param](db-param.md)|将指定的成员变量与输入或输出参数关联，并将变量分隔。|
|[db_source](db-source.md)|创建与数据源的连接。|
|[db_table](db-table.md)|打开 OLE DB 表。|
|[defaultbind](defaultbind.md)|指示最能表示对象的单个可绑定属性。|
|[displaybind](displaybind.md)|指示应作为可绑定属性显示给用户的属性。|
|[id](id.md)|为成员函数（在接口或调度接口中为属性或方法）指定 DISPID。|
|[range](range-cpp.md)|为其值在运行时设置的参数或字段指定一系列允许的值。|
|[rdx](rdx.md)|创建注册表项或修改现有注册表项。|
|[readonly](readonly-cpp.md)|禁止分配给数据成员。|
|[requestedit](requestedit.md)|指示该属性支持 `OnRequestEdit` 通知。|

## <a name="see-also"></a>另请参阅

[按用法分的特性](attributes-by-usage.md)
