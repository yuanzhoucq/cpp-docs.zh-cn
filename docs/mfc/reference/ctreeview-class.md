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
ms.openlocfilehash: fec8379a3944d981672754274f50dd4e60f71b61
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426773"
---
# <a name="ctreeview-class"></a>CTreeView 类

简化对树控件和[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)（封装树控件功能的类，以及 MFC 文档视图体系结构）的使用。

## <a name="syntax"></a>语法

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CTreeView：： CTreeView](#ctreeview)|构造 `CTreeView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CTreeView：： GetTreeCtrl](#gettreectrl)|返回与视图关联的树控件。|

## <a name="remarks"></a>备注

有关此体系结构的详细信息，请参阅[CView](../../mfc/reference/cview-class.md)类和引用的交叉引用的概述。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>要求

**标头：** afxcview

##  <a name="ctreeview"></a>CTreeView：： CTreeView

构造 `CTreeView` 对象。

```
CTreeView();
```

##  <a name="gettreectrl"></a>CTreeView：： GetTreeCtrl

返回对与视图关联的树控件的引用。

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>另请参阅

[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)
