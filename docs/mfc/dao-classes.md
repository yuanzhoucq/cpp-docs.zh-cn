---
title: DAO 类
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 51abd29ef4de5d70f4a5b2b6b14b53510e7876a1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615932"
---
# <a name="dao-classes"></a>DAO 类

DAO 与 Access 数据库结合使用，并受 Office 2013 的支持。 DAO 3.6 是最终版本，被视为已过时。

这些类与其他应用程序框架类结合使用，以便轻松访问数据访问对象（DAO）数据库，该数据库使用与 Microsoft Visual Basic 和 Microsoft Access 相同的数据库引擎。 DAO 类还可以访问各种数据库，这些数据库提供开放式数据库连接（ODBC）驱动程序。

使用 DAO 数据库的程序将至少具有一个 `CDaoDatabase` 对象和一个 `CDaoRecordset` 对象。

> [!NOTE]
> Visual C++ 环境和向导不再支持 DAO （尽管包含 DAO 类，但仍可以使用）。 Microsoft 建议对新的 MFC 项目使用 ODBC。 只应在维护现有应用程序时使用 DAO。

[CDaoWorkspace](reference/cdaoworkspace-class.md)<br/>
管理登录到注销的已命名、受密码保护的数据库会话。 大多数程序都使用默认工作区。

[CDaoDatabase](reference/cdaodatabase-class.md)<br/>
与数据库的连接，通过它可以对数据进行操作。

[CDaoRecordset](reference/cdaorecordset-class.md)<br/>
表示从数据源选择的一组记录。

[CDaoRecordView](reference/cdaorecordview-class.md)<br/>
显示控件中数据库记录的视图。

[CDaoQueryDef](reference/cdaoquerydef-class.md)<br/>
表示通常保存在数据库中的查询定义。

[CDaoTableDef](reference/cdaotabledef-class.md)<br/>
表示基表或附加表的已存储定义。

[CDaoException](reference/cdaoexception-class.md)<br/>
表示由 DAO 类引起的异常条件。

[CDaoFieldExchange](reference/cdaofieldexchange-class.md)<br/>
支持 DAO 数据库类使用的 DAO 记录字段交换 (DFX) 例程。 通常不会直接使用此类。

## <a name="related-classes"></a>相关类

[CLongBinary](reference/clongbinary-class.md)<br/>
封装二进制大型对象（BLOB）（如位图）的存储句柄。 `CLongBinary`对象用于管理存储在数据库表中的大型数据对象。

[COleCurrency](reference/colecurrency-class.md)<br/>
OLE 自动化类型**货币**的包装，一个固定点算术类型，小数点前有15个数字，后接四位数字。

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE 自动化类型**日期**的包装。 表示日期和时间值。

[COleVariant](reference/colevariant-class.md)<br/>
OLE 自动化类型**变量**的包装。 **变体**中的数据可存储为多种格式。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
