---
title: 命令和表 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 23d2739807a065b93b10a209a9ea68070b36970b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098675"
---
# <a name="commands-and-tables"></a>命令和表
命令和表使你能够访问行集;也就是说，打开行集、 执行命令，并将列绑定。 [CCommand](../../data/oledb/ccommand-class.md)和[CTable](../../data/oledb/ctable-class.md)类实例化的命令和表的对象，分别。 这些类派生自[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)下图中所示。  
  
 ![CCommand 和 CTable](../../data/oledb/media/vccommandstables.gif "vccommandstables")  
命令和表类  
  
 在前面的表中，`TAccessor`可以中列出的任何访问器类型[访问器类型](../../data/oledb/accessors-and-rowsets.md)。 *TRowset*可以中列出的任何行集类型[行集类型](../../data/oledb/accessors-and-rowsets.md)。 *TMultiple*指定 （单个或多个结果集） 的结果类型。  
  
 [ATL OLE DB 使用者向导](../../atl/reference/atl-ole-db-consumer-wizard.md)允许你指定是否希望命令或表对象。  
  
-   对于不带命令数据源，可以使用`CTable`类。 你通常将其不指定任何参数，并且要求没有多个结果的简单行集。 此简单的类将打开上使用你指定的表名称的数据源的表。  
  
-   对于支持命令的数据源，可以使用`CCommand`类。 若要执行命令，调用[打开](../../data/oledb/ccommand-open.md)此类。 作为替代方法，可以调用`Prepare`准备你想要执行一次以上的命令。  
  
     **CCommand**具有三个模板自变量： 访问器类型、 行集类型和的结果类型 (`CNoMultipleResults`，默认情况下，或`CMultipleResults`)。 如果指定`CMultipleResults`、`CCommand`类支持**IMultipleResults**接口，并在处理多个行集。 [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)示例演示如何处理多个结果。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)