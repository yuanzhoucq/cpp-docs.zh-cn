---
title: "COM Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], reference topics"
  - "attributes [COM]"
  - "COM, attributes"
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# COM Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

COM 特性插入代码支持 COM 开发和 .NET framework 公共语言运行时开发许多范围。  这些区域从自定义接口实现大小并支持现有接口来支持常用属性、方法和事件。  此外，支持可以为复合和 Activex 控件实现中。  
  
|特性|说明|  
|--------|--------|  
|[可聚集的](../windows/aggregatable.md)|指示控件可由另一个复合控件。|  
|[聚合](../windows/aggregates.md)|指示控件复合目标类。|  
|[coclass](../windows/coclass.md)|创建 COM 对象，可以实现 COM 接口。|  
|[com\_interface\_entry](../windows/com-interface-entry-cpp.md)|添加接口项添加到 COM 映射。|  
|[implements\_category](../windows/implements-category.md)|标识实现了类的组件类。|  
|[progid](../windows/progid.md)|定义控件的 ProgID。|  
|[rdx](../windows/rdx.md)|创建或修改一个注册表项。|  
|[registration\_script](../windows/registration-script.md)|执行指定的注册脚本。|  
|[requires\_category](../windows/requires-category.md)|标识为类必需组件类。|  
|[support\_error\_info](../windows/support-error-info.md)|支持目标对象的错误报告。|  
|[同步](../windows/synchronize.md)|同步到方法。|  
|[线程处理](../windows/threading-cpp.md)|为 COM 对象指定线程模型。|  
|[vi\_progid](../windows/vi-progid.md)|定义控件的版本中立性 ProgID。|  
  
## 请参阅  
 [Attributes by Group](../windows/attributes-by-group.md)