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
ms.openlocfilehash: 698e37b2853a2ca3698ee0a426c8ded688c99c58
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776617"
---
# <a name="clistview-class"></a>CListView 类

可以使用列表控件和简化[CListCtrl](../../mfc/reference/clistctrl-class.md)，封装列表控件功能，使用 MFC 文档视图体系结构的类。

## <a name="syntax"></a>语法

```
class CListView : public CCtrlView
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CListView::CListView](#clistview)|构造 `CListView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CListView::GetListCtrl](#getlistctrl)|返回与视图关联的列表控件。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CListView::RemoveImageList](#removeimagelist)|从列表视图中删除指定的图像列表。|

## <a name="remarks"></a>备注

此体系结构的详细信息，请参阅的概览[CView](../../mfc/reference/cview-class.md)类和交叉引用那里引用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>要求

**标头：** afxcview.h

##  <a name="clistview"></a>  CListView::CListView

构造 `CListView` 对象。

```
CListView();
```

##  <a name="getlistctrl"></a>  CListView::GetListCtrl

调用此成员函数以获取对与视图关联的列表控件的引用。

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>返回值

对列表控件与视图关联的引用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

##  <a name="removeimagelist"></a>  CListView::RemoveImageList

从列表视图中删除指定的图像列表。

```
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>参数

*nImageList*<br/>
要移除的图像的从零开始的索引。

## <a name="see-also"></a>请参阅

[MFC 示例 ROWLIST](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)
