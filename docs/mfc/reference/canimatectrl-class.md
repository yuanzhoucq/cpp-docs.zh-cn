---
title: CAnimateCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
ms.openlocfilehash: e570681c899d58e8659635d55da843c23d1e95ee
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752883"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl 类

提供 Windows 公共动画控件的功能。

## <a name="syntax"></a>语法

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[克拉万克：：克拉万克Ctrl](#canimatectrl)|构造 `CAnimateCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAnimateCtrl：关闭](#close)|关闭 AVI 剪辑。|
|[CAnimateCtrl：：创建](#create)|创建动画控件并将其附加到`CAnimateCtrl`对象。|
|[创刊：：创建Ex](#createex)|使用指定的 Windows 扩展样式创建动画控件并将其附加到`CAnimateCtrl`对象。|
|[CAnimateCtrl：正在播放](#isplaying)|指示是否正在播放音频视频交错 （AVI） 剪辑。|
|[CAnimateCtrl：：打开](#open)|从文件或资源打开 AVI 剪辑并显示第一个帧。|
|[克拉万克克：:P莱](#play)|播放没有声音的 AVI 剪辑。|
|[CAnimateCtrl：：寻找](#seek)|显示 AVI 剪辑的选定单帧。|
|[克拉万克：：停止](#stop)|停止播放 AVI 剪辑。|

## <a name="remarks"></a>备注

此控件（因此该`CAnimateCtrl`类）仅适用于在 Windows 95、Windows 98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

动画控件是一个矩形窗口，以 AVI（音频视频交错）格式显示剪辑 — 标准 Windows 视频/音频格式。 AVI 剪辑是一系列位图帧，与电影相似。

动画控件只能播放简单的 AVI 剪辑。 具体而言，动画控件要播放的剪辑必须满足以下要求：

- 必须正好有一个视频流，并且必须至少有一个帧。

- 文件中最多只能有两个流（如果存在，通常另一个流是音频流，尽管动画控件忽略音频信息）。

- 剪辑必须解压缩或使用 RLE8 压缩进行压缩。

- 视频流中不允许更改调色板。

您可以将 AVI 剪辑作为 AVI 资源添加到您的应用程序中，也可以作为单独的 AVI 文件随同应用程序。

由于线程在显示 AVI 剪辑时继续执行，因此动画控件的一个常见用途是指示长时间操作期间的系统活动。 例如，在系统搜索文件时，"查找文件资源管理器"对话框将显示移动的放大镜。

如果在对话框中或使用`CAnimateCtrl`对话框编辑器从对话框资源创建对象，则当用户关闭对话框时，该对象将自动销毁。

如果在窗口中创建`CAnimateCtrl`对象，则可能需要销毁它。 如果在堆栈上`CAnimateCtrl`创建对象，则会自动销毁该对象。 如果使用新函数在`CAnimateCtrl`堆上创建对象，则必须调用**new**对象上的**delete**以销毁它。 如果从`CAnimateCtrl`该类派生新类并分配该类中的任何内存，请重写`CAnimateCtrl`析构函数以释放分配。

有关 使用`CAnimateCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)[和使用 CAnimateCtrl](../../mfc/using-canimatectrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a>克拉万克：：克拉万克Ctrl

构造 `CAnimateCtrl` 对象。

```
CAnimateCtrl();
```

### <a name="remarks"></a>备注

必须先调用[Create](#create)成员函数，然后才能对创建的对象执行任何其他操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a>CAnimateCtrl：关闭

关闭以前在动画控件中打开的 AVI 剪辑（如果有），并将其从内存中删除。

```
BOOL Close();
```

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

  请参阅[CAnimateCtrl 的示例：：CAnimateCtrl](#canimatectrl)。

## <a name="canimatectrlcreate"></a><a name="create"></a>CAnimateCtrl：：创建

创建动画控件并将其附加到`CAnimateCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定动画控件的样式。 应用下面"备注"部分中描述的窗口样式的任意组合以及 Windows SDK 中的[动画控件样式中描述的动画控件样式](/windows/win32/Controls/animation-control-styles)。

*矩形*<br/>
指定动画控件的位置和大小。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构。

*pparentwnd*<br/>
指定动画控件的父窗口，通常为`CDialog`。 值不得为 NULL。

*nID*<br/>
指定动画控件的 ID。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

在两个步骤`CAnimateCtrl`中构造 一个。 首先调用构造函数，然后调用`Create`，这将创建动画控件并将其附加到`CAnimateCtrl`对象。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于动画控件。

- WS_CHILD始终

- WS_VISIBLE 通常

- WS_DISABLED很少

如果要将扩展窗口样式与动画控件一起使用，请调用[CreateEx](#createex) `Create`而不是 。

除了上面列出的窗口样式外，您可能还希望将一个或多个动画控件样式应用于动画控件。 有关[动画控件样式](/windows/win32/Controls/animation-control-styles)的详细信息，请参阅 Windows SDK。

### <a name="example"></a>示例

  请参阅[CAnimateCtrl 的示例：：CAnimateCtrl](#canimatectrl)。

## <a name="canimatectrlcreateex"></a><a name="createex"></a>创刊：：创建Ex

创建控件（子窗口），并将其与`CAnimateCtrl`对象关联。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwExStyle*<br/>
指定要创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[创建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定动画控件的样式。 应用 Windows SDK 中的[动画控件样式](/windows/win32/Controls/animation-control-styles)中描述的窗口和动画控件样式的任意组合。

*矩形*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，描述要创建的窗口的大小和位置，在*pParentWnd*的客户端坐标中。

*pparentwnd*<br/>
指向控件的父窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是["创建](#create)"来应用扩展的 Windows 样式，该样式由 Windows 扩展样式前言**WS_EX_** 指定。

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a>CAnimateCtrl：正在播放

指示是否正在播放音频视频交错 （AVI） 剪辑。

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>返回值

如果正在播放 AVI 剪辑，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying)消息，这在 Windows SDK 中介绍。

## <a name="canimatectrlopen"></a><a name="open"></a>CAnimateCtrl：：打开

调用此功能以打开 AVI 剪辑并显示其第一个帧。

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>参数

*lpszFile名称*<br/>
`CString`包含 AVI 文件名称或 AVI 资源名称的对象或指向 null 终止字符串的指针。 如果此参数为 NULL，系统将关闭以前为动画控件打开的 AVI 剪辑（如果有）。

*nID*<br/>
AVI 资源标识符。 如果此参数为 NULL，系统将关闭以前为动画控件打开的 AVI 剪辑（如果有）。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

AVI 资源从创建动画控件的模块加载。

`Open`不支持 AVI 剪辑中的声音;您只能打开静默的 AVI 剪辑。

如果动画控件具有`ACS_AUTOPLAY`样式，动画控件将在剪辑打开后立即开始播放。 当线程继续执行时，它将继续在后台播放剪辑。 播放完剪辑后，将自动重复剪辑。

如果动画控件具有`ACS_CENTER`样式，则 AVI 剪辑将居中于控件中，并且控件的大小不会更改。 如果动画控件没有`ACS_CENTER`样式，则当 AVI 剪辑打开到 AVI 剪辑中图像的大小时，控件将调整大小。 控件左上角的位置不会更改，只有控件的大小。

如果动画控件具有`ACS_TRANSPARENT`样式，则将使用透明背景而不是动画剪辑中指定的背景颜色绘制第一个帧。

### <a name="example"></a>示例

  请参阅[CAnimateCtrl 的示例：：CAnimateCtrl](#canimatectrl)。

## <a name="canimatectrlplay"></a><a name="play"></a>克拉万克克：:P莱

调用此函数以在动画控件中播放 AVI 剪辑。

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>参数

*n 从*<br/>
播放开始的框架的从零开始的索引。 值必须小于 65，536。 值 0 表示从 AVI 剪辑中的第一帧开始。

*nto*<br/>
播放结束帧的基于零的索引。 值必须小于 65，536。 值 - 1 表示以 AVI 剪辑中的最后一帧结尾。

*nRep*<br/>
重播 AVI 剪辑的次数。 值 - 1 表示无限期重播文件。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

动画控件将在线程继续执行时在后台播放剪辑。 如果动画控件具有`ACS_TRANSPARENT`样式，则使用透明背景而不是动画剪辑中指定的背景颜色播放 AVI 剪辑。

### <a name="example"></a>示例

  请参阅[CAnimateCtrl 的示例：：CAnimateCtrl](#canimatectrl)。

## <a name="canimatectrlseek"></a><a name="seek"></a>CAnimateCtrl：：寻找

调用此功能以静态显示 AVI 剪辑的单个帧。

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>参数

*nto*<br/>
要显示的帧的从零开始索引。 值必须小于 65，536。 值 0 表示在 AVI 剪辑中显示第一个帧。 值 -1 表示在 AVI 剪辑中显示最后一个帧。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

如果动画控件具有`ACS_TRANSPARENT`样式，则 AVI 剪辑将使用透明背景而不是动画剪辑中指定的背景颜色进行绘制。

### <a name="example"></a>示例

请参阅[CAnimateCtrl 的示例：：CAnimateCtrl](#canimatectrl)。

## <a name="canimatectrlstop"></a><a name="stop"></a>克拉万克：：停止

调用此函数停止在动画控件中播放 AVI 剪辑。

```
BOOL Stop();
```

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

  请参阅[CAnimateCtrl 的示例：：CAnimateCtrl](#canimatectrl)。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl：：创建](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
