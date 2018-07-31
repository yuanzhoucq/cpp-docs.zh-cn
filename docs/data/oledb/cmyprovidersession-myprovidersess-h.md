---
title: CMyProviderSession (MyProviderSess.H) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidersession
- myprovidersess.h
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6bc3a9d377592b16c7e90cf0e75a6fba0eb00a64
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340122"
---
# <a name="cmyprovidersession-myprovidersessh"></a>CMyProviderSession (MyProviderSess.H)
MyProviderSess.H 包含声明和实现 OLE DB 会话对象。 数据源对象创建会话对象，表示使用者和提供程序之间的对话。 多个同时会话可以打开一个数据源。 继承列表`CMyProviderSession`后面：  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSession  
class ATL_NO_VTABLE CMyProviderSession :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IGetDataSourceImpl<CMyProviderSession>,  
   public IOpenRowsetImpl<CMyProviderSession>,  
   public ISessionPropertiesImpl<CMyProviderSession>,  
   public IObjectWithSiteSessionImpl<CMyProviderSession>,  
   public IDBSchemaRowsetImpl<CMyProviderSession>,  
   public IDBCreateCommandImpl<CMyProviderSession, CMyProviderCommand>  
```  
  
 会话对象继承自`IGetDataSource`， `IOpenRowset`， `ISessionProperties`，和`IDBCreateCommand`。 `IGetDataSource`接口允许一个会话，以便检索数据源创建它。 这是您需要从你创建的数据源或数据源可以提供其他信息获取属性的情况下很有用。 `ISessionProperties`接口处理会话的所有属性。 `IOpenRowset`和`IDBCreateCommand`使用接口来执行数据库工作。 如果提供程序支持的命令，它实现`IDBCreateCommand`接口。 它用于创建可以执行命令的命令对象。 提供程序始终实现`IOpenRowset`对象。 它用于从提供程序生成简单行集合。 它是一个默认行集 (例如， `"select * from mytable"`) 从提供程序。  
  
 该向导还会生成三个会话类： `CMyProviderSessionColSchema`， `CMyProviderSessionPTSchema`，和`CMyProviderSessionTRSchema`。 这些会话用于架构行集。 架构行集允许的提供程序没有使用者无需执行查询或提取数据的情况下向使用者返回的元数据。 提取元数据可以是比发现提供程序功能更快。  
  
 OLE DB 规范要求的提供程序实现`IDBSchemaRowset`接口支持三个架构行集类型： DBSCHEMA_COLUMNS、 DBSCHEMA_PROVIDER_TYPES 和 DBSCHEMA_TABLES。 该向导生成每个架构行集的实现。 向导生成的每个类包含`Execute`方法。 在此`Execute`方法，您可以对有关哪些表、 列和数据类型支持的提供程序返回数据。 此数据通常是在编译时已知的。  
  
## <a name="see-also"></a>请参阅  
 [提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)