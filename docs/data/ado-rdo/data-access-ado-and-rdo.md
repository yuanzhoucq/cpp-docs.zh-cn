---
title: "数据访问：ADO 和 RDO | Microsoft Docs"
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
  - "绑定控件 [C++], ADO"
  - "绑定控件 [C++], RDO"
  - "控件 [C++], 数据绑定"
  - "数据访问 [C++], RDO 数据控件"
  - "数据绑定 [C++], ADO"
  - "数据绑定 [C++], RDO"
  - "数据控件 [C++]"
  - "数据绑定控件 [C++], ADO"
  - "数据绑定控件 [C++], RDO"
ms.assetid: 92da8f1e-144b-4605-ac0a-43c25bdc14a7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数据访问：ADO 和 RDO
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下表显示两项支持数据源或数据绑定控件的基础技术。  
  
 **ADO**  
 ADO 是 OLE DB 的 COM 包装，有利于编写数据访问应用程序（使用者）。  OLE DB 是基于 COM 的通用数据访问方法，允许使用任何数据源，不只是已索引的、连续的访问方法 \(ISAM\) 和基于 SQL 的数据库。  
  
 OLE DB 提供程序可以从各种不同的数据源访问数据，而且并不仅限于用 SQL 查询来检索数据，而是可以使用提供程序中定义的任何查询。  
  
 **RDO**  
 RDO 是 ODBC 的 COM 包装。  ODBC 是一个基于 C 的 API，允许通用用途（异类）的数据访问。  但是，RDO 依赖 SQL 作为命令语言来访问数据。  
  
 您可能要考虑使用基于 ADO 的数据访问控件而不是 RDO 数据访问控件。  
  
 下表显示 ADO 和 RDO 数据控件之间的主要差异。  
  
 **数据绑定控件**  
 RDO 数据绑定控件使用 **ICursor** 接口；ADO 控件使用 OLE DB `IRowset` 接口。  两种情况中，控件使用的接口都返回行集合。  
  
 基于 RDO 的数据绑定控件被设计为与 Visual Basic 一起使用时效果最佳。  因此，RDO 数据绑定控件的某些功能（特别是格式上的）在 Visual C\+\+ 应用程序中不可用。  ADO 数据绑定控件中不存在此问题。  
  
 **数据控件**  
 ADO 数据控件实现 **IDataSource** 接口，RDO 数据控件实现 **IVBDSC** 接口。  可以调用 **IDataSource** 方法来接收 `IRowset` 接口指针。  同样，可以调用 IVBDSC 方法来获取 **ICursor** 接口指针。  
  
## 请参阅  
 [在 Visual C\+\+ 中使用 ActiveX 控件进行数据绑定](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)