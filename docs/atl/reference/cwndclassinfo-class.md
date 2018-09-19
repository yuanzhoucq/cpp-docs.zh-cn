---
title: CWndClassInfo 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d674b2e3049d27f0e79eb082a44640f67a395dea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097872"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo 类

此类提供了用于注册窗口类信息的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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
|[m_bSystemCursor](#m_bsystemcursor)|指定游标资源是指系统光标，还是为模块资源中包含的光标。|
|[m_lpszCursorID](#m_lpszcursorid)|指定游标资源的名称。|
|[m_lpszOrigName](#m_lpszorigname)|包含现有窗口类的名称。|
|[m_szAutoName](#m_szautoname)|保留窗口类的 ATL 生成的名称。|
|[m_wc](#m_wc)|维护窗口中的类信息`WNDCLASSEX`结构。|
|[pWndProc](#pwndproc)|指向现有窗口类的窗口过程。|

## <a name="remarks"></a>备注

`CWndClassInfo` 管理窗口类的信息。 通常使用`CWndClassInfo`通过三个宏、 {2&gt;declare_wnd_class&lt;2、 DECLARE_WND_CLASS_EX 或 DECLARE_WND_SUPERCLASS 下, 表中所述之一：

|宏|描述|
|-----------|-----------------|
|[{2&AMP;GT;DECLARE_WND_CLASS&AMP;LT;2](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` 注册新的窗口类信息。|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` 注册为新的窗口类，其中包括类参数的信息。|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` 注册窗口类，基于现有类，但使用不同的窗口过程的信息。 这一技术称为创建超类。|

默认情况下[CWindowImpl](../../atl/reference/cwindowimpl-class.md)包括`DECLARE_WND_CLASS`宏来创建一个窗口，基于一个新的窗口类。 {2&gt;declare_wnd_class&lt;2 提供控件的默认样式和背景色。 如果你想要指定样式和背景色自己，派生类从`CWindowImpl`并在类定义中包括 DECLARE_WND_CLASS_EX 宏。

如果你想要创建基于现有的窗口类的窗口，派生类从`CWindowImpl`并在类定义中包括 DECLARE_WND_SUPERCLASS 宏。 例如：

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

有关窗口类的详细信息，请参阅[窗口类](https://msdn.microsoft.com/library/windows/desktop/ms632596)Windows SDK 中。

有关使用 ATL 中的窗口的详细信息，请参阅文章[ATL 窗口类](../../atl/atl-window-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="m_atom"></a>  CWndClassInfo::m_atom

包含已注册的窗口类的唯一标识符。

```
ATOM m_atom;
```

##  <a name="m_bsystemcursor"></a>  CWndClassInfo::m_bSystemCursor

如果为 TRUE，注册窗口类时将加载系统游标资源。

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>备注

否则，将加载你的模块中包含的光标资源。

`CWndClassInfo` 使用`m_bSystemCursor`仅当[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class) (中的默认值[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)指定宏。 在这种情况下，`m_bSystemCursor`初始化为 TRUE。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

##  <a name="m_lpszcursorid"></a>  CWndClassInfo::m_lpszCursorID

指定游标资源的名称或资源标识符中的低序字和高位字中的为零。

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>备注

注册窗口类时，由标识光标的句柄`m_lpszCursorID`检索和存储的[m_wc](#m_wc)。

`CWndClassInfo` 使用`m_lpszCursorID`仅当[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class) (中的默认值[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)指定宏。 在这种情况下，`m_lpszCursorID`初始化为 IDC_ARROW。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

##  <a name="m_lpszorigname"></a>  CWndClassInfo::m_lpszOrigName

包含现有窗口类的名称。

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>备注

`CWndClassInfo` 使用`m_lpszOrigName`仅包括[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)在类定义中的宏。 在这种情况下，`CWndClassInfo`寄存器窗口类基于类的名为`m_lpszOrigName`。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

##  <a name="m_szautoname"></a>  CWndClassInfo::m_szAutoName

保留窗口类的名称。

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>备注

`CWndClassInfo` 使用`m_szAutoName`仅当将 NULL 传递`WndClassName`参数[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class)，则[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)或者[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL 窗口类注册时将构造的名称。

##  <a name="m_wc"></a>  CWndClassInfo::m_wc

维护中的窗口类信息[WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577)结构。

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>备注

如果已指定[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class) (在默认[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏，`m_wc`包含有关的信息新的窗口类。

如果已指定[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏，`m_wc`包含有关超类信息 — 的窗口类，基于现有类，但使用不同的窗口过程。 [m_lpszOrigName](#m_lpszorigname)并[pWndProc](#pwndproc)分别保存现有的窗口类名称和窗口过程。

##  <a name="pwndproc"></a>  CWndClassInfo::pWndProc

指向现有窗口类的窗口过程。

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>备注

`CWndClassInfo` 使用`pWndProc`仅包括[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)在类定义中的宏。 在这种情况下，`CWndClassInfo`注册窗口类，基于现有类，但使用不同的窗口过程。 在保存现有窗口类的窗口过程`pWndProc`。 有关详细信息，请参阅[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

##  <a name="register"></a>  CWndClassInfo::Register

调用[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)注册窗口类，如果尚未注册。

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>参数

*pProc*<br/>
[out]指定现有的窗口类的原始窗口过程。

### <a name="return-value"></a>返回值

如果成功，atom 唯一标识要注册的窗口类。 否则为为 0。

### <a name="remarks"></a>备注

如果已指定[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class) (在默认[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏，`Register`注册新的窗口类。 在这种情况下， *pProc*未使用参数。

如果已指定[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏，`Register`注册超类 — 的窗口类，基于现有类，但使用不同的窗口过程。 现有窗口类的窗口过程中返回*pProc*。

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)