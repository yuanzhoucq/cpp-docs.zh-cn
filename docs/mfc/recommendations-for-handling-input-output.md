---
title: 有关处理输入输出的建议
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: 956a92fd1761f61081afa2eb9c6cb35fe72b46d6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446896"
---
# <a name="recommendations-for-handling-inputoutput"></a>关于处理输入/输出的建议

是否使用基于文件的 i/o 取决于您如何响应以下决策树中的问题：

**应用程序中的主数据是否驻留在磁盘文件中**

- 是的，主数据驻留在磁盘文件中：

     **应用程序是否在打开文件时将整个文件读取到内存中，并在文件保存后将整个文件写入磁盘**

   - 是：这是默认的 MFC 文档事例。 使用 `CDocument` 序列化。

   - 不是：这通常是基于事务的文件更新的情况。 您可以基于每个事务更新文件，而不需要 `CDocument` 序列化。

- 不，主数据不驻留在磁盘文件中：

     **数据是否驻留在 ODBC 数据源中**

   - 是的，数据驻留在 ODBC 数据源中：

      使用 MFC 的数据库支持。 这种情况的标准 MFC 实现包括 `CDatabase` 对象，如[MFC：将数据库类与文档和视图结合使用](../data/mfc-using-database-classes-with-documents-and-views.md)一文中所述。 应用程序还可以读取和写入辅助文件，即应用程序向导的目的 "数据库视图和文件支持" 选项。 在这种情况下，将对辅助文件使用序列化。

   - 不会，数据不会驻留在 ODBC 数据源中。

      这种情况的示例：数据驻留在非 ODBC DBMS 中;数据是通过某些其他机制（如 OLE 或 DDE）读取的。

      在这种情况下，你不会使用序列化，你的应用程序将不会打开和保存菜单项。 您可能仍想要将 `CDocument` 用作主数据库，就像 MFC ODBC 应用程序使用该文档存储 `CRecordset` 对象一样。 但不会使用框架的默认文件打开/保存文档序列化。

为了支持 "文件" 菜单上的 "打开"、"保存" 和 "另存为" 命令，该框架提供了文档序列化。 序列化读取和写入数据（包括从类 `CObject`派生的对象）到永久存储（通常是磁盘文件）。 序列化易于使用并满足您的多种需求，但它可能不适合许多数据访问应用程序。 数据访问应用程序通常基于每个事务更新数据。 它们更新受事务影响的记录，而不是一次读取和写入整个数据文件。

有关序列化的信息，请参阅[序列化](../mfc/serialization-in-mfc.md)。

## <a name="see-also"></a>另请参阅

[序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)
