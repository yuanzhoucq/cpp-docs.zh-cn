---
title: IDBSchemaRowsetImpl::CheckRestrictions | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
dev_langs:
- C++
helpviewer_keywords:
- CheckRestrictions method
ms.assetid: 3c9d77d2-0e4b-48fa-80db-d735da19f1cf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab19a661e02bcfd0f5ca3730c69e22adfc3ae4db
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="idbschemarowsetimplcheckrestrictions"></a>IDBSchemaRowsetImpl::CheckRestrictions
检查针对架构行集的限制的有效性。  
  
## <a name="syntax"></a>语法  
  
```
HRESULT CheckRestrictions(REFGUID rguidSchema,  
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);  
```  
  
#### <a name="parameters"></a>参数  
 `rguidSchema`  
 [in] 对所请求架构行集 GUID（例如， `DBSCHEMA_TABLES`）的引用。  
  
 `cRestrictions`  
 [in] 使用者为架构行集传入的限制数目。  
  
 `rgRestrictions`  
 [in] 要设置的限制值的长度 *cRestrictions* 数组。 有关详细信息，请参阅 `rgRestrictions` SetRestrictions [中的](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)参数描述。  
  
## <a name="remarks"></a>备注  
 使用 `CheckRestrictions` 可对架构行集检查限制的有效性。 它将检查 `DBSCHEMA_TABLES`、 **DBSCHEMA_COLUMNS**和 **DBSCHEMA_PROVIDER_TYPES** 架构行集的限制。 调用它可确定使用者对 **IDBSchemaRowset::GetRowset** 的调用是否正确。 如果要支持上面所列架构行集以外的架构行集，应当创建自己的函数来执行此任务。  
  
 `CheckRestrictions` 将确定使用者是否正在使用提供程序支持的正确限制和正确限制类型（例如，对字符串使用 [）调用](../../data/oledb/idbschemarowsetimpl-getrowset.md) GetRowset `VT_BSTR` 。 它还确定是否支持正确的限制数目。 默认情况下， `CheckRestrictions` 将通过 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 调用询问提供程序其在给定行集上支持的限制。 然后，它会将使用者提供的限制与提供程序支持的限制进行比较，并且要么成功要么失败。  
  
 有关架构行集的详细信息，请参阅[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程序员参考*Windows SDK 中。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IDBSchemaRowsetImpl 类](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl 类成员](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)