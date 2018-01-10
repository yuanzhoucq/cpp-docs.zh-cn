---
title: "COM 特性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- attributes [C++], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63e23f6a6520085ff5a5a072cb349d079615b6f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="com-attributes"></a>COM 特性
COM 特性注入代码以支持的 COM 开发和.NET Framework 公共语言运行时开发的许多方面。 这些区域的范围为自定义接口的实现和支持的现有接口到支持常用属性、 方法和事件。 此外，支持可以找到复合和 ActiveX 控件实现。  
  
|特性|描述|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|表示一个控件，可以由另一个控件聚合。|  
|[aggregates](../windows/aggregates.md)|指示控件聚合目标类。|  
|[coclass](../windows/coclass.md)|创建 COM 对象，可以实现 COM 接口。|  
|[com_interface_entry](../windows/com-interface-entry-cpp.md)|将一个接口条目添加到 COM 映射。|  
|[implements_category](../windows/implements-category.md)|指定类的实现的组件类别。|  
|[progid](../windows/progid.md)|定义控件的 ProgID。|  
|[rdx](../windows/rdx.md)|在创建或修改注册表项。|  
|[registration_script](../windows/registration-script.md)|执行指定的注册脚本。|  
|[requires_category](../windows/requires-category.md)|指定所需的组件类别的类。|  
|[support_error_info](../windows/support-error-info.md)|支持的错误报告目标对象。|  
|[synchronize](../windows/synchronize.md)|将对方法的访问进行同步。|  
|[线程处理](../windows/threading-cpp.md)|指定 COM 对象的线程模型。|  
|[vi_progid](../windows/vi-progid.md)|定义一个控件其独立于版本的 ProgID。|  
  
## <a name="see-also"></a>请参阅  
 [按组分的特性](../windows/attributes-by-group.md)