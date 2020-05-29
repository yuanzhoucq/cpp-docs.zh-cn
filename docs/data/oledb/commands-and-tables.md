---
title: 命令和表
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB consumer templates, table support
- CCommand class, OLE DB consumer templates
- commands [C++], OLE DB Consumer Templates
- CTable class
- CAccessorRowset class, command and table classes
- rowsets, accessing
- tables [C++], OLE DB Consumer Templates
- OLE DB consumer templates, command support
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
ms.openlocfilehash: 0d5f6bd8d5f813497cba399e5c071f43dc1a7c4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211518"
---
# <a name="commands-and-tables"></a>命令和表

使用命令和表可以访问行集;也就是说，打开行集、执行命令和绑定列。 [CCommand](../../data/oledb/ccommand-class.md)和[CTable](../../data/oledb/ctable-class.md)类分别实例化命令对象和表对象。 这些类派生自[CAccessorRowset](../../data/oledb/caccessorrowset-class.md) ，如下图所示。

![CCommand 和 CTable](../../data/oledb/media/vccommandstables.gif "CCommand 和 CTable")<br/>
命令和表类

在上表中，`TAccessor` 可以是[访问器类型](../../data/oledb/accessors-and-rowsets.md)中列出的任何取值函数类型。 `TRowset` 可以是[行集类型](../../data/oledb/accessors-and-rowsets.md)中列出的任何行集类型。 `TMultiple` 指定结果类型（单个或多个结果集）。

[ATL OLE DB 使用者向导](../../atl/reference/atl-ole-db-consumer-wizard.md)允许您指定是否要使用命令或表对象。

- 对于没有命令的数据源，可以使用 `CTable` 类。 通常将其用于无需指定参数且不需要多个结果的简单行集。 此简单类使用指定的表名打开数据源上的表。

- 对于支持命令的数据源，可以改为使用 `CCommand` 类。 若要执行命令，请对此类调用[Open](../../data/oledb/ccommand-open.md) 。 作为替代方法，可以调用 `Prepare` 来准备要执行的命令。

   `CCommand` 具有三个模板参数：取值函数类型、行集类型和结果类型（默认情况下为`CNoMultipleResults`或 `CMultipleResults`）。 如果指定 `CMultipleResults`，则 `CCommand` 类支持 `IMultipleResults` 接口并处理多个行集。 [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)示例演示如何处理多个结果。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)
