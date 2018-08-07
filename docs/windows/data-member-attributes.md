---
title: 数据成员特性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- data members [C++], attributes
- data members [C++]
ms.assetid: 95b2397d-1daf-4ae4-8cd0-06956d005b13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf8dab858b98e1f1a0433eabaa25a94275ee53ec
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570725"
---
# <a name="data-member-attributes"></a>数据成员特性
以下属性应用于类、 组件类或接口中的数据成员。  
  
|特性|描述|  
|---------------|-----------------|  
|[db_accessor](../windows/db-accessor.md)|组`db_column`参与属性`IAccessor`-基于绑定。|  
|[db_column](../windows/db-column.md)|将指定的列绑定到行集。|  
|[db_command](../windows/db-command.md)|创建 OLE DB 命令。|  
|[db_param](../windows/db-param.md)|指定的成员变量相关联的输入或输出参数和分隔变量。|  
|[db_source](../windows/db-source.md)|创建与数据源的连接。|  
|[db_table](../windows/db-table.md)|将打开一个 OLE DB 表。|  
|[defaultbind](../windows/defaultbind.md)|指示最能代表对象的单个、 可绑定属性。|  
|[displaybind](../windows/displaybind.md)|指示应显示给用户作为可绑定的属性。|  
|[id](../windows/id.md)|指定的成员函数 （属性或方法，请在接口或调度接口） 的 DISPID。|  
|[范围](../windows/range-cpp.md)|指定参数或在运行时设置其值的字段的允许值的范围。|  
|[rdx](../windows/rdx.md)|创建注册表项或修改现有的注册表项。|  
|[readonly](../windows/readonly-cpp.md)|禁止分配给数据成员。|  
|[requestedit](../windows/requestedit.md)|指示该属性支持`OnRequestEdit`通知。|  
  
## <a name="see-also"></a>请参阅  
 [按用法分的特性](../windows/attributes-by-usage.md)