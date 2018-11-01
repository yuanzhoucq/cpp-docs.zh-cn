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
ms.openlocfilehash: 739bf08139c56992af883b5cefa5c235bf08f551
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623647"
---
# <a name="cdraglistbox-class"></a>CDragListBox 类

除了提供 Windows 列表框中，功能`CDragListBox`类允许用户在列表框内移动文件名等列表框项。

## <a name="syntax"></a>语法

```
class CDragListBox : public CListBox
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDragListBox::CDragListBox](#cdraglistbox)|构造 `CDragListBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDragListBox::BeginDrag](#begindrag)|在拖动操作开始时由框架调用。|
|[CDragListBox::CancelDrag](#canceldrag)|已取消拖动操作时由框架调用。|
|[CDragListBox::Dragging](#dragging)|在拖动操作期间由框架调用。|
|[CDragListBox::DrawInsert](#drawinsert)|绘制拖动列表框的插入参考线。|
|[CDragListBox::Dropped](#dropped)|已删除项后，由框架调用。|
|[CDragListBox::ItemFromPt](#itemfrompt)|返回被拖动的项的坐标。|

## <a name="remarks"></a>备注

借助此功能的列表框允许用户列表中的任何方式是对他们最有用的项进行排序。 默认情况下，列表框会将项移动到列表中的新位置。 但是，`CDragListBox`可以自定义对象要复制的项而不是移动它们。

与关联的列表框控件`CDragListBox`类不能 LBS_SORT 或 LBS_MULTIPLESELECT 样式。 列表框样式的说明，请参阅[列表框样式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)。

若要使用现有应用程序的对话框中的拖动列表框，添加列表框控件到对话框模板使用对话框编辑器，然后将成员变量 (的类别`Control`和变量类型`CDragListBox`) 对应于列表框控制在对话框模板中。

将控件分配到成员变量的详细信息，请参阅[定义对话框控件成员变量的快捷方式](../../windows/defining-member-variables-for-dialog-controls.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="begindrag"></a>  CDragListBox::BeginDrag

由框架事件发生时无法开始拖动操作，例如，按下鼠标左键。

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含正在拖动的项的坐标。

### <a name="return-value"></a>返回值

如果拖动允许，否则为 0，非零值。

### <a name="remarks"></a>备注

如果你想要控制在拖动操作开始时，会发生什么情况，重写此函数。 默认实现捕获鼠标并停留在拖动模式，直到用户单击鼠标左键或右键按钮或按 esc 键，此时拖动操作已取消。

##  <a name="canceldrag"></a>  CDragListBox::CancelDrag

已取消拖动操作时由框架调用。

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含正在拖动的项的坐标。

### <a name="remarks"></a>备注

重写此函数以处理在列表框控件的任何特殊处理。

##  <a name="cdraglistbox"></a>  CDragListBox::CDragListBox

构造 `CDragListBox` 对象。

```
CDragListBox();
```

##  <a name="dragging"></a>  CDragListBox::Dragging

内正在拖动的列表框项时由框架调用`CDragListBox`对象。

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含 x 和 y 屏幕坐标的光标。

### <a name="return-value"></a>返回值

要显示光标的资源 ID。 还可能有以下值：

- DL_COPYCURSOR 指示要复制该项目。

- DL_MOVECURSOR 指示将移动该项目。

- DL_STOPCURSOR 指示当前的拖放目标不是可接受。

### <a name="remarks"></a>备注

默认行为返回 DL_MOVECURSOR。 如果你想要提供其他功能，重写此函数。

##  <a name="drawinsert"></a>  CDragListBox::DrawInsert

由框架调用以绘制插入指南之前具有所指示的索引的项。

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>参数

*nItem*<br/>
插入点的从零开始索引。

### <a name="remarks"></a>备注

值为-1 清除插入参考线。 重写此函数可修改的外观或行为插入参考线。

##  <a name="dropped"></a>  CDragListBox::Dropped

在删除某个项时由框架调用`CDragListBox`对象。

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>参数

*nSrcIndex*<br/>
指定删除字符串的从零开始的索引。

*pt*<br/>
一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，它包含放置站点的坐标。

### <a name="remarks"></a>备注

默认行为将列表框项和其数据复制到新位置，然后删除原始项。 重写此函数可自定义默认行为，例如启用列表框项拖动到列表中其他位置的副本。

##  <a name="itemfrompt"></a>  CDragListBox::ItemFromPt

调用此函数可检索列表框项的从零开始的索引位于*pt*。

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>参数

*pt*<br/>
一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，包含在列表框内的点的坐标。

*bAutoScroll*<br/>
如果允许滚动，否则为 0，非零值。

### <a name="return-value"></a>返回值

将列表框项的从零开始的索引。

## <a name="see-also"></a>请参阅

[MFC 示例 TSTCON](../../visual-cpp-samples.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)
