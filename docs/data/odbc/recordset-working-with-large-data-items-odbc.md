---
title: "记录集： 处理大数据项 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bf82e1fabd45e9bccd63e4ba46068b75d2c2a0a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-working-with-large-data-items-odbc"></a>记录集：处理大数据项 (ODBC)
本主题适用于 MFC ODBC 类和 MFC DAO 类。  
  
> [!NOTE]
>  如果你正在使用 MFC DAO 类，管理大型数据项与类[CByteArray](../../mfc/reference/cbytearray-class.md)而不是类[CLongBinary](../../mfc/reference/clongbinary-class.md)。 如果将 MFC ODBC 类用于批量行提取，使用`CLongBinary`而非`CByteArray`。 有关批量行提取的详细信息，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 假设你的数据库可以存储大片的数据，例如位图 （员工的照片、 映射或图片的产品、 OLE 对象等）。 此类数据通常称为二进制大型对象 （或 BLOB） 因为：  
  
-   每个字段值很大。  
  
-   与不同数字和其他简单数据类型，它具有大小不可预知。  
  
-   数据为从你的程序的角度不定型数据。  
  
 本主题介绍了哪些数据库类提供用于处理此类对象的支持。  
  
##  <a name="_core_managing_large_objects"></a>管理大型对象  
 记录集有两个方法来解决管理二进制大型对象的特殊的难度。 你可以使用类[CByteArray](../../mfc/reference/cbytearray-class.md)或者你可以使用类[CLongBinary](../../mfc/reference/clongbinary-class.md)。 一般情况下，`CByteArray`是首选的方法来管理大型二进制数据。  
  
 `CByteArray`需要更多的开销比`CLongBinary`但功能更强大中, 所述[CByteArray 类](#_core_the_cbytearray_class)。 `CLongBinary`简要中所述[CLongBinary 类](#_core_the_clongbinary_class)。  
  
 有关使用的详细信息`CByteArray`若要使用的大型数据项，请参阅[技术说明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。  
  
##  <a name="_core_the_cbytearray_class"></a>CByteArray 类  
 `CByteArray`是 MFC 集合类之一。 A`CByteArray`对象存储为动态的字节数组-数组可以根据需要进行扩展。 此类与内置 c + + 数组的索引，提供快速访问。 `CByteArray`对象可以序列化和转储以进行诊断。 类提供用于获取和设置指定的字节、 插入和追加字节，和删除 1 个字节或所有字节的成员函数。 这些功能使得分析更轻松的二进制数据。 例如，如果二进制对象是一个 OLE 对象，你可能需要完成某些头字节才能访问实际对象。  
  
##  <a name="_core_using_cbytearray_in_recordsets"></a>在记录集中使用 CByteArray  
 通过为记录集中的字段数据成员提供类型`CByteArray`，提供从中固定的基[RFX](../../data/odbc/record-field-exchange-rfx.md)可以管理此类对象的传输，记录集和数据源之间而通过你可以操作在对象内的数据。 RFX 需要特定的站点检索到的数据，并且需要用于访问基础数据的方法。  
  
 有关使用的详细信息`CByteArray`若要使用的大型数据项，请参阅[技术说明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。  
  
##  <a name="_core_the_clongbinary_class"></a>CLongBinary 类  
 A [CLongBinary](../../mfc/reference/clongbinary-class.md)对象是围绕简单 shell`HGLOBAL`的堆上分配的存储块的句柄。 当它绑定包含二进制大型对象的表列时，RFX 将其分配`HGLOBAL`处理时它需要将数据传输到记录集并存储中的句柄`CLongBinary`记录集的字段。  
  
 反过来，使用`HGLOBAL`处理， `m_hData`，以便使用数据本身，方式上任何处理数据操作等。 这就是[CByteArray](../../mfc/reference/cbytearray-class.md)添加功能。  
  
> [!CAUTION]
>  CLongBinary 对象不能作为函数调用中的参数。 此外，其实现，它可以调用**:: SQLGetData**、 一定会降低可滚动快照滚动性能。 这也可能是 true 当你使用**:: SQLGetData**自行检索动态架构列调用。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 获取 Sum 及其他聚合结果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)