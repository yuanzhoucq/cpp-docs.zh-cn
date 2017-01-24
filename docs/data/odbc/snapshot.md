---
title: "快照 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "游标库 [ODBC], 快照"
  - "游标 [ODBC], static"
  - "ODBC 游标库 [ODBC], 快照"
  - "ODBC 记录集, 快照"
  - "记录集, 快照"
  - "快照"
  - "快照, ODBC 中的支持"
  - "静态游标"
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 快照
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

快照是反映数据在快照创建时的静态视图的记录集。  当您打开快照并移动到所有记录时，直到您调用 **Requery** 重新生成快照后，快照所包含的记录集和记录的值才会更改。  
  
> [!NOTE]
>  本主题适用于 MFC ODBC 类。  如果您使用的是 MFC DAO 类，而不是 MFC ODBC 类，那么有关快照型记录集的说明，请参见 [CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md)。  
  
 可以用数据库类创建可更新或只读快照。  与动态集不同，可更新快照不反映其他用户对记录值所做的更改，但反映您的程序所做的更新和删除。  在您调用 **Requery** 之前，添加到快照中的记录对该对快照不会是可见的。  
  
> [!TIP]
>  快照是一个 ODBC 静态游标。  在滚动到某个记录之前，静态游标并不真正获取一行数据。  为确保立即检索所有记录，可以滚动到记录集末尾，然后滚动到要查看的第一个记录。  但是要注意，滚动到记录集末尾会增加额外的系统开销，并会降低系统性能。  
  
 如果需要数据的位置在操作过程中保持固定（例如在生成报告或执行计算时），这时快照最有用。  尽管如此，数据源和快照可能会有很大的不同，因此可能需要经常重新生成它。  
  
 快照支持基于 ODBC 游标库，游标库为所有的 1 级驱动程序提供静态游标和定位更新（这对可更新性是必需的）。  该项支持要求必须在内存中加载游标库 DLL。  当构造 `CDatabase` 对象并调用它的 `OpenEx` 成员函数时，必须指定 `dwOptions` 参数的 **CDatabase::useCursorLib** 选项。  如果调用 **Open** 成员函数，默认情况下将加载游标库。  如果使用的是动态集而不是快照，则不需要加载游标库。  
  
 只有在构造 `CDatabase` 对象时加载了 ODBC 游标库，或者所使用的 ODBC 驱动程序支持静态游标时，才能使用快照。  
  
> [!NOTE]
>  对于某些 ODBC 驱动程序，快照（静态游标）可能不可更新。  请查看您的驱动程序文档以了解所支持的游标类型和它们所支持的并发类型。  若要保证可更新快照，请确保在创建 `CDatabase` 对象时将游标库加载到内存中。  有关更多信息，请参见 [ODBC：ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!NOTE]
>  如果要同时使用快照和动态集，必须将它们建立在两个不同的 `CDatabase` 对象上（两个不同的连接）。  
  
 有关快照和所有记录集共享的属性的更多信息，请参见 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)。  有关 ODBC 和快照（包括 ODBC 游标库）的更多信息，请参见 [ODBC](../../data/odbc/odbc-basics.md)。  
  
## 请参阅  
 [开放式数据库连接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)