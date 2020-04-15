---
title: CListView 类
ms.date: 11/04/2016
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
helpviewer_keywords:
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
ms.openlocfilehash: ae1a76e4cdd052ff44dcbd69d467c51741bcc2ff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370141"
---
# <a name="clistview-class"></a>CListView 类

使用 MFC 的文档视图体系结构简化了列表控件和[CListCtrl（](../../mfc/reference/clistctrl-class.md)封装列表控制功能的类）的使用。

## <a name="syntax"></a>语法

```
class CListView : public CCtrlView
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CListView：CListView](#clistview)|构造 `CListView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CListView：获取列表Ctrl](#getlistctrl)|返回与视图关联的列表控件。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CList查看：删除图片列表](#removeimagelist)|从列表视图中删除指定的图像列表。|

## <a name="remarks"></a>备注

有关此体系结构的详细信息，请参阅[CView](../../mfc/reference/cview-class.md)类的概述以及其中引用的交叉引用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>要求

**标题：** afxcview.h

## <a name="clistviewclistview"></a><a name="clistview"></a>CListView：CListView

构造 `CListView` 对象。

```
CListView();
```

## <a name="clistviewgetlistctrl"></a><a name="getlistctrl"></a>CListView：获取列表Ctrl

调用此成员函数以获取对与视图关联的列表控件的引用。

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>返回值

对与视图关联的列表控件的引用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

## <a name="clistviewremoveimagelist"></a><a name="removeimagelist"></a>CList查看：删除图片列表

从列表视图中删除指定的图像列表。

```
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>参数

*n图像列表*<br/>
要删除的图像的零基索引。

## <a name="see-also"></a>另请参阅

[MFC 样品 ROWLIST](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)
