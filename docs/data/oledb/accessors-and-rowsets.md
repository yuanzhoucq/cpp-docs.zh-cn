---
title: 访问器和行集合 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- accessors [C++]
- OLE DB consumer templates, rowset support
- OLE DB consumer templates, accessors
- rowsets [C++], accessing
- bulk rowsets
- CAccessorRowset class, accessor types
- single rowsets
- CArrayRowset class, accessors
- CBulkRowset class, accessors
- array rowsets
- CAccessorBase class
- CRowset class, accessors and rowsets
- accessors [C++], rowsets
- rowsets [C++], supported types
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 49f5415f6c75984f968b25fb709c20d80dde554f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="accessors-and-rowsets"></a>访问器和行集合
若要设置和检索数据，OLE DB 模板使用访问器和行集通过[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)类。 此类可以处理不同类型的多个访问器。  
  
## <a name="accessor-types"></a>访问器类型  
 所有访问器派生自[CAccessorBase](../../data/oledb/caccessorbase-class.md)。 `CAccessorBase` 提供参数和列绑定。  
  
 下图显示访问器类型。  
  
 ![访问器类型](../../data/oledb/media/vcaccessortypes.gif "vcaccessortypes")  
访问器类  
  
-   [CAccessor](../../data/oledb/caccessor-class.md)当你在设计时知道数据库源的结构时使用此访问器。 `CAccessor` 将数据库记录，其中包含缓冲区，静态绑定到数据源。  
  
-   [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)在设计时不知道数据库的结构时使用此访问器。 `CDynamicAccessor` 调用`IColumnsInfo::GetColumnInfo`获取的数据库列信息。 它创建和管理访问器和缓冲区。  
  
-   [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)此访问器用于处理未知的命令类型。 当你准备命令，`CDynamicParameterAccessor`即可获取参数信息从`ICommandWithParameters`接口，如果该提供程序支持`ICommandWithParameters`。  
  
-   [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)， [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)，和[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)在不知道数据库架构时使用这些类。 `CDynamicStringAccessorA` 将数据检索为 ANSI 字符串;`CDynamicStringAccessorW`将数据检索为 Unicode 字符串。  
  
-   [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)与此类，可以使用任何你希望如果提供程序可以将类型转换的数据类型。 它处理结果列和命令参数。  
  
 下表总结了中的 OLE DB 模板访问器类型的支持。  
  
|访问器类型|动态|句柄 params|缓冲区|多个访问器|  
|-------------------|-------------|--------------------|------------|------------------------|  
|`CAccessor`|否|是|“用户”|是|  
|`CDynamicAccessor`|是|否|OLE DB 模板|否|  
|`CDynamicParameterAccessor`|是|是|OLE DB 模板|否|  
|`CDynamicStringAccessor[A,W]`|是|否|OLE DB 模板|否|  
|`CManualAccessor`|是|是|“用户”|是|  
  
## <a name="rowset-types"></a>行集合类型  
 OLE DB 模板支持三种类型的行集 （请参阅前图所示）： 单一行集 (由实现[CRowset](../../data/oledb/crowset-class.md))，大容量行集 (由实现[CBulkRowset](../../data/oledb/cbulkrowset-class.md))，和数组 （实现的行集通过[CArrayRowset](../../data/oledb/carrayrowset-class.md))。 单个行处理时的单个行集提取`MoveNext`调用。 大容量行集可以提取多个行句柄。 数组行集是可以使用数组语法访问的行集。  
  
 下图显示的行集类型。  
  
 ![RowsetType 图](../../data/oledb/media/vcrowsettypes.gif "vcrowsettypes")  
行集类  
  
 [架构行集](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)执行不访问数据中的数据存储，但改为访问有关数据存储区，称为元数据信息。 在数据库结构在编译时未知，并且必须在运行时获取的情况下，通常使用架构行集合。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)