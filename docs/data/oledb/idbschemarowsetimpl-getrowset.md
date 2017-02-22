---
title: "IDBSchemaRowsetImpl::GetRowset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IDBSchemaRowsetImpl::GetRowset"
  - "ATL.IDBSchemaRowsetImpl.GetRowset"
  - "IDBSchemaRowsetImpl<SessionClass>::GetRowset"
  - "IDBSchemaRowsetImpl.GetRowset"
  - "IDBSchemaRowsetImpl::GetRowset"
  - "ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset"
  - "GetRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRowset 方法"
ms.assetid: 3ae28c22-e186-4a15-8591-b0192e784a6f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IDBSchemaRowsetImpl::GetRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回架构行集。  
  
## 语法  
  
```  
  
STDMETHOD (GetRowset)(  
   IUnknown *  
pUnkOuter  
,  
   REFGUID   
rguidSchema  
,  
   ULONG   
cRestrictions  
,  
   const VARIANT   
rgRestrictions  
[],  
   REFIID   
riid  
,  
   ULONG   
cPropertySets  
,  
   DBPROPSET   
rgPropertySets  
[],  
   IUnknown **  
ppRowset  
);  
  
```  
  
#### 参数  
 `pUnkOuter`  
 \[in\] 聚合时为外部 **IUnknown**；否则为 **NULL**。  
  
 `rguidSchema`  
 \[in\] 对所请求架构行集 GUID（例如，`DBSCHEMA_TABLES`）的引用。  
  
 `cRestrictions`  
 \[in\] 要应用于行集的限制计数。  
  
 `rgRestrictions`  
 \[in\] 一个表示限制的 `cRestrictions` **VARIANT** 数组。  
  
 `riid`  
 \[in\] 新建架构行集请求的 IID。  
  
 `cPropertySets`  
 \[in\] 要设置的属性集数目。  
  
 `rgPropertySets`  
 \[in\/out\] 要在新建架构行集上设置的 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 结构数组。  
  
 `ppRowset`  
 \[out\] 一个指针，指向新建架构行集上所请求的接口。  
  
## 备注  
 此方法要求用户在会话类中有架构映射。 利用架构映射信息，`GetRowset` 可在 `rguidSchema` 参数等于其中一个映射条目 GUID 时创建给定行集对象。 有关映射条目的描述，请参阅 [SCHEMA\_ENTRY](../../data/oledb/schema-entry.md)。  
  
 请参阅 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 中的 [IDBSchemaRowset::GetRowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx)。  
  
## 要求  
 **标头：**atldb.h  
  
## 请参阅  
 [IDBSchemaRowsetImpl 类](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl Class Members](http://msdn.microsoft.com/zh-cn/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)   
 [架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)