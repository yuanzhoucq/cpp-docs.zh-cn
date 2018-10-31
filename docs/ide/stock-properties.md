---
title: 常用属性 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- stock properties, about stock properties
- stock properties
ms.assetid: a89fc454-0b8e-447a-9033-4c8af46a24d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 201e6f0591d446dc0e6b036cfd7ac6f3028eb812
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430255"
---
# <a name="stock-properties"></a>常用属性

如果使用[添加属性向导](../ide/idl-attributes-add-property-wizard.md)将属性添加到 MFC 调度接口，则可从向导[名称](../ide/names-add-property-wizard.md)页的“属性名”列表中选择常用属性。 这些属性如下所示：

|属性名称|描述|
|-------------------|-----------------|
|**Appearance**|退回或设置确定控件外观的值。 控件的 Appearance 属性可包含或省略三维显示效果。 这是环境的读取/写入属性。|
|`BackColor`|返回控件的环境 `BackColor` 属性，或将其设置为调色板 (RGB) 颜色或预定义的系统颜色。 默认情况下，其值对应于控件容器的前景色。 这是环境的读取/写入属性。|
|`BorderStyle`|返回或设置控件的边框样式。 这是读取/写入属性。|
|**标题**|返回或设置控件的 Caption 属性。 标题是窗口的标题。 Caption 未包含“成员变量”实现类型。|
|**启用**|返回或设置控件的 Enabled 属性。 已启用的控件可响应用户生成的事件。|
|**字体**|返回或设置控件的环境字体。 如果控件没有字体，则为 NULL。|
|`ForeColor`|返回或设置控件的环境 `ForeColor` 属性。|
|**hWnd**|返回或设置控件的 hWnd 属性。 hWnd 未包含“成员变量”实现类型。|
|**ReadyState**|返回或设置控件的 ReadyState 属性。 控件可以取消初始化或进行初始化，也可以是正在加载，或者是交互的或完整的。 有关详细信息，请参阅 Internet SDK 中的 [READYSTATE](https://msdn.microsoft.com/library/aa768362.aspx)。|
|**文本**|返回或设置控件中包含的文本。 Text 未包含“成员变量”实现类型。|

## <a name="see-also"></a>请参阅

[添加属性](../ide/adding-a-property-visual-cpp.md)<br>
[IDL 特性，添加属性向导](../ide/idl-attributes-add-property-wizard.md)