---
title: 使用存储过程
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: 436c796b24b0fa498f2b3f45e848392635b22a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376030"
---
# <a name="using-stored-procedures"></a>使用存储过程

存储过程是存储在数据库中的可执行对象。 调用存储过程类似于调用 SQL 命令。 在数据源上使用存储过程（而不是在客户端应用程序中执行或准备语句）可以提供几个优点，包括更高的性能、减少网络开销以及提高一致性和准确性。

存储过程可以具有任意数量的（包括零）输入或输出参数，并可以传递返回值。 可以将硬代码参数值作为特定数据值，也可以使用参数标记（问号"？"

> [!NOTE]
> 使用 Visual C++创建的 CLR SQL Server 存储过程`/clr:safe`必须使用编译器选项进行编译。

用于 SQL Server （SQLOLEDB） 的 OLE DB 提供程序支持存储过程用于返回数据的以下机制：

- 过程中的每个**SELECT**语句都会生成结果集。

- 过程可以通过输出参数返回数据。

- 过程可以具有整数返回代码。

> [!NOTE]
> 不能将存储过程与 Jet 的 OLE DB 提供程序一起使用，因为该提供程序不支持存储过程;因此，该提供程序不支持"处理程序"。"这些过程"查询字符串中只允许常量。

## <a name="see-also"></a>另请参阅

[使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)
