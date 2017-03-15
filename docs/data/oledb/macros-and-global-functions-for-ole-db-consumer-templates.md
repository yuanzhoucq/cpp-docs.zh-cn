---
title: "OLE DB 使用者模板的宏和全局函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "宏, OLE DB 使用者模板"
  - "OLE DB 使用者模板, 宏"
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OLE DB 使用者模板的宏和全局函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由 OLE DB 使用者模板以下全局函数和宏：  
  
### 全局函数  
  
|||  
|-|-|  
|[AtlTraceErrorRecords](../../data/oledb/atltraceerrorrecords.md)|false，则返回，转储 OLE DB 错误记录信息转储到设备。|  
  
### 访问器映射宏  
  
|||  
|-|-|  
|[BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)|标记访问函数入口的开头。|  
|[BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)|标记存取器映射项的开始。|  
|[END\_ACCESSOR](../../data/oledb/end-accessor.md)|标记访问函数入口的结尾。|  
|[END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)|标记存取器映射项的结束。|  
  
### 列映射宏  
  
|||  
|-|-|  
|[BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)|将列映射项的开头在用户记录类。|  
|[BLOB\_ENTRY](../../data/oledb/blob-entry.md)|用于绑定二进制大对象 \(BLOB\) \(BLOB\)。|  
|[BLOB\_ENTRY\_LENGTH](../../data/oledb/blob-entry-length.md)|报告 BLOB 数据列的长度。|  
|[BLOB\_ENTRY\_LENGTH\_STATUS](../../data/oledb/blob-entry-length-status.md)|报告 BLOB 数据列的长度和状态。|  
|[BLOB\_ENTRY\_STATUS](../../data/oledb/blob-entry-status.md)|报告 BLOB 数据列的状态。|  
|[BLOB\_NAME](../../data/oledb/blob-name.md)|用于按列名绑定二进制大对象 \(BLOB\)。|  
|[BLOB\_NAME\_LENGTH](../../data/oledb/blob-name-length.md)|报告 BLOB 数据列的长度。|  
|[BLOB\_NAME\_LENGTH\_STATUS](../../data/oledb/blob-name-length-status.md)|报告 BLOB 数据列的长度和状态。|  
|[BLOB\_NAME\_STATUS](../../data/oledb/blob-name-status.md)|报告 BLOB 数据列的状态。|  
|[BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md)|对行集合的一书签项。  书签项是特定的列类型。|  
|[COLUMN\_ENTRY](../../data/oledb/column-entry.md)|表示绑定到数据库中的特定列。|  
|[COLUMN\_ENTRY\_EX](../../data/oledb/column-entry-ex.md)|表示绑定到数据库中的特定列。  支持 `type`、*长度*、*精度*、*状态* 和 `scale`参数。|  
|[COLUMN\_ENTRY\_LENGTH](../../data/oledb/column-entry-length.md)|表示绑定到数据库中的特定列。  支持 *长度* 变量。|  
|[COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)|表示绑定到数据库中的特定列。  支持 *状态* 和 *长度* 参数。|  
|[COLUMN\_ENTRY\_PS](../../data/oledb/column-entry-ps.md)|表示绑定到数据库中的特定列。  支持 *精度* 和 `scale` 参数。|  
|[COLUMN\_ENTRY\_PS\_LENGTH](../../data/oledb/column-entry-ps-length.md)|表示绑定到数据库中的特定列。  支持变量 *长度*、*精度* 和 `scale` 参数。|  
|[COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)|表示绑定到数据库中的特定列。  支持 *状态* 变量和 *长度*、*精度* 和 `scale` 参数。|  
|[COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)|表示绑定到数据库中的特定列。  支持变量 *状态*、*精度* 和 `scale` 参数。|  
|[COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)|表示绑定到数据库中的特定列。  支持 *状态* 变量。|  
|[COLUMN\_ENTRY\_TYPE](../../data/oledb/column-entry-type.md)|表示绑定到数据库中的特定列。  支持 `type` 参数。|  
|[COLUMN\_ENTRY\_TYPE\_SIZE](../../data/oledb/column-entry-type-size.md)|表示绑定到数据库中的特定列。  支持 `type` 和 `size` 参数。|  
|[COLUMN\_NAME](../../data/oledb/column-name.md)|表示绑定到数据库中的特定列。|  
|[COLUMN\_NAME\_EX](../../data/oledb/column-name-ex.md)|表示绑定到数据库中的特定列。  支持数据类型、范围、精度、缩放、列长度和列状态的规范。|  
|[COLUMN\_NAME\_LENGTH](../../data/oledb/column-name-length.md)|表示绑定到数据库中的特定列。  支持列长度的规范。|  
|[COLUMN\_NAME\_LENGTH\_STATUS](../../data/oledb/column-name-length-status.md)|表示绑定到数据库中的特定列。  支持列长度和状态的规范。|  
|[COLUMN\_NAME\_PS](../../data/oledb/column-name-ps.md)|表示绑定到数据库中的特定列。  支持精度和小数位数的规范。|  
|[COLUMN\_NAME\_PS\_LENGTH](../../data/oledb/column-name-ps-length.md)|表示绑定到数据库中的特定列。  支持精度、小数位数和列长度的规范。|  
|[COLUMN\_NAME\_PS\_LENGTH\_STATUS](../../data/oledb/column-name-ps-length-status.md)|表示绑定到数据库中的特定列。  支持精度、缩放、列长度和列状态的规范。|  
|[COLUMN\_NAME\_PS\_STATUS](../../data/oledb/column-name-ps-status.md)|表示绑定到数据库中的特定列。  支持精度、小数位数和列状态的规范。|  
|[COLUMN\_NAME\_STATUS](../../data/oledb/column-name-status.md)|表示绑定到数据库中的特定列。  支持列状态的规范。|  
|[COLUMN\_NAME\_TYPE](../../data/oledb/column-name-type.md)|表示绑定到数据库中的特定列。  支持数据类型的规范。|  
|[COLUMN\_NAME\_TYPE\_PS](../../data/oledb/column-name-type-ps.md)|表示绑定到数据库中的特定列。  支持数据类型、精度和小数位数的规范。|  
|[COLUMN\_NAME\_TYPE\_SIZE](../../data/oledb/column-name-type-size.md)|表示绑定到数据库中的特定列。  支持数据类型和大小的规范。|  
|[COLUMN\_NAME\_TYPE\_STATUS](../../data/oledb/column-name-type-status.md)|表示绑定到数据库中的特定列。  支持数据类型和列状态的规范。|  
|[END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)|标记提供程序列映射项的结尾。|  
  
### 命令宏  
  
|||  
|-|-|  
|[DEFINE\_COMMAND](../../data/oledb/define-command.md)|指定要用于创建该行集合，并使用 [CCommand](../../data/oledb/ccommand-class.md) 类中的命令。  接受与指定的应用程序类型的某些字符串类型 \(ANSI 或 Unicode。\)  建议您改用 [DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md) 而不是 `DEFINE_COMMAND`。|  
|[DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md)|指定要用于创建该行集合，并使用 [CCommand](../../data/oledb/ccommand-class.md) 类中的命令。  支持 ANSI 和 Unicode 应用程序。|  
  
### 参数映射宏  
  
|||  
|-|-|  
|[BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md)|将参数映射项的开头在用户记录类。|  
|[END\_PARAM\_MAP](../../data/oledb/end-param-map.md)|标记参数器映射项的结束。|  
|[SET\_PARAM\_TYPE](../../data/oledb/set-param-type.md)|`SET_PARAM_TYPE` 宏指定在输入、输出或"输入\/输出"的 `COLUMN_ENTRY` 宏。|  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)