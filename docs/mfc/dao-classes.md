---
title: "DAO 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c80351071318b88956fa3717875561bdf30232dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dao-classes"></a>DAO 类
这些类可与其他应用程序框架类以便轻松访问使用相同的数据库引擎作为 Microsoft Visual Basic 和 Microsoft Access 的数据访问对象 (DAO) 数据库。 DAO 类还可以访问各种数据库为其开放式数据库连接 (ODBC) 驱动程序都可用。  
  
 使用 DAO 数据库的程序将至少具有一个`CDaoDatabase`对象和一个`CDaoRecordset`对象。  
  
> [!NOTE]
>  Visual c + + 环境和向导不再支持 DAO （尽管 DAO 类包括并且仍可以使用它们）。 Microsoft 建议你为新 MFC 项目使用 ODBC。 你只应在维护现有应用程序使用 DAO。  
  
 [CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)  
 管理从登录到注销的已命名并受密码保护数据库会话。 大多数程序使用默认工作区。  
  
 [CDaoDatabase](../mfc/reference/cdaodatabase-class.md)  
 与通过其可操作数据的数据库的连接。  
  
 [CDaoRecordset](../mfc/reference/cdaorecordset-class.md)  
 表示从数据源选择的一组记录。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 显示控件中数据库记录的视图。  
  
 [CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)  
 表示一个查询定义，通常一个保存在数据库中。  
  
 [CDaoTableDef](../mfc/reference/cdaotabledef-class.md)  
 表示基表或附加表的已存储定义。  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 表示由 DAO 类引起的异常条件。  
  
 [CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)  
 支持 DAO 数据库类使用的 DAO 记录字段交换 (DFX) 例程。 你通常不将直接使用此类。  
  
## <a name="related-classes"></a>相关的类  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 如位图封装为二进制大型对象 (BLOB) 存储的句柄。 `CLongBinary`对象用于管理存储在数据库表中的大型数据对象。  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 OLE 自动化类型的包装**货币**，定点算数类型，有 15 位，小数点前的小数点后的有 4 位。  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 OLE 自动化类型的包装**日期**。 表示日期和时间值。  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 OLE 自动化类型的包装**VARIANT**。 中的数据**VARIANT**可用多种格式存储。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

