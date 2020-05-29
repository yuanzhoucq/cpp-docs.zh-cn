---
title: 窗口类宏
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: 18c0912c506bc52421b18d36346204b557c0fc5c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325732"
---
# <a name="window-class-macros"></a>窗口类宏

这些宏定义窗口类实用程序。

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|允许您指定新窗口类的名称。|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|（视觉工作室 2017）允许您指定新窗口类的名称和封闭类的名称，其窗口过程将使用新类。|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|允许您指定新窗口类将基于的现有窗口类的名称。|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|允许您指定类的参数。|

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="declare_wnd_class"></a><a name="declare_wnd_class"></a>DECLARE_WND_CLASS

允许您指定新窗口类的名称。 将此宏放在 ATL ActiveX 控件的控制类中。

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>参数

*WndClass名称*<br/>
[在]新窗口类的名称。 如果为 NULL，ATL 将生成窗口类名称。

### <a name="remarks"></a>备注

如果使用 /允许编译器选项，则DECLARE_WND_CLASS将导致编译器错误;如果使用 /允许 - 编译器选项，则DECLARE_WND_CLASS将导致编译器错误。因此，DECLARE_WND_CLASS将会导致编译器错误。改用DECLARE_WND_CLASS2。

DECLARE_WND_CLASS允许您指定一个新窗口类的名称，其信息将由[CWndClassInfo](cwndclassinfo-class.md)管理。 DECLARE_WND_CLASS通过实现以下静态函数来定义新的窗口类：

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS为新窗口指定以下样式：

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS还指定默认窗口的背景颜色。 使用[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)宏提供您自己的样式和背景颜色。

[CWindowImpl](cwindowimpl-class.md)使用DECLARE_WND_CLASS宏基于新窗口类创建窗口。 要重写此行为，请使用[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)宏，或提供您自己的[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函数的实现。

有关在 ATL 中使用窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。

## <a name="declare_wnd_class2"></a><a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2

（视觉工作室 2017）类似于DECLARE_WND_CLASS，但具有一个额外的参数，在编译 /允许选项时可以避免从属名称错误。

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>参数

*WndClass名称*<br/>
[在]新窗口类的名称。 如果为 NULL，ATL 将生成窗口类名称。

*封闭类*<br/>
[在]包含新窗口类的窗口类的名称。 不能为 NULL。

### <a name="remarks"></a>备注

如果使用 /允许选项，则DECLARE_WND_CLASS将导致编译错误，因为它包含从属名称。 DECLARE_WND_CLASS2要求您显式命名此宏中使用的类，并且不会在 /允许 - 标志下导致错误。
否则，此宏与[DECLARE_WND_CLASS](#declare_wnd_class)相同。

## <a name="declare_wnd_superclass"></a><a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS

允许您指定类的参数。 将此宏放在 ATL ActiveX 控件的控制类中。

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>参数

*WndClass名称*<br/>
[在]将超类*OrigwndClassName*的窗口类的名称。 如果为 NULL，ATL 将生成窗口类名称。

*折元类名称*<br/>
[在]现有窗口类的名称。

### <a name="remarks"></a>备注

此宏允许您指定将超类现有窗口类的窗口类的名称。 [CWndClassInfo](cwndclassinfo-class.md)管理超类的信息。

DECLARE_WND_SUPERCLASS实现以下静态函数：

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

默认情况下[，CWindowImpl](cwindowimpl-class.md)使用[DECLARE_WND_CLASS](#declare_wnd_class)宏基于新的窗口类创建窗口。 通过在`CWindowImpl`派生类中指定DECLARE_WND_SUPERCLASS宏，窗口类将基于现有类，但将使用窗口过程。 此技术称为超类。

除了使用DECLARE_WND_CLASS和DECLARE_WND_SUPERCLASS宏外，您还可以使用自己的实现覆盖[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函数。

有关在 ATL 中使用窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。

## <a name="declare_wnd_class_ex"></a><a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX

允许您指定新窗口类将基于的现有窗口类的名称。 将此宏放在 ATL ActiveX 控件的控制类中。

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>参数

*WndClass名称*<br/>
[在]新窗口类的名称。 如果为 NULL，ATL 将生成窗口类名称。

*风格*<br/>
[在]窗口的样式。

*布亨德*<br/>
[在]窗口的背景颜色。

### <a name="remarks"></a>备注

此宏允许您指定新窗口类的类参数，其信息将由[CWndClassInfo](cwndclassinfo-class.md)管理。 DECLARE_WND_CLASS_EX通过实现以下静态函数来定义新的窗口类：

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

如果要使用默认样式和背景颜色，请使用[DECLARE_WND_CLASS](#declare_wnd_class)宏。 有关在 ATL 中使用窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。

## <a name="see-also"></a>另请参阅

[宏](atl-macros.md)
