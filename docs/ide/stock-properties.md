---
title: "常用属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "常用属性"
  - "常用属性, 关于常用属性"
ms.assetid: a89fc454-0b8e-447a-9033-4c8af46a24d9
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 常用属性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果使用[“添加属性向导”](../ide/idl-attributes-add-property-wizard.md)向 MFC 调度接口添加属性，则可以从向导[名称](../ide/names-add-property-wizard.md)页的**“属性名称”**列表中选择常用属性。  这些属性如下所示：  
  
|属性名|说明|  
|---------|--------|  
|**外观**|返回或设置确定控件外观的值。  控件的 **Appearance** 属性可包括或省略三维显示效果。  这是一个环境读\/写属性。|  
|`BackColor`|返回控件的环境 `BackColor` 属性或将其设置为调色板 \(RGB\) 颜色或预定义的系统颜色。  默认情况下，其值对应于控件容器的前景色。  这是一个环境读\/写属性。|  
|`BorderStyle`|返回或设置控件的边框样式。  这是一个读\/写属性。|  
|**Caption**|返回或设置控件的 **Caption** 属性。  此标题是窗口的标题。  **Caption** 没有“成员变量”实现类型。|  
|**Enabled**|返回或设置控件的 **Enabled** 属性。  启用的控件可以响应用户生成的事件。|  
|**字体**|返回或设置控件的环境字体。  如果控件没有字体，则为空。|  
|`ForeColor`|返回或设置控件的环境 `ForeColor` 属性。|  
|**hWnd**|返回或设置控件的 **hWnd** 属性。  **hWnd** 没有“成员变量”实现类型。|  
|**ReadyState**|返回或设置控件的 **ReadyState** 属性。  控件可以是未初始化、已初始化、正在加载、交互或完成等状态。  有关更多信息，请参见 Internet SDK 中的 [READYSTATE](https://msdn.microsoft.com/en-us/library/aa768362.aspx)。|  
|**Text**|设置或返回包含在控件中的文本。  **Text** 没有“成员变量”实现类型。|  
  
## 请参阅  
 [添加属性](../ide/adding-a-property-visual-cpp.md)   
 [“添加属性向导”\-\>“IDL 特性”](../ide/idl-attributes-add-property-wizard.md)