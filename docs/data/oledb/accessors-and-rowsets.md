---
title: 访问器和行集合
ms.date: 11/19/2018
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
ms.openlocfilehash: 45180b3ac2647c9f4f5d25a1322794552bd79004
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212376"
---
# <a name="accessors-and-rowsets"></a>访问器和行集合

若要设置和检索数据，OLE DB 模板通过[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)类使用访问器和行集。 此类可处理多个不同类型的访问器。

## <a name="accessor-types"></a>取值函数类型

所有访问器均派生自[CAccessorBase](../../data/oledb/caccessorbase-class.md)。 `CAccessorBase` 提供参数和列绑定。

下图显示了访问器类型。

![取值函数类型](../../data/oledb/media/vcaccessortypes.gif "访问器类型")<br/>
访问器类

- [CAccessor](../../data/oledb/caccessor-class.md)如果在设计时知道数据库源的结构，请使用此访问器。 `CAccessor` 将包含缓冲区的数据库记录静态绑定到数据源。

- [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)如果在设计时不知道数据库的结构，请使用此访问器。 `CDynamicAccessor` 调用 `IColumnsInfo::GetColumnInfo` 获取数据库列信息。 它创建和管理访问器和缓冲区。

- [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)使用此访问器处理未知的命令类型。 准备命令时，如果访问接口支持 `ICommandWithParameters`，`CDynamicParameterAccessor` 可以从 `ICommandWithParameters` 接口获取参数信息。

- 当你不知道数据库架构时， [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)、 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)和[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)将使用这些类。 `CDynamicStringAccessorA` 以 ANSI 字符串的形式检索数据;`CDynamicStringAccessorW` 以 Unicode 字符串的形式检索数据。

- [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)使用此类时，如果提供程序可以转换类型，则可以使用所需的任何数据类型。 它处理结果列和命令参数。

下表汇总了 OLE DB 模板访问器类型中的支持。

|访问器类型|动态|处理参数|Buffer|多个访问器|
|-------------------|-------------|--------------------|------------|------------------------|
|`CAccessor`|否|是|用户|是|
|`CDynamicAccessor`|是|否|OLE DB 模板|否|
|`CDynamicParameterAccessor`|是|是|OLE DB 模板|否|
|`CDynamicStringAccessor[A,W]`|是|否|OLE DB 模板|否|
|`CManualAccessor`|是|是|用户|是|

## <a name="rowset-types"></a>行集合类型

OLE DB 模板支持三种类型的行集（请参阅上图）：单个行集（由[CRowset](../../data/oledb/crowset-class.md)实现）、批量行集（由[CBulkRowset](../../data/oledb/cbulkrowset-class.md)实现）和数组行集（由[CArrayRowset](../../data/oledb/carrayrowset-class.md)实现）。 调用 `MoveNext` 时，单个行集会提取单个行句柄。 大容量行集可以提取多个行句柄。 数组行集是可使用数组语法访问的行集。

下图显示行集类型。

![RowsetType 图](../../data/oledb/media/vcrowsettypes.gif "RowsetType 图")<br/>
行集类

[架构行集](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)不会访问数据存储区中的数据，而是访问有关数据存储的信息（称为元数据）。 架构行集通常用于数据库结构在编译时未知且必须在运行时获取的情况。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)
