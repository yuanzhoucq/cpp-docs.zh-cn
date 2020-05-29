---
title: CMFCTabDropTarget 类
ms.date: 11/04/2016
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
ms.openlocfilehash: 83432fdb90fe28214fb1faaf843556deb2f44750
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367346"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget 类

提供选项卡控件和 OLE 库之间的通信机制。

## <a name="syntax"></a>语法

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|`CMFCTabDropTarget::CMFCTabDropTarget`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFCTabDrop目标：：onDragenter](#ondragenter)|当用户将对象拖动到选项卡窗口中时，由框架调用。 （覆盖[COleDrop 目标：：OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).）|
|[CMFCTabDrop目标：：OnDragLeave](#ondragleave)|当用户在具有焦点的选项卡窗口外拖动对象时，由框架调用。 （覆盖[COleDrop 目标：：OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).）|
|[CMFCTabDrop目标：：OnDragover](#ondragover)|当用户将对象拖动到具有焦点的选项卡窗口时，由框架调用。 （覆盖[COleDrop 目标：：OnDragover.）](../../mfc/reference/coledroptarget-class.md#ondragover)|
|[CMFCTabDrop目标：：OnDropEx](#ondropex)|当用户在拖动操作结束时释放鼠标按钮时，由框架调用。 （覆盖[COleDrop 目标：onDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).）|
|[CMFCTabDrop目标：：注册](#register)|将控件注册为可作为 OLE 拖放操作目标的控件。|

### <a name="remarks"></a>备注

此类为`CMFCBaseTabCtrl`类提供拖放支持。 如果应用程序使用[AfxOleInit](ole-initialization.md#afxoleinit)函数初始化 OLE 库，`CMFCBaseTabCtrl`则对象将自行注册以执行拖放操作。

当`CMFCTabDropTarget`拖动操作发生活动时，类通过使光标下方的选项卡变为活动来扩展其基类。 有关拖放操作的详细信息，请参阅[OLE 拖放](../../mfc/drag-and-drop-ole.md)操作 。

## <a name="example"></a>示例

下列示例演示如何构造 `CMFCTabDropTarget` 对象并使用其 `Register` 方法。

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDrop目标](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>要求

**标头：** afxbasetabctrl.h

## <a name="cmfctabdroptargetondragenter"></a><a name="ondragenter"></a>CMFCTabDrop目标：：onDragenter

当用户将对象拖动到选项卡窗口中时，由框架调用。

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pwnd*|[在]闲置。|
|*pDataObject*|[在]指向用户拖动的对象的指针。|
|*德基州*|[在]包含修改器键的状态。 这是以下任意数量的组合：MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。|
|*点*|[在]游标在客户端坐标中的位置。|

### <a name="return-value"></a>返回值

如果放置发生在*点*指定的位置，则产生的效果。 它可以是以下一个或多个：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>备注

如果工具栏框架未处于自定义模式或剪贴板数据格式不可用，则此方法将返回DROPEFFECT_NONE。 否则，它将返回使用提供的参数调用`CMFCBaseTabCtrl::OnDragEnter`的结果。

有关自定义模式的详细信息，请参阅[CMFCToolBar：：是自定义模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 有关剪贴板数据格式的详细信息，请参阅[COleDataObject：：是数据可用](../../mfc/reference/coledataobject-class.md#isdataavailable)。

## <a name="cmfctabdroptargetondragleave"></a><a name="ondragleave"></a>CMFCTabDrop目标：：OnDragLeave

当用户在具有焦点的选项卡窗口外拖动对象时，由框架调用。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pwnd*|[在]闲置。|

### <a name="remarks"></a>备注

此方法调用 方法`CMFCBaseTabCtrl::OnDragLeave`以执行拖动操作。

## <a name="cmfctabdroptargetondragover"></a><a name="ondragover"></a>CMFCTabDrop目标：：OnDragover

当用户将对象拖动到具有焦点的选项卡窗口时，由框架调用。

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pwnd*|[在]闲置。|
|*pDataObject*|[在]指向用户拖动的对象的指针。|
|*德基州*|[在]包含修改器键的状态。 这是以下任意数量的组合：MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。|
|*点*|[在]鼠标指针在客户端坐标中的位置。|

### <a name="return-value"></a>返回值

如果放置发生在*点*指定的位置，则产生的效果。 它可以是以下一个或多个：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>备注

此方法使拖动操作发生时光标下方的选项卡处于活动状态。 如果工具栏框架未处于自定义模式或剪贴板数据格式不可用，则返回DROPEFFECT_NONE。 否则，它将返回使用提供的参数调用`CMFCBaseTabCtrl::OnDragOver`的结果。

有关自定义模式的详细信息，请参阅[CMFCToolBar：：是自定义模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 有关剪贴板数据格式的详细信息，请参阅[COleDataObject：：是数据可用](../../mfc/reference/coledataobject-class.md#isdataavailable)。

## <a name="cmfctabdroptargetondropex"></a><a name="ondropex"></a>CMFCTabDrop目标：：OnDropEx

当用户在拖动操作结束时释放鼠标按钮时，由框架调用。

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pwnd*|[在]闲置。|
|*pDataObject*|[在]指向用户拖动的对象的指针。|
|*滴效果*|[在]默认放置操作。|
|*下拉列表*|[在]闲置。|
|*点*|[在]鼠标指针在客户端坐标中的位置。|

### <a name="return-value"></a>返回值

生成的放置效果。 它可以是以下一个或多个：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>备注

如果工具栏框架`CMFCBaseTabCtrl::OnDrop`处于自定义模式且剪贴板数据格式可用，则此方法将调用。 如果调用返回`CMFCBaseTabCtrl::OnDrop`非零值，此方法将返回*drop效果*指定的默认删除效果。 否则，此方法将返回DROPEFFECT_NONE。 有关放置效果的详细信息，请参阅[COleDropTarget：：onDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。

有关自定义模式的详细信息，请参阅[CMFCToolBar：：是自定义模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 有关剪贴板数据格式的详细信息，请参阅[COleDataObject：：是数据可用](../../mfc/reference/coledataobject-class.md#isdataavailable)。

## <a name="cmfctabdroptargetregister"></a><a name="register"></a>CMFCTabDrop目标：：注册

将控件注册为可作为 OLE 拖放操作目标的控件。

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pOwner*|[在]要注册为放置目标的选项卡控件。|

### <a name="return-value"></a>返回值

注册成功时非零;否则 0。

### <a name="remarks"></a>备注

此方法调用[COleDropTarget：：注册](../../mfc/reference/coledroptarget-class.md#register)以注册拖放操作的控件。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[OLE 拖放](../../mfc/drag-and-drop-ole.md)
