---
title: DAO 类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: cce9831cb317b468bfc51777eedbde261e798108
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538937"
---
# <a name="dao-classes"></a>DAO 类

这些类别的工作与其他应用程序框架类要让数据访问对象 (DAO) 数据库，作为 Microsoft Visual Basic 和 Microsoft Access 中使用相同的数据库引擎能够轻松访问。 DAO 类还可以访问各种数据库的开放式数据库连接 (ODBC) 驱动程序为可用。

使用 DAO 数据库的程序将具有最少`CDaoDatabase`对象和一个`CDaoRecordset`对象。

> [!NOTE]
>  Visual c + + 环境和向导不再支持 DAO （尽管 DAO 类包含并且仍可以使用它们）。 Microsoft 建议为新 MFC 项目使用 ODBC。 仅应在维护现有应用程序使用 DAO。

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
从登录名的名称时，受密码保护的数据库会话管理以注销。 大多数程序使用默认工作区。

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
与通过它您可以对数据进行操作的数据库的连接。

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
表示从数据源选择的一组记录。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
显示控件中数据库记录的视图。

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
表示一个查询定义，通常一个保存在数据库中。

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
表示基表或附加表的已存储定义。

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
表示从 DAO 类引起的异常条件。

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
支持 DAO 数据库类使用的 DAO 记录字段交换 (DFX) 例程。 一般情况下不会直接使用此类。

## <a name="related-classes"></a>相关的类

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
封装如位图的句柄存储二进制大型对象 (BLOB)。 `CLongBinary` 对象用于管理存储在数据库表中的大型数据对象。

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
OLE 自动化类型的包装器**货币**，定点算数类型，小数点前的 15 个数字和后的 4 位数字。

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE 自动化类型的包装器**日期**。 表示日期和时间值。

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
OLE 自动化类型的包装器**变体**。 中的数据**变体**s 可以多种格式存储。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

