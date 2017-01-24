---
title: "PROPERTY_INFO_ENTRY | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROPERTY_INFO_ENTRY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROPERTY_INFO_ENTRY 宏"
ms.assetid: f7bd23d6-52b4-4d6a-aa9a-1fca9834c8dc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROPERTY_INFO_ENTRY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示属性集中的特定属性。  
  
## 语法  
  
```  
  
PROPERTY_INFO_ENTRY(  
dwPropID   
)  
  
```  
  
#### 参数  
 *dwPropID*  
 \[in\] 一个 [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) 值，该值可与属性集 GUID 一起使用以标识属性。  
  
## 备注  
 此宏将 `DWORD` 类型的属性值设置为 ATLDB.H 中定义的默认值。 若要将属性设置为所选的值，请使用 [PROPERTY\_INFO\_ENTRY\_VALUE](../../data/oledb/property-info-entry-value.md)。 若要同时为属性设置 [VARTYPE](http://msdn.microsoft.com/zh-cn/317b911b-1805-402d-a9cb-159546bc88b4) 和 [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx)，请使用 [PROPERTY\_INFO\_ENTRY\_EX](../../data/oledb/property-info-entry-ex.md)。  
  
## 示例  
 请参阅 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)。  
  
## 要求  
 **标头：**atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)