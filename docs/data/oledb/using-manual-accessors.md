---
title: 使用手动访问器
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: a6c0e5236702229a61a828344ba5d0d288898aee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209320"
---
# <a name="using-manual-accessors"></a>使用手动访问器

处理未知命令时，需要执行以下四项操作：

- 确定参数

- 执行命令

- 确定输出列

- 查看是否有多个返回行集

若要使用 OLE DB 使用者模板执行这些操作，请使用 `CManualAccessor` 类，然后执行以下步骤：

1. 使用 `CManualAccessor` 作为模板参数打开 `CCommand` 对象。

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. 在会话中查询 `IDBSchemaRowset` 接口，并使用过程参数行集。 如果 `IDBSchemaRowset` 接口不可用，则查询 `ICommandWithParameters` 接口。 有关信息，请调用 `GetParameterInfo`。 如果这两个接口均不可用，则可以假设没有参数。

1. 对于每个参数，调用 `AddParameterEntry` 以添加参数并设置它们。

1. 打开行集，但将绑定参数设置为**false**。

1. 调用 `GetColumnInfo` 以检索输出列。 使用 `AddBindEntry` 将输出列添加到绑定。

1. 调用 `GetNextResult` 以确定是否有更多的行集可用。 重复步骤2到5。

有关手动访问器的示例，请参阅[DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)示例中的 `CDBListView::CallProcedure`。

## <a name="see-also"></a>另请参阅

[使用访问器](../../data/oledb/using-accessors.md)
