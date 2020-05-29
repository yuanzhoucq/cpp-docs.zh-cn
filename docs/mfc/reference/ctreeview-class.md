---
title: CTreeView 类
ms.date: 11/04/2016
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
ms.openlocfilehash: 2ef93152c83d3bbec2b89ada0596ee612b24701b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373293"
---
# <a name="ctreeview-class"></a>CTreeView 类

使用 MFC 的文档视图体系结构简化了树控件和[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)的类，该类封装了树控制功能。

## <a name="syntax"></a>语法

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CTree视图：CTreeView](#ctreeview)|构造 `CTreeView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CTreeView：：获取树谱](#gettreectrl)|返回与视图关联的树控件。|

## <a name="remarks"></a>备注

有关此体系结构的详细信息，请参阅[CView](../../mfc/reference/cview-class.md)类的概述以及其中引用的交叉引用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>要求

**标题：** afxcview.h

## <a name="ctreeviewctreeview"></a><a name="ctreeview"></a>CTree视图：CTreeView

构造 `CTreeView` 对象。

```
CTreeView();
```

## <a name="ctreeviewgettreectrl"></a><a name="gettreectrl"></a>CTreeView：：获取树谱

返回对与视图关联的树控件的引用。

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>另请参阅

[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)
