---
title: 窗口类宏
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: c4617a04c199741b97316122456e417a94275e89
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862953"
---
# <a name="window-class-macros"></a>窗口类宏

这些宏定义了 window 类实用程序。

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|允许您指定新窗口类的名称。|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|（Visual Studio 2017）允许您指定新窗口类的名称以及新类将使用的窗口过程的封闭类。|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|允许您指定新的窗口类将基于的现有窗口类的名称。|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|允许您指定类的参数。|

## <a name="requirements"></a>要求

**标头：** atlwin。h

##  <a name="declare_wnd_class"></a>DECLARE_WND_CLASS

允许您指定新窗口类的名称。 将此宏置于 ATL ActiveX 控件的控件类中。

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>参数

*WndClassName*<br/>
中新窗口类的名称。 如果为 NULL，则 ATL 将生成一个窗口类名。

### <a name="remarks"></a>备注

如果使用/permissive-编译器选项，则 DECLARE_WND_CLASS 将导致编译器错误;改用 DECLARE_WND_CLASS2。

DECLARE_WND_CLASS 允许你指定新窗口类的名称，该窗口类的信息将由[CWndClassInfo](cwndclassinfo-class.md)管理。 DECLARE_WND_CLASS 通过实现以下静态函数来定义新的窗口类：

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS 为新窗口指定以下样式：

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS 还指定了默认窗口的背景色。 使用[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)宏提供您自己的样式和背景色。

[CWindowImpl](cwindowimpl-class.md)使用 DECLARE_WND_CLASS 宏基于新的窗口类创建窗口。 若要重写此行为，请使用[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)宏，或提供自己的[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函数的实现。

有关在 ATL 中使用 windows 的详细信息，请参阅[Atl 窗口类](../../atl/atl-window-classes.md)一文。

##  <a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2

（Visual Studio 2017）与 DECLARE_WND_CLASS 类似，但在使用/permissive-选项进行编译时，使用额外的参数可避免依赖名称错误。

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>参数

*WndClassName*<br/>
中新窗口类的名称。 如果为 NULL，则 ATL 将生成一个窗口类名。

*EnclosingClass*<br/>
中括起新窗口类的窗口类的名称。 不能为 NULL。

### <a name="remarks"></a>备注

如果使用/permissive-选项，则 DECLARE_WND_CLASS 会导致编译错误，因为它包含依赖名称。 DECLARE_WND_CLASS2 要求你显式命名在其中使用此宏的类，而不会导致/permissive-标志下的错误。
否则，此宏等同于[DECLARE_WND_CLASS](#declare_wnd_class)。

##  <a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS

允许您指定类的参数。 将此宏置于 ATL ActiveX 控件的控件类中。

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>参数

*WndClassName*<br/>
中将*OrigWndClassName*的超类的窗口类的名称。 如果为 NULL，则 ATL 将生成一个窗口类名。

*OrigWndClassName*<br/>
中现有窗口类的名称。

### <a name="remarks"></a>备注

此宏允许您指定将向现有窗口类超类的窗口类的名称。 [CWndClassInfo](cwndclassinfo-class.md)管理超类的信息。

DECLARE_WND_SUPERCLASS 实现以下静态函数：

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

默认情况下， [CWindowImpl](cwindowimpl-class.md)使用[DECLARE_WND_CLASS](#declare_wnd_class)宏基于新的窗口类创建窗口。 通过在 `CWindowImpl`派生类中指定 DECLARE_WND_SUPERCLASS 宏，窗口类将基于现有类，但将使用您的窗口过程。 此方法称为 superclassing。

除了使用 DECLARE_WND_CLASS 和 DECLARE_WND_SUPERCLASS 宏以外，还可以使用自己的实现来重写[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函数。

有关在 ATL 中使用 windows 的详细信息，请参阅[Atl 窗口类](../../atl/atl-window-classes.md)一文。

##  <a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX

允许您指定新的窗口类将基于的现有窗口类的名称。 将此宏置于 ATL ActiveX 控件的控件类中。

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>参数

*WndClassName*<br/>
中新窗口类的名称。 如果为 NULL，则 ATL 将生成一个窗口类名。

style<br/>
中窗口的样式。

*背景*<br/>
中窗口的背景色。

### <a name="remarks"></a>备注

此宏允许您指定新窗口类的类参数，该窗口类的信息将由[CWndClassInfo](cwndclassinfo-class.md)管理。 DECLARE_WND_CLASS_EX 通过实现以下静态函数来定义新的窗口类：

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

如果要使用默认样式和背景色，请使用[DECLARE_WND_CLASS](#declare_wnd_class)宏。 有关在 ATL 中使用 windows 的详细信息，请参阅[Atl 窗口类](../../atl/atl-window-classes.md)一文。

## <a name="see-also"></a>另请参阅

[宏](atl-macros.md)
