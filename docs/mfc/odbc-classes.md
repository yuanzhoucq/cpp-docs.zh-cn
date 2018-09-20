---
title: ODBC 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97bbdb74d122e633574dcf76876f0907de8ef2c4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400571"
---
# <a name="odbc-classes"></a>ODBC 类

这些类适用于应用程序框架的其他类以让各种的开放式数据库连接 (ODBC) 驱动程序为可用的数据库能够轻松访问。

使用 ODBC 数据库的程序将具有最少`CDatabase`对象和一个`CRecordset`对象。

[CDatabase](../mfc/reference/cdatabase-class.md)<br/>
封装与数据源，通过它可操作数据源的连接。

[CRecordset](../mfc/reference/crecordset-class.md)<br/>
封装一组从数据源中选择的记录。 记录集启用滚动记录到记录、 更新记录 （添加、 编辑和删除记录）、 使用筛选器，限定所选内容进行排序所选内容，并参数化的信息与所选内容中获取，或运行时计算的。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
提供了一种直接连接到记录集对象的视图。 对话框数据交换 (DDX) 记录集和记录视图的控件之间的机制交换数据。 所有窗体视图中，如记录视图基于对话框模板资源。 记录视图还支持在记录集中移动记录，更新的记录，以及记录视图关闭时关闭关联的记录集。

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
导致从数据访问中的故障处理的异常。 此类中的类库的异常处理机制提供其他的异常类相同的目的。

[CFieldExchange](../mfc/reference/cfieldexchange-class.md)<br/>
提供上下文信息，以支持记录字段交换 (RFX) 的字段数据成员和参数数据成员的记录集对象和数据源上相应的表列之间交换数据。 类似于类[CDataExchange](../mfc/reference/cdataexchange-class.md)，它同样用于对话框数据交换 (DDX)。

## <a name="related-classes"></a>相关的类

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
封装如位图的句柄存储二进制大型对象 (BLOB)。 `CLongBinary` 对象用于管理存储在数据库表中的大型数据对象。

[CDBVariant](../mfc/reference/cdbvariant-class.md)<br/>
可以用来存储值，而无需担心值的数据类型。 `CDBVariant` 跟踪存储在联合中的当前值的数据类型。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

