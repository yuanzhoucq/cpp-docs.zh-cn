---
title: MFC ActiveX 控件：添加自定义属性
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 5014a32386a0a140f0fdc00b23a0ac24a54afcee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626148"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC ActiveX 控件：添加自定义属性

自定义属性不同于中的常用属性，因为自定义属性尚未由 `COleControl` 类实现。 自定义属性用于向使用控件的程序员公开某个特定的或外观的 ActiveX 控件。

本文介绍如何使用 "添加属性向导" 将自定义属性添加到 ActiveX 控件，并说明生成的代码修改。 主题包括：

- [使用 "添加属性向导" 添加自定义属性](#_core_using_classwizard_to_add_a_custom_property)

- [为自定义属性添加属性向导更改](#_core_classwizard_changes_for_custom_properties)

自定义属性分为四种实现方式：成员变量、带有通知的成员变量、Get/Set 方法和参数化。

- 成员变量实现

   此实现将属性的状态表示为控件类中的成员变量。 当属性值更改不重要时，使用成员变量实现。 在这三种类型中，此实现为属性创建的支持代码数量最少。 成员变量实现的调度映射条目宏[DISP_PROPERTY](reference/dispatch-maps.md#disp_property)。

- 具有通知实现的成员变量

   此实现由 "添加属性向导" 创建的成员变量和通知函数组成。 在属性值更改后，框架会自动调用通知函数。 如果需要在属性值更改后收到通知，请将成员变量与通知实现一起使用。 此实现需要更多时间，因为它需要一个函数调用。 此实现的调度映射条目宏[DISP_PROPERTY_NOTIFY](reference/dispatch-maps.md#disp_property_notify)。

- 获取/设置方法实现

   此实现包含控件类中的一对成员函数。 当控件的用户请求属性的当前值，并在控件的用户请求属性发生更改时，Get/Set 方法实现将自动调用 Get 成员函数。 当你需要在运行时计算属性的值、在更改实际属性之前验证控件用户传递的值，或实现只读或只写属性类型时，请使用此实现。 此实现的调度映射条目宏[DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex)。 以下部分[使用 "添加属性向导" 添加自定义属性](#_core_using_classwizard_to_add_a_custom_property)，使用 CircleOffset 自定义属性来演示此实现。

- 参数化实现

   "添加属性向导" 支持参数化实现。 参数化属性（有时称为属性数组）可用于通过控件的单个属性访问一组值。 此实现的调度映射条目宏 DISP_PROPERTY_PARAM。 有关实现此类型的详细信息，请参阅文章 ActiveX 控件：高级主题中的[实现参数化属性](mfc-activex-controls-advanced-topics.md)。

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a>使用 "添加属性向导" 添加自定义属性

下面的过程演示了如何添加自定义属性 CircleOffset，该属性使用 Get/Set 方法实现。 CircleOffset 自定义属性允许控件的用户从控件边框的中心偏移圆圈。 使用 Get/Set 方法之外的实现添加自定义属性的过程非常相似。

此过程也可用于添加其他所需的自定义属性。 替换 CircleOffset 属性名称和参数的自定义属性名称。

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>使用 "添加属性向导" 添加 CircleOffset 自定义属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加属性**"。

   这将打开 "[添加属性向导](../ide/names-add-property-wizard.md)"。

1. 在 "**属性名称**" 框中，键入*CircleOffset*。

1. 对于“实现类型” ****，请单击“Get/Set 方法” ****。

1. 在 "**属性类型**" 框中，选择**short**。

1. 为 Get 和 Set 函数键入唯一的名称，或接受默认名称。

1. 单击“完成”。

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a>为自定义属性添加属性向导更改

添加 CircleOffset 自定义属性时，添加属性向导会更改标头（。H）和实现（。CPP）文件。

以下行将添加到中。用于声明两个名为和的函数的 H 文件 `GetCircleOffset` `SetCircleOffset` ：

[!code-cpp[NVC_MFC_AxUI#25](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

以下行将添加到控件的。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#26](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

此行将 CircleOffset 属性指定为特定 ID 号，从该方法在添加属性向导的 "方法和属性" 列表中获取。

此外，还会将以下行添加到调度映射中（在中）。用于将 CircleOffset 属性映射到控件的两个处理函数的 CPP 文件：

[!code-cpp[NVC_MFC_AxUI#27](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

最后，将 `GetCircleOffset` 和函数的实现 `SetCircleOffset` 添加到控件的末尾。CPP 文件。 在大多数情况下，你将修改 Get 函数以返回属性的值。 集函数通常包含应在属性更改之前或之后执行的代码。

[!code-cpp[NVC_MFC_AxUI#28](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

请注意，添加属性向导会自动向集函数的主体添加对[SetModifiedFlag](reference/colecontrol-class.md#setmodifiedflag)的调用。 调用此函数会将控件标记为已修改。 如果控件已被修改，则在保存该容器时会保存其新状态。 每当作为控件持久状态的一部分保存的属性更改值时，都应调用此函数。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：属性](mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控件：方法](mfc-activex-controls-methods.md)<br/>
[COleControl 类](reference/colecontrol-class.md)
