---
title: TN055： 将迁移到 MFC DAO 类 MFC ODBC 数据库类应用程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.odbc
dev_langs:
- C++
helpviewer_keywords:
- DAO [MFC], migration
- TN055
- migration [MFC], ODBC database applications
- ODBC classes [MFC], DAO classes
- migrating ODBC database applications [MFC]
- porting database applications to DAO
- ODBC [MFC], DAO
- porting ODBC database applications to DAO
- migrating database applications [MFC]
ms.assetid: 0f858bd1-e168-4e2e-bcd1-8debd82856e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa9c7870492fed78e65c3ac25f74726acf35b7eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055：将 MFC ODBC 数据库类应用程序迁移到 MFC DAO 类
> [!NOTE]
>  Visual c + + 环境和向导不支持 DAO （尽管 DAO 类包括并且仍可以使用它们）。 Microsoft 建议你使用[OLE DB 模板](../data/oledb/ole-db-templates.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)为新项目。 你只应在维护现有应用程序使用 DAO。  
  
 **概述**  
  
 在许多情况下，可能需要将使用 MFC 的 ODBC 数据库类的应用程序迁移到使用 MFC 的 DAO 数据库类。 此技术说明将详述 MFC ODBC 类和 DAO 类之间的大部分差异。 了解差异后，在需要时将应用程序从 ODBC 类迁移到 MFC 类应该不会太难。  
  
 **为什么从 ODBC 迁移到 DAO**  
  
 您为什么需要将应用程序从 ODBC 数据库类迁移到 DAO 数据库类的原因有很多，但决定必定不简单或显而易见。 要记住一件事情，DAO 使用的 Microsoft Jet 数据库引擎可读取您对其具有 ODBC 驱动程序的任何 ODBC 数据源。 使用 ODBC 数据库类或直接调用 ODBC 可能更有效，但 Microsoft Jet 数据库引擎可读取 ODBC 数据。  
  
 一些使 ODBC/DAO 决策变得很轻松的简单案例。 例如，当您只需要访问 Microsoft Jet 引擎可直接读取的格式（Access 格式、Excel 格式等）的数据时，最明显的选择是使用 DAO 数据库类。  
  
 当您的数据存在于服务器或各种不同的服务器上时，将出现更复杂的情况。 在这种情况下，很难决定使用 ODBC 数据库类还是 DAO 数据库类。 如果您需要执行如异类联接（联接多种格式（如 SQL Server 和 Oracle）的服务器中的数据）等操作，则在您使用 ODBC 数据库类或直接调用 ODBC 时，Microsoft Jet 数据库引擎将为您执行此联接，而不是强制您必需执行此操作。 如果您使用的是支持驱动程序光标的 ODBC 驱动程序，则最佳选择可能是 ODBC 数据库类。  
  
 此选择可能很复杂，因此鉴于你的特殊需求，你可能希望编写一些代码示例来测试各种方法的性能。 此技术说明假定您已决定从 ODBC 数据库类迁移到 DAO 数据库类。  
  
 **ODBC 数据库类与 MFC DAO 数据库类相似之处**  
  
 MFC ODBC 类的原始设计基于已在 Microsoft Access 和 Microsoft Visual Basic 中使用的 DAO 对象模型。 这意味着，ODBC 和 DAO MFC 类具有许多共同的功能，本节并未一一列出这些功能。 一般而言，编程模型是一样的。  
  
 重点介绍一些相似之处：  
  
-   ODBC 和 DAO 类具有使用基础数据库和管理系统 (DBMS) 管理的数据库对象。  
  
-   均具有表示从 DBMS 返回的结果集的记录集对象。  
  
-   DAO 数据库和记录集对象具有几乎与 ODBC 类相同的成员。  
  
-   对于这两组类，用于检索数据的代码除一些对象和成员名称更改外是相同的。 从 ODBC 类切换到 DAO 类时，需要更改，但此过程一般是直接的名称更改。  
  
 例如，在这两种模式中，检索数据的过程都是创建并打开一个数据库对象、创建并打开一个记录集对象，然后在执行某个操作时浏览（移动）数据。  
  
 **ODBC 和 DAO MFC 类之间的差异**  
  
 DAO 类包括更多对象和更丰富的方法集，但本节将仅详述相似类和功能之间的差异。  
  
 这两种类之间最明显的差异可能是相似类和全局函数的名称更改。 下面的列表显示与数据库类关联的对象、方法和全局函数的名称更改：  
  
|类或函数|MFC DAO 类中的等效项|  
|-----------------------|-----------------------------------|  
|`CDatabase`|`CDaoDatabase`|  
|`CDatabase::ExecuteSQL`|`CDaoDatabase::Execute`|  
|`CRecordset`|`CDaoRecordset`|  
|`CRecordset::GetDefaultConnect`|`CDaoRecordset::GetDefaultDBName`|  
|`CFieldExchange`|`CDaoFieldExchange`|  
|`RFX_Bool`|`DFX_Bool`|  
|`RFX_Byte`|`DFX_Byte`|  
|`RFX_Int`|`DFX_Short`|  
|`RFX_Long`|`DFX_Long`|  
||`DFX_Currency`|  
|`RFX_Single`|`DFX_Single`|  
|`RFX_Double`|`DFX_Double`|  
|**RFX_Date \***|**DFX_Date** (`COleDateTime`-基于)|  
|`RFX_Text`|`DFX_Text`|  
|`RFX_Binary`|`DFX_Binary`|  
|`RFX_LongBinary`|`DFX_LongBinary`|  
  
 \*    `RFX_Date`函数基于`CTime`和**TIMESTAMP_STRUCT**。  
  
 下面列出了对可能影响您的应用程序和需要多次简单名称更改的函数的主要更改。  
  
-   用于指定记录集开放类型和记录集开放选项等的常量和宏已更改。  
  
     对于 ODBC 类，MFC 需要通过宏或枚举类型定义这些选项。  
  
     对于 DAO 类，DAO 在标头文件 (DBDAOINT.H) 中提供了对这些选项的定义。 因此，记录集类型是 `CRecordset` 的枚举成员，但对于 DAO，此类型是一个常量。 例如，你将使用**快照**时指定的一种`CRecordset`ODBC 中但**DB_OPEN_SNAPSHOT**时指定的一种`CDaoRecordset`。  
  
-   默认记录集类型`CRecordset`是**快照**时的默认记录集类型`CDaoRecordset`是**动态集**（请参阅下面有关 ODBC 类快照的其他问题的说明）。  
  
-   ODBC `CRecordset` 类具有创建仅前移记录集类型的选项。 在 `CDaoRecordset` 类中，仅前移不是记录集类型，而是记录集特定类型的属性（或选项）。  
  
-   打开 `CRecordset` 对象时的仅追加记录集意味着记录集的数据可读取并追加。 对于 `CDaoRecordset` 对象，仅追加选项的字面意思是，记录集的数据只能追加（不能读取）。  
  
-   ODBC 类的事务成员函数是 `CDatabase` 的成员，充当数据库级别。 在 DAO 类中，事务成员函数是高级类 (`CDaoWorkspace`) 的成员，因此可能影响共享同一工作区（事务区）的多个 `CDaoDatabase` 对象。  
  
-   异常类已更改。 **CDBExceptions**在 ODBC 类中引发和**CDaoExceptions**在 DAO 类中。  
  
-   `RFX_Date` 使用`CTime`和**TIMESTAMP_STRUCT**对象，而**DFX_Date**使用`COleDateTime`。 `COleDateTime`几乎等同于`CTime`，但依赖于使用 8 字节 OLE**日期**而不是一个 4 字节`time_t`以便它可以存放多范围较大的数据。  
  
    > [!NOTE]
    >  DAO (`CDaoRecordset`) 快照为只读，而 ODBC (`CRecordset`) 快照是可根据驱动程序和 ODBC 光标库的使用进行更新的。 如果您使用的是光标库，则可更新 `CRecordset` 快照。 如果您使用的是 Desktop Driver Pack 3.0 中的任何 Microsoft 驱动程序，则 `CRecordset` 快照为只读。 如果你使用的另一个驱动程序，请检查驱动程序的文档，了解如果快照 (**STATIC_CURSORS**) 是只读的。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

