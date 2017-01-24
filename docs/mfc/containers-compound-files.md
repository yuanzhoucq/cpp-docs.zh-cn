---
title: "容器：复合文件 | Microsoft Docs"
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
  - "文件的访问模式 [C++]"
  - "复合文档"
  - "复合文件"
  - "容器 [C++], 复合文件"
  - "文档 [C++], 复合"
  - "文档 [C++], OLE"
  - "文件 [C++], 复合"
  - "OLE 容器, 复合文件"
  - "OLE 文档, 复合文件"
  - "性能 [C++], 复合文件"
  - "标准化文件结构的复合文件"
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 容器：复合文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文演示复合文件的组件并实现和使用复合文件的优点和缺点。OLE 应用程序。  
  
 复合文件是 OLE 的组成部分  它们实现用于数据传输和 OLE 文档存储。  复合文件是激活结构化存储模型的实现。  一致性的接口存在支持序列化到存储、流或文件对象。  复合文件在 Microsoft 基础类库类支持 `COleStreamFile` 和 `COleDocument`。  
  
> [!NOTE]
>  使用复合文件信息并不表示来自一个 OLE 文档或组合件文档。  复合文件是一种存储文档复合，OLE 文档和其他数据。  
  
##  <a name="_core_components_of_a_compound_file"></a> 复合文件的组件  
 复合文件的 OLE 实现使用三个对象类型：流对象、存储对象和 `ILockBytes` 对象。  这些对象下面的方法类似于标准文件系统的组件：  
  
-   流对象，如文件，存储的任何数据类型。  
  
-   存储对象，类似于目录，可以包含其他存储和流对象。  
  
-   **LockBytes** 对象所表示存储对象和物理硬件之间的接口。  它们确定实际字节如何写入任何存储设备 **LockBytes** 对象，如访问全局硬盘或内存区域。  有关 **LockBytes** 对象和 `ILockBytes` 接口的更多信息，请参见 *OLE 程序引用*。  
  
##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a> 复合文件的优点和缺点  
 复合文件提供可用的优点与文件中早期的方法。  它们包括：  
  
-   增量文件访问。  
  
-   文件访问方式。  
  
-   .vstemplate 文件的结构  
  
 是处于应用程序时应考虑复合文件 \- 大和性能问题的潜在缺点与磁盘上的存储相关，即当决定使用它们。  
  
###  <a name="_core_incremental_access_to_files"></a> 增量对文件的访问权限  
 对文件的访问权限是使用一个自动增量复合文件的优点。  由于复合文件视为在文件中的“文件系统”，各个对象类型，例如流或存储空间，可以访问，而无需加载整个文件。  这可以显著减少应用程序需要访问按用户编辑新对象的时间。  增量更新，根据相同的概念，可提供类似的优点。  而是将整个文件将所做更改保存到一个对象中，OLE 保存用户编辑流或存储对象中。  
  
###  <a name="_core_file_access_modes"></a> 文件访问方式。  
 可以确定对对象的更改以复合文件中时提交到磁盘。使用复合文件另一优势。  文件访问，或处理处理模式，以确定何时更改提交。  
  
-   事务模式以复合文件使用两阶段提交操作对对象的更改，从而保持可用的文档的旧值和新复制，直到用户选择要保存或撤消更改。  
  
-   直接方式组合到文档的更改，在进行，而无需能力后将这些更改撤消。  
  
 有关对可用性的更多信息，请参见 *OLE 程序引用*。  
  
###  <a name="_core_standardization"></a> 数据  
 复合文件的标准化结构允许不同的 OLE 应用程序通过 OLE 应用程序创建的复合文件浏览没有实际创建文件应用程序的知识。  
  
###  <a name="_core_size_and_performance_considerations"></a> 性能注意事项  
 由于复合文件存储结构和能力的复杂增量保存数据，文件使用此格式大于其他文件往往使用非结构化或“平文件”存储空间。  如果应用程序频繁地加载和保存文件，使用复合文件比 noncompound 文件会导致文件大小增加快速。  由于复合文件大，可以获取文件的访问时间存储上并从软盘加载也可以影响，则为文件的较慢的访问权限。  
  
 影响性能的另一个文件是议题碎片。  复合文件的大小取决于文件和磁盘扇区之间的差异。最后使用的第一个。  分割一的文件可以包含不包含数据可用空间的，但许多区域，计数，在计算范围。  在复合文件的生存期期间，这些区域由存储对象的插入或删除。创建  
  
##  <a name="_core_using_compound_files_format_for_your_data"></a> 使用数据的复合文件格式  
 在成功创建一个类后文档的应用程序从 `COleDocument`派生的，确保主文档构造函数调用 `EnableCompoundFile`。  当应用程序向导"创建 OLE 容器应用程序时，此插入您的调用。  
  
 在 *OLE 程序参考*，请参见、[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)[IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015)和 [ILockBytes](http://msdn.microsoft.com/library/windows/desktop/aa379238)。  
  
## 请参阅  
 [容器](../mfc/containers.md)   
 [容器：用户界面问题](../mfc/containers-user-interface-issues.md)   
 [COleStreamFile Class](../mfc/reference/colestreamfile-class.md)   
 [COleDocument Class](../mfc/reference/coledocument-class.md)