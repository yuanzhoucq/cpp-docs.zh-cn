---
title: 处理输入输出的建议
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: c365120a385c440f09f0ee4c0a2fc52afb55834f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371738"
---
# <a name="recommendations-for-handling-inputoutput"></a>关于处理输入/输出的建议

是否使用基于文件的 I/O 取决于您如何回答以下决策树中的问题：

**应用程序中的主要数据是否驻留在磁盘文件中**

- 是的，主数据驻留在磁盘文件中：

   **应用程序在文件打开时将整个文件读入内存，并将整个文件写回文件保存上的磁盘吗？**

  - 是：这是默认的 MFC 文档案例。 使用`CDocument`序列化。

  - 否：通常情况下是基于事务的文件更新。 基于每个事务更新文件，不需要`CDocument`序列化。

- 否，主数据不驻留在磁盘文件中：

   **数据是否驻留在 ODBC 数据源中**

  - 是的，数据驻留在 ODBC 数据源中：

      使用 MFC 的数据库支持。 此案例的标准 MFC 实现包括一`CDatabase`个对象，如 MFC 一文中所述[：使用包含文档和视图的数据库类](../data/mfc-using-database-classes-with-documents-and-views.md)。 应用程序还可以读取和写入辅助文件 - 应用程序向导"数据库视图和文件支持"选项的目的。 在这种情况下，您将对辅助文件使用序列化。

  - 否，数据不驻留在 ODBC 数据源中。

      这种情况的示例：数据驻留在非 ODBC DBMS 中;数据通过其他机制（如 OLE 或 DDE）读取。

      在这种情况下，您不会使用序列化，并且应用程序将没有"打开"和"保存"菜单项。 您可能仍要使用 作为`CDocument`主数据库，就像 MFC ODBC 应用程序使用文档存储`CRecordset`对象一样。 但是，您不会使用框架的默认文件打开/保存文档序列化。

为了在"文件"菜单上支持"打开"、"保存"和"保存为"命令，框架提供文档序列化。 序列化将数据（包括从类`CObject`派生的对象）读取和写入永久存储，通常是磁盘文件。 序列化易于使用，可满足您的许多需求，但在许多数据访问应用程序中可能不合适。 数据访问应用程序通常根据每个事务更新数据。 它们更新受事务影响的记录，而不是一次读取和写入整个数据文件。

有关序列化的信息，请参阅[序列化](../mfc/serialization-in-mfc.md)。

## <a name="see-also"></a>另请参阅

[序列化：序列化与数据库输入/输出的对比](../mfc/serialization-serialization-vs-database-input-output.md)
