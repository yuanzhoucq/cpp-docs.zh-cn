---
title: MFC ActiveX 控件：高级属性实现
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: f5abef4db2f9c6d375428c0b0fd313198ce6283f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621221"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC ActiveX 控件：高级属性实现

本文介绍与在 ActiveX 控件中实现高级属性相关的主题。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

- [只读和只写属性](#_core_read2donly_and_write2donly_properties)

- [从属性返回错误代码](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>只读和只写属性

"添加属性向导" 提供了一种快速简单的方法来实现控件的只读或只写属性。

#### <a name="to-implement-a-read-only-or-write-only-property"></a>实现只读或只写属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加属性**"。

   这将打开 "[添加属性向导](../ide/names-add-property-wizard.md)"。

1. 在 "**属性名称**" 框中，键入属性的名称。

1. 对于“实现类型” ****，请单击“Get/Set 方法” ****。

1. 在 "**属性类型**" 框中，为属性选择适当的类型。

1. 如果需要只读属性，请清除 "设置函数名称"。 如果需要只写属性，请清除 "获取函数名称"。

1. 单击“完成”。

执行此操作时，添加属性向导将 `SetNotSupported` `GetNotSupported` 在调度映射项中插入函数或，而不是正常的 Set 或 Get 函数。

如果要将现有属性更改为只读或只写，则可以手动编辑调度映射，并从控件类中删除不必要的 Set 或 Get 函数。

如果要将属性设置为条件只读或只写（例如，仅当控件在特定模式下操作时），则可以提供 "设置" 或 "获取" 函数（正常），并 `SetNotSupported` 在适当的位置调用或 `GetNotSupported` 函数。 例如：

[!code-cpp[NVC_MFC_AxUI#29](codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

`SetNotSupported`如果 `m_bReadOnlyMode` 数据成员为**TRUE**，则此代码示例会调用。 如果**为 FALSE**，则将属性设置为新值。

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>从属性返回错误代码

若要指示在尝试获取或设置属性时出错，请使用 `COleControl::ThrowError` 函数，该函数将 SCODE （状态代码）用作参数。 可以使用预定义的 SCODE，也可以定义自己的。 有关定义自定义 SCODEs 的预定义 SCODEs 的列表，请参阅文章 ActiveX 控件：高级主题中的[处理 Activex 控件](mfc-activex-controls-advanced-topics.md)中的错误。

对于最常见的预定义的 SCODEs （如[COleControl：： SetNotSupported](reference/colecontrol-class.md#setnotsupported)、 [COleControl：： GetNotSupported](reference/colecontrol-class.md#getnotsupported)和[COleControl：： SetNotPermitted](reference/colecontrol-class.md#setnotpermitted)）存在 Helper 函数。

> [!NOTE]
> `ThrowError`仅用作从属性的 Get 或 Set 函数或自动化方法中返回错误的方法。 这是适当异常处理程序将出现在堆栈上的唯一时间。

有关在代码的其他区域报告异常的详细信息，请参阅 ActiveX 控件：高级主题一文中的[COleControl：： FireError](reference/colecontrol-class.md#fireerror)和[处理 activex 控件](mfc-activex-controls-advanced-topics.md)中的错误部分。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：属性](mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控件：方法](mfc-activex-controls-methods.md)<br/>
[COleControl 类](reference/colecontrol-class.md)
