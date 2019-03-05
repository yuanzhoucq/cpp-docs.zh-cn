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
ms.openlocfilehash: 0c1c845640be2dfaa6aeda2defb478afb650b83b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303334"
---
# <a name="mfc-activex-controls-serializing"></a>MFC ActiveX 控件：序列化

本文介绍如何序列化的 ActiveX 控件。 序列化是从读取或写入到永久存储媒体，如磁盘文件的过程。 Microsoft 基础类 (MFC) 库中类进行序列化提供了内置支持`CObject`。 `COleControl` 扩展了此支持添加到通过属性交换机制使用的 ActiveX 控件。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

通过重写实现 ActiveX 控件的序列化[COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)。 此函数中，在加载过程中调用，并保存的控件对象，将存储使用成员变量或更改通知的成员变量实现的所有属性。

下列主题介绍了与序列化的 ActiveX 控件相关的主要问题：

- 实现`DoPropExchange`函数控制对象序列化

- [自定义序列化过程](#_core_customizing_the_default_behavior_of_dopropexchange)

- [实现版本支持](#_core_implementing_version_support)

##  <a name="_core_implementing_the_dopropexchange_function"></a> 实现 DoPropExchange 函数

ActiveX 控件向导用于生成控件项目，当多个默认处理程序函数会自动添加到控件类，其中包括默认实现[COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)。 下面的示例显示了添加到使用 ActiveX 控件向导创建的类的代码：

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

如果你想要让属性保持不变，修改`DoPropExchange`通过添加对属性 exchange 函数的调用。 下面的示例演示的自定义布尔 CircleShape 属性，其中 CircleShape 属性具有默认值为序列化 **，则返回 TRUE**:

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

下表列出了可能的属性交换函数可用于序列化该控件的属性：

|属性交换函数|目标|
|---------------------------------|-------------|
|**PX_Blob( )**|序列化为二进制大型对象 (BLOB) 数据属性的类型。|
|**PX_Bool( )**|序列化类型的布尔值属性。|
|**PX_Color( )**|序列化的类型颜色属性。|
|**PX_Currency( )**|将类型序列化为**CY** （货币） 属性。|
|**PX_Double( )**|将类型序列化为**double**属性。|
|**PX_Font( )**|序列化的字体类型属性。|
|**PX_Float( )**|将类型序列化为**float**属性。|
|**PX_IUnknown( )**|序列化类型的属性`LPUNKNOWN`。|
|**PX_Long( )**|将类型序列化为**长**属性。|
|**PX_Picture( )**|序列化类型图片属性。|
|**PX_Short( )**|将类型序列化为**短**属性。|
|**PXstring( )**|序列化类型`CString`属性。|
|**PX_ULong( )**|将类型序列化为**ULONG**属性。|
|**PX_UShort( )**|将类型序列化为**USHORT**属性。|

有关这些属性交换函数的详细信息，请参阅[暂留的 OLE 控件](../mfc/reference/persistence-of-ole-controls.md)中*MFC 参考*。

##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> 自定义 DoPropExchange 的默认行为

默认实现`DoPropertyExchange`（如在上一主题中所示） 会调用基类`COleControl`。 这将自动支持的属性集序列化为`COleControl`，这将比仅自定义控件的属性进行序列化的更多存储空间。 删除此调用允许您进行序列化只显示那些您认为重要属性的对象。 对控件已实现的任何常用属性状态将不进行序列化时保存或加载的控件对象，除非显式将添加**PX_** 调用它们。

##  <a name="_core_implementing_version_support"></a> 实现版本支持

版本支持，修改后的 ActiveX 控件添加新的持久性属性，并仍将能够检测并加载该控件的早期版本创建的持久性状态。 若要使控件的版本可作为其持久性数据的一部分，调用[COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion)在该控件的`DoPropExchange`函数。 如果使用 ActiveX 控件向导创建 ActiveX 控件，将自动插入此调用。 如果不需要版本支持，则可以删除它。 但是，在控件的大小的成本是非常小 （4 字节） 的灵活性更高版本支持提供。

如果未使用 ActiveX 控件向导创建控件，添加对的调用`COleControl::ExchangeVersion`的方法是插入以下行的开头你`DoPropExchange`函数 (对调用之前`COleControl::DoPropExchange`):

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

你可以使用任何**DWORD**作为版本号。 项目生成的 ActiveX 控件向导使用`_wVerMinor`和`_wVerMajor`为默认值。 这些是项目的 ActiveX 控件类的实现文件中定义的全局常量。 中的其余部分您`DoPropExchange`函数，可以调用[CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion)在任何时间，以检索要保存或检索的版本。

在以下示例中，版本 1 的此示例控件具有"ReleaseDate"属性。 版本 2 添加了一个"OriginalDate"属性。 如果指示控件时要加载的持久状态从旧版本，则会初始化为默认值的新属性的成员变量。

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

默认情况下，控件""旧数据转换为最新的格式。 例如，如果版本 2 的控件加载保存的版本 1 的数据，它将再次保存时编写第 2 版格式。 如果你想要将数据保存在格式最后一次阅读的控件，则传递**FALSE**作为第三个参数调用时`ExchangeVersion`。 此第三个参数是可选的它是 **，则返回 TRUE**默认情况下。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)
