---
title: MFC ActiveX 控件：添加自定义属性
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 00f7a879582bca562ce626fe224206094fd19bc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364704"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC ActiveX 控件：添加自定义属性

自定义属性与股票属性不同，因为类尚未实现`COleControl`自定义属性。 自定义属性用于向使用 该控件的程序员公开 ActiveX 控件的特定状态或外观。

本文介绍如何使用"添加属性向导"向 ActiveX 控件添加自定义属性，并解释生成的代码修改。 主题包括：

- [使用"添加属性向导"添加自定义属性](#_core_using_classwizard_to_add_a_custom_property)

- [为自定义属性添加属性向导更改](#_core_classwizard_changes_for_custom_properties)

自定义属性有四种实现类型：成员变量、带有通知的成员变量、获取/设置方法和参数化。

- 成员变量实现

   此实现表示属性的状态作为控件类中的成员变量。 当不知道属性值何时更改并不重要时，请使用成员变量实现。 在三种类型中，此实现为属性创建的支持代码最少。 成员变量实现的调度映射条目宏[DISP_PROPERTY。](../mfc/reference/dispatch-maps.md#disp_property)

- 具有通知实现的成员变量

   此实现由成员变量和由添加属性向导创建的通知函数组成。 属性值更改后，框架会自动调用通知函数。 在属性值更改后需要通知时，将"成员变量"与通知实现一起使用。 此实现需要更多时间，因为它需要函数调用。 此实现的调度映射条目宏[DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify)。

- 获取/设置方法实现

   此实现由控制类中的一对成员函数组成。 当控件的用户请求属性的当前值和"设置成员"函数时，当控件的用户请求更改该属性时，"获取/设置方法"实现会自动调用 Get 成员函数。 当您需要在运行时计算属性的值、在更改实际属性之前验证控件用户传递的值或实现只读或只写属性类型时，请使用此实现。 此实现的调度映射条目宏[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)。 以下部分"[使用添加属性向导添加自定义属性](#_core_using_classwizard_to_add_a_custom_property)"使用 CircleOffset 自定义属性来演示此实现。

- 参数化实现

   添加属性向导支持参数化实现。 参数化属性（有时称为属性数组）可用于通过控件的单个属性访问一组值。 此实现的调度映射条目宏DISP_PROPERTY_PARAM。 有关实现此类型的详细信息，请参阅在"ActiveX 控件：高级主题"一文中[实现参数化属性](../mfc/mfc-activex-controls-advanced-topics.md)。

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a>使用"添加属性向导"添加自定义属性

以下过程演示了添加自定义属性 CircleOffset，它使用获取/设置方法实现。 CircleOffset 自定义属性允许控件的用户从控件的边界矩形的中心偏移圆。 使用获取/设置方法以外的实现添加自定义属性的过程非常相似。

此过程还可用于添加所需的其他自定义属性。 将自定义属性名称替换为 CircleOffset 属性名称和参数。

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>使用"添加属性向导"添加"圈偏移"自定义属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加属性**"。

   这将打开[添加属性向导](../ide/names-add-property-wizard.md)。

1. 在**属性名称**框中，键入 *"圆偏移*"。

1. 对于“实现类型” ****，请单击“Get/Set 方法” ****。

1. 在 **"属性类型"** 框中，选择 **"短**"。

1. 为获取和设置函数键入唯一名称，或接受默认名称。

1. 单击“完成”  。

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a>为自定义属性添加属性向导更改

添加"圈偏移"自定义属性时，"添加属性向导"会更改标头 （。H） 和实现 （.控制类的 CPP）文件。

以下行将添加到 。H 文件声明两个函数`GetCircleOffset`，`SetCircleOffset`称为 和 ：

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

以下行将添加到控件的 。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

此行为 CircleOffset 属性分配一个特定的 ID 号，该 ID 号取自该方法在添加属性向导的方法和属性列表中的位置。

此外，以下行将添加到调度映射（在 中）。控件类的 CPP 文件）将 CircleOffset 属性映射到控件的两个处理程序函数：

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

最后，将`GetCircleOffset`和`SetCircleOffset`函数的实现添加到控件的末尾。CPP 文件。 在大多数情况下，您将修改 Get 函数以返回属性的值。 Set 函数通常包含应在属性更改之前或之后执行的代码。

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

请注意，添加属性向导会自动将调用"[设置修改Flag"](../mfc/reference/colecontrol-class.md#setmodifiedflag)添加到 Set 函数的正文中。 调用此函数将控件标记为已修改。 如果控件已被修改，则在保存容器时将保存其新状态。 每当作为控件持久状态的一部分保存的属性更改值时，都应调用此函数。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)
