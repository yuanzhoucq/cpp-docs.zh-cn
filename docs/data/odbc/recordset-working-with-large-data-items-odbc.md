---
title: 记录集：处理大数据项 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 3ba8d4af5b0781c425dd3b1223e2208b279f055e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230977"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>记录集：处理大数据项 (ODBC)

本主题适用于 MFC ODBC 类和 MFC DAO 类。

> [!NOTE]
>  如果使用 MFC DAO 类时，管理大型数据项与类[CByteArray](../../mfc/reference/cbytearray-class.md)而不是类[CLongBinary](../../mfc/reference/clongbinary-class.md)。 如果使用批量行提取使用 MFC ODBC 类，使用`CLongBinary`而非`CByteArray`。 有关批量行提取的详细信息，请参阅[记录集：(ODBC) 批量提取记录](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

假设您的数据库可以存储大的数据，如位图 （雇员照片、 映射、 图片的产品、 OLE 对象等）。 此类数据通常称为二进制大型对象 （或 BLOB） 因为：

- 每个字段值都大。

- 与不同的数字和其他简单数据类型，它具有大小不可预知。

- 不从应用程序的角度来看定型数据。

本主题介绍数据库类用于处理此类对象提供哪些支持。

##  <a name="_core_managing_large_objects"></a> 管理大型对象

记录集有两种方法来解决特别难管理二进制大型对象。 可以使用类[CByteArray](../../mfc/reference/cbytearray-class.md)也可以使用类[CLongBinary](../../mfc/reference/clongbinary-class.md)。 一般情况下，`CByteArray`是管理大型二进制数据的首选的方法。

`CByteArray` 需要更多的开销比`CLongBinary`但功能更强大，如中所述[CByteArray 类](#_core_the_cbytearray_class)。 `CLongBinary` 简要中所述[CLongBinary 类](#_core_the_clongbinary_class)。

有关使用的详细信息`CByteArray`若要处理大数据项，请参阅[技术说明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。

##  <a name="_core_the_cbytearray_class"></a> CByteArray 类

`CByteArray` 是 MFC 集合类之一。 一个`CByteArray`对象将存储为动态的字节数组，数组可以根据需要进行扩展。 类提供快速访问的索引，如同内置C++数组。 `CByteArray` 对象可以序列化和转储以用于诊断目的。 类提供成员函数用于获取和设置将指定的字节、 插入和追加字节和删除 1 个字节或所有字节。 这些功能使得分析更轻松的二进制数据。 例如，如果二进制对象是一个 OLE 对象，您可能需要完成一些标头字节来访问实际对象。

##  <a name="_core_using_cbytearray_in_recordsets"></a> 在记录集中使用 CByteArray

通过提供类型的记录集的字段数据成员`CByteArray`，提供的固定的基础[RFX](../../data/odbc/record-field-exchange-rfx.md)可以管理记录集和数据源之间以及通过可操作此类对象的传输对象中的数据。 RFX 检索到的数据，所需的特定站点，你需要用于访问基础数据的方法。

有关使用的详细信息`CByteArray`若要处理大数据项，请参阅[技术说明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。

##  <a name="_core_the_clongbinary_class"></a> CLongBinary 类

一个[CLongBinary](../../mfc/reference/clongbinary-class.md)对象是围绕一个简单 shell`HGLOBAL`句柄存储在堆上分配的块。 它将绑定包含二进制大型对象的表列，会分配 RFX`HGLOBAL`处理需要将数据传输到记录集和存储中的句柄时`CLongBinary`记录集的字段。

反过来，使用`HGLOBAL`处理， `m_hData`，可以使用数据本身，来在任何处理数据操作。 这就是[CByteArray](../../mfc/reference/cbytearray-class.md)添加功能。

> [!CAUTION]
>  CLongBinary 对象不能用作函数调用中的参数。 此外，其实现，它调用`::SQLGetData`，一定会降低可滚动的快照的滚动性能。 这也可能是 true 时使用`::SQLGetData`自行检索动态架构列调用。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：获取 SUM 及其他聚合结果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)