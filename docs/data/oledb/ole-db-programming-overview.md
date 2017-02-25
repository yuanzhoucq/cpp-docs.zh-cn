---
title: "OLE DB 编程概述 | Microsoft Docs"
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
  - "OLE DB, 关于 OLE DB"
  - "通用数据访问"
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# OLE DB 编程概述
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 是什么，它为何不同于其他数据库技术？  OLE DB 是 Microsoft 开发的一种高性能的、基于 COM 的数据库技术。  OLE DB 和其他 Microsoft 数据库技术的不同之处在于其提供通用数据访问的方式。  
  
## 通用数据访问  
 通用数据访问提供一种统一的数据访问方式，不管数据是以何种形式存储。  在通常的业务中，有大量的信息存储在公司的数据库之外。  这些信息分散在各处，例如各种不同的文件系统（如 FAT 或 NTFS）、索引顺序文件、个人数据库（如 Access）、电子表格（如 Excel）、项目规划应用程序（如 Project）以及电子邮件（如 Outlook）中。  
  
 使用多种相关联的应用程序来访问这些数据成为工作中的主要瓶颈，或者至少是一件很麻烦的事情。  大多数公司都发现自身面临这种情况，他们通过将信息合并到一个数据库管理系统 \(DBMS\) 来解决此问题。  但是，这种解决方案不仅昂贵、耗时，而且在许多情况下并不可行。  
  
 另一种解决方案就是开发通用数据访问。  OLE DB 和 ADO 提供通用数据访问功能。  在这两者中，OLE DB 的性能更强一些，并且被推荐和 Visual C\+\+ 应用程序一起使用。  
  
 通用数据访问意味着两项功能：其一是分布式查询或统一访问多个（分布式）数据源功能；其二是能够使非 DBMS 数据源可由数据库应用程序访问。  
  
-   分布式查询  
  
     统一访问多（即，分布式）数据源中的数据的能力。  数据源既可以是同一类型，例如两个单独的 Access 数据库；也可以是不同的类型，例如一个 SQL Server 数据库和一个 Access 数据库。  “统一”表示可以有目的地对所有数据源运行相同的查询。  
  
-   非 DBMS 访问  
  
     让非 DBMS 数据源能为数据库应用程序所访问的能力。  DBMS 数据源的例子有 IMS、DB2、Oracle、SQL Server、Access 以及 Paradox 等。  非 DBMS 数据源的示例包括文件系统、电子邮件、电子表格和项目管理工具中的信息。  
  
 假设有这样一种情况：销售部门需要查找一周中来自某一地区的客户的所有电子邮件。  该查询可能需要对电子邮件应用程序的邮箱文件和客户的 Access 表进行搜索，以指定客户的名称。  其中，Access 是一个 DBMS 应用程序，而 Outlook 是非 DBMS 应用程序。  
  
 OLE DB 支持开发能访问各种数据源的应用程序，无论是 DBMS 还是非 DBMS 数据源。  OLE DB 通过使用支持某一给定数据源相应的 DBMS 功能的 COM 接口，使得对数据源的通用访问成为可能。  COM 不仅在数据源之间而且还在其他各种应用程序之间减少了不必要的服务重复，同时还使它们之间的交互操作达到最大限度。  
  
## COM 的优点  
 这是 COM 产生的原因。  OLE DB 是一组 COM 接口。  用户可通过一组统一的接口访问数据，从而把一个数据库组织成一个合作组件的基地。  
  
 基于 COM 规范，OLE DB 定义了一批可扩展并且可以维护的接口，这些接口代管并封装 DBMS 功能中一致、可重复使用的部分。  这些接口定义了 DBMS 组件的边界，例如行容器、查询处理器和事务处理协调器，使用这些组件可对各种信息源进行统一事务访问。  
  
 OLE DB 应用程序通常写作 DLL，但是其 COM 实现通过使用组件化代码克服了 DLL 的缺陷（例如命名和版本问题）。  在 OLE DB 中，可使用全局唯一标识符 \(GUID\) 来调用接口或者访问其他组件。  
  
 最后一点，COM 使用引用计数来保持对组件使用的跟踪。  调用接口方法时，引用计数递增；方法返回时，引用计数递减。  当计数等于零时，该方法所属的组件被释放。  
  
## 请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 模板](../../data/oledb/ole-db-templates.md)