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
ms.openlocfilehash: f16a8cd21fe724c44a1ed648f29e42cb5d00dcd1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663293"
---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd 类

表示通常在浮动工具条周围出现的半高框架窗口。

## <a name="syntax"></a>语法

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|构造 `CMiniFrameWnd` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMiniFrameWnd::Create](#create)|创建`CMiniFrameWnd`构造后的对象。|
|[CMiniFrameWnd::CreateEx](#createex)|创建`CMiniFrameWnd`后构造对象 （与其他选项）。|

## <a name="remarks"></a>备注

这些微型框架窗口类似于普通的框架窗口，只不过它们不具有最小化/最大化按钮或菜单和您只需单击系统菜单关闭它们。

若要使用`CMiniFrameWnd`对象，请首先定义的对象。 然后调用[创建](#create)成员函数以显示微型框架窗口。

有关如何使用的详细信息`CMiniFrameWnd`对象，请参阅文章[停靠和浮动工具栏](../../mfc/docking-and-floating-toolbars.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cminiframewnd"></a>  CMiniFrameWnd::CMiniFrameWnd

构造`CMiniFrameWnd`对象，但不会创建窗口。

```
CMiniFrameWnd();
```

### <a name="remarks"></a>备注

若要创建窗口，调用[CMiniFrameWnd::Create](#create)。

##  <a name="create"></a>  CMiniFrameWnd::Create

创建 Windows 微型框架窗口，并将其附加到`CMiniFrameWnd`对象。

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

*lpClassName*<br/>
指向以 null 结尾的字符串命名的 Windows 类。 类名可以是任何名称注册到全局[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函数。 如果为 NULL，将由框架为你注册窗口类。 MFC 提供的默认类的以下样式和特性：

- 设置样式位的 CS_DBLCLKS，它会将双击消息到窗口过程当用户双击鼠标。

- 设置样式位 CS_HREDRAW 和 CS_VREDRAW，这指示客户端区域窗口大小更改时重绘的内容。

- 设置为 Windows 标准 IDC_ARROW 类游标。

- 将类背景画笔设置为 NULL，因此窗口不会擦除其背景。

- 将类图标设置为标准的飘扬标志 Windows 徽标图标。

- 将窗口设置为默认大小和位置，由 Windows。

*lpWindowName*<br/>
指向包含窗口名称的以 null 结尾的字符字符串。

*dwStyle*<br/>
指定的窗口样式特性。 其中可包括标准的窗口样式和一个或多个以下特殊样式：

- MFS_MOVEFRAME 允许通过单击窗口中，而不仅仅是标题的任何边缘移动微型框架窗口。

- MFS_4THICKFRAME 禁用调整微型框架窗口的大小。

- MFS_SYNCACTIVE 同步微型框架窗口到其父窗口的激活的激活。

- MFS_THICKFRAME 允许允许微型框架窗口进行大小调整最小可为客户端区域中的内容。

- MFS_BLOCKSYSMENU 禁用访问系统菜单和控制菜单中，并将它们转换为标题 （标题栏） 的一部分。

请参阅[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)有关可能的窗口样式值的说明。 典型的组合用于微型框架窗口是 WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU。

*rect*<br/>
一个`RECT`结构，它指定窗口的所需的维度。

*pParentWnd*<br/>
指向父窗口。 使用空值的顶级窗口。

*nID*<br/>
如果微型框架窗口创建为子窗口，这是子控件; 标识符否则为 0。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`Create` 初始化窗口的类名和窗口名称，并注册的样式和父的默认值。

##  <a name="createex"></a>  CMiniFrameWnd::CreateEx

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
指定的扩展的样式`CMiniFrameWnd`正在创建。 应用的任何[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)到窗口。

*lpClassName*<br/>
指向以 null 结尾的字符串命名的 Windows 类 ( [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576)结构)。 类名可以是任何名称注册到全局[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函数或任何预定义的控件类名称。 它不能为 NULL。

*lpWindowName*<br/>
指向包含窗口名称的以 null 结尾的字符字符串。

*dwStyle*<br/>
指定的窗口样式特性。 请参阅[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)并[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)有关可能的值的说明。

*rect*<br/>
大小和位置的窗口中，在客户端坐标*pParentWnd*。

*pParentWnd*<br/>
指向父窗口对象。

*nID*<br/>
子窗口的标识符。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

`CreateEx`参数指定 WNDCLASS、 窗口样式和 （可选） 初始位置和窗口的大小。 `CreateEx` 此外指定窗口的父级 （如果有） 和 id。

当`CreateEx`执行时，Windows 将发送[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)， [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，并且[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)到窗口消息。

若要扩展的默认消息处理，从派生类`CMiniFrameWnd`、 将消息映射添加到新的类，并为上述消息中提供成员函数。 重写`OnCreate`，例如，若要执行的一个新类所需的初始化。

重写进一步`On`*消息*消息处理程序以向你的派生类添加更多的功能。

如果给定 WS_VISIBLE 样式，则 Windows 将发送窗口激活和显示窗口所需的所有消息。 如果窗口样式指定的标题栏，窗口标题指向*lpszWindowName*参数显示在标题栏中。

*DwStyle*参数可以是任何组合[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

不再支持旧样式调色板工具箱窗口。 在以前版本的 Windows，运行 MFC 应用程序时支持的旧样式，不具有"X"关闭按钮，但在 Visual c + +.NET 中不再受支持。 现在支持只是新的 WS_EX_TOOLWINDOW 样式;此样式的说明，请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

## <a name="see-also"></a>请参阅

[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)
