---
title: MFC ActiveX 控件：高级的属性实现
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: 438c95c56961cc587b64e494678ade191f18ab6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392786"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC ActiveX 控件：高级的属性实现

本指南介绍了与实现高级中的 ActiveX 控件的属性相关的主题。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

- [只读和只写属性](#_core_read2donly_and_write2donly_properties)

- [从属性中返回错误代码](#_core_returning_error_codes_from_a_property)

##  <a name="_core_read2donly_and_write2donly_properties"></a> 只读和只写属性

添加属性向导提供的快速而简单的方法来实现控件的只读或只写属性。

#### <a name="to-implement-a-read-only-or-write-only-property"></a>若要实现只读或只写属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加属性**。

   这将打开[添加属性向导](../ide/names-add-property-wizard.md)。

1. 在中**属性名称**框中，键入您的属性的名称。

1. 对于“实现类型” ，请单击“Get/Set 方法” 。

1. 在中**属性类型**框中，选择适当的类型的属性。

1. 如果你想只读属性，请清除集函数名称。 如果你想只写属性，则清除 Get 函数名。

9. 单击 **“完成”**。

添加属性向导时执行此操作时，将插入函数`SetNotSupported`或`GetNotSupported`代替常规的调度映射项中设置或获取函数。

如果你想要更改现有属性为只读或只写的可以手动编辑调度映射，并从 control 类中删除不必要的 Set 或 Get 函数。

如果你想要为有条件地只读或只写 （例如，仅当在特定的模式下运行您的控件） 的属性，可以提供 Set 或 Get 函数，按正常方式，并调用`SetNotSupported`或`GetNotSupported`函数在适当的位置。 例如：

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

此代码示例会调用`SetNotSupported`如果`m_bReadOnlyMode`数据成员是**TRUE**。 如果**FALSE**，则该属性设置为新值。

##  <a name="_core_returning_error_codes_from_a_property"></a> 从属性返回错误代码

若要指示错误发生时尝试获取或设置一个属性，使用`COleControl::ThrowError`函数采用 SCODE （状态代码） 作为参数。 可以使用预定义的 SCODE 或你自己的一个定义。 预定义 SCODEs 和用于定义自定义 SCODEs 说明的列表，请参阅[ActiveX 控件中处理错误](../mfc/mfc-activex-controls-advanced-topics.md)文章 ActiveX 控件中：高级的主题。

最常见的预定义 SCODEs，例如，存在帮助器函数[colecontrol:: Setnotsupported](../mfc/reference/colecontrol-class.md#setnotsupported)， [colecontrol:: Getnotsupported](../mfc/reference/colecontrol-class.md#getnotsupported)，和[COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
>  `ThrowError` 用于返回属性的 Get 或 Set 中从错误的一种方法只可用作函数或自动化方法。 这是适当异常处理程序将出现在堆栈上的唯一时间。

有关报告其他区域中的代码的异常的详细信息，请参阅[COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror)和部分[ActiveX 控件中处理错误](../mfc/mfc-activex-controls-advanced-topics.md)文章 ActiveX 控件中：高级的主题。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)
