---
title: "访问器和行集合 | Microsoft Docs"
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
  - "访问器 [C++]"
  - "访问器 [C++], 行集合"
  - "数组行集合"
  - "批量行集合"
  - "CAccessorBase 类"
  - "CAccessorRowset 类, 访问器类型"
  - "CArrayRowset 类, 访问器"
  - "CBulkRowset 类, 访问器"
  - "CRowset 类, 访问器和行集合"
  - "OLE DB 使用者模板, 访问器"
  - "OLE DB 使用者模板, 行集合支持"
  - "行集合 [C++], 访问"
  - "行集合 [C++], 支持的类型"
  - "单个行集合"
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 访问器和行集合
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为了设置和检索数据，OLE DB 模板通过 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) 类使用访问器和行集合。  此类可以处理多个不同类型的访问器。  
  
## 访问器类型  
 所有访问器均从 [CAccessorBase](../../data/oledb/caccessorbase-class.md) 派生。  `CAccessorBase` 既提供参数又提供列绑定。  
  
 下图显示访问器类型。  
  
 ![访问器类型](../../data/oledb/media/vcaccessortypes.gif "vcAccessorTypes")  
访问器类  
  
-   [CAccessor](../../data/oledb/caccessor-class.md) 如果您在设计时知道数据库源的结构，则使用此访问器。  `CAccessor` 将包含缓冲区的数据库记录静态绑定到数据源。  
  
-   [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 如果您在设计时不知道数据库的结构，则使用此访问器。  `CDynamicAccessor` 调用 `IColumnsInfo::GetColumnInfo` 以获取数据库列信息。  它创建并管理访问器和缓冲区。  
  
-   [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) 使用此访问器处理未知的命令类型。  在准备命令时，如果提供程序支持 `ICommandWithParameters`，`CDynamicParameterAccessor` 就可以从 `ICommandWithParameters` 接口获取参数信息。  
  
-   [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)、[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md) 和 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md) 如果您不知道数据库架构，则使用这些类。  `CDynamicStringAccessorA` 检索 ANSI 字符串形式的数据；`CDynamicStringAccessorW` 检索 Unicode 字符串形式的数据。  
  
-   [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) 通过此类可以使用任何所需的数据类型（只要提供程序可以转换此类型）。  它既可以处理结果列，也可以处理命令参数。  
  
 下表概述了 OLE DB 模板访问器类型中的支持。  
  
|访问器类型|Dynamic|处理参数|缓冲区|多个访问器|  
|-----------|-------------|----------|---------|-----------|  
|`CAccessor`|否|是|用户|是|  
|`CDynamicAccessor`|是|否|OLE DB 模板|否|  
|`CDynamicParameterAccessor`|是|是|OLE DB 模板|否|  
|`CDynamicStringAccessor[A,W]`|是|否|OLE DB 模板|否|  
|`CManualAccessor`|是|是|用户|是|  
  
## 行集合类型  
 OLE DB 模板支持三种行集合（见上图）：单个行集合（由 [CRowset](../../data/oledb/crowset-class.md) 实现）、批量行集合（由 [CBulkRowset](../../data/oledb/cbulkrowset-class.md) 实现）和数组行集合（由 [CArrayRowset](../../data/oledb/carrayrowset-class.md) 实现）。  单个行集合在 `MoveNext` 被调用时获取单个行句柄。  批量行集合可以获取多个行句柄。  数组行集合是可以使用数组语法进行访问的行集合。  
  
 下图显示行集合类型。  
  
 ![RowsetType 图](../Image/vcRowsetTypes.gif "vcRowsetTypes")  
行集合类  
  
 [架构行集合](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)不访问数据存储区中的数据，而是访问关于数据存储区的信息（称为元数据）。  对于在编译时不知道数据库结构、但必须在运行时获取此结构的情况，通常需使用架构行集合。  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)