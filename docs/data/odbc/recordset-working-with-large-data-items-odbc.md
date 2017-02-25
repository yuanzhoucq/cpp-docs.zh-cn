---
title: "记录集：处理大数据项 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "二进制大对象"
  - "BLOB（二进制大对象）, 记录集"
  - "CLongBinary 类, 在记录集中使用"
  - "ODBC 记录集, 二进制大对象"
  - "记录集, 二进制大对象"
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 记录集：处理大数据项 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文既适用于 MFC ODBC 类也适用于 MFC DAO 类。  
  
> [!NOTE]
>  如果使用的是 MFC DAO 类，则用 [CByteArray](../../mfc/reference/cbytearray-class.md) 类而不是 [CLongBinary](../../mfc/reference/clongbinary-class.md) 类来管理大数据项。  如果使用的是 MFC ODBC 类进行批量取行，则使用 `CLongBinary` 而非 `CByteArray`。  有关批量取行的更多信息，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 假设您的数据库可以存储大数据块，如位图（雇员照片、地图、产品图片、OLE 对象等）。  这种类型的数据通常称为二进制大对象（或 BLOB），因为：  
  
-   每个字段值都很大。  
  
-   与数字或其他简单的数据类型不同，其大小不可预知。  
  
-   从程序角度来看，此类数据为不定型数据。  
  
 本文解释数据库类为处理此类对象提供哪些支持。  
  
##  <a name="_core_managing_large_objects"></a> 管理大对象  
 记录集可通过两种方式解决管理二进制大对象时遇到的特殊困难。  可使用 [CByteArray](../../mfc/reference/cbytearray-class.md) 类 [CLongBinary](../../mfc/reference/clongbinary-class.md) 类。  通常，`CByteArray` 是管理大二进制数据的首选方法。  
  
 `CByteArray` 比 `CLongBinary` 需要更多的系统开销但是功能更强，如 [CByteArray 类](#_core_the_cbytearray_class)中描述的。  `CLongBinary` 在 [CLongBinary 类](#_core_the_clongbinary_class)中有简要描述。  
  
 有关使用 `CByteArray` 处理大数据项的详细信息，请参见[技术说明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。  
  
##  <a name="_core_the_cbytearray_class"></a> CByteArray 类  
 `CByteArray` 是 MFC 集合类中的一员。  `CByteArray` 对象存储字节的动态数组（该数组可根据需要进行扩展）。  该类提供快速索引访问，就像内置 C\+\+ 数组一样。  `CByteArray` 对象可以序列化并转储以用于诊断目的。  该类提供了用于获取与设置指定字节、插入与追加字节以及移除一个或所有字节的成员函数。  这些功能使得分析二进制数据更为容易。  例如，如果二进制对象为 OLE 对象，则可能必须处理完某些头字节才能到达实际的对象。  
  
##  <a name="_core_using_cbytearray_in_recordsets"></a> 在记录集中使用 CByteArray  
 将 `CByteArray` 类型给予记录集中的字段数据成员，便提供了一个固定基，[RFX](../../data/odbc/record-field-exchange-rfx.md) 可通过该固定基在记录集与数据源之间管理这类对象的传输，而您可通过该固定基处理此对象中的数据。  RFX 需要为检索到的数据准备一个特定的站点，而您则需要一种可以访问基础数据的方法。  
  
 有关使用 `CByteArray` 处理大数据项的详细信息，请参见[技术说明 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。  
  
##  <a name="_core_the_clongbinary_class"></a> CLongBinary 类  
 [CLongBinary](../../mfc/reference/clongbinary-class.md) 对象相对于分配在堆上的存储块来讲是 `HGLOBAL` 句柄周围的一个简单 shell。  该对象绑定一个包含二进制大对象的表列后，RFX 在需要将数据传输到记录集时分配 `HGLOBAL` 句柄，并将该句柄存储在记录集的 `CLongBinary` 字段中。  
  
 反过来，您使用 `HGLOBAL` 句柄 \(`m_hData`\) 处理数据本身，就像操作任何句柄数据那样操作该数据。  这便是 [CByteArray](../../mfc/reference/cbytearray-class.md) 添加的功能。  
  
> [!CAUTION]
>  CLongBinary 对象不能用作函数调用中的参数。  此外，这些对象的实现（调用 **::SQLGetData**）必然会降低可滚动快照的滚动性能。  当您自己使用 **::SQLGetData** 调用来检索动态架构列时，这种情况也可能出现。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：获取 SUM 及其他聚合结果 \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [记录字段交换 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)