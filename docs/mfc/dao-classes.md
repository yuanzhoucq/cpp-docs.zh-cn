---
title: "DAO 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], 类"
  - "数据库类 [C++], DAO"
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DAO 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些类与其他应用程序框架类一起使用为便于访问数据访问对象 \(DAO\) \(DAO\) 数据库，使用数据库引擎和 Microsoft Visual Basic 和 Microsoft Access 相同。  DAO 类还访问开放式数据库连接 \(ODBC\) 的各种数据库驱动程序可用。  
  
 使用 DAO 数据库的程序将具有 `CDaoDatabase` 对象和至少一个 `CDaoRecordset` 对象。  
  
> [!NOTE]
>  从 Visual C\+\+ .NET 起，Visual C\+\+ 环境和向导不再支持 DAO（不过提供了 DAO 类，仍可供您使用）。  Microsoft 建议对新项目使用 ODBC或 MFC。  DAO 只应用于维护现有的应用程序。  
  
 [CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)  
 管理单个用户从登录到注销的已命名并受密码保护的数据库会话。  大多数程序使用默认工作区。  
  
 [CDaoDatabase](../mfc/reference/cdaodatabase-class.md)  
 表示与数据库的连接，通过此连接可操作数据。  
  
 [CDaoRecordset](../mfc/reference/cdaorecordset-class.md)  
 表示从数据源选择的一组记录。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 显示控件中数据库记录的视图。  
  
 [CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)  
 表示通常保存在数据库中的查询定义（即“querydef”）。  
  
 [CDaoTableDef](../mfc/reference/cdaotabledef-class.md)  
 表示基表或附加表的已存储定义。  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 表示由数据库类引起的异常条件。  
  
 [CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)  
 支持 DAO 数据库类使用的 DAO 记录字段交换 \(DFX\) 例程。  您通常不会直接使用该类。  
  
## 相关类  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 封装的句柄。一个二进制大对象 \(BLOB\) \(BLOB\) 的存储空间，如位图。  `CLongBinary` 对象用于管理数据库中表中存储大量数据对象。  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 OLE 自动化类型 **CURRENCY**的包装，使用定点算术类型，小数点前 15 位和 小数点后4 位。  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 OLE 自动化类型**DATE**的包装。  表示日期和时间值。  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 OLE 自动化类型**VARIANT**的包装。  在 **VARIANT**中可以存储多格式数据。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)