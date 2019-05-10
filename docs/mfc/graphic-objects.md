---
title: 图形对象
ms.date: 11/04/2016
f1_keywords:
- HRGN
- HFONT
- HBITMAP
helpviewer_keywords:
- CRgn class [MFC], HRGN handle type
- HPEN [MFC]
- objects [MFC], graphic
- palettes [MFC], creating in device context
- pens [MFC], creating in device context
- bitmaps [MFC], creating in device contexts
- palette objects [MFC]
- memory [MFC], display contexts
- MFC, graphic objects
- regions [MFC], creating in device context
- CPen class [MFC], HPEN handle type
- GDI objects [MFC]
- HRGN [MFC]
- graphic objects [MFC]
- GDI objects [MFC], graphic-object classes
- CFont class [MFC], HFONT handle type
- HFONT and class CFont [MFC]
- HBITMAP and class CBitmap [MFC]
- fonts [MFC], creating in device context
- images [MFC], graphic objects [MFC]
- CBitmap class [MFC], HBITMAP handle type
- HPALETTE and class CPalette [MFC]
- CBrush class [MFC], HBRUSH handle type
- objects [MFC], graphic objects
- drawing [MFC], in device contexts
- device contexts [MFC], graphic objects [MFC]
- brushes [MFC], creating in device context
- region objects [MFC]
- pen objects [MFC]
- GDI [MFC], graphic-object classes
- graphic objects [MFC], creating in device context
- HBRUSH and class CBrush [MFC]
- painting and device context [MFC]
- CPalette class [MFC], HPALETTE handle type
ms.assetid: 41963b25-34b7-4343-8446-34ba516b83ca
ms.openlocfilehash: 58ecf680d64f39ab61589a0ad668c15d1a9cd68c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359055"
---
# <a name="graphic-objects"></a>图形对象

Windows 提供了各种可在设备上下文中使用的绘图工具。 它提供了用于绘制线条的笔、用于填充内部的画笔以及用于绘制文本的字体。 MFC 提供等效于 Windows 中的绘图工具的图形对象类。 下表显示可用类以及等效的 Windows 图形设备接口 (GDI) 句柄类型。

> [!NOTE]
>  有关详细信息，请参阅上的 GDI + SDK 文档： [ https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp ](https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp)。

本文说明了这些图形对象类的用法：

### <a name="classes-for-windows-gdi-objects"></a>用于 Windows GDI 对象的类

|类|Windows 句柄类型|
|-----------|-------------------------|
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|
|[CBrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|
|[CFont](../mfc/reference/cfont-class.md)|**HFONT**|
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|

> [!NOTE]
>  该类[中的 CImage](../atl-mfc-shared/reference/cimage-class.md)提供增强的位图支持。

类库中的每个图形对象类都具有一个构造函数，使你可以创建该类的图形对象，随后必须使用适当的创建函数（如 `CreatePen`）初始化这些对象。

类库中的每个图形对象类都具有一个强制转换运算符，可将 MFC 对象强制转换为关联的 Windows 句柄。 生成的句柄在关联对象将它分离之前都有效。 使用对象的`Detach`成员函数可分离句柄。

下面的代码将 `CPen` 对象强制转换为 Windows 句柄：

[!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/cpp/graphic-objects_1.cpp)]

#### <a name="to-create-a-graphic-object-in-a-device-context"></a>在设备上下文中创建图形对象

1. 在堆栈帧上定义图形对象。 使用特定于类型的创建函数（如 `CreatePen`）初始化对象。 或者，在构造函数中初始化对象。 请参阅的讨论[一阶段和两个阶段创建](../mfc/one-stage-and-two-stage-construction-of-objects.md)，其中提供了示例代码。

1. [选择对象进入当前设备上下文](../mfc/selecting-a-graphic-object-into-a-device-context.md)之前, 选择了保存旧图形对象。

1. 处理了当前图形对象之后，选择旧图形对象返回设备上下文以还原其状态。

1. 允许在退出范围时自动删除帧分配的图形对象。

> [!NOTE]
>  如果重复使用图形对象，则可以分配它一次，然后在每次需要时选择它进入设备上下文中。 请务必在不再需要时删除这类对象。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [图形对象的一阶段和两阶段构建](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [在一个或两个阶段构造笔的示例](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [将图形对象选入设备上下文](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [设备上下文](../mfc/device-contexts.md)

## <a name="see-also"></a>请参阅

[窗口对象](../mfc/window-objects.md)
