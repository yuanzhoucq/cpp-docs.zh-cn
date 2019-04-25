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
ms.openlocfilehash: 867bec619dc633b7b1fbf9785e14132ba8c493ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151280"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl 类

提供 Windows 公共动画控件的功能。

## <a name="syntax"></a>语法

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|构造 `CAnimateCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAnimateCtrl::Close](#close)|关闭 AVI 剪辑。|
|[CAnimateCtrl::Create](#create)|创建动画控件，并将其附加到`CAnimateCtrl`对象。|
|[CAnimateCtrl::CreateEx](#createex)|使用指定的 Windows 扩展样式创建动画控件，并将其附加到`CAnimateCtrl`对象。|
|[CAnimateCtrl::IsPlaying](#isplaying)|指示是否将正在播放音频和视频交错 (AVI) 剪辑。|
|[CAnimateCtrl::Open](#open)|从文件或资源打开 AVI 剪辑并显示第一个帧。|
|[CAnimateCtrl::Play](#play)|播放 AVI 剪辑，而无需声音。|
|[CAnimateCtrl::Seek](#seek)|显示所选的 AVI 剪辑单个帧。|
|[CAnimateCtrl::Stop](#stop)|停止播放 AVI 剪辑。|

## <a name="remarks"></a>备注

此控件 (并因此`CAnimateCtrl`类) 仅适用于 Windows 95、 Windows 98 和 Windows NT 版本 3.51 下运行的程序和更高版本。

动画控件是 AVI （音频和视频交错） 格式显示剪辑的矩形窗口 — 标准 Windows 视频/音频格式。 AVI 剪辑是一系列位图帧，与电影相似。

动画控件可以播放仅简单的 AVI 剪辑。 具体而言，剪辑要播放的动画控件必须满足以下要求：

- 必须有且只有一个视频流，并且它必须至少一个帧。

- 可以有最多两个流在文件中 （通常在其他流，如果存在，为音频流，尽管在动画控件将忽略音频信息）。

- 剪辑必须未压缩或使用 RLE8 压缩压缩。

- 在视频流允许没有调色板更改。

可以将 AVI 剪辑添加到你的应用程序作为 AVI 资源，或者它可以附带应用程序作为一个单独的 AVI 文件。

由于线程会继续执行显示 AVI 剪辑时，动画控件的一个常见用途是在较长的操作期间指示系统活动。 例如，文件资源管理器的查找对话框中显示移动的放大镜，为系统搜索文件。

如果您创建`CAnimateCtrl`对象，在一个对话框框中或通过使用对话框编辑器对话框资源，它将被自动销毁当用户关闭对话框。

如果您创建`CAnimateCtrl`对象内一个窗口，可能需要将其销毁。 如果您创建`CAnimateCtrl`对象在堆栈上被自动销毁。 如果您创建`CAnimateCtrl`通过使用堆上的对象**新**函数，必须调用**删除**上要将其销毁的对象。 如果类派生新类从`CAnimateCtrl`和分配任何内存在该类中的，重写`CAnimateCtrl`析构函数释放的分配。

有关使用的详细信息`CAnimateCtrl`，请参阅[控件](../../mfc/controls-mfc.md)并[使用 CAnimateCtrl](../../mfc/using-canimatectrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="canimatectrl"></a>  CAnimateCtrl::CAnimateCtrl

构造 `CAnimateCtrl` 对象。

```
CAnimateCtrl();
```

### <a name="remarks"></a>备注

必须调用[创建](#create)成员函数，然后才能执行任何其他操作在您创建的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

##  <a name="close"></a>  CAnimateCtrl::Close

关闭以前已经打开了动画控件 （如果有） 中的 AVI 剪辑并将其从内存中删除。

```
BOOL Close();
```

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

  有关示例，请参阅[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

##  <a name="create"></a>  CAnimateCtrl::Create

创建动画控件，并将其附加到`CAnimateCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定动画控件的样式。 应用的 windows 详见下面的备注部分和动画控件样式的样式中所述的任意组合[动画控件样式](/windows/desktop/Controls/animation-control-styles)Windows SDK 中。

*rect*<br/>
指定动画控件的位置和大小。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/desktop/api/windef/ns-windef-tagrect)结构。

*pParentWnd*<br/>
通常指定动画控件的父窗口， `CDialog`。 它不能为 NULL。

*nID*<br/>
指定动画控件的 id。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

构造`CAnimateCtrl`中两个步骤。 首先，调用构造函数中，，然后调用`Create`，它创建动画控件并将其附加到`CAnimateCtrl`对象。

将以下内容应用[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)到动画控件。

- WS_CHILD 始终

- WS_VISIBLE 通常

- WS_DISABLED 很少

如果想要扩展的 windows 样式用于动画控件，调用[CreateEx](#createex)而不是`Create`。

除了上面列出的窗口样式，您可能想要应用于动画控件的一个或多个动画控件样式。 请参阅 Windows SDK 的详细信息[动画控件样式](/windows/desktop/Controls/animation-control-styles)。

### <a name="example"></a>示例

  有关示例，请参阅[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

##  <a name="createex"></a>  CAnimateCtrl::CreateEx

创建控件 （子窗口），并将其与`CAnimateCtrl`对象。

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
指定要创建的控件的扩展的样式。 扩展 Windows 样式的列表，请参阅*dwExStyle*参数[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*dwStyle*<br/>
指定动画控件的样式。 应用窗口的任意组合和动画控件样式中所述[动画控件样式](/windows/desktop/Controls/animation-control-styles)Windows SDK 中。

*rect*<br/>
对引用[RECT](/previous-versions/dd162897\(v=vs.85\))结构的结构描述的大小和窗口的工作区中创建的位置*pParentWnd*。

*pParentWnd*<br/>
指向控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是[创建](#create)若要将应用扩展的 Windows 样式，指定的 Windows 扩展的样式加**WS_EX_**。

##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying

指示是否将正在播放音频和视频交错 (AVI) 剪辑。

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>返回值

如果正在播放 AVI 剪辑; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[ACM_ISPLAYING](/windows/desktop/Controls/acm-isplaying)消息，Windows SDK 中所述。

##  <a name="open"></a>  CAnimateCtrl::Open

调用此函数可打开 AVI 剪辑并显示其第一个帧。

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>参数

*lpszFileName*<br/>
一个`CString`对象或指向包含 AVI 文件的名称或 AVI 资源的名称的以 null 结尾的字符串的指针。 如果此参数为 NULL，系统将关闭以前已经打开了动画控件的 AVI 剪辑，如果有的话。

*nID*<br/>
AVI 资源标识符。 如果此参数为 NULL，系统将关闭以前已经打开了动画控件的 AVI 剪辑，如果有的话。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

从创建动画控件的模块加载 AVI 资源。

`Open` 不支持声音中 AVI 剪辑;您可以打开无提示 AVI 剪辑。

如果动画在控件有`ACS_AUTOPLAY`样式，动画控件将自动开始播放剪辑后将其打开。 它将继续在后台播放剪辑时线程会继续执行。 当完成剪辑播放，它将自动重复。

如果动画在控件有`ACS_CENTER`样式，将在控件中居中显示 AVI 剪辑和控件的大小不会更改。 如果在动画控件不具有`ACS_CENTER`样式，将调整控件的大小，当 AVI 剪辑打开 AVI 剪辑中的图像的大小。 控件的左上角的位置不会更改，仅该控件的大小。

如果动画在控件有`ACS_TRANSPARENT`样式，将使用具有透明背景色绘制第一个帧而不是在中指定的背景色的动画剪辑。

### <a name="example"></a>示例

  有关示例，请参阅[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

##  <a name="play"></a>  CAnimateCtrl::Play

调用此函数可在动画控件播放 AVI 剪辑。

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>参数

*nFrom*<br/>
播放开始处的帧的从零开始索引。 值必须是小于 65536。 值为 0 意味着开头 AVI 剪辑中的第一个帧。

*nTo*<br/>
帧的从零开始的索引位置播放结束。 值必须是小于 65536。 值为-1 表示结尾 AVI 剪辑中的最后一帧。

*nRep*<br/>
若要重播 AVI 剪辑次数。 值为-1 表示无限期地重播文件。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

线程会继续执行时，动画控件将在后台播放剪辑。 如果动画在控件有`ACS_TRANSPARENT`样式，AVI 剪辑，都将播放使用透明背景，而非动画剪辑中指定的背景色。

### <a name="example"></a>示例

  有关示例，请参阅[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

##  <a name="seek"></a>  CAnimateCtrl::Seek

调用此函数以静态显示 AVI 剪辑的单个帧。

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>参数

*nTo*<br/>
若要显示的帧的从零开始索引。 值必须是小于 65536。 值为 0 意味着在 AVI 剪辑中显示的第一帧。 值为-1 表示在 AVI 剪辑中显示的最后一帧。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

如果动画在控件有`ACS_TRANSPARENT`样式，将使用具有透明背景色绘制 AVI 剪辑而不是在中指定的背景色的动画剪辑。

### <a name="example"></a>示例

  有关示例，请参阅[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

##  <a name="stop"></a>  CAnimateCtrl::Stop

调用此函数可停止在动画控件播放 AVI 剪辑。

```
BOOL Stop();
```

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

  有关示例，请参阅[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
