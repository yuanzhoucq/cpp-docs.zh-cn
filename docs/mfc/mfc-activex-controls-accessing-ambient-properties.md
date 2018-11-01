---
title: MFC ActiveX 控件：访问环境属性
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: f6daff09969e82daa4e8f76c8b1eb4972ddd6eeb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585622"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>MFC ActiveX 控件：访问环境属性

本文讨论了 ActiveX 控件访问其控件容器的环境属性的方式。

控件可以通过访问容器的环境属性来获取有关其容器的信息。 这些属性将公开可视化特征，例如容器的背景色，请使用容器和操作特征，例如无论容器是当前在用户模式或设计器模式下的当前字体。 控件可以使用环境属性来调整其外观和行为以在其中嵌入的特定容器。 但是，控件应永远不会假定其容器将支持任何特定的环境属性。 事实上，一些容器可能不完全支持任何环境属性。 缺少的环境属性的情况下，控件应假定合理的默认值。

若要访问环境属性，请调用[COleControl::GetAmbientProperty](../mfc/reference/colecontrol-class.md#getambientproperty)。 此函数应环境属性的调度 ID，第一个参数 （OLECTL 的文件。H 定义调度 Id 的环境属性的标准集）。

参数`GetAmbientProperty`函数是调度 ID，该值指示预期的属性类型，以及指向内存的指针的变体标记应在其中返回的值。 此指针所引用的数据的类型而异的变体的标记。 该函数将返回 **，则返回 TRUE**如果容器支持属性，否则它将返回**FALSE**。

下面的代码示例获取名为"用户模式。"的环境属性的值 如果该属性不支持通过容器，默认值为 **，则返回 TRUE**假定：

[!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

为方便起见，`COleControl`提供帮助器函数，访问许多常用的环境属性和属性不可用时返回适当的默认值。 这些帮助器函数如下所示：

- [COleControl::AmbientBackColor](../mfc/reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](../mfc/reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](../mfc/reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  调用方必须调用`Release( )`上返回字体。

- [AmbientForeColor](../mfc/reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](../mfc/reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](../mfc/reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](../mfc/reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](../mfc/reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](../mfc/reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](../mfc/reference/colecontrol-class.md#ambientshowgrabhandles)

如果环境属性的值发生更改 （通过容器的某些操作）、`OnAmbientPropertyChanged`调用控件的成员函数。 重写此成员函数以处理此类通知。 为参数`OnAmbientPropertyChanged`是受影响的环境属性的调度 ID。 此调度 ID 的值可以是 DISPID_UNKNOWN，指示一个或多个环境的属性已更改，但有关哪些属性受影响的信息不可用。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

