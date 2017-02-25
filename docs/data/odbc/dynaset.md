---
title: "动态集 | Microsoft Docs"
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
  - "游标库 [ODBC], 动态集可用性"
  - "游标 [ODBC], 动态集中键集驱动的游标"
  - "动态集"
  - "动态集中键集驱动的游标"
  - "ODBC 游标库 [ODBC], 动态集"
  - "ODBC 记录集, 动态集"
  - "记录集 [C++], 动态集"
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 动态集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题介绍动态集，并讨论它们的[可用性](#_core_availability_of_dynasets)。  
  
> [!NOTE]
>  本主题适用于 MFC ODBC 类，包括 [CRecordset](../../mfc/reference/crecordset-class.md)。  有关 DAO 类中动态集的信息，请参见 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  用 DAO 可以打开动态集类型记录集。  
  
 动态集是具有动态属性的记录集。  在其生存期期间，动态集模式的记录集对象（通常称为动态集）以下列方式与数据源保持同步。  在多用户环境中，其他用户能够编辑或删除您的动态集中的记录，或者向您的动态集表示的表中添加记录。  应用程序向记录集添加的记录或者从中删除的记录将反映在您的动态集中。  其他用户向表中添加的记录直到您调用其 **Requery** 成员函数重建动态集时才在您的动态集中反映出来。  其他用户删除记录时，MFC 代码在您的记录集中跳过删除的记录。  其他用户对现有记录做的编辑改动将在您滚动到受影响的记录时在动态集中反映出来。  
  
 与此类似，您对动态集中的记录所做的编辑也会在其他用户使用的动态集中反映出来。  在其他用户再次查询他们的动态集之前，您添加的记录不会在他们的动态集中反映出来。  您删除的记录在其他用户的记录集中被标记为“已删除”。  如果到同一数据库有多个连接（多个 `CDatabase` 对象），与这些连接相关的记录集的状态与其他用户的记录集相同。  
  
 当数据必须是动态的时候（如在航空订票系统中），动态集非常有用。  
  
> [!NOTE]
>  若要使用动态集，必须具有支持动态集的数据源的 ODBC 驱动程序，并且决不能加载 ODBC 游标库。  有关更多信息，请参见[动态集可用性](#_core_availability_of_dynasets)。  
  
 若要指定某记录集是动态集，请将 **CRecordset::dynaset** 作为第一个参数传递给记录集对象的 **Open** 成员函数。  
  
> [!NOTE]
>  对于可更新动态集，ODBC 驱动程序必须支持定位更新语句或 **::SQLSetPos** ODBC API 函数。  如果这两个都支持，则 MFC 使用 **::SQLSetPos** 函数以提高效率。  
  
##  <a name="_core_availability_of_dynasets"></a> 动态集的可用性  
 如果满足下类条件，MFC 数据库类则支持动态集：  
  
-   对于该数据源，一定不要使用 ODBC 游标库 DLL。  
  
     如果使用了游标库，它则会屏蔽动态集支持所必需的基础 ODBC 驱动程序的一些功能。  如果您要使用动态集（并且您的 ODBC 驱动程序具备动态集所需功能，如本节中其他部分描述的功能），则可以使 MFC 在您创建 `CDatabase` 对象时不加载游标库。  有关更多信息，请参见 [ODBC](../../data/odbc/odbc-basics.md) 和类 `CDatabase` 的 [OpenEx](../Topic/CDatabase::OpenEx.md) 或 [Open](../Topic/CDatabase::Open.md) 成员函数。  
  
     在 ODBC 术语中，动态集和快照都称为“游标”。  游标是用于在记录集中跟踪其位置的一种机制。  
  
-   数据源的 ODBC 驱动程序必须支持键集驱动游标。  
  
     键集驱动游标通过获取和存储键集的方法管理表数据。  用户滚动到某一特定记录时，将使用这些键获得表中的当前数据。  若要确定您的驱动程序是否提供这种支持，请用 **SQL\_SCROLL\_OPTIONS** 参数调用 **::SQLGetInfo** ODBC API 函数。  
  
     若要在没有键集支持时尝试打开动态集，您会得到一个返回代码值为 **AFX\_SQL\_ERROR\_DYNASET\_NOT\_SUPPORTED** 的 `CDBException`。  
  
-   您的数据源的 ODBC 驱动程序必须支持扩展获取。  
  
     “扩展获取”是在 SQL 查询结果记录中后滚和前滚的能力。  若要确定您的驱动程序是否支持这种能力，请用 **SQL\_API\_SQLEXTENDEDFETCH** 参数调用 **::SQLGetFunctions** ODBC API 函数。  
  
 假如您想有可更新动态集（或快照），您的 ODBC 驱动程序也必须支持 **::SQLSetPos** ODBC API 函数或定位更新。  **::SQLSetPos** 函数使 MFC 不用发送 SQL 语句就能更新数据源。  有了该项支持，MFC 就用该函数进行更新，而不再通过 SQL 进行更新。  若要确定您的驱动程序是否支持 **::SQLSetPos**，请用 **SQL\_POS\_OPERATIONS** 参数调用 **::SQLGetInfo**。  
  
 定位更新使用 SQL 语法（格式为 **WHERE CURRENT OF** \<游标名\>）识别数据源上表中的特定行。  若要确定您的驱动程序是否支持定位更新，请用 **SQL\_POSITIONED\_STATEMENTS** 参数调用 **::SQLGetInfo**。  
  
 通常，MFC 动态集（不是仅向前记录集）要求具有 2 级 API 一致性的 ODBC 驱动程序。  如果您的数据源驱动程序符合 1 级 API 集，则仍能使用可更新和只读的快照以及仅向前记录集，但不能使用动态集。  但是，如果 1 级驱动程序支持扩展获取和键集驱动游标，它就能支持动态集。  有关 ODBC 一致性级别的更多信息，请参见 [ODBC](../../data/odbc/odbc-basics.md)。  
  
> [!NOTE]
>  如果要同时使用快照和动态集，必须将它们建立在两个不同的 `CDatabase` 对象上（两个不同的连接）。  
  
 与快照不同，快照使用 ODBC 游标库维护的中间存储，而动态集在您一滚动到记录上时就直接从数据源获取该记录。  这保证了动态集原来所选的记录与数据源保持同步。  
  
 有关 Visual C\+\+ 此版本中包括的 ODBC 驱动程序列表以及有关获取其他驱动程序的信息，请参见 [ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。  
  
## 请参阅  
 [开放式数据库连接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)