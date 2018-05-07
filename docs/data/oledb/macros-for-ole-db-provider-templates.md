---
title: OLE DB 提供程序模板宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab7611c49f625a36023b4e31bf6aff47ab16f156
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="macros-for-ole-db-provider-templates"></a>OLE DB 提供程序模板宏
OLE DB 模板 Provider 宏，可以按以下类别的功能：  
  
### <a name="property-set-map-macros"></a>属性设置映射宏  
  
|||  
|-|-|  
|[BEGIN_PROPERTY_SET](../../data/oledb/begin-property-set.md)|标记属性集的开始。|  
|[BEGIN_PROPERTY_SET_EX](../../data/oledb/begin-property-set-ex.md)|标记属性集的开始。|  
|[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)|属性的开头设置的标记可以隐藏或定义的提供程序的作用域之外。|  
|[CHAIN_PROPERTY_SET](../../data/oledb/chain-property-set.md)|链接在一起属性组。|  
|[END_PROPERTY_SET](../../data/oledb/end-property-set.md)|将标记属性集的末尾。|  
|[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)|将标记属性集映射的末尾。|  
|[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)|中的属性设置为默认值设置的特定属性。|  
|[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)|中的属性设置为你提供的值设置的特定属性。 另外，可以设置标志和选项。|  
|[PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)|中的属性设置为你提供的值设置的特定属性。|  
  
### <a name="column-map-macros"></a>列映射宏  
  
|||  
|-|-|  
|[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)|标记提供程序列映射条目的开始。|  
|[END_PROVIDER_COLUMN_MAP](../../data/oledb/end-provider-column-map.md)|标记提供程序列映射条目的末尾。|  
|[PROVIDER_COLUMN_ENTRY](../../data/oledb/provider-column-entry.md)|表示提供程序支持的特定列。|  
|[PROVIDER_COLUMN_ENTRY_GN](../../data/oledb/provider-column-entry-gn.md)|表示提供程序支持的特定列。 你可以指定列的大小、 数据类型、 精度、 小数位数和架构行集 GUID。|  
|[PROVIDER_COLUMN_ENTRY_FIXED](../../data/oledb/provider-column-entry-fixed.md)|表示提供程序支持的特定列。 你可以指定列数据类型。|  
|[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)|表示提供程序支持的特定列。 你可以指定的列大小。|  
|[PROVIDER_COLUMN_ENTRY_STR](../../data/oledb/provider-column-entry-str.md)|表示提供程序支持的特定列。 它假定列类型为字符串。|  
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](../../data/oledb/provider-column-entry-type-length.md)|表示提供程序支持的特定列。 像 PROVIDER_COLUMN_ENTRY_LENGTH，但也可以指定列的数据类型，以及大小。|  
|[PROVIDER_COLUMN_ENTRY_WSTR](../../data/oledb/provider-column-entry-wstr.md)|表示提供程序支持的特定列。 它假定列类型是 Unicode 字符字符串。|  
  
### <a name="schema-rowset-macros"></a>架构行集宏  
  
|||  
|-|-|  
|[BEGIN_SCHEMA_MAP](../../data/oledb/begin-schema-map.md)|标记架构映射的开始。|  
|[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)|将 GUID 与类相关联。|  
|[END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)|将标记架构映射的末尾。|  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)   
 [OLE DB 提供程序模板参考](../../data/oledb/ole-db-provider-templates-reference.md)