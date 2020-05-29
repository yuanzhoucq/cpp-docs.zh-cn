---
title: CCustomSession (CustomSess.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidersession
- myprovidersess.h
- ccustomsession
- customsess.h
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
- CCustomSession class in CustomSess.H
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
ms.openlocfilehash: 4775f21c1e0fa7666d24b4d6a55e099bc6ae55a2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079760"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*自定义*Ses 包含 OLE DB session 对象的声明和实现。 数据源对象创建 session 对象并表示使用者与提供者之间的会话。 对于一个数据源，可以打开多个同时会话。 `CCustomSession` 的继承列表如下：

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSession
class ATL_NO_VTABLE CCustomSession :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IGetDataSourceImpl<CCustomSession>,
   public IOpenRowsetImpl<CCustomSession>,
   public ISessionPropertiesImpl<CCustomSession>,
   public IObjectWithSiteSessionImpl<CCustomSession>,
   public IDBSchemaRowsetImpl<CCustomSession>,
   public IDBCreateCommandImpl<CCustomSession, CCustomCommand>
```

会话对象继承自 `IGetDataSource`、`IOpenRowset`、`ISessionProperties`和 `IDBCreateCommand`。 `IGetDataSource` 接口允许会话检索创建它的数据源。 如果需要从创建的数据源获取属性或数据源可以提供的其他信息，这将很有用。 `ISessionProperties` 接口处理会话的所有属性。 `IOpenRowset` 和 `IDBCreateCommand` 接口用于执行数据库工作。 如果提供程序支持命令，则它实现 `IDBCreateCommand` 接口。 它用于创建可执行命令的命令对象。 提供程序始终实现 `IOpenRowset` 对象。 它用于从提供程序生成行集。 它是提供程序中的默认行集（例如 `"select * from mytable"`）。

该向导还会生成三个会话类： `CCustomSessionColSchema`、`CCustomSessionPTSchema`和 `CCustomSessionTRSchema`。 这些会话用于架构行集。 通过架构行集，提供程序可以将元数据返回给使用者，而不需要使用者执行查询或提取数据。 提取元数据的速度比查找提供程序的功能要快得多。

OLE DB 规范要求实现 `IDBSchemaRowset` 接口的提供程序支持三个架构行集类型： DBSCHEMA_COLUMNS、DBSCHEMA_PROVIDER_TYPES 和 DBSCHEMA_TABLES。 向导将为每个架构行集生成实现。 向导生成的每个类都包含一个 `Execute` 方法。 在此 `Execute` 方法中，你可以向提供程序返回有关你支持的表、列和数据类型的数据。 此数据在编译时是已知的。

## <a name="see-also"></a>另请参阅

[提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)<br/>
