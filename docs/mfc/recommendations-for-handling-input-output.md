---
title: 关于处理输入-输出的建议 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a8d0d2c7e560338bbef5cbe432c325385734c56
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385022"
---
# <a name="recommendations-for-handling-inputoutput"></a>关于处理输入/输出的建议

您使用基于文件的 I/O 取决于如何应对以下决策树中的问题：

**在应用程序中的主数据位于磁盘文件**

- 是的主数据驻留在磁盘中：

     **应用程序的整个文件读入内存在文件打开和写入整个文件返回磁盘上保存文件的**

   - 是： 这是默认 MFC 文档大小写。 使用`CDocument`序列化。

   - 否： 这通常是基于事务的更新文件的大小写。 更新每个事务的基础上的文件并不需要`CDocument`序列化。

- 不是，主数据不会驻留在磁盘中：

     **数据位于 ODBC 数据源**

   - 是的数据驻留在 ODBC 数据源：

         Use MFC's database support. The standard MFC implementation for this case includes a `CDatabase` object, as discussed in the article [MFC: Using Database Classes with Documents and Views](../data/mfc-using-database-classes-with-documents-and-views.md). The application might also read and write an auxiliary file — the purpose of the application wizard "both a database view and file support" option. In this case, you'd use serialization for the auxiliary file.

   - 不可以，数据不会驻留在 ODBC 数据源中。

         Examples of this case: the data resides in a non-ODBC DBMS; the data is read via some other mechanism, such as OLE or DDE.

         In such cases, you won't use serialization, and your application won't have Open and Save menu items. You might still want to use a `CDocument` as a home base, just as an MFC ODBC application uses the document to store `CRecordset` objects. But you won't use the framework's default File Open/Save document serialization.

若要支持打开、 保存，并在文件菜单上另存为命令，该框架提供文档序列化。 序列化读取和写入数据，包括对象派生自类`CObject`，到永久存储，通常为磁盘文件。 序列化是易于使用并提供许多您的需求，但它可能不适合在多个数据访问应用程序中。 数据访问应用程序通常会更新每个事务的基础上的数据。 他们更新受影响的事务而不是读取和写入整个数据文件在一次记录。

有关序列化的信息，请参阅[序列化](../mfc/serialization-in-mfc.md)。

## <a name="see-also"></a>请参阅

[序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)
