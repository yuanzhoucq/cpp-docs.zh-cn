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
ms.openlocfilehash: 45b4698cc70487a6c3fe1470fe27f7b5c4f95402
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504591"
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
|[CMiniFrameWnd::Create](#create)|在构造后创建对象。`CMiniFrameWnd`|
|[CMiniFrameWnd::CreateEx](#createex)|构造后`CMiniFrameWnd`创建一个对象 (包含附加选项)。|

## <a name="remarks"></a>备注

这些袖珍框架窗口的行为类似于正常框架窗口, 不同之处在于它们不具有最小化/最大化按钮或菜单, 并且你只需单击系统菜单即可将其关闭。

若要使用`CMiniFrameWnd`对象, 请先定义对象。 然后调用[Create](#create)成员函数以显示袖珍框架窗口。

有关如何使用`CMiniFrameWnd`对象的详细信息, 请参阅文章[停靠和浮动工具栏](../../mfc/docking-and-floating-toolbars.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd

构造一个`CMiniFrameWnd`对象, 但不创建窗口。

```
CMiniFrameWnd();
```

### <a name="remarks"></a>备注

若要创建窗口, 请调用[CMiniFrameWnd:: create](#create)。

##  <a name="create"></a>CMiniFrameWnd:: Create

创建 Windows 袖珍框架窗口并将其附加到`CMiniFrameWnd`对象。

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
指向以 null 结尾的字符串, 该字符串对 Windows 类进行命名。 类名称可以是任何注册到 global [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函数的名称。 如果为 NULL, 则框架将为你注册窗口类。 MFC 为默认类提供以下样式和特性:

- 设置样式位 CS_DBLCLKS, 当用户双击鼠标时, 它会将双击消息发送到窗口过程。

- 设置样式位 CS_HREDRAW 和 CS_VREDRAW, 它指示在窗口大小改变时要重新绘制的工作区的内容。

- 将类游标设置为 Windows standard IDC_ARROW。

- 将类背景画笔设置为 NULL, 使窗口不会擦除其背景。

- 将类图标设置为标准的飘扬 Windows 徽标图标。

- 按照 Windows 的指示, 将窗口设置为默认大小和位置。

*lpWindowName*<br/>
指向以 null 结尾的字符串, 该字符串包含窗口名称。

*dwStyle*<br/>
指定窗口样式特性。 其中可能包括标准窗口样式和一个或多个以下特殊样式:

- MFS_MOVEFRAME 允许通过单击窗口的任意边缘而不只是标题来移动微型框架窗口。

- MFS_4THICKFRAME 禁用袖珍框架窗口的大小调整。

- MFS_SYNCACTIVE 使袖珍框架窗口激活与其父窗口激活同步。

- MFS_THICKFRAME 允许将袖珍框架窗口的大小调整为小, 使其大小与客户端区域的内容相同。

- MFS_BLOCKSYSMENU 禁止访问 "系统" 菜单和 "控制" 菜单, 并将其转换为标题的一部分 (标题栏)。

有关可能的窗口样式值的说明, 请参阅[CWnd:: Create](../../mfc/reference/cwnd-class.md#create) 。 用于袖珍框架窗口的典型组合是 WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU。

*rect*<br/>
指定所需的窗口尺寸的结构。`RECT`

*pParentWnd*<br/>
指向父窗口。 对于顶级窗口, 请使用 NULL。

*nID*<br/>
如果将袖珍框架窗口创建为子窗口, 则这是子控件的标识符;否则为0。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`Create`初始化窗口的类名称和窗口名称, 并为其样式和父级注册默认值。

##  <a name="createex"></a>CMiniFrameWnd:: CreateEx

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
指定正在创建的`CMiniFrameWnd`的扩展样式。 将任何扩展的[窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)应用于该窗口。

*lpClassName*<br/>
指向以 null 结尾的字符串, 该字符串对 Windows 类 ( [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)结构) 进行命名。 类名称可以是任何用全局[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函数或任何预定义的控件类名称注册的名称。 它不能为 NULL。

*lpWindowName*<br/>
指向以 null 结尾的字符串, 该字符串包含窗口名称。

*dwStyle*<br/>
指定窗口样式特性。 有关可能值的说明, 请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[CWnd:: Create](../../mfc/reference/cwnd-class.md#create) 。

*rect*<br/>
窗口的大小和位置 (以*pParentWnd*的工作区坐标表示)。

*pParentWnd*<br/>
指向父窗口对象。

*nID*<br/>
子窗口的标识符。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

`CreateEx`参数指定窗口的 WNDCLASS、窗口样式和 (可选) 初始位置和大小。 `CreateEx`还指定窗口的父项 (如果有) 和 ID。

执行`CreateEx`时, Windows 会将[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)、 [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)和[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)消息发送到窗口。

若要扩展默认消息处理, 请从`CMiniFrameWnd`派生类, 将消息映射添加到新类, 并为上述消息提供成员函数。 例如`OnCreate`, 重写, 为新类执行所需的初始化。

重写`On`进一步的*消息*消息处理程序, 以便向派生类添加更多功能。

如果提供了 WS_VISIBLE 样式, 则 Windows 将发送激活并显示该窗口所需的所有消息。 如果窗口样式指定了标题栏, 则*lpszWindowName*参数指向的窗口标题将显示在标题栏中。

*DwStyle*参数可以是[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的任意组合。

不再支持旧样式调色板工具箱窗口。 在以前版本的 Windows 上运行 MFC 应用程序时, 不支持 "X" 关闭按钮的旧样式, 但在 Visual C++.net 中不再支持该样式。 现在仅支持新的 WS_EX_TOOLWINDOW 样式;有关此样式的说明, 请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

## <a name="see-also"></a>请参阅

[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)
