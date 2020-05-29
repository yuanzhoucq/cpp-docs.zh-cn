---
title: MFC ActiveX 控件：序列化
ms.date: 09/12/2018
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
ms.openlocfilehash: d804486b612906f537b6ed1665dfc0cec5149826
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364558"
---
# <a name="mfc-activex-controls-serializing"></a>MFC ActiveX 控件：序列化

本文讨论如何序列化 ActiveX 控件。 序列化是从持久存储介质（如磁盘文件）读取或写入的过程。 微软基础类 （MFC） 库为类`CObject`中的序列化提供了内置支持。 `COleControl`使用属换机制将此支持扩展到 ActiveX 控件。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

ActiveX 控件的序列化是通过重写[COleControl：:DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)实现的。 此函数在加载和保存控件对象期间调用，存储使用成员变量或成员变量实现的所有属性以及更改通知。

以下主题涵盖与序列化 ActiveX 控件相关的主要问题：

- 实现`DoPropExchange`对控件对象进行序列化的功能

- [自定义序列化过程](#_core_customizing_the_default_behavior_of_dopropexchange)

- [实现版本支持](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>实现 DoPropExchange 功能

当您使用 ActiveX 控件向导生成控件项目时，多个默认处理程序函数将自动添加到控件类中，包括[COleControl：:DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)的默认实现。 以下示例显示添加到使用 ActiveX 控件向导创建的类的代码：

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

如果要使属性持久化，请通过向属性`DoPropExchange`交换函数添加调用进行修改。 下面的示例演示了自定义布尔环形状属性的序列化，其中 CircleShape 属性的默认值为**TRUE**：

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

下表列出了可用于序列化控件属性的可能属换函数：

|属换功能|目标|
|---------------------------------|-------------|
|**PX_Blob）**|序列化类型二进制大对象 （BLOB） 数据属性。|
|**PX_Bool）**|序列化布尔属性类型。|
|**PX_Color）**|序列化类型颜色属性。|
|**PX_Currency）**|序列化类型**CY（** 货币）属性。|
|**PX_Double）**|序列化类型**双属性**。|
|**PX_Font）**|序列化字体类型属性。|
|**PX_Float）**|序列化类型**浮动**属性。|
|**PX_IUnknown）**|序列化类型`LPUNKNOWN`的属性。|
|**PX_Long）**|序列化类型**长**属性。|
|**PX_Picture）**|序列化类型图片属性。|
|**PX_Short）**|序列化类型**短**属性。|
|**PXstring（ ）**|序列化类型`CString`属性。|
|**PX_ULong）**|序列化类型**ULONG**属性。|
|**PX_UShort）**|序列化类型**USHORT**属性。|

有关这些属换函数的详细信息，请参阅*MFC 参考*中的[OLE 控件持久性](../mfc/reference/persistence-of-ole-controls.md)。

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>自定义 DoPropExchange 的默认行为

的`DoPropertyExchange`默认实现（如上一个主题所示）对基类`COleControl`进行调用。 这将序列化 由`COleControl`自动支持的属性集，该属性使用比仅序列化控件的自定义属性更多的存储空间。 删除此调用允许对象仅序列化您认为重要的属性。 保存或加载控件对象时，不会序列化控件已实现的任何股票属性，除非您显式添加**PX_** 调用它们。

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>实现版本支持

版本支持使修订后的 ActiveX 控件能够添加新的持久性属性，并且仍然能够检测和加载控件的早期版本创建的持久状态。 要使控件的版本作为其持久数据的一部分可用，请调用控件`DoPropExchange`函数中的[COleControl：：ExchangeVersion。](../mfc/reference/colecontrol-class.md#exchangeversion) 如果使用 ActiveX 控制向导创建 ActiveX 控件，则会自动插入此调用。 如果不需要版本支持，可以将其删除。 但是，对于版本支持提供的额外灵活性，控制大小的成本非常小（4 字节）。

如果未使用 ActiveX 控件向导创建控件，`COleControl::ExchangeVersion`请通过在`DoPropExchange`函数开头插入以下行（在调用 之前）`COleControl::DoPropExchange`添加调用。

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

您可以使用任何**DWORD**作为版本号。 由 ActiveX 控件向导生成的项目`_wVerMinor`使用`_wVerMajor`并作为默认值。 这些是在项目 ActiveX 控件类的实现文件中定义的全局常量。 在`DoPropExchange`函数的其余部分中，您可以随时调用[CPropExchange：GetVersion](../mfc/reference/cpropexchange-class.md#getversion)检索要保存或检索的版本。

在下面的示例中，此示例控件的版本 1 仅具有"发布日期"属性。 版本 2 添加了"原始日期"属性。 如果指示控件从旧版本中加载持久状态，它将新属性的成员变量初始化为默认值。

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

默认情况下，控件会将旧数据"转换为"最新格式。 例如，如果控件的版本 2 加载由版本 1 保存的数据，则当再次保存版本 2 格式时，它将编写版本 2 格式。 如果希望控件在上次读取时以格式保存数据，则在调用**FALSE**`ExchangeVersion`时将 FALSE 作为第三个参数传递。 此第三个参数是可选的，默认情况下为**TRUE。**

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)
