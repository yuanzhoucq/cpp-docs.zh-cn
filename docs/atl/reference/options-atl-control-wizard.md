---
title: "选项，ATL 控件向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.control.options
dev_langs: C++
helpviewer_keywords: ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60cc90ca5d5c374c223f9fe350d1a6a7357329ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="options-atl-control-wizard"></a>选项，ATL 控件向导
在此处插入摘要的"搜索结果"。  
  
 向导的此页用于定义要创建的控件的类型，并且它包含的接口支持级别。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **控件类型**  
 你想要创建的控件的种类。  
  
-   **标准控制： ActiveX 控件。**  
  
-   **复合控件**: ActiveX 控件可以包含 （类似于对话框） 其他 ActiveX 控件或 Windows 控件。 复合控件包括：  
  
    -   用于实现复合控件的对话框中的模板。  
  
    -   自定义资源，注册表，自动注册复合控件时调用。  
  
    -   实现复合控件的 c + + 类。  
  
    -   COM 接口中，公开由复合控件。  
  
    -   包含复合控件的 HTML 测试页。  
  
     默认情况下，此控件将设置[CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)为真，以指示这是有窗口控件。 它可实现接收器映射。 有关详细信息，请参阅[支持 DHTML 控件](../../atl/atl-support-for-dhtml-controls.md)。  
  
-   **DHTML 控件**: ATL DHTML 控件指定的用户界面，使用 HTML。 DHTML UI 类包含 COM 映射。 默认情况下，此控件将设置[CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)为真，以指示这是有窗口控件。  
  
     有关详细信息，请参阅[确定 DHTML 控件项目元素](../../atl/identifying-the-elements-of-the-dhtml-control-project.md)。  
  
 **最低限度的控制**  
 支持绝对所需的大多数容器中的接口。 你可以设置**最低限度的控制**控件类型的任何： 你可以创建最小的标准控件、 最小的复合控件或最小 DHTML 控件。  
  
 **聚合**  
 添加聚合支持你创建的控件。 有关详细信息，请参阅[聚合](../../atl/aggregation.md)。  
  
-   **是**： 创建可聚合的控件。  
  
-   **不**： 创建不能聚合的控件。  
  
-   **仅**： 创建仅可以通过聚合实例化的控件。  
  
 **线程处理模型**  
 指定由控件使用的线程模型。  
  
-   **单个**： 控件将仅在主 COM 线程中运行。  
  
-   **单元**： 可以在任何单线程单元中创建控件。 默认值。  
  
 **Interface**  
 此控件可公开到容器的接口的类型。  
  
-   **双**： 创建属性和方法通过公开的接口`IDispatch`和直接通过 VTBL。  
  
-   **自定义**： 创建公开直接通过 VTBL 方法的接口。  
  
     如果你选择**自定义**，则你可以指定控件是**自动化兼容**。 如果你选择**自动化兼容**，则该向导将添加[oleautomation](../../windows/oleautomation.md)属性在 IDL，接口和在 oleaut32.dll 通用封送处理程序可以封送的接口。 请参阅[封送处理的详细信息](http://msdn.microsoft.com/library/windows/desktop/ms692621)适用于详细信息的 Windows SDK 中。  
  
     此外，如果你选择**自动化兼容**，则该控件中的所有方法的所有参数必须都是**VARIANT**兼容。  
  
 **支持**  
 设置控件的其他杂项支持。  
  
-   **连接点**： 使对象的类派生来使你的对象的连接点[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)并允许它公开源接口。  
  
-   **许可**： 将支持添加到的控件[许可](http://msdn.microsoft.com/library/windows/desktop/ms690543)。 如果客户端计算机具有正确的许可证，则仅可以承载授权的控件。  
  
## <a name="see-also"></a>请参阅  
 [ATL 控件向导](../../atl/reference/atl-control-wizard.md)

