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
ms.openlocfilehash: 3a1e27ca6c1019eb8716194b3b7711238d015d6d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504005"
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
|[COleDropSource::GiveFeedback](#givefeedback)|在拖放操作过程中更改光标。|
|[COleDropSource::OnBeginDrag](#onbegindrag)|在拖放操作过程中处理鼠标捕获。|
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|检查以确定是否应继续拖动。|

## <a name="remarks"></a>备注

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)类处理拖放操作的接收部分。 `COleDropSource`对象负责确定拖动操作的开始时间, 在拖动操作过程中提供反馈, 并确定拖动操作的结束时间。

若要使用`COleDropSource`对象, 只需调用构造函数。 这可以简化确定哪些事件 (例如鼠标单击) 开始使用 COleDataSource 的拖动操作的过程[::D odragdrop](../../mfc/reference/coledatasource-class.md#dodragdrop)、 [COleClientItem::D odragdrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)或[COleServerItem::D odragdrop](../../mfc/reference/coleserveritem-class.md#dodragdrop)函数。 这些函数将为您`COleDropSource`创建一个对象。 你可能需要修改可`COleDropSource`重写函数的默认行为。 框架将在适当的时间调用这些成员函数。

有关使用 OLE 拖放操作的详细信息, 请参阅[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)一文。

有关详细信息, 请参阅 Windows SDK 中的[IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) 。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>要求

**标头:** afxole

##  <a name="coledropsource"></a>COleDropSource::COleDropSource

构造 `COleDropSource` 对象。

```
COleDropSource();
```

##  <a name="givefeedback"></a>COleDropSource:: System.windows.dragdrop.givefeedback>

在调用[COleDropTarget:: system.windows.uielement.ondragover](../../mfc/reference/coledroptarget-class.md#ondragover)或[COleDropTarget:D: ragenter](../../mfc/reference/coledroptarget-class.md#ondragenter)后, 由框架调用。

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>参数

*dropEffect*<br/>
希望向用户显示的效果, 通常指示在此点处发生了选定数据时将发生的情况。 通常, 这是最新调用[CView:: system.windows.uielement.ondragenter](../../mfc/reference/cview-class.md#ondragenter)或[Cview:: system.windows.uielement.ondragover](../../mfc/reference/cview-class.md#ondragover)的值。 它可以是下列一项或多项:

- DROPEFFECT_NONE 不允许删除。

- DROPEFFECT_COPY 将执行复制操作。

- DROPEFFECT_MOVE 将执行移动操作。

- DROPEFFECT_LINK 会建立从已删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 将发生拖动滚动操作, 或在目标中发生。

### <a name="return-value"></a>返回值

如果正在进行拖动, 则返回 DRAGDROP_S_USEDEFAULTCURSORS, 如果不是, 则返回 NOERROR。

### <a name="remarks"></a>备注

重写此函数以向用户提供有关在此时发生的情况下会发生什么情况的反馈。 默认实现使用 OLE 默认游标。 有关使用 OLE 拖放操作的详细信息, 请参阅[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)一文。

有关详细信息, 请参阅 Windows SDK 中的[IDropSource:: system.windows.dragdrop.givefeedback>](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback)、 [IDropTarget::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)和[IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) 。

##  <a name="onbegindrag"></a>COleDropSource::OnBeginDrag

当发生可能开始拖动操作的事件时 (如按鼠标左键), 由框架调用。

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向包含所选数据的窗口。

### <a name="return-value"></a>返回值

如果允许拖动, 则为非零; 否则为0。

### <a name="remarks"></a>备注

如果要修改拖动过程的启动方式, 请重写此函数。 默认实现将捕获鼠标并一直处于拖动模式, 直到用户按下鼠标左键或按 ESC 键 (此时它释放鼠标)。

##  <a name="querycontinuedrag"></a>COleDropSource:: System.windows.dragdrop.querycontinuedrag>

开始拖动后, 框架将重复调用此函数, 直到取消或完成拖动操作。

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>参数

*bEscapePressed*<br/>
指示自上次调用`COleDropSource::QueryContinueDrag`后是否已按下了 ESC 键。

*dwKeyState*<br/>
包含键盘上的修改键的状态。 这是以下任意数量的组合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。

### <a name="return-value"></a>返回值

如果按下了 ESC 键或右键, 则 DRAGDROP_S_CANCEL, 或在拖动开始之前引发左键。 如果应执行删除操作, 则为 DRAGDROP_S_DROP。 否则为 S_OK。

### <a name="remarks"></a>备注

如果要更改取消拖动或发生放置的点, 请重写此函数。

默认实现启动删除或取消拖动, 如下所示。 当按下 ESC 键或鼠标右键时, 它将取消拖动操作。 在开始拖动后引发鼠标左键时, 它将启动一个删除操作。 否则, 它将返回 S_OK 并不执行进一步的操作。

由于此函数经常被调用, 因此应尽可能优化。

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
