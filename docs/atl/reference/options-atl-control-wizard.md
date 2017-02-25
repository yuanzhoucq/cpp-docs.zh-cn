---
title: "选项，ATL 控件向导 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.control.options"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 控件向导，选项"
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 选项，ATL 控件向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在此处插入“搜索结果”摘要。  
  
 使用此向导页定义正在创建的控件类型及其包含的接口支持级别。  
  
## UIElement 列表  
 **控件类型**  
 要创建的控件类型。  
  
-   **标准控件：ActiveX 控件。**  
  
-   **“复合控件”**：可包含（类似于对话框）其他 ActiveX 控件或 Windows 控件的 ActiveX 控件。  复合控件包含以下内容：  
  
    -   实现复合控件的对话框模板。  
  
    -   调用时自动注册复合控件的自定义资源 REGISTRY。  
  
    -   实现复合控件的 C\+\+ 类。  
  
    -   由复合控件公开的 COM 接口。  
  
    -   包含复合控件的 HTML 测试页。  
  
     默认情况下，此控件将 [CComControlBase::m\_bWindowOnly](../Topic/CComControlBase::m_bWindowOnly.md) 设置为真，以指示这是一个有窗口的控件。  它实现接收器映射。  有关更多信息，请参见 [支持 DHTML 控件](../../atl/atl-support-for-dhtml-controls.md)。  
  
-   **DHTML 控件**：ATL DHTML 控件使用 HTML 指定用户界面。  DHTML UI 类包含 COM 映射。  默认情况下，此控件将 [CComControlBase::m\_bWindowOnly](../Topic/CComControlBase::m_bWindowOnly.md) 设置为真，以指示这是一个有窗口的控件。  
  
     有关更多信息，请参见 [Identifying the Elements of the DHTML Control Project](../../atl/identifying-the-elements-of-the-dhtml-control-project.md)。  
  
 **最小控制**  
 仅支持大多数容器绝对需要的接口。  可为任何控件类型设置**“最小控制”**：可创建最小标准控件、最小复合控件或最小 DHTML 控件。  
  
 **Aggregation**  
 为正在创建的控件添加聚合支持。  有关更多信息，请参见 [Aggregation](../../atl/aggregation.md)。  
  
-   **“是”**：创建可聚合的控件。  
  
-   **“否”**：创建不能聚合的控件。  
  
-   **“仅限”**：创建只能通过聚合实例化的控件。  
  
 **线程模型**  
 指定控件使用的线程模型。  
  
-   **“单一”**：控件只在主 COM 线程内运行。  
  
-   **“单元”**：控件可以在任何单线程单元内创建。  默认值。  
  
 **接口**  
 此控件向容器公开的接口类型。  
  
-   **“双重”**：创建通过 `IDispatch` 和直接通过 VTBL 公开属性和方法的接口。  
  
-   **“自定义”**：创建直接通过 VTBL 公开方法的接口。  
  
     如果选择**“自定义”**，则可以指定控件为**“自动化兼容”**。  如果选择**“自动化兼容”**，则向导在 IDL 中添加接口的 [oleautomation](../../windows/oleautomation.md) 特性，并且接口可由 oleaut32.dll 中的通用封送拆收器封送。  有关更多信息，请参见 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的[封送处理详细信息](http://msdn.microsoft.com/library/windows/desktop/ms692621)。  
  
     另外，如果选择“自动化兼容”，则控件中所有方法的所有参数必须与 **VARIANT** 兼容。  
  
 **支持**  
 设置控件的其他杂项支持。  
  
-   **“连接点”**：通过使对象的类从 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) 派生并允许它公开源接口，为对象启用连接点。  
  
-   **“已授权”**：添加对用于[授权](http://msdn.microsoft.com/library/windows/desktop/ms690543)的控件的支持。  只有客户端计算机有正确的许可证时，才能承载授权控件。  
  
## 请参阅  
 [ATL 控件向导](../../atl/reference/atl-control-wizard.md)