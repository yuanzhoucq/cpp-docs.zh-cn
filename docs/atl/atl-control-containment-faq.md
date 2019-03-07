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
ms.openlocfilehash: 42f9b41b99e13fcfe2fb003acb348c9464e0fd05
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296561"
---
# <a name="atl-control-containment-faq"></a>ATL 控件包含常见问题

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>哪些 ATL 类促进 ActiveX 控件包含？

ATL 的控件承载代码不会要求你使用任何 ATL 类;您可以只需创建 **"AtlAxWin80"** 窗口和控件承载 API，如有必要使用 (有关详细信息，请参阅**什么是 ATL 控件承载 API**。 但是，以下类使包含功能易于使用。

|类|描述|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|包装 **"AtlAxWin80"** 窗口中，提供用于创建窗口、 创建控件和/或将一个控件附加到窗口，并检索该主机对象上的接口指针的方法。|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|包装 **"AtlAxWinLic80"** 窗口中，提供用于创建窗口、 创建控件和/或将一个授权的控件附加到窗口，并检索该主机对象上的接口指针的方法。|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|充当基于对话框资源的 ActiveX 控件类的基类。 此类控件可以包含其他 ActiveX 控件。|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|充当基于对话框资源的对话框类的基类。 此类对话框可以包含 ActiveX 控件。|
|[CWindow](../atl/reference/cwindow-class.md)|提供了一种方法， [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol)，这将返回的接口指针上的控件，给定及其主机窗口的 ID。 此外，Windows API 包装器公开的`CWindow`通常使窗口管理更加轻松。|

## <a name="what-is-the-atl-control-hosting-api"></a>什么是 ATL 控件承载 API？

ATL 的控件承载 API 是允许任何窗口，使其作为 ActiveX 控件容器的函数集。 这些函数可以是静态或动态链接到你的项目，因为它们可为源代码和由 ATL90.dll 公开。 下表中列出的控件承载的函数。

|函数|描述|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|创建主机对象，将其连接到提供的窗口，然后将附加现有的控件。|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|创建主机对象，将其连接到提供的窗口，然后加载控件。|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|创建授权的 ActiveX 控件，初始化它，并在指定窗口中，类似于承载[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)。|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|创建主机对象，将其连接到提供的窗口，然后加载控件 （也允许事件接收器设置）。|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|创建授权的 ActiveX 控件，初始化它，并在指定窗口中，类似于承载[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)。|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|通过对话框资源创建无模式对话框并返回窗口句柄。|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|从对话框资源创建模式对话框。|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|返回**IUnknown**承载在窗口中的控件的接口指针。|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|返回**IUnknown**接口指针的宿主对象连接到一个窗口。|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|初始化控件承载代码。|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|取消初始化的控件承载代码。|

`HWND`中前三个函数的参数必须是现有 （几乎） 任何类型的窗口。 如果显式调用这三个函数的任何 （通常情况下，不需要），请不要将句柄传递到已充当主机窗口 （如果这样做，现有的宿主对象将不会释放）。

前七个函数调用[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)隐式。

> [!NOTE]
>  控件承载 API 窗体的 ActiveX 控件包含的 ATL 的支持的基础。 但是，通常会有很少需要直接调用这些函数，如果您充分利用或充分利用 ATL 的包装类。 有关详细信息，请参阅[的 ATL 类促进 ActiveX 控件包含](which-atl-classes-facilitate-activex-control-containment-q.md)。

## <a name="what-is-atlaxwin100"></a>什么是 AtlAxWin100？

`AtlAxWin100` 是一个窗口类来帮助提供 ATL 的控件承载功能的名称。 创建此类的实例时，窗口过程将自动使用控件承载 API 来创建与窗口相关联的主机对象，然后将其与指定为窗口的标题控件。

## <a name="when-do-i-need-to-call-atlaxwininit"></a>何时需要调用 AtlAxWinInit？

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)注册 **"AtlAxWin80"** 窗口类 （以及一些自定义窗口消息），因此在尝试创建宿主窗口之前，必须调用此函数。 但是，始终不需要自承载 Api （和使用它们的类） 显式调用此函数通常为您调用此函数。 超过一次调用此函数没有什么坏处。

## <a name="what-is-a-host-object"></a>什么是宿主对象？

主机对象是 COM 对象，表示为特定窗口提供由 ATL ActiveX 控件容器。 该主机对象子类容器窗口中，以便它可以反映到该控件的消息，它提供必要的容器接口，由该控件，并且将公开[IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md)和[IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md)接口以便可以将该控件的环境配置。

可以使用该主机对象来设置容器的环境属性。

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>可以托管多个控件中的单个窗口？

不可以托管多个控件中单个 ATL 主机窗口。 每个主机窗口旨在 （这允许一个简单的机制，用于处理消息反射和控制每个环境属性） 一次存放一个控件。 但是，如果需要用户若要查看单个窗口中的多个控件，则可以轻松地为该窗口的子级创建多个主机窗口。

## <a name="can-i-reuse-a-host-window"></a>可以重复使用宿主窗口？

建议不要重复使用宿主窗口。 若要确保你的代码的可靠性，应将绑定到单个控件的生命周期主机窗口的生存期。

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>何时需要调用 AtlAxWinTerm？

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)注销 **"AtlAxWin80"** 窗口类。 所有现有主机窗口已销毁之后，应 （如果不再需要创建主机 windows） 调用此函数。 如果不调用此函数，窗口类将自动取消注册在进程终止时。

## <a name="hosting-activex-controls-using-atl-axhost"></a>使用 ATL AXHost 承载 ActiveX 控件

本部分中的示例演示如何创建 AXHost 以及如何托管 ActiveX 控件使用各种 ATL 函数。 它还演示如何访问控制和接收器事件 (使用[IDispEventImpl](../atl/reference/idispeventimpl-class.md)) 从承载的控件。 此示例承载日历控件在主窗口中或在子窗口。

请注意，定义`USE_METHOD`符号。 可以更改此符号来改变介于 1 和 8 之间的值。 符号的值确定将如何创建控件：

- 偶数值`USE_METHOD`，调用创建主机子类的窗口，并将它转换为控件宿主。 对于奇数的值，该代码创建充当一个主机的子窗口。

- 值的`USE_METHOD`之间 1 和 4 中，访问控制和接收的事件都完成的调用还会创建该主机中。 介于 5 到 8 之间的值查询接口的主机，并挂接接收器。

摘要如下：

|USE_METHOD|Host|控制访问和事件接收|说明的函数|
|-----------------|----------|--------------------------------------|---------------------------|
|1|子窗口|一个步骤|CreateControlLicEx|
|2|主窗口|一个步骤|AtlAxCreateControlLicEx|
|3|子窗口|一个步骤|CreateControlEx|
|4|主窗口|一个步骤|AtlAxCreateControlEx|
|5|子窗口|多个步骤|CreateControlLic|
|6|主窗口|多个步骤|AtlAxCreateControlLic|
|7|子窗口|多个步骤|CreateControl|
|8|主窗口|多个步骤|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>请参阅

[控件包含常见问题](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[CAxWindow2T 类](../atl/reference/caxwindow2t-class.md)<br/>
[IAxWinHostWindowLic 接口](../atl/reference/iaxwinhostwindowlic-interface.md)
