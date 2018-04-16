---
title: "宏和全局函数 OLE DB 使用者模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 755762e8b77cee9603074fdc8050d227fbd2eeb1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>OLE DB 使用者模板的宏和全局函数
OLE DB 使用者模板包括以下宏和全局函数：  
  
### <a name="global-functions"></a>全局函数  
  
|||  
|-|-|  
|[AtlTraceErrorRecords](../../data/oledb/atltraceerrorrecords.md)|如果返回错误，则转储到转储设备的 OLE DB 错误记录信息。|  
  
### <a name="accessor-map-macros"></a>访问器映射宏  
  
|||  
|-|-|  
|[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)|标记访问器条目的开始。|  
|[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)|标记取值函数映射条目的开始。|  
|[END_ACCESSOR](../../data/oledb/end-accessor.md)|将标记的末尾的访问器条目。|  
|[END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)|标记访问器映射条目的末尾。|  
  
### <a name="column-map-macros"></a>列映射宏  
  
|||  
|-|-|  
|[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)|标记的用户记录类中的列映射条目的开始。|  
|[BLOB_ENTRY](../../data/oledb/blob-entry.md)|用于绑定二进制大型对象 (BLOB)。|  
|[BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)|报告 BLOB 数据列的长度。|  
|[BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)|报告的长度和 BLOB 数据列的状态。|  
|[BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)|报告的 BLOB 数据列的状态。|  
|[BLOB_NAME](../../data/oledb/blob-name.md)|用于绑定的二进制大型对象列名称。|  
|[BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)|报告 BLOB 数据列的长度。|  
|[BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)|报告的长度和 BLOB 数据列的状态。|  
|[BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)|报告的 BLOB 数据列的状态。|  
|[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)|表示行集上的书签条目。 书签项是一种特殊的列条目。|  
|[COLUMN_ENTRY](../../data/oledb/column-entry.md)|表示一种绑定到数据库中的特定列。|  
|[COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)|表示数据库中的特定列的绑定。 支持`type`，*长度*，*精度*， `scale`，和*状态*参数。|  
|[COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)|表示数据库中的特定列的绑定。 支持*长度*变量。|  
|[COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)|表示数据库中的特定列的绑定。 支持*状态*和*长度*参数。|  
|[COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)|表示数据库中的特定列的绑定。 支持*精度*和`scale`参数。|  
|[COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)|表示数据库中的特定列的绑定。 支持*长度*变量，*精度*和`scale`参数。|  
|[COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)|表示数据库中的特定列的绑定。 支持*状态*和*长度*变量，*精度*和`scale`参数。|  
|[COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)|表示数据库中的特定列的绑定。 支持*状态*变量，*精度*和`scale`参数。|  
|[COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)|表示数据库中的特定列的绑定。 支持*状态*变量。|  
|[COLUMN_ENTRY_TYPE](../../data/oledb/column-entry-type.md)|表示一种绑定到数据库中的特定列。 支持`type`参数。|  
|[COLUMN_ENTRY_TYPE_SIZE](../../data/oledb/column-entry-type-size.md)|表示数据库中的特定列的绑定。 支持`type`和`size`参数。|  
|[COLUMN_NAME](../../data/oledb/column-name.md)|按名称表示一种绑定到数据库中的特定列。|  
|[COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)|按名称表示一种绑定到数据库中的特定列。 支持的数据类型、 大小、 精度、 缩放、 列长度和列状态的规范。|  
|[COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)|按名称表示一种绑定到数据库中的特定列。 支持的列长度的规范。|  
|[COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)|按名称表示一种绑定到数据库中的特定列。 支持的列长度和状态的规范。|  
|[COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)|按名称表示一种绑定到数据库中的特定列。 支持的精度和小数位数的规范。|  
|[COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)|按名称表示一种绑定到数据库中的特定列。 支持的精度、 小数位数和列长度的规范。|  
|[COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)|按名称表示一种绑定到数据库中的特定列。 支持的精度、 缩放、 列长度和列状态的规范。|  
|[COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)|按名称表示一种绑定到数据库中的特定列。 支持的精度、 小数位数和列的状态的规范。|  
|[COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)|按名称表示一种绑定到数据库中的特定列。 支持的列状态的规范。|  
|[COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)|按名称表示一种绑定到数据库中的特定列。 支持的数据类型的规范。|  
|[COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)|按名称表示一种绑定到数据库中的特定列。 支持的数据类型、 精度和小数位数的规范。|  
|[COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)|按名称表示一种绑定到数据库中的特定列。 支持的数据类型和大小的规范。|  
|[COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)|按名称表示一种绑定到数据库中的特定列。 支持的数据类型和列状态的规范。|  
|[END_COLUMN_MAP](../../data/oledb/end-column-map.md)|标记列映射条目的末尾。|  
  
### <a name="command-macros"></a>命令宏  
  
|||  
|-|-|  
|[DEFINE_COMMAND](../../data/oledb/define-command.md)|指定将用于创建行集时使用的命令[CCommand](../../data/oledb/ccommand-class.md)类。 接受仅与指定的应用程序类型 （ANSI 或 Unicode） 匹配的字符串类型。 建议你使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是`DEFINE_COMMAND`。|  
|[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)|指定将用于创建行集时使用的命令[CCommand](../../data/oledb/ccommand-class.md)类。 支持 ANSI 和 Unicode 应用程序。|  
  
### <a name="parameter-map-macros"></a>参数映射宏  
  
|||  
|-|-|  
|[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)|标记的用户记录类中的参数映射条目的开始。|  
|[END_PARAM_MAP](../../data/oledb/end-param-map.md)|将标记参数映射项的末尾。|  
|[SET_PARAM_TYPE](../../data/oledb/set-param-type.md)|指定`COLUMN_ENTRY`按照的宏`SET_PARAM_TYPE`宏作为输入、 输出或输入/输出。|  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)