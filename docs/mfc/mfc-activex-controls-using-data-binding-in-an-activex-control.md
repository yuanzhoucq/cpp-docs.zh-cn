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
ms.openlocfilehash: b32dbd8e1777f11998085a90e8851b25e4298e1a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224989"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC ActiveX 控件：在 ActiveX 控件中使用数据绑定

ActiveX 控件的一个功能更强大的用途是数据绑定，它允许控件的属性绑定到数据库中的特定字段。 当用户修改此绑定属性中的数据时，控件将通知数据库，并请求更新记录字段。 然后，数据库通知控制请求是成功还是失败。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

本文介绍任务的控件端。 实现与数据库的数据绑定交互是控件容器的责任。 在容器中管理数据库交互的方式超出了本文档的范围。 本文的其余部分介绍了如何准备控件以便进行数据绑定。

![数据&#45;绑定控件的概念关系图](../mfc/media/vc374v1.gif "数据&#45;绑定控件的概念关系图") <br/>
数据绑定控件的概念图

`COleControl`类提供两个成员函数，使数据绑定成为实现的简单过程。 第一个函数[BoundPropertyRequestEdit](reference/colecontrol-class.md#boundpropertyrequestedit)用于请求更改属性值的权限。 [BoundPropertyChanged](reference/colecontrol-class.md#boundpropertychanged)，第二个函数在属性值成功更改后调用。

本文涵盖以下主题：

- [创建可绑定的常用属性](#vchowcreatingbindablestockproperty)

- [创建可绑定的 Get/Set 方法](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>创建可绑定的常用属性

尽管更有可能需要可[绑定的 get/set 方法](#vchowcreatingbindablegetsetmethod)，但也可以创建数据绑定的常用属性。

> [!NOTE]
> `bindable`默认情况下，Stock 属性具有和 `requestedit` 属性。

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>使用 "添加属性向导" 添加可绑定的常用属性

1. 使用[MFC ActiveX 控件向导](reference/mfc-activex-control-wizard.md)启动项目。

1. 右键单击控件的接口节点。

   这会打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加属性**"。

1. 从 "**属性名称**" 下拉列表中选择一个条目。 例如，您可以选择**文本**。

   由于**Text**是常用属性，因此已检查可**绑定**属性和**requestedit**属性。

1. 从 " **IDL 特性**" 选项卡中选择以下复选框： **displaybind**和**defaultbind** ，以将特性添加到项目的中的属性定义。IDL 文件。 这些属性使控件对用户可见，并使 stock 属性成为默认的可绑定属性。

此时，您的控件可以显示数据源中的数据，但用户将无法更新数据字段。 如果希望控件也能够更新数据，请将 `OnOcmCommand` [OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md)函数更改为如下所示：

[!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

现在可以生成项目，该项目将注册控件。 在对话框中插入控件时，将添加**数据字段**和**数据源**属性，您现在可以选择要在控件中显示的数据源和字段。

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>创建可绑定的 Get/Set 方法

除了数据绑定的 get/set 方法之外，还可以创建可[绑定的常用属性](#vchowcreatingbindablestockproperty)。

> [!NOTE]
> 此过程假定你有一个用于对 Windows 控件进行子类控制的 ActiveX 控件项目。

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>使用 "添加属性向导" 添加可绑定的 get/set 方法

1. 加载控件的项目。

1. 在 "**控件设置**" 页上，为控件选择要划分子类的窗口类。 例如，你可能想要为编辑控件划分子类。

1. 加载控件的项目。

1. 右键单击控件的接口节点。

   这会打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加属性**"。

1. 在 "**属性名称**" 框中键入属性名称。 在 `MyProp` 此示例中使用。

1. 从 "**属性类型**" 下拉列表框中选择一种数据类型。 在 **`short`** 此示例中使用。

1. 对于“实现类型” ****，请单击“Get/Set 方法” ****。

1. 从 "IDL 特性" 选项卡中选择以下复选框：可**绑定**、 **requestedit**、 **displaybind**和**defaultbind** ，以将特性添加到项目的中的属性定义。IDL 文件。 这些属性使控件对用户可见，并使 stock 属性成为默认的可绑定属性。

1. 单击 **“完成”** 。

1. 修改函数的主体， `SetMyProp` 使其包含以下代码：

   [!code-cpp[NVC_MFC_AxData#2](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. 传递给 `BoundPropertyChanged` 和函数的参数 `BoundPropertyRequestEdit` 是属性的 dispid，它是传递给中的属性的 id （）特性的参数。IDL 文件。

1. 修改[OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md)函数，使其包含以下代码：

   [!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. 修改 `OnDraw` 函数，使其包含以下代码：

   [!code-cpp[NVC_MFC_AxData#3](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. 对于控件类的标头文件的公共部分，为成员变量添加以下定义（构造函数）：

   [!code-cpp[NVC_MFC_AxData#4](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. 使下面的行成为函数的最后一行 `DoPropExchange` ：

   [!code-cpp[NVC_MFC_AxData#5](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. 修改 `OnResetState` 函数，使其包含以下代码：

   [!code-cpp[NVC_MFC_AxData#6](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. 修改 `GetMyProp` 函数，使其包含以下代码：

   [!code-cpp[NVC_MFC_AxData#7](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

现在可以生成项目，该项目将注册控件。 在对话框中插入控件时，将添加**数据字段**和**数据源**属性，您现在可以选择要在控件中显示的数据源和字段。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)
