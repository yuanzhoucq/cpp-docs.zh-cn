---
title: COleDropTarget 类
ms.date: 11/04/2016
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
helpviewer_keywords:
- COleDropTarget [MFC], COleDropTarget
- COleDropTarget [MFC], OnDragEnter
- COleDropTarget [MFC], OnDragLeave
- COleDropTarget [MFC], OnDragOver
- COleDropTarget [MFC], OnDragScroll
- COleDropTarget [MFC], OnDrop
- COleDropTarget [MFC], OnDropEx
- COleDropTarget [MFC], Register
- COleDropTarget [MFC], Revoke
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
ms.openlocfilehash: 01eb277da029d06ee44d8e048cf3244f4371a9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374992"
---
# <a name="coledroptarget-class"></a>COleDropTarget 类

提供窗口和 OLE 库之间的通信机制。

## <a name="syntax"></a>语法

```
class COleDropTarget : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleDrop目标：：COleDrop目标](#coledroptarget)|构造 `COleDropTarget` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleDrop目标：：OnDragEnter](#ondragenter)|当光标首次进入窗口时调用。|
|[COleDrop目标：：OnDragLeave](#ondragleave)|当光标拖出窗口时调用。|
|[COleDrop目标：：OnDragover](#ondragover)|当光标拖过窗口时重复调用。|
|[COleDrop目标：：OnDragscroll](#ondragscroll)|调用 以确定光标是否拖入窗口的滚动区域。|
|[COleDrop目标：：上投](#ondrop)|当数据放入窗口时调用，默认处理程序。|
|[COleDrop目标：：OnDropEx](#ondropex)|当数据放入窗口时调用，初始处理程序。|
|[COleDrop目标：：注册](#register)|将窗口注册为有效的放置目标。|
|[COleDrop目标：：撤销](#revoke)|使窗口不再是有效的放置目标。|

## <a name="remarks"></a>备注

创建此类的对象允许窗口通过 OLE 拖放机制接受数据。

要获取窗口以接受放置命令，应首先创建`COleDropTarget`类的对象，然后使用指向所需`CWnd`对象的指针调用[Register](#register)函数作为唯一的参数。

有关使用 OLE 拖放操作的详细信息，请参阅文章[OLE 拖放](../../mfc/drag-and-drop-ole.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="coledroptargetcoledroptarget"></a><a name="coledroptarget"></a>COleDrop目标：：COleDrop目标

构造类`COleDropTarget`的对象 。

```
COleDropTarget();
```

### <a name="remarks"></a>备注

调用[注册以](#register)将此对象与窗口关联。

## <a name="coledroptargetondragenter"></a><a name="ondragenter"></a>COleDrop目标：：OnDragEnter

当光标首次拖入窗口时，由框架调用。

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向光标正在输入的窗口。

*pDataObject*<br/>
指向包含可删除的数据的数据对象。

*德基州*<br/>
包含修改器键的状态。 这是以下任意数量的组合：MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*点*<br/>
在客户端坐标中包含光标的当前位置。

### <a name="return-value"></a>返回值

如果在*点*指定的位置尝试放置时将导致的效果。 它可以是以下一个或多个：

- DROPEFFECT_NONE不允许掉下。

- DROPEFFECT_COPY将执行复制操作。

- DROPEFFECT_MOVE将执行移动操作。

- DROPEFFECT_LINK将建立从删除数据到原始数据的链接。

- DROPEFFECT_SCROLL拖动滚动操作即将发生或发生在目标中。

### <a name="remarks"></a>备注

重写此函数以允许在窗口中执行放置操作。 默认实现调用[CView：：onDragEnter](../../mfc/reference/cview-class.md#ondragenter)，默认情况下只需返回DROPEFFECT_NONE。

有关详细信息，请参阅 Windows SDK 中的[IDropTarget：:D拉格Enter。](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter)

## <a name="coledroptargetondragleave"></a><a name="ondragleave"></a>COleDrop目标：：OnDragLeave

当光标离开窗口时，当拖动操作生效时，由框架调用。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向光标要离开的窗口。

### <a name="remarks"></a>备注

如果要在拖动操作离开指定窗口时需要特殊行为，请覆盖此函数。 此函数的默认实现调用[CView：onDragLeave](../../mfc/reference/cview-class.md#ondragleave)。

有关详细信息，请参阅 Windows SDK 中的[IDropTarget：:D拉格离开](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave)。

## <a name="coledroptargetondragover"></a><a name="ondragover"></a>COleDrop目标：：OnDragover

当光标拖过窗口时，由框架调用。

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向光标已结束的窗口。

*pDataObject*<br/>
指向包含要删除的数据的数据对象。

*德基州*<br/>
包含修改器键的状态。 这是以下任意数量的组合：MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*点*<br/>
在客户端坐标中包含光标的当前位置。

### <a name="return-value"></a>返回值

如果在*点*指定的位置尝试放置时将导致的效果。 它可以是以下一个或多个：

- DROPEFFECT_NONE不允许掉下。

- DROPEFFECT_COPY将执行复制操作。

- DROPEFFECT_MOVE将执行移动操作。

- DROPEFFECT_LINK将建立从删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 指示拖动滚动操作即将发生或发生在目标中。

### <a name="remarks"></a>备注

应重写此函数以允许在窗口中执行放置操作。 此函数的默认实现称为[CView：：onDragOver](../../mfc/reference/cview-class.md#ondragover)，默认情况下返回DROPEFFECT_NONE。 由于此函数在拖放操作期间频繁调用，因此应尽可能对其进行优化。

有关详细信息，请参阅 Windows SDK 中的[IDropTarget：:D拉格。](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

## <a name="coledroptargetondragscroll"></a><a name="ondragscroll"></a>COleDrop目标：：OnDragscroll

在调用[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)之前由框架调用，以确定*点*是否位于滚动区域中。

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向光标当前结束的窗口。

*德基州*<br/>
包含修改器键的状态。 这是以下任意数量的组合：MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*点*<br/>
包含光标相对于屏幕的位置（以像素为单位）。

### <a name="return-value"></a>返回值

如果在*点*指定的位置尝试放置时将导致的效果。 它可以是以下一个或多个：

- DROPEFFECT_NONE不允许掉下。

- DROPEFFECT_COPY将执行复制操作。

- DROPEFFECT_MOVE将执行移动操作。

- DROPEFFECT_LINK将建立从删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 指示拖动滚动操作即将发生或发生在目标中。

### <a name="remarks"></a>备注

如果要为此事件提供特殊行为，请重写此函数。 此函数的默认实现称为[CView：：OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll)，当光标拖动到窗口边框内的默认滚动区域时，它返回DROPEFFECT_NONE并滚动窗口。

## <a name="coledroptargetondrop"></a><a name="ondrop"></a>COleDrop目标：：上投

当发生放置操作时，由框架调用。

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向光标当前结束的窗口。

*pDataObject*<br/>
指向包含要删除的数据的数据对象。

*滴效果*<br/>
用户为放置操作选择的效果。 它可以是以下一个或多个：

- DROPEFFECT_COPY将执行复制操作。

- DROPEFFECT_MOVE将执行移动操作。

- DROPEFFECT_LINK将建立从删除数据到原始数据的链接。

*点*<br/>
包含光标相对于屏幕的位置（以像素为单位）。

### <a name="return-value"></a>返回值

如果丢弃成功，则非零;否则 0。

### <a name="remarks"></a>备注

框架首先调用[OnDropEx](#ondropex)。 如果`OnDropEx`函数不处理丢弃，则框架将调用此成员函数`OnDrop`。 通常，应用程序将覆盖视图类中的[OnDropEx，](../../mfc/reference/cview-class.md#ondropex)以处理鼠标右键拖放。 通常，视图类[OnDrop](../../mfc/reference/cview-class.md#ondrop)用于处理简单的拖放。

调用`COleDropTarget::OnDrop`[CView：：onDrop](../../mfc/reference/cview-class.md#ondrop)的默认实现，默认情况下只需返回 FALSE。

有关详细信息，请参阅 Windows SDK 中的[IDropTarget：:Drop。](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop)

## <a name="coledroptargetondropex"></a><a name="ondropex"></a>COleDrop目标：：OnDropEx

当发生放置操作时，由框架调用。

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向光标当前结束的窗口。

*pDataObject*<br/>
指向包含要删除的数据的数据对象。

*丢弃默认*<br/>
用户根据当前键状态为默认放置操作选择的效果。 它可以DROPEFFECT_NONE。 "注释"部分将讨论放置效果。

*下拉列表*<br/>
放置源支持的放置效果的列表。 可以使用位或 （**&#124;**） 操作组合放置效果值。 "注释"部分将讨论放置效果。

*点*<br/>
包含光标相对于屏幕的位置（以像素为单位）。

### <a name="return-value"></a>返回值

从*点指定的位置*的放置尝试产生的放置效果。 "注释"部分将讨论放置效果。

### <a name="remarks"></a>备注

框架首先调用此函数。 如果它不处理丢弃，则框架将调用[OnDrop](#ondrop)。 通常，您将在视图类中覆盖[OnDropEx](../../mfc/reference/cview-class.md#ondropex)以支持鼠标右键拖放。 通常，视图类[OnDrop](../../mfc/reference/cview-class.md#ondrop)用于处理支持简单拖放的情况。

调用 CView`COleDropTarget::OnDropEx`的默认实现[：onDropEx](../../mfc/reference/cview-class.md#ondropex)。 默认情况下[，CView：onDropEx](../../mfc/reference/cview-class.md#ondropex)仅返回一个虚拟值，以指示应调用[OnDrop](#ondrop)成员函数。

放置效果描述与放置操作关联的操作。 请参阅以下放置效果列表：

- DROPEFFECT_NONE不允许掉下。

- DROPEFFECT_COPY将执行复制操作。

- DROPEFFECT_MOVE将执行移动操作。

- DROPEFFECT_LINK将建立从删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 指示拖动滚动操作即将发生或发生在目标中。

有关详细信息，请参阅 Windows SDK 中的[IDropTarget：:Drop。](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop)

## <a name="coledroptargetregister"></a><a name="register"></a>COleDrop目标：：注册

调用此函数以将窗口注册为有效的放置目标。

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向要注册为放置目标的窗口。

### <a name="return-value"></a>返回值

注册成功时非零;否则 0。

### <a name="remarks"></a>备注

必须调用此函数才能接受放置操作。

有关详细信息，请参阅 Windows SDK 中的[注册DragDrop。](/windows/win32/api/ole2/nf-ole2-registerdragdrop)

## <a name="coledroptargetrevoke"></a><a name="revoke"></a>COleDrop目标：：撤销

在通过"[注册"](#register)调用销毁已注册为放置目标的任何窗口之前调用此函数，以便将其从放置目标列表中删除。

```
virtual void Revoke();
```

### <a name="remarks"></a>备注

此函数从已注册窗口的[On销毁](../../mfc/reference/cwnd-class.md#ondestroy)处理程序自动调用，因此通常不需要显式调用此函数。

有关详细信息，请参阅 Windows SDK 中的["撤销DragDrop"。](/windows/win32/api/ole2/nf-ole2-revokedragdrop)

## <a name="see-also"></a>另请参阅

[MFC 样品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDrop源类](../../mfc/reference/coledropsource-class.md)
