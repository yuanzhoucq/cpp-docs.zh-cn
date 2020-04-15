---
title: CDragListBox 类
ms.date: 11/04/2016
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
ms.openlocfilehash: 0d1ae94948e1143a5bac17985423c4bd1bfbaf65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374034"
---
# <a name="cdraglistbox-class"></a>CDragListBox 类

除了提供 Windows 列表框的功能外，`CDragListBox`该类还允许用户在列表框中移动列表框项（如文件名）。

## <a name="syntax"></a>语法

```
class CDragListBox : public CListBox
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDragListBox：CDraglistBox](#cdraglistbox)|构造 `CDragListBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDragListBox：：开始拖动](#begindrag)|拖动操作开始时由框架调用。|
|[CDragListBox：：取消拖动](#canceldrag)|当拖动操作被取消时由框架调用。|
|[CDragListBox：:D](#dragging)|在拖动操作期间由框架调用。|
|[CDragListBox：:D原始插入](#drawinsert)|绘制拖动列表框的插入指南。|
|[CDragListBox：:D](#dropped)|删除项后由框架调用。|
|[CDraglistBox：：项目从Pt](#itemfrompt)|返回要拖动的项的坐标。|

## <a name="remarks"></a>备注

具有此功能的列表框允许用户以对它们最有用的任何方式对列表中的项目排序。 默认情况下，列表框会将项目移动到列表中的新位置。 但是，`CDragListBox`可以自定义对象以复制项目，而不是移动它们。

与`CDragListBox`类关联的列表框控件不得具有LBS_SORT或LBS_MULTIPLESELECT样式。 有关列表框样式的说明，请参阅[列表框样式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)。

要在应用程序的现有对话框中使用拖动列表框，请使用对话框编辑器向对话框模板添加列表框控件，然后分配与对话框模板中的列表框控件对应的成员变量（类别`Control`和变量类型）。 `CDragListBox`

有关将控件分配给成员变量的详细信息，请参阅[为对话框控件定义成员变量的快捷方式](../../windows/defining-member-variables-for-dialog-controls.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a>CDragListBox：：开始拖动

当可能发生可能开始拖动操作的事件（如按下鼠标左键）时，由框架调用。

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
包含要拖动的项的坐标的[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

### <a name="return-value"></a>返回值

如果允许拖动，则不为零，否则为 0。

### <a name="remarks"></a>备注

如果要控制拖动操作开始时发生的情况，请覆盖此函数。 默认实现捕获鼠标并保持拖动模式，直到用户单击鼠标左键或右键或按 ESC，此时拖动操作将被取消。

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a>CDragListBox：：取消拖动

当拖动操作被取消时由框架调用。

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
包含要拖动的项的坐标的[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

### <a name="remarks"></a>备注

重写此函数以处理列表框控件的任何特殊处理。

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a>CDragListBox：CDraglistBox

构造 `CDragListBox` 对象。

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a>CDragListBox：:D

在`CDragListBox`对象内拖动列表框项时，由框架调用。

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
包含光标的 x 和 y 屏幕坐标的[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

### <a name="return-value"></a>返回值

要显示的游标的资源 ID。 可能的值如下：

- DL_COPYCURSOR 指示将复制该项目。

- DL_MOVECURSOR 指示将移动该项目。

- DL_STOPCURSOR 指示当前放置目标不可接受。

### <a name="remarks"></a>备注

默认行为返回DL_MOVECURSOR。 如果要提供其他功能，请重写此函数。

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a>CDragListBox：:D原始插入

由框架调用，以使用指示的索引在项目之前绘制插入指南。

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>参数

*nItem*<br/>
插入点的零索引。

### <a name="remarks"></a>备注

值 - 1 清除插入参考线。 重写此函数以修改插入参考线的外观或行为。

## <a name="cdraglistboxdropped"></a><a name="dropped"></a>CDragListBox：:D

当项在`CDragListBox`对象中删除时，由框架调用。

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>参数

*nSrcIndex*<br/>
指定删除字符串的零基索引。

*pt*<br/>
包含放置站点坐标的[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

### <a name="remarks"></a>备注

默认行为将列表框项及其数据复制到新位置，然后删除原始项。 重写此函数以自定义默认行为，例如启用要拖动到列表中其他位置的列表框项的副本。

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a>CDraglistBox：：项目从Pt

调用此函数以检索位于*pt*的列表框项的零基索引。

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>参数

*pt*<br/>
包含列表框中点坐标的[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。

*bAutoScroll*<br/>
如果允许滚动，则非零，否则为 0。

### <a name="return-value"></a>返回值

拖动列表框项的零基索引。

## <a name="see-also"></a>另请参阅

[MFC 样品 TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)
