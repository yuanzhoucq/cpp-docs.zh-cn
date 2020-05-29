---
title: ATL 控件包含常见问题
ms.date: 11/04/2016
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
ms.openlocfilehash: 36ff3381447b46b28908522d65be9f34fe23addf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317404"
---
# <a name="atl-control-containment-faq"></a>ATL 控件包含常见问题

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>哪些 ATL 类促进 ActiveX 控件包含？

ATL 的控制托管代码不要求您使用任何 ATL 类;您可以简单地创建一个 **"AtlAxWin80"** 窗口，并在必要时使用控制托管 API（有关详细信息，请参阅**什么是 ATL 控制托管 API。** 但是，以下类使包含功能更易于使用。

|类|说明|
|-----------|-----------------|
|[萨克斯窗口](../atl/reference/caxwindow-class.md)|包装 **"AtlAxWin80"** 窗口，提供创建窗口、创建控件和/或将控件附加到窗口以及检索主机对象上的接口指针的方法。|
|[萨克斯窗口2T](../atl/reference/caxwindow2t-class.md)|包装 **"AtlAxWinLic80"** 窗口，提供创建窗口、创建控件和/或将许可控件附加到窗口以及检索主机对象上的接口指针的方法。|
|[CCom复合控制](../atl/reference/ccomcompositecontrol-class.md)|充当基于对话框资源的 ActiveX 控件类的基类。 此类控件可以包含其他 ActiveX 控件。|
|[CAx对话](../atl/reference/caxdialogimpl-class.md)|充当基于对话框资源的对话框类的基类。 此类对话框可以包含 ActiveX 控件。|
|[CWindow](../atl/reference/cwindow-class.md)|提供一种方法[GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol)，该方法将在控件上返回接口指针，给定其主机窗口的 ID。 此外，通常通过打开的`CWindow`Windows API 包装器使窗口管理更加容易。|

## <a name="what-is-the-atl-control-hosting-api"></a>什么是 ATL 控件承载 API？

ATL 的控制宿主 API 是允许任何窗口充当 ActiveX 控制容器的功能集。 这些函数可以静态或动态地链接到您的项目中，因为它们可作为源代码提供，并由 ATL90.dll 公开。 下表列出了控制托管功能。

|函数|说明|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|创建主机对象，将其连接到提供的窗口，然后附加现有控件。|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|创建主机对象，将其连接到提供的窗口，然后加载控件。|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|创建许可的 ActiveX 控件，初始化它，并将其托管在指定的窗口中，类似于[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)。|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|创建主机对象，将其连接到提供的窗口，然后加载控件（还允许设置事件接收器）。|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|创建许可的 ActiveX 控件，初始化它，并将其托管在指定的窗口中，类似于[AtlAxCreateControllic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)。|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|从对话框资源创建无模式对话框并返回窗口句柄。|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|从对话框资源创建模式对话框。|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|返回托管在窗口中的控件的**I 未知**接口指针。|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|返回连接到窗口的主机对象的**I 未知**接口指针。|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|初始化控件托管代码。|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|取消初始化控件托管代码。|

前`HWND`三个函数中的参数必须是（几乎）任何类型的现有窗口。 如果显式调用这三个函数中的任何一个（通常，您不必这样做），则不要将句柄传递给已充当主机的窗口（如果这样做，则不会释放现有主机对象）。

前七个函数隐式调用[AtlAxWininit。](reference/composite-control-global-functions.md#atlaxwininit)

> [!NOTE]
> 控制托管 API 构成了 ATL 支持 ActiveX 控制遏制的基础。 但是，如果您利用或充分利用 ATL 的包装类，通常不需要直接调用这些函数。 有关详细信息，请参阅哪些[ATL 类有助于 ActiveX 控制遏制](which-atl-classes-facilitate-activex-control-containment-q.md)。

## <a name="what-is-atlaxwin100"></a>什么是 AtlAxWin100？

`AtlAxWin100`是有助于提供 ATL 控制托管功能的窗口类的名称。 创建此类的实例时，窗口过程将自动使用控件宿主 API 创建与窗口关联的主机对象，并使用指定为窗口标题的控件加载该对象。

## <a name="when-do-i-need-to-call-atlaxwininit"></a>何时需要调用 AtlAxWinInit？

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)注册 **"AtlAxWin80"** 窗口类（加上几个自定义窗口消息），因此在尝试创建主机窗口之前必须调用此函数。 但是，您并不总是需要显式调用此函数，因为托管 API（以及使用它们的类）通常为您调用此函数。 多次调用此函数没有坏处。

## <a name="what-is-a-host-object"></a>什么是宿主对象？

主机对象是表示 ATL 为特定窗口提供的 ActiveX 控制容器的 COM 对象。 主机对象对容器窗口进行子类化，以便它可以向控件反映消息，它提供了控件使用的必要容器接口，并公开[IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md)和[IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md)接口，以允许您配置控件的环境。

可以使用主机对象设置容器的环境属性。

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>是否可在单个窗口中承载多个控件？

不可能在单个 ATL 主机窗口中承载多个控件。 每个主机窗口都设计为一次完全保留一个控件（这允许一个简单的机制来处理消息反射和每个控件的环境属性）。 但是，如果需要用户在单个窗口中看到多个控件，则创建多个主机窗口作为该窗口的子级是件简单的事情。

## <a name="can-i-reuse-a-host-window"></a>是否可重复使用宿主窗口？

不建议您重复使用主机窗口。 为了确保代码的鲁棒性，应将主机窗口的生存期与单个控件的生存期绑定。

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>何时需要调用 AtlAxWinTerm？

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)取消注册 **"AtlAxWin80"** 窗口类。 在销毁所有现有主机窗口后，应调用此函数（如果不再需要创建主机窗口）。 如果不调用此函数，则进程终止时将自动取消注册窗口类。

## <a name="hosting-activex-controls-using-atl-axhost"></a>使用 ATL AXHost 承载 ActiveX 控件

本节中的示例演示如何创建 AXHost 以及如何使用各种 ATL 函数托管 ActiveX 控件。 它还演示如何从托管的控件访问控件和接收器事件（使用[IDispEventImpl）。](../atl/reference/idispeventimpl-class.md) 该示例在主窗口中或子窗口中承载"日历"控件。

请注意符号的定义`USE_METHOD`。 您可以更改此符号的值，以介于 1 和 8 之间。 符号的值决定了如何创建控件：

- 对于 偶数值`USE_METHOD`，创建主机子类的调用将窗口转换为控件主机。 对于奇数值，代码将创建充当主机的子窗口。

- 对于`USE_METHOD`介于 1 和 4 之间的值，在同时创建主机的调用中完成对事件的控制和下沉的访问。 值介于 5 和 8 之间，查询主机的接口并挂接接收器。

摘要如下：

|USE_METHOD|主机|控制访问和事件下沉|演示功能|
|-----------------|----------|--------------------------------------|---------------------------|
|1|子窗口|一步|创建控制|
|2|主窗口|一步|AtlAxCreateControlLicEx|
|3|子窗口|一步|创建控制Ex|
|4|主窗口|一步|AtlAxCreateControlEx|
|5|子窗口|多个步骤|创建控制|
|6|主窗口|多个步骤|AtlAxCreateControlLic|
|7|子窗口|多个步骤|CreateControl|
|8|主窗口|多个步骤|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>另请参阅

[控件包含常见问题](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[CAxWindow2T 类](../atl/reference/caxwindow2t-class.md)<br/>
[IAxwinHost窗口接口](../atl/reference/iaxwinhostwindowlic-interface.md)
