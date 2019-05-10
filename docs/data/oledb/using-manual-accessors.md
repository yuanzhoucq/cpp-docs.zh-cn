---
title: 使用手动访问器
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: 4a7e2dcde20cdb06a2f4e708149e24ee7144597c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311990"
---
# <a name="using-manual-accessors"></a>使用手动访问器

有四件事情时处理未知的命令：

- 确定参数

- 执行命令

- 确定输出列

- 查看是否有多个返回行集

若要执行这些操作与 OLE DB 使用者模板，请使用`CManualAccessor`类，请执行以下步骤：

1. 打开`CCommand`对象与`CManualAccessor`作为模板参数。

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. 查询的会话`IDBSchemaRowset`接口，并使用过程参数行集。 如果`IDBSchemaRowset`接口不可用，查询`ICommandWithParameters`接口。 调用`GetParameterInfo`有关信息。 如果两个接口都可用，可以假定没有任何参数。

1. 对于每个参数，调用`AddParameterEntry`以添加参数并将其设置。

1. 打开行集，但将绑定参数设置为**false**。

1. 调用`GetColumnInfo`检索输出列。 使用`AddBindEntry`向绑定添加输出列。

1. 调用`GetNextResult`以确定多个行集是否可用。 重复步骤 2 到 5。

手动访问器的示例，请参阅`CDBListView::CallProcedure`中[DBVIEWER](https://github.com/Microsoft/VCSamples)示例。

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)