---
title: 'Idbschemarowsetimpl:: Setrestrictions |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
dev_langs:
- C++
helpviewer_keywords:
- SetRestrictions method
ms.assetid: 707d5065-b853-4d38-9b67-3066b4d3b279
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8b6effd432b033941d404c4935cdbad5a2336ac8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="idbschemarowsetimplsetrestrictions"></a>IDBSchemaRowsetImpl::SetRestrictions
指定在特定架构行集上支持哪些限制。  
  
## <a name="syntax"></a>语法  
  
```
void SetRestrictions(ULONG cRestrictions,  
  GUID* /* rguidSchema */,  
   ULONG* rgRestrictions);  
```  
  
#### <a name="parameters"></a>参数  
 `cRestrictions`  
 [in] `rgRestrictions` 数组中的限制数目和 `rguidSchema` 数组中的 GUID 数目。  
  
 `rguidSchema`  
 [in] 要为其提取限制的架构行集的 GUID 数组。 每个数组元素均包含一个架构行集的 GUID（例如， `DBSCHEMA_TABLES`）。  
  
 `rgRestrictions`  
 [in] 要设置的限制值的长度 `cRestrictions` 数组。 各元素对应于由 GUID 标识的架构行集上的限制。 如果某个架构行集不受提供程序支持，则该元素设置为零。 否则， **ULONG** 值将包含一个表示该架构行集上支持的限制的位掩码。 有关相对应的限制为特定架构行集的详细信息，请查阅上的架构行集 Guid 表中[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程序员参考*的窗口中SDK。  
  
## <a name="remarks"></a>备注  
 **IDBSchemaRowset** 对象调用 `SetRestrictions` 来确定在特定架构行集合（它由 [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) 通过一个向上转换的指针调用）上支持哪些限制。 限制允许使用者只提取匹配行（例如，查找表“MyTable”中的所有列）。 限制是可选的，如果不支持任何限制（默认设置），则始终返回所有数据。  
  
 此方法的默认实现将 `rgRestrictions` 数组元素设置为 0。 在会话类中重写默认设置，以设置默认限制以外的限制。  
  
 有关实现架构行集支持的信息，请参阅 [支持架构行集](../../data/oledb/supporting-schema-rowsets.md)。  
  
 有关支持架构行集的提供程序的示例，请参阅 [UpdatePV](../../visual-cpp-samples.md) 示例。  
  
 有关架构行集的详细信息，请参阅[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程序员参考*Windows SDK 中。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IDBSchemaRowsetImpl 类](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl 类成员](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [支持架构行集合](../../data/oledb/supporting-schema-rowsets.md)   
 [UpdatePV](../../visual-cpp-samples.md)