---
title: MFC ActiveX 控件：访问环境属性
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: e5c78c9943f8baeadcc1198ee8c96f2023ac0215
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625435"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>MFC ActiveX 控件：访问环境属性

本文讨论 ActiveX 控件如何访问其控件容器的环境属性。

控件可以通过访问容器的环境属性来获取有关其容器的信息。 这些属性公开可视特征，例如容器的背景色、容器使用的当前字体以及操作特征，例如容器当前是否处于用户模式或设计器模式。 控件可以使用环境属性将其外观和行为定制为嵌入它的特定容器。 不过，控件绝不应假定其容器将支持任何特定环境属性。 事实上，一些容器根本不支持任何环境属性。 如果没有环境属性，控件应采用合理的默认值。

若要访问环境属性，请调用[COleControl：： GetAmbientProperty](reference/colecontrol-class.md#getambientproperty)。 此函数需要环境属性的调度 ID 作为第一个参数（文件 OLECTL。H 为环境属性的标准集定义调度 Id。

函数的参数 `GetAmbientProperty` 为调度 ID、表示预期属性类型的变量标记，以及指向应返回值的内存的指针。 此指针所引用的数据类型将因 variant 标记而异。 如果容器支持属性，则函数返回**TRUE** ，否则返回**FALSE**。

下面的代码示例获取名为 "UserMode" 的环境属性的值。 如果容器不支持该属性，则假定默认值为**TRUE** ：

[!code-cpp[NVC_MFC_AxUI#30](codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

为方便起见， `COleControl` 提供了 helper 函数，这些函数可访问许多常用的环境属性，并且在属性不可用时返回相应的默认值。 这些帮助器函数如下所示：

- [COleControl：： AmbientBackColor](reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  调用方必须 `Release( )` 对返回的字体调用。

- [AmbientForeColor](reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](reference/colecontrol-class.md#ambientshowgrabhandles)

如果环境属性的值发生更改（通过容器的某个操作），则 `OnAmbientPropertyChanged` 会调用控件的成员函数。 重写此成员函数以处理此类通知。 的参数 `OnAmbientPropertyChanged` 为受影响的环境属性的调度 ID。 此调度 ID 的值可能是 DISPID_UNKNOWN，这表示一个或多个环境属性已更改，但是有关哪些属性受影响的信息不可用。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)
