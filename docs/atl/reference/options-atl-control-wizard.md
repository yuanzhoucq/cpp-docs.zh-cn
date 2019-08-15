---
title: 选项，ATL 控件向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 25db3995687011de5e9cc0a98506cd26f2f1af0b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495442"
---
# <a name="options-atl-control-wizard"></a>选项，ATL 控件向导

使用向导的此页定义要创建的控件的类型以及它所包含的接口支持的级别。

## <a name="uielement-list"></a>UIElement 列表

### <a name="control-type"></a>控件类型

要创建的控件的类型。

- **标准控件**:ActiveX 控件。

- **复合控件**:一个 ActiveX 控件, 它可以包含其他 ActiveX 控件或 Windows 控件 (类似于对话框)。 复合控件包括以下内容:

  - 用于实现复合控件的对话框的模板。

  - 自定义资源, 用于在调用时自动注册复合控件的注册表。

  - 实现C++复合控件的类。

  - 一个 COM 接口, 由复合控件公开。

  - 包含复合控件的 HTML 测试页。

    默认情况下, 此控件将[CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)设置为 true, 以指示这是一个有窗口的控件。 它实现接收器映射。 有关详细信息, 请参阅[支持 DHTML 控制](../../atl/atl-support-for-dhtml-controls.md)。

- **DHTML 控件**:ATL DHTML 控件使用 HTML 指定用户界面。 DHTML UI 类包含 COM 映射。 默认情况下, 此控件将[CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)设置为 true, 以指示这是一个有窗口的控件。

   有关详细信息, 请参阅[标识 DHTML 控件项目的元素](../../atl/identifying-the-elements-of-the-dhtml-control-project.md)。

### <a name="minimal-control"></a>最小控制

仅支持大多数容器绝对需要的接口。 可以为任何控件类型设置**最小控制**: 可以创建最小标准控件、最小复合控件或最小 DHTML 控件。

### <a name="aggregation"></a>聚合

为正在创建的控件添加聚合支持。 有关详细信息, 请参阅[聚合](../../atl/aggregation.md)。

- **是**:创建可以聚合的控件。

- **否**:创建无法聚合的控件。

- **仅限**:创建只能通过聚合实例化的控件。

### <a name="threading-model"></a>线程模型

指定控件使用的线程模型。

- **单一**:控件将仅在主 COM 线程中运行。

- **单元**:可以在任何单线程单元中创建控件。 默认值。

### <a name="interface"></a>接口

此控件向容器公开的接口类型。

- **双重**:创建一个接口, 该接口通过`IDispatch`和直接通过 VTBL 公开属性和方法。

- **自定义**：创建直接通过 VTBL 公开方法的接口。

   如果选择 "**自定义**", 则可以指定控件是**自动化兼容**的。 如果选择 "**自动化兼容**", 则向导会将[oleautomation](../../windows/oleautomation.md)属性添加到 IDL 中的接口, 并且接口可由 oleaut32.dll 中的通用封送拆收器进行封送处理。 有关详细信息, 请参阅 Windows SDK 中的[封送详细](/windows/win32/com/marshaling-details)信息。

   此外, 如果选择 "**自动化兼容**", 则控件中所有方法的所有参数都必须与变量兼容。

### <a name="support"></a>支持

为控件设置其他杂项支持。

- **连接点**:通过使对象的类派生自[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)并允许其公开源接口, 为对象启用连接点。

- **许可**:向控件添加对[授权](/windows/win32/com/licensing)的支持。 仅当客户端计算机具有正确的许可证时, 才能承载许可的控件。

## <a name="see-also"></a>请参阅

[ATL 控件向导](../../atl/reference/atl-control-wizard.md)
