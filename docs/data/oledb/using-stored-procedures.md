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
ms.openlocfilehash: 7ace43283c56c0c859b193f63e8ca104f6b52a31
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041171"
---
# <a name="using-stored-procedures"></a>使用存储过程

存储的过程是存储在数据库中的可执行对象。 调用存储的过程是类似于调用 SQL 命令。 在数据源 （而不是执行或准备客户端应用程序中的语句） 上使用存储的过程可以提供多项优点，包括更高的性能、 减少的网络开销，并可提高的一致性和准确性。

存储的过程可以有任意数量的 （包括零个） 输入或输出参数，并可以传递返回值。 可以将值硬编码参数为特定的数据值，也可以使用参数标记 (问号？)。

> [!NOTE]
>  CLR 必须使用编译使用 Visual c + + 创建的存储的过程的 SQL Server`/clr:safe`编译器选项。

OLE DB 访问接口的 SQL Server (SQLOLEDB) 支持以下存储过程使用可返回数据的机制：

- 每个**选择**过程中的语句生成的结果集。

- 该过程可以返回通过输出参数的数据。

- 该过程可具有整数返回代码。

> [!NOTE]
> 你无法将存储的过程的 OLE DB 访问接口用于 Jet 因为该提供程序不支持存储的过程;只允许使用常量查询字符串中。

## <a name="see-also"></a>请参阅

[使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)