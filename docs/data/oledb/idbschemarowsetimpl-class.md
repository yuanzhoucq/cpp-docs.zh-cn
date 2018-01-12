---
title: "IDBSchemaRowsetImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDBSchemaRowsetImpl
dev_langs: C++
helpviewer_keywords: IDBSchemaRowsetImpl class
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6b4f451fa408f2f6470281206e5de3670d069b6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl 类
提供架构行集的实现。  
  
## <a name="syntax"></a>语法  
  
```  
template <class SessionClass>  
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset  
```  
  
#### <a name="parameters"></a>参数  
 `SessionClass`  
 继承 `IDBSchemaRowsetImpl` 的类。 通常情况下，此类将是用户的会话类。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md)|检查针对架构行集的限制的有效性。|  
|[CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)|对模板参数指定的对象实现 COM 对象创建程序函数。|  
|[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)|指定在特定架构行集上支持哪些限制。|  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)|返回架构行集。|  
|[GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)|返回可由 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)访问的架构行集的列表。|  
  
## <a name="remarks"></a>备注  
 此类实现 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) 接口和模板化创建程序函数 [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)。  
  
 OLE DB 使用架构行集返回与提供程序中的数据有关的数据。 此类数据通常称为“元数据”。 默认情况下，提供程序必须始终支持 `DBSCHEMA_TABLES`、 **DBSCHEMA_COLUMNS**和 **DBSCHEMA_PROVIDER_TYPES**，如 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms713686.aspx) 中的 *IDBSchemaRowset*所述。 架构行集在架构映射中指定。 有关架构映射项的信息，请参阅 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)。  
  
 ATL 对象向导中的 OLE DB 提供程序向导自动生成项目中的架构行集的代码。 （默认情况下，该向导支持前面提到的必需的架构行集。）当你使用 ATL 对象向导创建使用者时，该向导使用架构行集将正确数据绑定到提供程序。 如果未实现架构行集来提供正确的元数据，向导将不会绑定正确的数据。  
  
 有关如何支持提供程序中的架构行集的信息，请参阅 [支持架构行集](../../data/oledb/supporting-schema-rowsets.md)。  
  
 有关架构行集的详细信息，请参阅 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms712921.aspx) 中的 *架构行集*。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IDBSchemaRowsetImpl 类成员](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [支持架构行集](../../data/oledb/supporting-schema-rowsets.md)