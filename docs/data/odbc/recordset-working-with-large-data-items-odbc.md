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
ms.openlocfilehash: 872fa7229738314b86b6ae6c0d5dc5a5562b27f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360605"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>记录集：处理大数据项 (ODBC)

本主题适用于 MFC ODBC 类和 MFC DAO 类。

> [!NOTE]
> 如果使用 MFC DAO 类，请使用类[CByteArray](../../mfc/reference/cbytearray-class.md)而不是[CLongBinary](../../mfc/reference/clongbinary-class.md)管理大型数据项。 如果使用具有批量行提取的 MFC ODBC 类，请使用`CLongBinary`而不是`CByteArray`。 有关批量行提取的详细信息，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

假设您的数据库可以存储大量数据，如位图（员工照片、地图、产品图片、OLE 对象等）。 此类数据通常称为二进制大对象（或 BLOB），因为：

- 每个字段值都很大。

- 与数字和其他简单数据类型不同，它没有可预测的大小。

- 从程序的角度来看，数据是无成形的。

本主题介绍数据库类为处理此类对象提供哪些支持。

## <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>管理大型对象

记录集有两种方法可以解决管理二进制大型对象的特殊困难。 您可以使用类[CByteArray，](../../mfc/reference/cbytearray-class.md)也可以使用[CLongBinary](../../mfc/reference/clongbinary-class.md)类 。 通常，`CByteArray`是管理大型二进制数据的首选方法。

`CByteArray`所需的开销比`CLongBinary`但更有能力，如[CByteArray 类](#_core_the_cbytearray_class)中所述。 `CLongBinary`在[CLongBinary类](#_core_the_clongbinary_class)中简要描述。

有关使用`CByteArray`大型数据项的详细信息，请参阅[技术说明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。

## <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>C字节类

`CByteArray`是 MFC 集合类之一。 `CByteArray`对象存储字节的动态数组 - 如果需要，数组可以增长。 类提供按索引快速访问，与内置C++数组一样。 `CByteArray`出于诊断目的，可以序列化并转储对象。 类提供成员函数，用于获取和设置指定的字节、插入和追加字节以及删除一个字节或所有字节。 这些功能使分析二进制数据更容易。 例如，如果二进制对象是 OLE 对象，则可能需要处理某些标头字节才能到达实际对象。

## <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>在记录集中使用 CByteArray

通过为记录集的字段数据成员提供类型`CByteArray`，可以提供固定的基[，RFX](../../data/odbc/record-field-exchange-rfx.md)可以从中管理记录集和数据源之间的此类对象的传输，并通过该库操作对象内的数据。 RFX 需要一个用于检索数据的特定站点，并且您需要一种方法来访问基础数据。

有关使用`CByteArray`大型数据项的详细信息，请参阅[技术说明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。

## <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>CLongBinary 类

[CLongBinary](../../mfc/reference/clongbinary-class.md)对象是围绕`HGLOBAL`句柄对堆上分配的存储块的简单外壳。 当它绑定包含二进制大型对象的表列时，RFX 在需要将数据传输到`HGLOBAL`记录集并将句柄存储在记录集`CLongBinary`的字段中时分配句柄。

反过来，使用`HGLOBAL`句柄`m_hData`， 处理数据本身， 操作它，就像对任何句柄数据一样. 这是[CByteArray](../../mfc/reference/cbytearray-class.md)添加功能的位置。

> [!CAUTION]
> CLongBinary 对象不能用作函数调用中的参数。 此外，它们的实现（调用`::SQLGetData`）必然会降低可滚动快照的滚动性能。 当您使用`::SQLGetData`自己调用来检索动态架构列时，情况可能也是如此。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：获取 SUM 及其他聚合结果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)
