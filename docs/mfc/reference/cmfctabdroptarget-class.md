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
ms.openlocfilehash: d0090386b1ebb4d89b9a7613a0b2a28529decbe5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127422"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget 类

提供选项卡控件和 OLE 库之间的通信机制。

## <a name="syntax"></a>语法

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|`CMFCTabDropTarget::CMFCTabDropTarget`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFCTabDropTarget：： System.windows.uielement.ondragenter](#ondragenter)|当用户将对象拖到选项卡窗口时由框架调用。 （重写[COleDropTarget：： system.windows.uielement.ondragenter](../../mfc/reference/coledroptarget-class.md#ondragenter)。）|
|[CMFCTabDropTarget：： System.windows.uielement.ondragleave](#ondragleave)|当用户将对象拖到具有焦点的选项卡窗口之外时由框架调用。 （重写[COleDropTarget：： system.windows.uielement.ondragleave](../../mfc/reference/coledroptarget-class.md#ondragleave)。）|
|[CMFCTabDropTarget：： System.windows.uielement.ondragover](#ondragover)|当用户将对象拖动到具有焦点的选项卡窗口时由框架调用。 （重写[COleDropTarget：： system.windows.uielement.ondragover](../../mfc/reference/coledroptarget-class.md#ondragover)。）|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|当用户在拖动操作结束时释放鼠标按钮时，由框架调用。 （重写[COleDropTarget：： OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。）|
|[CMFCTabDropTarget：： Register](#register)|将控件注册为一个可以作为 OLE 拖放操作的目标的控件。|

### <a name="remarks"></a>备注

此类提供对 `CMFCBaseTabCtrl` 类的拖放支持。 如果你的应用程序使用[AfxOleInit](ole-initialization.md#afxoleinit)函数初始化 OLE 库，`CMFCBaseTabCtrl` 对象将自行注册以进行拖放操作。

在拖动操作发生活动时，`CMFCTabDropTarget` 类通过使光标下的选项卡来扩展其基类。 有关拖放操作的详细信息，请参阅[OLE 拖放](../../mfc/drag-and-drop-ole.md)。

## <a name="example"></a>示例

下列示例演示如何构造 `CMFCTabDropTarget` 对象并使用其 `Register` 方法。

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>要求

**标头：** afxbasetabctrl.h

##  <a name="ondragenter"></a>CMFCTabDropTarget：： System.windows.uielement.ondragenter

当用户将对象拖到选项卡窗口时由框架调用。

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
|*pWnd*|中用.|
|*pDataObject*|中指向用户拖动的对象的指针。|
|*dwKeyState*|中包含修改键的状态。 这是以下任意数量的组合： "MK_CONTROL"、"MK_SHIFT"、"MK_ALT"、"MK_LBUTTON"、"MK_MBUTTON" 和 "MK_RBUTTON"。|
|*情况*|中光标在工作区坐标中的位置。|

### <a name="return-value"></a>返回值

如果在*点*指定的位置发生放置，则会产生效果。 它可以是下列一项或多项：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>备注

如果工具栏框架未处于自定义模式或剪贴板数据格式不可用，则此方法将返回 DROPEFFECT_NONE。 否则，它将返回调用 `CMFCBaseTabCtrl::OnDragEnter` 与提供的参数的结果。

有关自定义模式的详细信息，请参阅[CMFCToolBar：： IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 有关剪贴板数据格式的详细信息，请参阅[COleDataObject：： IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。

##  <a name="ondragleave"></a>CMFCTabDropTarget：： System.windows.uielement.ondragleave

当用户将对象拖到具有焦点的选项卡窗口之外时由框架调用。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pWnd*|中用.|

### <a name="remarks"></a>备注

此方法调用 `CMFCBaseTabCtrl::OnDragLeave` 方法来执行拖动操作。

##  <a name="ondragover"></a>CMFCTabDropTarget：： System.windows.uielement.ondragover

当用户将对象拖动到具有焦点的选项卡窗口时由框架调用。

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
|*pWnd*|中用.|
|*pDataObject*|中指向用户拖动的对象的指针。|
|*dwKeyState*|中包含修改键的状态。 这是以下任意数量的组合： "MK_CONTROL"、"MK_SHIFT"、"MK_ALT"、"MK_LBUTTON"、"MK_MBUTTON" 和 "MK_RBUTTON"。|
|*情况*|中鼠标指针在工作区坐标中的位置。|

### <a name="return-value"></a>返回值

如果在*点*指定的位置发生放置，则会产生效果。 它可以是下列一项或多项：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>备注

此方法使在拖动操作发生活动时光标下的选项卡处于活动状态。 如果工具栏框架未处于自定义模式或剪贴板数据格式不可用，它将返回 DROPEFFECT_NONE。 否则，它将返回调用 `CMFCBaseTabCtrl::OnDragOver` 与提供的参数的结果。

有关自定义模式的详细信息，请参阅[CMFCToolBar：： IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 有关剪贴板数据格式的详细信息，请参阅[COleDataObject：： IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。

##  <a name="ondropex"></a>CMFCTabDropTarget::OnDropEx

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
|*pWnd*|中用.|
|*pDataObject*|中指向用户拖动的对象的指针。|
|*dropEffect*|中默认放置操作。|
|*dropList*|中用.|
|*情况*|中鼠标指针在工作区坐标中的位置。|

### <a name="return-value"></a>返回值

生成的放置效果。 它可以是下列一项或多项：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>备注

如果工具栏框架处于自定义模式且剪贴板数据格式可用，则此方法将调用 `CMFCBaseTabCtrl::OnDrop`。 如果 `CMFCBaseTabCtrl::OnDrop` 对的调用将返回一个非零值，则此方法将返回*dropEffect*指定的默认投影效果。 否则，此方法将返回 DROPEFFECT_NONE。 有关 drop 特效的详细信息，请参阅[COleDropTarget：： OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。

有关自定义模式的详细信息，请参阅[CMFCToolBar：： IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 有关剪贴板数据格式的详细信息，请参阅[COleDataObject：： IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。

##  <a name="register"></a>CMFCTabDropTarget：： Register

将控件注册为一个可以作为 OLE 拖放操作的目标的控件。

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pOwner*|中要注册为拖放目标的选项卡控件。|

### <a name="return-value"></a>返回值

如果注册成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

此方法调用[COleDropTarget：： register](../../mfc/reference/coledroptarget-class.md#register)来注册控件以便进行拖放操作。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[OLE 拖放](../../mfc/drag-and-drop-ole.md)
