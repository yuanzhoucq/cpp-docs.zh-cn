---
title: 数据成员特性 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- data members [C++], attributes
- data members [C++]
ms.assetid: 95b2397d-1daf-4ae4-8cd0-06956d005b13
ms.openlocfilehash: e188f4d9ad2c553ff142e45ec84bc0a04630b816
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512926"
---
# <a name="data-member-attributes"></a>数据成员特性

以下属性应用于类、 组件类或接口中的数据成员。

|特性|描述|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|组`db_column`参与属性`IAccessor`-基于绑定。|
|[db_column](db-column.md)|将指定的列绑定到行集。|
|[db_command](db-command.md)|创建 OLE DB 命令。|
|[db_param](db-param.md)|指定的成员变量相关联的输入或输出参数和分隔变量。|
|[db_source](db-source.md)|创建与数据源的连接。|
|[db_table](db-table.md)|将打开一个 OLE DB 表。|
|[defaultbind](defaultbind.md)|指示最能代表对象的单个、 可绑定属性。|
|[displaybind](displaybind.md)|指示应显示给用户作为可绑定的属性。|
|[id](id.md)|指定的成员函数 （属性或方法，请在接口或调度接口） 的 DISPID。|
|[range](range-cpp.md)|指定参数或在运行时设置其值的字段的允许值的范围。|
|[rdx](rdx.md)|创建注册表项或修改现有的注册表项。|
|[readonly](readonly-cpp.md)|禁止分配给数据成员。|
|[requestedit](requestedit.md)|指示该属性支持`OnRequestEdit`通知。|

## <a name="see-also"></a>请参阅

[按用法分的特性](attributes-by-usage.md)