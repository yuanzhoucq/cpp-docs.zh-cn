---
title: 选项，ATL 控件向导 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92c3ece3ddef00161a769c0c45a4d31712d6f691
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208756"
---
# <a name="options-atl-control-wizard"></a>选项，ATL 控件向导
在此处插入摘要的"搜索结果"。  
  
 在向导的此页用于定义要创建的控件的类型和它包含的接口支持的级别。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **控件类型**  
 想要创建的控件类型。  
  
-   **标准控件： ActiveX 控件。**  
  
-   **复合控件**: ActiveX 控件可以包含 （类似于一个对话框） 的其他 ActiveX 控件或 Windows 控件。 复合控件包括：  
  
    -   用于实现复合控件的对话框中的模板。  
  
    -   自定义资源，注册表，会自动注册复合控件时调用。  
  
    -   实现复合控件的 c + + 类。  
  
    -   复合控件公开一个 COM 接口。  
  
    -   包含复合控件的 HTML 测试页。  
  
     默认情况下，此控件设置[CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)为 true，以指示这是有窗口的控件。 它实现了接收器映射。 有关详细信息，请参阅[支持 DHTML 控件](../../atl/atl-support-for-dhtml-controls.md)。  
  
-   **DHTML 控件**: ATL DHTML 控件指定用户界面，使用 HTML。 DHTML UI 类包含 COM 映射。 默认情况下，此控件设置[CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)为 true，以指示这是有窗口的控件。  
  
     有关详细信息，请参阅[标识 DHTML 控件项目的元素](../../atl/identifying-the-elements-of-the-dhtml-control-project.md)。  
  
 **最低限度的控制**  
 支持大多数容器绝对所需的接口。 可以设置**最低限度的控制**任何控件类型： 您可以创建最小标准控件、 最小的复合控件或最小的 DHTML 控件。  
  
 **聚合**  
 添加聚合支持您创建的控件。 有关详细信息，请参阅[聚合](../../atl/aggregation.md)。  
  
-   **是**： 创建可聚合的控件。  
  
-   **不**： 创建不能聚合的控件。  
  
-   **仅**： 创建仅可以通过聚合实例化的控件。  
  
 **线程处理模型**  
 指定由控件使用的线程模型。  
  
-   **单个**： 控件将仅在主 COM 线程中运行。  
  
-   **单元**： 可以在任何单线程单元中创建控件。 默认值。  
  
 **Interface**  
 此控件向容器公开的接口的类型。  
  
-   **双**： 创建属性和方法通过公开的接口`IDispatch`以及直接通过 VTBL。  
  
-   **自定义**： 创建一个直接通过 VTBL 公开方法的接口。  
  
     如果选择**自定义**，则可以指定的控件是**自动化兼容**。 如果选择**自动化兼容**，然后该向导将添加[oleautomation](../../windows/oleautomation.md)属性到 idl，接口和接口可以封送处理中 oleaut32.dll 通用封送处理程序。 请参阅[封送处理的详细信息](/windows/desktop/com/marshaling-details)Windows SDK for 的详细信息中。  
  
     此外，如果您选择**自动化兼容**，则在控件中的所有方法的所有参数必须都是变体兼容。  
  
 **支持**  
 设置控件的其他杂项支持。  
  
-   **连接点**： 使对象的类派生来使您的对象的连接点[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)并使其能够公开源接口。  
  
-   **许可**： 将支持添加到的控件[许可](/windows/desktop/com/licensing)。 如果客户端计算机具有正确的许可证，则仅可以托管授权的控件。  
  
## <a name="see-also"></a>请参阅  
 [ATL 控件向导](../../atl/reference/atl-control-wizard.md)

