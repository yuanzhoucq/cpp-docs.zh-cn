---
title: CMiniFrameWnd 类
ms.date: 11/04/2016
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
ms.openlocfilehash: e9b91161f4207f4d2215d8777beade93617ddfac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319815"
---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd 类

表示通常在浮动工具条周围出现的半高框架窗口。

## <a name="syntax"></a>语法

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMiniFramewnd：：CMiniFramewnd](#cminiframewnd)|构造 `CMiniFrameWnd` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMiniFramewnd：：创建](#create)|在构造`CMiniFrameWnd`后创建对象。|
|[CMiniFramewnd：：创建Ex](#createex)|在构造`CMiniFrameWnd`后创建对象（具有附加选项）。|

## <a name="remarks"></a>备注

这些微型框架窗口与普通框架窗口一样，只是它们没有最小化/最大化按钮或菜单，您只需要单击系统菜单即可将其关闭。

要使用对象`CMiniFrameWnd`，请先定义该对象。 然后调用["创建](#create)成员"函数以显示微型框架窗口。

有关如何使用`CMiniFrameWnd`对象的详细信息，请参阅文章["停靠"和"浮动工具栏](../../mfc/docking-and-floating-toolbars.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cminiframewndcminiframewnd"></a><a name="cminiframewnd"></a>CMiniFramewnd：：CMiniFramewnd

构造`CMiniFrameWnd`对象，但不创建窗口。

```
CMiniFrameWnd();
```

### <a name="remarks"></a>备注

要创建窗口，请致电[CMiniFramewnd：：创建](#create)。

## <a name="cminiframewndcreate"></a><a name="create"></a>CMiniFramewnd：：创建

创建 Windows 迷你框架窗口并将其附加到`CMiniFrameWnd`对象。

```
virtual BOOL Create(
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>参数

*lpClass名称*<br/>
指向命名 Windows 类的 null 端接字符串。 类名称可以是注册到全局[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函数的任何名称。 如果 NULL，则框架将为您注册窗口类。 MFC 为默认类提供以下样式和属性：

- 设置样式位CS_DBLCLKS，当用户双击鼠标时，将双击消息发送到窗口过程。

- 设置样式位CS_HREDRAW和CS_VREDRAW，引导工作区的内容在窗口更改大小时重绘。

- 将类游标设置到 Windows 标准IDC_ARROW。

- 将类背景画笔设置为 NULL，因此窗口不会擦除其背景。

- 将类图标设置为标准、挥舞标志的 Windows 徽标图标。

- 将窗口设置为默认大小和位置，如 Windows 所示。

*lpWindow名称*<br/>
指向包含窗口名称的 null 端接字符串。

*dwStyle*<br/>
指定窗口样式属性。 这些可以包括标准窗口样式和一个或多个以下特殊样式：

- MFS_MOVEFRAME 允许通过单击窗口的任何边缘（而不仅仅是标题）移动微型框架窗口。

- MFS_4THICKFRAME禁用小型框架窗口大小。

- MFS_SYNCACTIVE将小型框架窗口的激活同步到其父窗口的激活。

- MFS_THICKFRAME 允许将微型框架窗口的大小调整为客户端区域允许的大小。

- MFS_BLOCKSYSMENU禁用对系统菜单和控制菜单的访问，并将其转换为标题的一部分（标题栏）。

请参阅[CWnd：：创建](../../mfc/reference/cwnd-class.md#create)有关可能的窗口样式值的说明。 用于微型框架窗口的典型组合WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU。

*矩形*<br/>
指定`RECT`窗口所需尺寸的结构。

*pparentwnd*<br/>
指向父窗口。 对顶级窗口使用 NULL。

*nID*<br/>
如果将小框架窗口创建为子窗口，则这是子控件的标识符;如果将微型框架窗口创建为子窗口，则为子控件的标识符。否则 0。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`Create`初始化窗口的类名称和窗口名称，并注册其样式和父项的默认值。

## <a name="cminiframewndcreateex"></a><a name="createex"></a>CMiniFramewnd：：创建Ex

创建一个 `CMiniFrameWnd` 对象。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>参数

*dwExStyle*<br/>
指定正在创建的扩展`CMiniFrameWnd`样式。 将任何[扩展的窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)应用于窗口。

*lpClass名称*<br/>
指向命名 Windows 类[（WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)结构）的 null 端接字符串。 类名称可以是注册到全局[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函数或任何预定义的控制类名称的名称。 值不得为 NULL。

*lpWindow名称*<br/>
指向包含窗口名称的 null 端接字符串。

*dwStyle*<br/>
指定窗口样式属性。 请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[CWnd：：创建](../../mfc/reference/cwnd-class.md#create)可能的值的说明。

*矩形*<br/>
窗口的大小和位置，在*pParentWnd*的客户端坐标中。

*pparentwnd*<br/>
指向父窗口对象。

*nID*<br/>
子窗口的标识符。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

参数`CreateEx`指定窗口的 WNDCLASS、窗口样式和（可选）窗口的初始位置和大小。 `CreateEx`还指定窗口的父级（如果有）和 ID。

执行`CreateEx`时，Windows 会向窗口发送[WM_GETMINMAXINFO、WM_NCCREATE、WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccreate)和[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)消息。 [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)

要扩展默认消息处理，请从`CMiniFrameWnd`派生类，向新类添加消息映射，并为上述消息提供成员函数。 例如`OnCreate`，重写以执行新类所需的初始化。

覆盖其他`On`*消息消息*处理程序，以向派生类添加更多功能。

如果提供了WS_VISIBLE样式，Windows 会向窗口发送激活和显示窗口所需的所有消息。 如果窗口样式指定标题栏，*则 lpszWindowName*参数指向的窗口标题将显示在标题栏中。

*dwStyle*参数可以是[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的任意组合。

旧样式调色板工具箱窗口不再受支持。 在以前版本的 Windows 上运行 MFC 应用程序时，支持旧样式，该样式没有"X"关闭按钮，但在 Visual C++.NET 中不再支持。 现在仅支持新的WS_EX_TOOLWINDOW样式;有关此样式的说明，请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

## <a name="see-also"></a>另请参阅

[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)
