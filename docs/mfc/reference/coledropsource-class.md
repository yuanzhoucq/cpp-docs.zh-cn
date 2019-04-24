---
title: COleDropSource 类
ms.date: 11/04/2016
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
ms.openlocfilehash: a2773333ea1dd89f73e7bdf3c5dc2f36945e0810
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58778502"
---
# <a name="coledropsource-class"></a>COleDropSource 类

允许将数据拖动到放置目标。

## <a name="syntax"></a>语法

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleDropSource::COleDropSource](#coledropsource)|构造 `COleDropSource` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleDropSource::GiveFeedback](#givefeedback)|在拖放操作期间发生更改的游标。|
|[COleDropSource::OnBeginDrag](#onbegindrag)|在拖放操作过程中处理鼠标捕获。|
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|检查以确定拖动是否应继续。|

## <a name="remarks"></a>备注

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)类处理拖放操作的接收部分。 `COleDropSource`对象负责确定在拖动操作开始时，在拖动操作过程中提供的反馈以及确定当拖动操作结束时。

若要使用`COleDropSource`对象，只需调用构造函数。 这将简化确定哪些事件，如单击鼠标开始拖动操作使用的过程[coledatasource:: Dodragdrop](../../mfc/reference/coledatasource-class.md#dodragdrop)， [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)，或[COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop)函数。 这些函数将创建`COleDropSource`为您的对象。 你可能想要修改的默认行为`COleDropSource`可重写函数。 这些成员函数将由框架调用以合适的次数。

拖放操作的详细信息使用 OLE，请参阅文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。

有关详细信息，请参阅[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource) Windows SDK 中。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>要求

**标头：** afxole.h

##  <a name="coledropsource"></a>  COleDropSource::COleDropSource

构造 `COleDropSource` 对象。

```
COleDropSource();
```

##  <a name="givefeedback"></a>  COleDropSource::GiveFeedback

由框架调用之后调用[COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)或[COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)。

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>参数

*dropEffect*<br/>
如果与所选数据这一时刻发生放置，你想要向用户显示的效果，通常指示什么会发生情况。 通常情况下，这是到最新的调用所返回的值[CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)或[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)。 它可以是一个或多项操作：

- 不允许放置 DROPEFFECT_NONE。

- DROPEFFECT_COPY 会执行复制操作。

- DROPEFFECT_MOVE 会执行移动操作。

- 将建立 DROPEFFECT_LINK 链接放置的数据从原始数据。

- DROPEFFECT_SCROLL A 拖动滚动操作即将发生或目标中不存在。

### <a name="return-value"></a>返回值

返回 DRAGDROP_S_USEDEFAULTCURSORS 如果拖动过程中，如果不是 NOERROR。

### <a name="remarks"></a>备注

重写此函数向用户如果此时发生放置会发生什么情况提供反馈。 默认实现使用 OLE 默认光标。 拖放操作的详细信息使用 OLE，请参阅文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。

有关详细信息，请参阅[IDropSource::GiveFeedback](/windows/desktop/api/oleidl/nf-oleidl-idropsource-givefeedback)， [IDropTarget::DragOver](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragover)，并[IDropTarget::DragEnter](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragenter) Windows SDK 中。

##  <a name="onbegindrag"></a>  COleDropSource::OnBeginDrag

由框架事件发生时无法开始拖动操作，例如，按下鼠标左键。

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向包含所选的数据的窗口。

### <a name="return-value"></a>返回值

如果拖动允许，否则为 0，非零值。

### <a name="remarks"></a>备注

如果你想要修改的方法启动拖放的过程，重写此函数。 默认实现捕获鼠标并停留在拖动模式，直到用户单击鼠标左键或右键按钮，或点击 esc 键，此时它释放鼠标。

##  <a name="querycontinuedrag"></a>  COleDropSource::QueryContinueDrag

拖动开始后，此函数是重复调用，由框架直到取消或完成拖动操作。

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>参数

*bEscapePressed*<br/>
指出是否已按了 ESC 键下自上次调用以来`COleDropSource::QueryContinueDrag`。

*dwKeyState*<br/>
包含在键盘上的修改键的状态。 这是以下任意数量的组合：MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

### <a name="return-value"></a>返回值

拖动开始之前，将引发 DRAGDROP_S_CANCEL 如果 ESC 键或右侧的按钮按下或左按钮。 如果应发生放置操作，DRAGDROP_S_DROP。 否则为，则为 S_OK。

### <a name="remarks"></a>备注

重写此函数如果你想要更改哪些拖动的点将被取消或 drop 时发生。

默认实现将启动拖放或取消拖动，如下所示。 在按 ESC 键或鼠标右键时，它会取消拖动操作。 拖动启动后引发鼠标左键时，它启动拖放操作。 否则为它返回 S_OK，并执行任何进一步的操作。

因为频繁地调用此函数时，应尽可能多地进行优化。

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
