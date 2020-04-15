---
title: COleDrop源类
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
ms.openlocfilehash: 324c4b7273f021b43c319fb0a494ac843856c78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375028"
---
# <a name="coledropsource-class"></a>COleDrop源类

允许将数据拖动到放置目标。

## <a name="syntax"></a>语法

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleDrop 来源：COleDrop 来源](#coledropsource)|构造 `COleDropSource` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleDrop 来源：给反馈](#givefeedback)|在拖放操作期间更改光标。|
|[COleDrop 来源：：在BeginDrag](#onbegindrag)|在拖放操作期间处理鼠标捕获。|
|[COleDrop 来源：：查询继续拖动](#querycontinuedrag)|检查拖动是否应继续。|

## <a name="remarks"></a>备注

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)类处理拖放操作的接收部分。 对象`COleDropSource`负责确定拖动操作何时开始，在拖动操作期间提供反馈，并确定拖动操作何时结束。

要使用`COleDropSource`对象，只需调用构造函数。 这简化了确定哪些事件（如鼠标单击）使用[COleDataSource：:DoDragDrop、COleClientItem：:DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop)[COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)或[COleServerItem：:DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop)函数开始拖动操作的过程。 这些函数将为您创建`COleDropSource`一个对象。 您可能希望修改可重写函数的`COleDropSource`默认行为。 框架将在适当时间调用这些成员函数。

有关使用 OLE 拖放操作的详细信息，请参阅文章[OLE 拖放](../../mfc/drag-and-drop-ole.md)。

有关详细信息，请参阅 Windows SDK 中的[IDropSource。](/windows/win32/api/oleidl/nn-oleidl-idropsource)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="coledropsourcecoledropsource"></a><a name="coledropsource"></a>COleDrop 来源：COleDrop 来源

构造 `COleDropSource` 对象。

```
COleDropSource();
```

## <a name="coledropsourcegivefeedback"></a><a name="givefeedback"></a>COleDrop 来源：给反馈

调用 COleDropTarget 后由框架调用[：：onDragover](../../mfc/reference/coledroptarget-class.md#ondragover)或[COleDropTarget：:D拉格Enter](../../mfc/reference/coledroptarget-class.md#ondragenter)。

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>参数

*滴效果*<br/>
要向用户显示的效果，通常指示如果此时与所选数据发生丢弃会发生什么情况。 通常，这是最近调用[CView 返回的值：OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)或[CView：onDragOver。](../../mfc/reference/cview-class.md#ondragover) 它可以是以下一个或多个：

- DROPEFFECT_NONE不允许掉下。

- DROPEFFECT_COPY将执行复制操作。

- DROPEFFECT_MOVE将执行移动操作。

- DROPEFFECT_LINK将建立从删除数据到原始数据的链接。

- DROPEFFECT_SCROLL拖动滚动操作即将发生或发生在目标中。

### <a name="return-value"></a>返回值

如果拖动正在进行，则返回DRAGDROP_S_USEDEFAULTCURSORS;如果没有，则返回 NOERROR。

### <a name="remarks"></a>备注

重写此函数，向用户提供有关此时发生丢弃时将会发生什么情况的反馈。 默认实现使用 OLE 默认游标。 有关使用 OLE 拖放操作的详细信息，请参阅文章[OLE 拖放](../../mfc/drag-and-drop-ole.md)。

有关详细信息，请参阅[IDropSource：：给反馈](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback)[，IDropTarget：:DragOver，](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)和[IDropTarget：:D拉格Enter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter)在 Windows SDK 中。

## <a name="coledropsourceonbegindrag"></a><a name="onbegindrag"></a>COleDrop 来源：：在BeginDrag

当可能发生可能开始拖动操作的事件（如按下鼠标左键）时，由框架调用。

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向包含所选数据的窗口。

### <a name="return-value"></a>返回值

如果允许拖动，则不为零，否则为 0。

### <a name="remarks"></a>备注

如果要修改拖动过程的启动方式，请重写此函数。 默认实现捕获鼠标并保持拖动模式，直到用户单击鼠标左键或右键或单击 ESC，此时它会释放鼠标。

## <a name="coledropsourcequerycontinuedrag"></a><a name="querycontinuedrag"></a>COleDrop 来源：：查询继续拖动

拖动开始后，框架会反复调用此函数，直到拖动操作被取消或完成。

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>参数

*bEscape压榨*<br/>
指出自上次调用`COleDropSource::QueryContinueDrag`以来是否按下了 ESC 密钥。

*德基州*<br/>
包含键盘上修改器键的状态。 这是以下任意数量的组合：MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

### <a name="return-value"></a>返回值

DRAGDROP_S_CANCEL是否按下 ESC 键或右键，或者在拖动开始之前引发左键。 如果应执行放置操作，DRAGDROP_S_DROP。 否则S_OK。

### <a name="remarks"></a>备注

如果要更改取消拖动或放置的点，请覆盖此函数。

默认实现启动拖放或取消拖动，如下所示。 按下 ESC 键或鼠标右键时，它取消拖动操作。 当鼠标左键在拖动开始后启动时，它将启动放置操作。 否则，它将返回S_OK，并且不执行进一步的操作。

由于此函数是频繁调用的，因此应尽可能对其进行优化。

## <a name="see-also"></a>另请参阅

[MFC 样品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
