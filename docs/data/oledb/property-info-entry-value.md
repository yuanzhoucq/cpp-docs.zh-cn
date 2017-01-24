---
title: "PROPERTY_INFO_ENTRY_VALUE | Microsoft Docs"
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
  - "PROPERTY_INFO_ENTRY_VALUE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROPERTY_INFO_ENTRY_VALUE 宏"
ms.assetid: 9690f7f3-fb20-4a7e-a75f-8a3a1cb1ce0d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROPERTY_INFO_ENTRY_VALUE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示在属性设置的特定属性。  
  
## 语法  
  
```  
  
PROPERTY_INFO_ENTRY_VALUE(  
dwPropID  
, value )  
```  
  
#### 参数  
 *dwPropID*  
 \[in\] 与属性集的 GUID 标识属性结合使用的值。[DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx)  
  
 *值*  
 \[in\] 属性值的数据类型。`DWORD`。  
  
## 备注  
 此宏，您可以直接指定属性值类型 `DWORD`。  若要将属性设置为在 ATLDB.H 定义的默认值，请使用 [PROPERTY\_INFO\_ENTRY](../../data/oledb/property-info-entry.md)。  若要设置值，标志和选项。属性，请使用 [PROPERTY\_INFO\_ENTRY\_EX](../../data/oledb/property-info-entry-ex.md)。  
  
## 示例  
 参见 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)