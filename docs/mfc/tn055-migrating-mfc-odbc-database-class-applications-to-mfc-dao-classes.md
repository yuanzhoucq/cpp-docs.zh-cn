---
title: "TN055：将 MFC ODBC 数据库类应用程序迁移到 MFC DAO 类 | Microsoft Docs"
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
  - "vc.mfc.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], 迁移"
  - "迁移数据库应用程序"
  - "迁移 ODBC 数据库应用程序"
  - "迁移 [C++], ODBC 数据库应用程序"
  - "ODBC [C++], DAO"
  - "ODBC 类 [C++], DAO 类"
  - "将数据库应用程序迁移到 DAO"
  - "将 ODBC 数据库应用程序迁移到 DAO"
  - "TN055"
ms.assetid: 0f858bd1-e168-4e2e-bcd1-8debd82856e4
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN055：将 MFC ODBC 数据库类应用程序迁移到 MFC DAO 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  从 Visual C\+\+ .NET 起，Visual C\+\+ 环境和向导不再支持 DAO（不过提供了 DAO 类，仍可供您使用）。  Microsoft 建议对新项目使用[OLE DB 模版](../data/oledb/ole-db-templates.md) 或 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)。  DAO 只应用于维护现有的应用程序。  
  
 **概述**  
  
 大多数情况下可能需要使用 MFC的 ODBC 数据库类移植应用程序到 MFC的DAO 数据库类。  此技术声明将详述 MFC ODBC 和 DAO 类之间的很多区别。  如有必要记住了差异，迁移应用程序从 ODBC 类到 MFC 类不会过于困难。  
  
 **为什么从 ODBC 迁移到 DAO?**  
  
 可能你有很多原因可能想迁移应用程序从 ODBC 数据库类到DAO数据库类 ，但决定不易或明显。  需要谨记的一点是 DAO 使用的 Microsoft Jet 数据库引擎可以读取您具有 ODBC 驱动程序的任何 ODBC 数据源。  可能更为高效地使用 ODBC 数据库类或直接调用 ODBC，但 Microsoft Jet 数据库引擎可以读取 ODBC 数据。  
  
 一些简单的情况使做出 ODBC\/DAO决策更容易。  例如，当你仅需要访问 Microsoft Jet 引擎可以直接读取的格式时\(访问格式，Excel 格式，依此类推\)可以使用 DAO 数据库类。  
  
 当数据存储在服务器上或位于各种不同的服务器上，将出现更复杂的情况。  在这种情况下，很难决定是使用 ODBC 数据库类 或是DAO 数据库类。  如果想要异类联接 \(异类从服务器联接数据，如 SQL Server 和 Oracle 的多格式\)，则 Microsoft Jet 数据库引擎将为您执行联接而不是强制您需要完成的工作是否使用了 ODBC 数据库类或直接调用 ODBC。  如果使用支持驱动游标的 ODBC 驱动程序，可能最佳选择是用 ODBC 数据库类。  
  
 选项可以是复杂的，因此，您可能希望编写一些示例代码以测试特定需求的各种方法性能。  此技术说明假设你将ODBC 数据库类迁移到 DAO 数据库类。  
  
 **在 ODBC 数据库类和 MFC DAO 数据库类之间存在相似性**  
  
 MFC ODBC 类的原始设计基于正在使用中的 Microsoft Access 和 Microsoft Visual Basic 中的 DAO 对象模型。  这意味着具有 ODBC 和 MFC DAO 类的许多常用功能，本节不会列出。  通常，编程模型是相同的。  
  
 突出显示一些相似：  
  
-   ODBC 和 DAO 类具有管理使用基础数据库管理系统 \(DBMS\)的数据库对象。  
  
-   都具有一组表示结果的记录集对象返回该 DBMS。  
  
-   DAO 数据库和记录对象具有与ODBC 类几近相同的成员。  
  
-   两组类，用于检索数据的代码是相同的 ，除了这些名称更改了的对象和成员。  需要更改，但当从ODBC类切换到DAO类时，通常过程是直接更改名称。  
  
 例如，在两模型检索数据的过程是打开和创建数据库对象，创建并打开记录集对象以及导航 \(移动\) 数据执行某些操作。  
  
 **ODBC类与DAO MFC类之间的差异**  
  
 DAO 类包含一个或多个对象和更丰富的方法集，但是，本节将只提供在类似的类和功能上的区别。  
  
 可能类之间最明显的差异是类似的类和全局函数的名称更改。  下面的列表演示数据库类的对象、方法和全局函数的名称更改：  
  
|类或函数。|在 MFC DAO 类的等效项|  
|-----------|---------------------|  
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
|**RFX\_Date \***|**DFX\_Date** \(基于`COleDateTime`\)|  
|`RFX_Text`|`DFX_Text`|  
|`RFX_Binary`|`DFX_Binary`|  
|`RFX_LongBinary`|`DFX_LongBinary`|  
  
 \* `RFX_Date`函数 基于 `CTime` 和 **TIMESTAMP\_STRUCT**。  
  
 主要的功能更改可能会影响应用程序，这需要不止是更改名称，如下列出。  
  
-   更改用于指定记录打开类型和选项的常数和宏。  
  
     ODBC 类的 MFC 需要通过宏或者枚举类型定义这些选项。  
  
     DAO 类，DAO 提供头文件 \(DBDAOINT.H\)中这些选项的定义。  从而记录集类型为 `CRecordset`的枚举成员，但是 DAO使用的是常数。  例如当在ODBC中指定 `CRecordset` 类型时应使用 **快照**，但当指定 `CDaoRecordset`类型时应使用 **DB\_OPEN\_SNAPSHOT** 。  
  
-   `CRecordset` 记录集的默认类型为 **快照**，而 `CDaoRecordset` 的默认记录集类型为 **dynaset** \(有关 ODBC 类快照的其他问题，请参见下面的说明\)。  
  
-   ODBC `CRecordset` 类具有创建仅向前记录集类型的选项。  在 `CDaoRecordset`类中，仅转接不是记录集类型，而是 特定记录集类型的属性\(或选项\)。  
  
-   当打开 `CRecordset` 对象时，仅追加的记录集表示记录集的数据可能读取并追加。  `CDaoRecordset` 对象，仅追加选项按原义表示记录集的数据只能附加 \(而不是读取\)。  
  
-   ODBC 类的成员函数为 `CDatabase` 的成员，并在数据库级别执行。  在 MFC DAO 类中，事务成员函数是更高级别类\(`CDaoWorkspace`\)成员，因此这可能影响许多`CDaoDatabase` 对象共享相同的工作区 \(事务空间\)。  
  
-   异常类更改。  在 ODBC类中抛出**CDBExceptions** ，在DAO 类中抛出 **CDaoExceptions** 。  
  
-   当 **DFX\_Date** 使用 `COleDateTime`时，`RFX_Date` 使用 `CTime` 和 **TIMESTAMP\_STRUCT** 对象。  `COleDateTime` 与`CTime`是基本相同的，但是这是基于 OLE 8 字节的 **DATE** 而不是4 字节 `time_t`，以便它可以保存较大的范围数据。  
  
    > [!NOTE]
    >  DAO \(`CDaoRecordset`\) 快照是只读的，当 ODBC \(`CRecordset`\) 更新快照是根据 ODBC 游标库的驱动程序和使用。  如果您确实在使用游标库，`CRecordset` 可更新快照。  如果您使用以下任一从台式机驱动程序包 3.0 的 Microsoft 驱动程序，而不用 ODBC 游标库，`CRecordset` 快照是只读的。  如果您使用其他驱动程序，请检查驱动程序的文档，查看快照 \(**STATIC\_CURSORS**\) 是否为只读。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)