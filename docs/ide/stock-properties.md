---
title: 常用属性 |Microsoft 文档
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
ms.openlocfilehash: a3586fb33c30148c870b096d0d49a41d7ad8c6c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="stock-properties"></a>常用属性
如果你将属性添加到 MFC 调度接口使用[添加属性向导](../ide/idl-attributes-add-property-wizard.md)，您可以选择从常用属性**属性名称**列入[名称](../ide/names-add-property-wizard.md)页向导。 这些属性如下所示：  
  
|属性名称|描述|  
|-------------------|-----------------|  
|**外观**|返回或设置一个值，确定控件的外观。 控件的**外观**属性可以包括或忽略三维显示效果。 这是环境的读/写属性。|  
|`BackColor`|返回或设置控件的环境`BackColor`到调色板 (RGB) 颜色或预定义的系统颜色的属性。 默认情况下，其值对应于控件的容器的前景色。 这是环境的读/写属性。|  
|`BorderStyle`|返回或设置控件的边框样式。 这是一个读/写属性。|  
|**标题**|返回或设置控件的**标题**属性。 标题是该窗口的标题。 **标题**未包含任何**成员变量**实现类型。|  
|**启用**|返回或设置控件的**已启用**属性。 启用的控件可以响应用户生成的事件。|  
|**字体**|返回或设置控件的环境字体。 如果控件具有没有字体，则为 null。|  
|`ForeColor`|返回或设置控件的环境`ForeColor`属性。|  
|**hWnd**|返回或设置控件的**hWnd**属性。 **hWnd**未包含任何**成员变量**实现类型。|  
|**ReadyState**|返回或设置控件的**ReadyState**属性。 控件均可以是未初始化、 初始化、 加载、 交互式或完成。 请参阅[READYSTATE](https://msdn.microsoft.com/en-us/library/aa768362.aspx)中*Internet SDK*有关详细信息。|  
|**文本**|返回或设置在控件中包含的文本。 **文本**未包含任何**成员变量**实现类型。|  
  
## <a name="see-also"></a>请参阅  
 [添加属性](../ide/adding-a-property-visual-cpp.md)   
 [IDL 特性，添加属性向导](../ide/idl-attributes-add-property-wizard.md)