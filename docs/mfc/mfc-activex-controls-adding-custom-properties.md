---
title: MFC ActiveX 控件：添加自定义属性
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 2cc9cfa1886c6ba8e714736e0192b56bf3b154f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496416"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC ActiveX 控件：添加自定义属性

自定义属性不同于常用属性，自定义属性不会由已实现`COleControl`类。 自定义属性用于公开特定状态或使用控件的程序员 ActiveX 控件的外观。

本文介绍如何将自定义属性添加到使用添加属性向导的 ActiveX 控件，并说明生成的代码修改。 包括以下主题：

- [使用添加属性向导来添加自定义属性](#_core_using_classwizard_to_add_a_custom_property)

- [添加属性向导正在更改用于自定义属性](#_core_classwizard_changes_for_custom_properties)

自定义属性有四种实现的： 成员变量、 通知、 Get/Set 方法与参数化成员变量。

- 成员变量实现

   此实现在控件类的成员变量表示该属性的状态。 不一定要知道当属性值更改时，请使用成员变量的实现。 三种类型，此实现创建属性的支持代码量最少。 成员变量实现调度映射项宏[DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property)。

- 与通知实现的成员变量

   此实现中包含的成员变量和通过添加属性向导创建的通知函数。 属性值发生更改后通知函数自动调用框架。 成员变量时使用具有通知实现需要属性值发生更改后，收到通知。 此实现中需要更多的时间，因为它需要一个函数调用。 此实现调度映射项宏[DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify)。

- Get/Set 方法实现

   此实现包含一对中的控件类的成员函数。 Get/Set 方法实现自动调用的 Get 成员函数时该控件的用户请求的属性的当前值和 Set 成员函数时该控件的用户请求更改的属性。 当你需要在运行时计算的属性值验证实际的属性，在更改之前由该控件的用户传递的值或实现读取-或只写的属性类型，请使用此实现。 此实现调度映射项宏[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)。 以下部分中，[使用添加属性向导来添加自定义属性](#_core_using_classwizard_to_add_a_custom_property)，使用 CircleOffset 自定义属性来演示此实现。

- 参数化的实现

   添加属性向导支持参数化的实现。 （有时称为属性数组） 的参数化的属性可以用于通过您的控件的单个属性访问的一组值。 此实现的调度映射项宏是 DISP_PROPERTY_PARAM。 有关实现此类型的详细信息，请参阅[实现参数化属性](../mfc/mfc-activex-controls-advanced-topics.md)在文章的 ActiveX 控件： 高级主题。

##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> 使用添加属性向导添加自定义属性

以下过程演示如何添加自定义属性，CircleOffset，使用 Get/Set 方法的实现。 CircleOffset 自定义属性允许控件的用户控件的边框的中心圆的偏移量。 添加非 Get/Set 方法的实现的自定义属性的过程是非常相似。

此外可以使用此相同的过程添加所需的其他自定义属性。 替换为你 CircleOffset 属性名称和参数的自定义属性名称。

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>若要添加使用添加属性向导 CircleOffset 自定义属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加属性**。

   这将打开[添加属性向导](../ide/names-add-property-wizard.md)。

1. 在中**属性名称**框中，键入*CircleOffset*。

1. 对于“实现类型” ，请单击“Get/Set 方法” 。

1. 在中**属性类型**框中，选择**短**。

1. 键入 Get 和 Set 函数的唯一名称，或接受默认名称。

9. 单击 **“完成”**。

##  <a name="_core_classwizard_changes_for_custom_properties"></a> 用于自定义属性添加属性向导更改

添加属性向导时添加 CircleOffset 自定义属性，对标头进行更改 (。H） 和实现 (。控件类的 CPP) 文件。

以下行添加到。H 文件中声明两个函数调用`GetCircleOffset`和`SetCircleOffset`:

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

以下行添加到您的控件。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

此行将 CircleOffset 属性分配一个特定的 ID 号，从添加属性向导的方法和属性列表中的方法的位置。

此外，以下行添加到调度映射 (中。控件类的 CPP 文件） CircleOffset 属性映射到控件的两个处理程序函数：

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

最后，实现`GetCircleOffset`和`SetCircleOffset`函数添加到控件的末尾。CPP 文件。 在大多数情况下，将修改 Get 函数以返回属性的值。 Set 函数通常将包含之前或在属性更改后应执行的代码。

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

请注意，添加属性向导会自动添加一个调用，为[SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag)，到 Set 函数的正文。 为已修改调用此函数将控件的标记。 如果修改了一个控件，保存容器时，将保存其新状态。 每当另存为控件的持久状态的一部分的属性值更改时，应调用此函数。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)
