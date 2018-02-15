---
title: IDBSchemaRowsetImpl::CreateSchemaRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateSchemaRowset method
ms.assetid: ad3e3e4d-45b9-461c-b7b8-3af6843631b1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4975f452844a9efc8002b661efa224bf7cac8a3f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="idbschemarowsetimplcreateschemarowset"></a>IDBSchemaRowsetImpl::CreateSchemaRowset
对模板参数指定的对象实现 COM 对象创建程序函数。  
  
## <a name="syntax"></a>语法  
  
```cpp
template template <class SchemaRowsetClass>  
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   SchemaRowsetClass*& pSchemaRowset);  
```  
  
#### <a name="parameters"></a>参数  
 `pUnkOuter`  
 [in] 聚合时为外部 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) ；否则为 **NULL**。  
  
 `cRestrictions`  
 [in] 要应用于架构行集的限制的计数。  
  
 `rgRestrictions`  
 [in]数组`cRestrictions` **VARIANT**要应用于行集。  
  
 `riid`  
 [in] 输出 [IUnknown](../../atl/queryinterface.md) 的 **QueryInterface**的接口。  
  
 `cPropertySets`  
 [in] 要设置的属性集数目。  
  
 `rgPropertySets`  
 [in] 指定要设置的属性的 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 结构的数组。  
  
 `ppRowset`  
 [out] **请求的传出** IUnknown `riid`。 此 **IUnknown** 是架构行集对象上的接口。  
  
 `pSchemaRowset`  
 [out] 指向架构行集类的实例的指针。 通常不使用此参数，但如果你在将架构行集交给 COM 对象前必须在其上进行较多工作，则可使用此参数。 `pSchemaRowset` 的生存期受到 `ppRowset`约束。  
  
## <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
## <a name="remarks"></a>备注  
 此函数对所有类型的架构行集实现泛型创建程序。 通常情况下，用户不调用此函数。 它由架构映射的实现调用。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IDBSchemaRowsetImpl 类](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl 类成员](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)   
 [架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)