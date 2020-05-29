---
title: COleResizeBar 类
ms.date: 11/04/2016
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
ms.openlocfilehash: beb0c37b6ac23310b7d5c8506fbdaf677dd74d8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376152"
---
# <a name="coleresizebar-class"></a>COleResizeBar 类

支持调整现有 OLE 项的控件条类型。

## <a name="syntax"></a>语法

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle ResizeBar：COle resizebar](#coleresizebar)|构造 `COleResizeBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle Resize 栏：创建](#create)|创建 Windows 子窗口并将其初始化，并将其关联到`COleResizeBar`对象。|

## <a name="remarks"></a>备注

`COleResizeBar`对象显示为具有阴影边框和外部调整大小的控点的[CRectTracker。](../../mfc/reference/crecttracker-class.md)

`COleResizeBar`对象通常是派生自[COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)类的帧窗口对象的嵌入成员。

有关详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[C控制栏](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="coleresizebarcoleresizebar"></a><a name="coleresizebar"></a>COle ResizeBar：COle resizebar

构造 `COleResizeBar` 对象。

```
COleResizeBar();
```

### <a name="remarks"></a>备注

调用`Create`以创建调整条形对象的大小。

## <a name="coleresizebarcreate"></a><a name="create"></a>COle Resize 栏：创建

创建子窗口并将其与`COleResizeBar`对象关联。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向调整大小条的父窗口。

*dwStyle*<br/>
指定[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)属性。

*nID*<br/>
调整条形的子窗口 ID 的大小。

### <a name="return-value"></a>返回值

如果创建了调整大小条，则非零;否则 0。

## <a name="see-also"></a>另请参阅

[MFC 样品 SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)
