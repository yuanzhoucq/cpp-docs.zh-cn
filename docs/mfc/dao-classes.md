---
title: DAO 类
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 7ae85cbeb7790cadb8c26dfbdb7a5163dbcd47c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373514"
---
# <a name="dao-classes"></a>DAO 类

DAO 与 Access 数据库一起使用，并通过 Office 2013 支持。 DAO 3.6 是最终版本，它被视为过时版本。

这些类与其他应用程序框架类配合使用，以便轻松访问数据访问对象 （DAO） 数据库，这些数据库使用与 Microsoft Visual Basic 和 Microsoft Access 相同的数据库引擎。 DAO 类还可以访问开放数据库连接 （ODBC） 驱动程序可用的各种数据库。

使用 DAO 数据库的程序将至少具有一`CDaoDatabase`个对象和`CDaoRecordset`一个对象。

> [!NOTE]
> 可视化C++环境和向导不再支持 DAO（尽管包含 DAO 类，您仍可以使用它们）。 Microsoft 建议您将 ODBC 用于新的 MFC 项目。 您只应在维护现有应用程序时使用 DAO。

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
从登录到注销管理受密码保护的命名数据库会话。 大多数程序使用默认工作区。

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
到数据库的连接，通过该数据库可以对数据进行操作。

[CDao记录集](../mfc/reference/cdaorecordset-class.md)<br/>
表示从数据源选择的一组记录。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
显示控件中数据库记录的视图。

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
表示查询定义，通常保存在数据库中。

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
表示基表或附加表的已存储定义。

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
表示 DAO 类产生的异常条件。

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
支持 DAO 数据库类使用的 DAO 记录字段交换 (DFX) 例程。 您通常不会直接使用此类。

## <a name="related-classes"></a>相关类

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
封装二进制大型对象 （BLOB） 的存储句柄，如位图。 `CLongBinary`对象用于管理存储在数据库表中的大型数据对象。

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
OLE 自动化类型**货币**的包装器，一种定点算术类型，在小数点之前有 15 位数字，后为 4 位。

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE 自动化类型**DATE**的包装器 。 表示日期和时间值。

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
OLE 自动化类型**VARIANT**的包装器 。 **VARIANT**中的数据可以以多种格式存储。

## <a name="see-also"></a>另请参阅

[类概述](../mfc/class-library-overview.md)
