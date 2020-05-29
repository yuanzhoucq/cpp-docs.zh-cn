---
title: CWndClassInfo 类
ms.date: 11/04/2016
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
ms.openlocfilehash: 01706bf61c3b977c28998325ece68724cfbc7452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330327"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo 类

此类提供用于注册窗口类信息的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CWndClassInfo
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|||
|-|-|
|[注册](#register)|注册窗口类。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_atom](#m_atom)|唯一标识已注册的窗口类。|
|[m_bSystemCursor](#m_bsystemcursor)|指定游标资源是引用系统游标还是模块资源中包含的游标。|
|[m_lpszCursorID](#m_lpszcursorid)|指定游标资源的名称。|
|[m_lpszOrigName](#m_lpszorigname)|包含现有窗口类的名称。|
|[m_szAutoName](#m_szautoname)|保存窗口类的 ATL 生成名称。|
|[m_wc](#m_wc)|在`WNDCLASSEX`结构中维护窗口类信息。|
|[普恩德普罗克](#pwndproc)|指向现有窗口类的窗口过程。|

## <a name="remarks"></a>备注

`CWndClassInfo`管理窗口类的信息。 通常通过三`CWndClassInfo`个宏之一（DECLARE_WND_CLASS、DECLARE_WND_CLASS_EX 或DECLARE_WND_SUPERCLASS）使用，如下表所述：

|宏|说明|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`注册新窗口类的信息。|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`注册新窗口类的信息，包括类参数。|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`注册基于现有类但使用不同的窗口过程的窗口类的信息。 此技术称为超类。|

默认情况下[，CWindowImpl](../../atl/reference/cwindowimpl-class.md)包含`DECLARE_WND_CLASS`宏以基于新窗口类创建窗口。 DECLARE_WND_CLASS为控件提供默认样式和背景颜色。 如果要自己指定样式和背景颜色，请从`CWindowImpl`类派生，并在类定义中包括DECLARE_WND_CLASS_EX宏。

如果要基于现有窗口类创建窗口，请从`CWindowImpl`类派生，并在类定义中包括DECLARE_WND_SUPERCLASS宏。 例如：

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

有关窗口类的详细信息，请参阅 Windows SDK 中的[窗口类](/windows/win32/winmsg/window-classes)。

有关在 ATL 中使用窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="cwndclassinfom_atom"></a><a name="m_atom"></a>CWndClass信息：m_atom

包含已注册窗口类的唯一标识符。

```
ATOM m_atom;
```

## <a name="cwndclassinfom_bsystemcursor"></a><a name="m_bsystemcursor"></a>CWndClass信息：m_bSystemCursor

如果为 TRUE，则在注册窗口类时将加载系统游标资源。

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>备注

否则，将加载模块中包含的游标资源。

`CWndClassInfo`仅当`m_bSystemCursor`指定[DECLARE_WND_CLASS（CWindowImpl](../../atl/reference/cwindowimpl-class.md)中的默认值）或[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏时才使用。 在这种情况下，`m_bSystemCursor`将初始化为 TRUE。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

## <a name="cwndclassinfom_lpszcursorid"></a><a name="m_lpszcursorid"></a>CWndClassInfo：m_lpszCursorID

指定低阶单词中的游标资源的名称或资源标识符，在高阶单词中指定零。

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>备注

注册窗口类时，m_wc 检索并存储指向 标识`m_lpszCursorID`的游标的句柄。 [m_wc](#m_wc)

`CWndClassInfo`仅当`m_lpszCursorID`指定[DECLARE_WND_CLASS（CWindowImpl](../../atl/reference/cwindowimpl-class.md)中的默认值）或[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏时才使用。 在这种情况下，`m_lpszCursorID`将初始化为IDC_ARROW。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

## <a name="cwndclassinfom_lpszorigname"></a><a name="m_lpszorigname"></a>CWndClass信息：m_lpszOrigName

包含现有窗口类的名称。

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>备注

`CWndClassInfo`仅当`m_lpszOrigName`在类定义中包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏时才使用。 在这种情况下，`CWndClassInfo`根据 指定的`m_lpszOrigName`类注册窗口类。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

## <a name="cwndclassinfom_szautoname"></a><a name="m_szautoname"></a>CWndClass信息：m_szAutoName

保存窗口类的名称。

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>备注

`CWndClassInfo`仅当`m_szAutoName`将 NULL`WndClassName`传递给参数[以DECLARE_WND_CLASS、DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class)或[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)时，才使用 。 [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) ATL 将在注册窗口类时构造名称。

## <a name="cwndclassinfom_wc"></a><a name="m_wc"></a>CWndClass信息：m_wc

在[WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw)结构中维护窗口类信息。

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>备注

`m_wc`如果指定[了](window-class-macros.md#declare_wnd_class)DECLARE_WND_CLASS（CWindowImpl 中的[CWindowImpl](../../atl/reference/cwindowimpl-class.md)默认值）或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏，则包含有关新窗口类的信息。

如果指定了[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏，则`m_wc`包含有关超类的信息 - 一个基于现有类但使用不同的窗口过程的窗口类。 [m_lpszOrigName](#m_lpszorigname)和[pWndProc](#pwndproc)分别保存现有窗口类的名称和窗口过程。

## <a name="cwndclassinfopwndproc"></a><a name="pwndproc"></a>CWndClassInfo：:pWndProc

指向现有窗口类的窗口过程。

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>备注

`CWndClassInfo`仅当`pWndProc`在类定义中包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏时才使用。 在这种情况下，`CWndClassInfo`注册基于现有类但使用不同的窗口过程的窗口类。 现有窗口类的窗口过程保存在 中`pWndProc`。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

## <a name="cwndclassinforegister"></a><a name="register"></a>CWndClassInfo：：注册

由[CWindowImpl 调用：创建](../../atl/reference/cwindowimpl-class.md#create)以注册窗口类（如果尚未注册）。

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>参数

*pProc*<br/>
[出]指定现有窗口类的原始窗口过程。

### <a name="return-value"></a>返回值

如果成功，则唯一标识要注册的窗口类的原子。 否则为 0。

### <a name="remarks"></a>备注

如果指定了`Register`[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)DECLARE_WND_CLASS（CWindowImpl 中的[CWindowImpl](../../atl/reference/cwindowimpl-class.md)默认值）或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏，请注册一个新的窗口类。 在这种情况下，不使用*pProc*参数。

如果指定了[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏，请`Register`注册一个超级类 -一个基于现有类但使用不同的窗口过程的窗口类。 现有窗口类的窗口过程在*pProc*中返回。

## <a name="see-also"></a>另请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
