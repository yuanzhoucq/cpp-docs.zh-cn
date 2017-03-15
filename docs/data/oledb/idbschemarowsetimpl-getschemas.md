---
title: "IDBSchemaRowsetImpl::GetSchemas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IDBSchemaRowsetImpl::GetSchemas"
  - "GetSchemas"
  - "IDBSchemaRowsetImpl<SessionClass>::GetSchemas"
  - "ATL.IDBSchemaRowsetImpl.GetSchemas"
  - "ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas"
  - "IDBSchemaRowsetImpl.GetSchemas"
  - "IDBSchemaRowsetImpl::GetSchemas"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetSchemas 方法"
ms.assetid: fbe725a6-3acd-45f8-bcaf-10a6c1239cd2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IDBSchemaRowsetImpl::GetSchemas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回可由 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) 访问的架构行集的列表。  
  
## 语法  
  
```  
  
STDMETHOD  
( GetSchema s )(  
   ULONG *   
pcSchemas  
,  
   GUID **   
prgSchemas  
,  
   ULONG**   
prgRest  
);  
  
```  
  
#### 参数  
 *pcSchemas*  
 \[out\] 一个指针，指向使用架构数目填充的 **ULONG**。  
  
 *prgSchemas*  
 \[out\] 一个指向 GUID 数组的指针，该数组用指向架构行集 GUID 数组的指针填充。  
  
 *prgRest*  
 \[out\] 一个指针，指向要使用限制数组填充的 **ULONG** 数组。  
  
## 备注  
 此方法返回提供程序支持的所有架构行集的数组。 请参阅 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 中的 [IDBSchemaRowset::GetSchemas](https://msdn.microsoft.com/en-us/library/ms719605.aspx)。  
  
 若要实现此函数，用户在会话类中必须有架构映射。 然后，该函数会利用架构映射信息，使用映射中架构的 GUID 数组进行响应。 这表示提供程序支持的架构。  
  
## 要求  
 **标头：**atldb.h  
  
## 请参阅  
 [IDBSchemaRowsetImpl 类](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl Class Members](http://msdn.microsoft.com/zh-cn/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)   
 [IDBSchemaRowset::GetRowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx)   
 [架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)