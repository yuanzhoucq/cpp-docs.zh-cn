---
title: COM 特性
ms.date: 10/03/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
ms.openlocfilehash: eb87d3861c6b3066cf482108e2ce2243c8196093
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038924"
---
# <a name="com-attributes"></a>COM 特性

COM 特性注入的代码来支持 COM 开发和.NET Framework 公共语言运行时开发的许多方面。 这些区域的范围从自定义接口实现和支持的现有接口支持常用属性、 方法和事件。 此外，支持可以找到复合和 ActiveX 控件实现的。

|特性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示一个控件，可以聚合由另一个控件。|
|[aggregates](aggregates.md)|指示控件聚合的目标类。|
|[coclass](coclass.md)|创建 COM 对象，可以实现 COM 接口。|
|[com_interface_entry](com-interface-entry-cpp.md)|将接口条目添加到 COM 映射。|
|[implements_category](implements-category.md)|指定类的实现的组件类别。|
|[progid](progid.md)|定义控件的 ProgID。|
|[rdx](rdx.md)|创建或修改注册表项。|
|[registration_script](registration-script.md)|执行指定的注册脚本。|
|[requires_category](requires-category.md)|指定所需的组件类别的类。|
|[support_error_info](support-error-info.md)|支持的错误报告目标对象。|
|[synchronize](synchronize.md)|同步访问的方法。|
|[threading](threading-cpp.md)|指定 COM 对象的线程处理模型。|
|[vi_progid](vi-progid.md)|定义控件的独立于版本的 ProgID。|

## <a name="see-also"></a>请参阅

[按组分的特性](attributes-by-group.md)