---
title: "IDBSchemaRowsetImpl::CheckRestrictions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CheckRestrictions"
  - "IDBSchemaRowsetImpl::CheckRestrictions"
  - "IDBSchemaRowsetImpl.CheckRestrictions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CheckRestrictions 方法"
ms.assetid: 3c9d77d2-0e4b-48fa-80db-d735da19f1cf
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IDBSchemaRowsetImpl::CheckRestrictions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检查针对架构行集的限制的有效性。  
  
## 语法  
  
```  
  
HRESULT CheckRestrictions(  
   REFGUID   
rguidSchema  
,  
   ULONG   
cRestrictions  
,  
   const VARIANT   
rgRestrictions  
[]  
);  
  
```  
  
#### 参数  
 `rguidSchema`  
 \[in\] 对所请求架构行集 GUID（例如，`DBSCHEMA_TABLES`）的引用。  
  
 `cRestrictions`  
 \[in\] 使用者为架构行集传入的限制数目。  
  
 `rgRestrictions`  
 \[in\] 要设置的限制值的长度 *cRestrictions* 数组。 有关详细信息，请参阅 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 中的 `rgRestrictions` 参数描述。  
  
## 备注  
 使用 `CheckRestrictions` 可对架构行集检查限制的有效性。 它将检查 `DBSCHEMA_TABLES`、**DBSCHEMA\_COLUMNS** 和 **DBSCHEMA\_PROVIDER\_TYPES** 架构行集的限制。 调用它可确定使用者对 **IDBSchemaRowset::GetRowset** 的调用是否正确。 如果要支持上面所列架构行集以外的架构行集，应当创建自己的函数来执行此任务。  
  
 `CheckRestrictions` 将确定使用者是否正在使用提供程序支持的正确限制和正确限制类型（例如，对字符串使用 `VT_BSTR`）调用 [GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)。 它还确定是否支持正确的限制数目。 默认情况下，`CheckRestrictions` 将通过 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 调用询问提供程序其在给定行集上支持的限制。 然后，它会将使用者提供的限制与提供程序支持的限制进行比较，并且要么成功要么失败。  
  
 有关架构行集的详细信息，请参阅 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 中的 *OLE DB 程序员参考*中的 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)。  
  
## 要求  
 **标头：**atldb.h  
  
## 请参阅  
 [IDBSchemaRowsetImpl 类](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl Class Members](http://msdn.microsoft.com/zh-cn/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)