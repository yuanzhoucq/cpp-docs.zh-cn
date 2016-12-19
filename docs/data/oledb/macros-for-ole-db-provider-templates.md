---
title: "OLE DB 提供程序模板宏 | Microsoft Docs"
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
  - "vc.templates.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "宏, OLE DB 提供程序模板"
  - "OLE DB 提供程序模板宏"
  - "OLE DB 提供程序模板, 宏"
  - "提供程序模板宏 (OLE DB)"
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 提供程序模板宏
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 提供程序模板宏提供按照以下类别的功能：  
  
### 属性 集合 映射 宏命令  
  
|||  
|-|-|  
|[BEGIN\_PROPERTY\_SET](../../data/oledb/begin-property-set.md)|标记的属性开头。|  
|[BEGIN\_PROPERTY\_SET\_EX](../../data/oledb/begin-property-set-ex.md)|标记的属性开头。|  
|[BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)|标记在提供程序的范围外，可以隐藏或定义属性集的开头。|  
|[CHAIN\_PROPERTY\_SET](../../data/oledb/chain-property-set.md)|链接的属性组。|  
|[END\_PROPERTY\_SET](../../data/oledb/end-property-set.md)|标记的属性结尾。|  
|[END\_PROPSET\_MAP](../../data/oledb/end-propset-map.md)|标记的属性集合映射结尾。|  
|[PROPERTY\_INFO\_ENTRY](../../data/oledb/property-info-entry.md)|将属性设置的特定属性设置为默认值。|  
|[PROPERTY\_INFO\_ENTRY\_EX](../../data/oledb/property-info-entry-ex.md)|将属性设置的特定属性为您提供的值。  并将标志和选项。|  
|[PROPERTY\_INFO\_ENTRY\_VALUE](../../data/oledb/property-info-entry-value.md)|将属性设置的特定属性为您提供的值。|  
  
### 列映射宏  
  
|||  
|-|-|  
|[BEGIN\_PROVIDER\_COLUMN\_MAP](../../data/oledb/begin-provider-column-map.md)|标记提供程序列映射项的开始。|  
|[END\_PROVIDER\_COLUMN\_MAP](../../data/oledb/end-provider-column-map.md)|标记提供程序列映射项的结尾。|  
|[PROVIDER\_COLUMN\_ENTRY](../../data/oledb/provider-column-entry.md)|表示提供程序所支持的特定列。|  
|[PROVIDER\_COLUMN\_ENTRY\_GN](../../data/oledb/provider-column-entry-gn.md)|表示提供程序所支持的特定列。  可以指定列的大小、数据类型、精度、小数位数和架构行集的 GUID。|  
|[PROVIDER\_COLUMN\_ENTRY\_FIXED](../../data/oledb/provider-column-entry-fixed.md)|表示提供程序所支持的特定列。  可以指定列的数据类型。|  
|[PROVIDER\_COLUMN\_ENTRY\_LENGTH](../../data/oledb/provider-column-entry-length.md)|表示提供程序所支持的特定列。  可以指定列的大小。|  
|[PROVIDER\_COLUMN\_ENTRY\_STR](../../data/oledb/provider-column-entry-str.md)|表示提供程序所支持的特定列。  假定为是字符串。|  
|[PROVIDER\_COLUMN\_ENTRY\_TYPE\_LENGTH](../../data/oledb/provider-column-entry-type-length.md)|表示提供程序所支持的特定列。  就像 PROVIDER\_COLUMN\_ENTRY\_LENGTH，而且可以指定列的数据类型和大小。|  
|[PROVIDER\_COLUMN\_ENTRY\_WSTR](../../data/oledb/provider-column-entry-wstr.md)|表示提供程序所支持的特定列。  假定为是一个 Unicode 字符串。|  
  
### 架构行集宏  
  
|||  
|-|-|  
|[BEGIN\_SCHEMA\_MAP](../../data/oledb/begin-schema-map.md)|标记架构映射的开头。|  
|[SCHEMA\_ENTRY](../../data/oledb/schema-entry.md)|将一个GUID与一个类关联起来。|  
|[END\_SCHEMA\_MAP](../../data/oledb/end-schema-map.md)|标记架构映射的结尾。|  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)   
 [OLE DB 提供程序模板参考](../../data/oledb/ole-db-provider-templates-reference.md)