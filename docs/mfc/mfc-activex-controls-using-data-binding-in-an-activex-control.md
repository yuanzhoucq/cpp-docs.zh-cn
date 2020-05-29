---
title: MFC ActiveX 控件：在 ActiveX 控件中使用数据绑定
ms.date: 11/19/2018
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
ms.openlocfilehash: 41ac0180242aea3143a1df2c32dc81fb18cd7dca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370781"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC ActiveX 控件：在 ActiveX 控件中使用数据绑定

ActiveX 控件的一个功能更强大的用途是数据绑定，它允许控件的属性与数据库中的特定字段绑定。 当用户修改此绑定属性中的数据时，控件会通知数据库并请求更新记录字段。 然后，数据库通知对请求成功或失败的控制。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

本文介绍任务的控制侧。 实现与数据库的数据绑定交互是控制容器的责任。 如何管理容器中的数据库交互超出了本文档的范围。 本文的其余部分介绍了如何准备数据绑定控件。

![数据&#45;绑定控件的概念图](../mfc/media/vc374v1.gif "数据&#45;绑定控件的概念图") <br/>
数据绑定控件的概念图

该`COleControl`类提供了两个成员函数，使数据绑定成为易于实现的过程。 第一个函数[绑定属性请求编辑](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit)用于请求更改属性值的权限。 [绑定属性更改](../mfc/reference/colecontrol-class.md#boundpropertychanged)，第二个函数，在属性值成功更改后调用。

本文涵盖以下主题：

- [创建可绑定股票属性](#vchowcreatingbindablestockproperty)

- [创建可绑定获取/集方法](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>创建可绑定股票属性

可以创建数据绑定的股票属性，尽管您更有可能需要[一个可绑定的 get/set 方法](#vchowcreatingbindablegetsetmethod)。

> [!NOTE]
> 默认情况下，股票属性`bindable`具有`requestedit`和 属性。

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>使用添加属性向导添加可绑定的库存属性

1. 使用[MFC ActiveX 控制向导](../mfc/reference/mfc-activex-control-wizard.md)启动项目。

1. 右键单击控件的接口节点。

   这将打开快捷菜单。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加属性**"。

1. 从**属性名称**下拉列表中选择其中一个条目。 例如，您可以选择 **"文本**"。

   由于**Text**是一个股票属性，因此已检查**可绑定**属性和**请求属性**。

1. 从**IDL 属性**选项卡中选择以下复选框：**显示绑定**和**默认绑定**，以将属性添加到项目的属性定义中的属性定义。IDL 文件。 这些属性使控件对用户可见，并使 stock 属性成为默认的可绑定属性。

此时，控件可以显示数据源中的数据，但用户将无法更新数据字段。 如果希望控件也能更新数据，请更改`OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)函数，如下所示：

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

您现在可以生成项目，该项目将注册控件。 在对话框中插入控件时，将添加 **"数据字段**"和 **"数据源"** 属性，现在可以选择要在控件中显示的数据源和字段。

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>创建可绑定获取/集方法

除了数据绑定 get/set 方法外，您还可以创建[可绑定的股票属性](#vchowcreatingbindablestockproperty)。

> [!NOTE]
> 此过程假定您有一个 ActiveX 控件项目，该项目将 Windows 控件子类。

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>使用添加属性向导添加可绑定 get/set 方法

1. 加载控件的项目。

1. 在 **"控件设置"** 页上，为控件选择要子类的窗口类。 例如，您可能希望对 EDIT 控件进行子类。

1. 加载控件的项目。

1. 右键单击控件的接口节点。

   这将打开快捷菜单。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加属性**"。

1. 在 **"属性名称"** 框中键入属性名称。 用于`MyProp`此示例。

1. 从 **"属性类型**"下拉列表框中选择数据类型。 此示例使用**短。**

1. 对于“实现类型” ****，请单击“Get/Set 方法” ****。

1. 从 IDL 属性选项卡中选择以下复选框：**可绑定**、**请求、****显示绑定**和**默认绑定**，以将属性添加到项目的属性定义中的属性定义。IDL 文件。 这些属性使控件对用户可见，并使 stock 属性成为默认的可绑定属性。

1. 单击“完成”  。

1. 修改函数的`SetMyProp`正文，以便它包含以下代码：

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. 传递给`BoundPropertyChanged`和`BoundPropertyRequestEdit`函数的参数是 属性的"不pid"，该属性是传递给 中属性的 id（） 属性的参数。IDL 文件。

1. 修改[OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)函数，以便它包含以下代码：

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. 修改函数`OnDraw`，以便它包含以下代码：

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. 到标头文件的公共部分，控件类的标头文件，为成员变量添加以下定义（构造函数）：

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. 使以下行成为函数中的最后一`DoPropExchange`行：

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. 修改函数`OnResetState`，以便它包含以下代码：

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. 修改函数`GetMyProp`，以便它包含以下代码：

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

您现在可以生成项目，该项目将注册控件。 在对话框中插入控件时，将添加 **"数据字段**"和 **"数据源"** 属性，现在可以选择要在控件中显示的数据源和字段。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)
