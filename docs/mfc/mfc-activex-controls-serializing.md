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
ms.openlocfilehash: f5e3b4bdf203f90b3550a2521ba51ba451cf3a46
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225015"
---
# <a name="mfc-activex-controls-serializing"></a>MFC ActiveX 控件：序列化

本文介绍如何序列化 ActiveX 控件。 序列化是对持久存储介质（如磁盘文件）进行读取或写入操作的过程。 Microsoft 基础类（MFC）库为类中的序列化提供内置支持 `CObject` 。 `COleControl`通过使用属性交换机制将此支持扩展到 ActiveX 控件。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

ActiveX 控件的序列化是通过重写[COleControl：:D opropexchange](reference/colecontrol-class.md#dopropexchange)实现的。 此函数（在加载和保存控件对象的过程中调用）存储通过成员变量或具有更改通知的成员变量实现的所有属性。

以下主题介绍了有关序列化 ActiveX 控件的主要问题：

- 实现 `DoPropExchange` 函数以序列化控件对象

- [自定义序列化过程](#_core_customizing_the_default_behavior_of_dopropexchange)

- [实现版本支持](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>实现 DoPropExchange 函数

使用 ActiveX 控件向导生成控制项目时，会自动向 control 类添加几个默认的处理程序函数，包括 COleControl 的默认实现[：:D opropexchange](reference/colecontrol-class.md#dopropexchange)。 下面的示例演示添加到用 ActiveX 控件向导创建的类的代码：

[!code-cpp[NVC_MFC_AxUI#43](codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

如果要使属性持久，请 `DoPropExchange` 通过添加对属性交换函数的调用来进行修改。 下面的示例演示自定义布尔 CircleShape 属性的序列化，其中 CircleShape 属性的默认值**为 TRUE**：

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

下表列出了可用于序列化控件的属性的可能的属性交换函数：

|属性交换函数|目标|
|---------------------------------|-------------|
|**PX_Blob （）**|序列化类型二进制大型对象（BLOB）数据属性。|
|**PX_Bool （）**|序列化类型布尔属性。|
|**PX_Color （）**|序列化类型颜色属性。|
|**PX_Currency （）**|序列化类型**CY** （currency）属性。|
|**PX_Double （）**|序列化类型 **`double`** 属性。|
|**PX_Font （）**|序列化字体类型属性。|
|**PX_Float （）**|序列化类型 **`float`** 属性。|
|**PX_IUnknown （）**|序列化类型的属性 `LPUNKNOWN` 。|
|**PX_Long （）**|序列化类型 **`long`** 属性。|
|**PX_Picture （）**|序列化类型图片属性。|
|**PX_Short （）**|序列化类型 **`short`** 属性。|
|**PXstring( )**|序列化类型 `CString` 属性。|
|**PX_ULong （）**|序列化类型**ULONG**属性。|
|**PX_UShort （）**|序列化类型**USHORT**属性。|

有关这些属性交换函数的详细信息，请参阅*MFC 参考*中[的 OLE 控件的持久性](reference/persistence-of-ole-controls.md)。

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>自定义 DoPropExchange 的默认行为

`DoPropertyExchange`如前面的主题中所示，的默认实现将调用基类 `COleControl` 。 这会序列化自动支持的属性集 `COleControl` ，该属性使用比仅序列化控件的自定义属性更多的存储空间。 通过删除此调用，你的对象只会序列化你认为重要的那些属性。 在保存或加载控件对象时，不会序列化控件已经实现的任何常用属性状态，除非您显式添加了**PX_** 调用。

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>实现版本支持

版本支持使修改后的 ActiveX 控件能够添加新的持久性属性，同时仍然能够检测和加载由早期版本的控件创建的持久状态。 若要使控件的版本可作为其永久性数据的一部分，请在控件的函数中调用[COleControl：： ExchangeVersion](reference/colecontrol-class.md#exchangeversion) `DoPropExchange` 。 如果 ActiveX 控件是使用 ActiveX 控件向导创建的，则此调用会自动插入。 如果不需要版本支持，则可以将其删除。 不过，控件大小的成本非常小（4个字节），因为它提供了版本支持所提供的灵活性。

如果控件不是使用 ActiveX 控件向导创建的，则 `COleControl::ExchangeVersion` 通过在函数开头插入以下行来添加对的调用 `DoPropExchange` `COleControl::DoPropExchange` ：

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

可以使用任何**DWORD**作为版本号。 ActiveX 控件向导生成的项目使用 `_wVerMinor` 和 `_wVerMajor` 作为默认值。 这些是在项目的 ActiveX 控件类的实现文件中定义的全局常量。 在函数的其余部分中 `DoPropExchange` ，可以随时调用[CPropExchange：： GetVersion](reference/cpropexchange-class.md#getversion)来检索要保存或检索的版本。

在下面的示例中，此示例控件的第1版只有一个 "ReleaseDate" 属性。 版本2添加了 "OriginalDate" 属性。 如果指示控件从旧版本加载持久状态，则会将新属性的成员变量初始化为默认值。

[!code-cpp[NVC_MFC_AxSer#4](codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

默认情况下，控件 "将旧数据转换为最新格式"。 例如，如果控件的版本2加载了版本1保存的数据，则它将在再次保存时写入版本2格式。 如果希望控件以上次读取的格式保存数据，请在调用时将**FALSE**作为第三个参数传递 `ExchangeVersion` 。 此第三个参数是可选的，默认情况下为**TRUE** 。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)
