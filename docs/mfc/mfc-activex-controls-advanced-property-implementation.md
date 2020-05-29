---
title: MFC ActiveX 控件：高级属性实现
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: d4f1265e6540e9f84bdb680e7948a4e308d31bb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364652"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC ActiveX 控件：高级属性实现

本文介绍了与在 ActiveX 控件中实现高级属性相关的主题。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

- [只读和只写属性](#_core_read2donly_and_write2donly_properties)

- [从属性返回错误代码](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>只读和只写属性

Add 属性向导提供了一种快速简便的方法，用于实现控件的只读或只写属性。

#### <a name="to-implement-a-read-only-or-write-only-property"></a>实现只读或只写属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加属性**"。

   这将打开[添加属性向导](../ide/names-add-property-wizard.md)。

1. 在 **"属性名称"** 框中，键入属性的名称。

1. 对于“实现类型” ****，请单击“Get/Set 方法” ****。

1. 在 **"属性类型"** 框中，为属性选择正确的类型。

1. 如果需要只读属性，请清除 Set 函数名称。 如果需要仅写入属性，请清除 Get 函数名称。

1. 单击“完成”  。

执行此操作时，"添加属性向导"将函数插入函数`SetNotSupported`或`GetNotSupported`调度映射条目中，以代替正常的"设置"或"Get"函数。

如果要将现有属性更改为只读或只写，可以手动编辑调度映射，并从控件类中删除不必要的"设置"或"Get"函数。

如果希望属性是有条件只读或只写（例如，仅在控件在特定模式下运行时），则可以像往常一样提供"设置"或"Get"函数，并在适当情况下调用`SetNotSupported`或`GetNotSupported`函数。 例如：

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

如果数据成员为`SetNotSupported` `m_bReadOnlyMode` **TRUE，** 则此代码示例调用 。 如果**FALSE**，则属性设置为新值。

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>从属性返回错误代码

要指示在尝试获取或设置属性时发生错误，请使用`COleControl::ThrowError`函数，该函数以 SCODE（状态代码）为参数。 您可以使用预定义的 SCODE 或定义您自己的 SCODE。 有关预定义的 SCOD 列表和用于定义自定义 SCOD 的说明，请参阅["ActiveX"控件中的"处理活动X"控件中的错误](../mfc/mfc-activex-controls-advanced-topics.md)：高级主题。

帮助器函数存在于最常见的预定义的 SCOD 中，例如[COleControl：设置不受支持](../mfc/reference/colecontrol-class.md#setnotsupported)[、COleControl：：未受支持](../mfc/reference/colecontrol-class.md#getnotsupported)，以及[COleControl：设置不允许](../mfc/reference/colecontrol-class.md#setnotpermitted)。

> [!NOTE]
> `ThrowError`仅用于用作从属性的 Get 或 Set 函数或自动化方法中返回错误的方法。 这是适当异常处理程序将出现在堆栈上的唯一时间。

有关报告代码其他区域中的异常的详细信息，请参阅[COleControl：：FireError](../mfc/reference/colecontrol-class.md#fireerror)和["ActiveX 控件中处理"活动X控制中的错误](../mfc/mfc-activex-controls-advanced-topics.md)"一节：高级主题。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)
