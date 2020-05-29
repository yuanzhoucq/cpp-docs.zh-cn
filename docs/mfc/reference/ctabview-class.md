---
title: CTabView 类
ms.date: 11/04/2016
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
ms.openlocfilehash: ad30cbbf5de195708d2d357a76c38b661d095c2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365926"
---
# <a name="ctabview-class"></a>CTabView 类

该`CTabView`类简化了在使用 MFC 的文档/视图体系结构的应用程序中使用选项卡控制类 （ [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)）。

## <a name="syntax"></a>语法

```
class CTabbedView : public CView
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CTabView：：添加视图](#addview)|向选项卡控件添加新视图。|
|[CTabView：：查找选项卡](#findtab)|在选项卡控件中返回指定视图的索引。|
|[CTabView：获取活动视图](#getactiveview)|返回指向当前活动视图的指针|
|[CTabView：获取Tab控制](#gettabcontrol)|返回对与视图关联的选项卡控件的引用。|
|[CTabView：删除查看](#removeview)|从选项卡控件中删除视图。|
|[CTabView：设置活动视图](#setactiveview)|使视图处于活动状态。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CTabView：：IsScrollBar](#isscrollbar)|创建选项卡视图时由框架调用，以确定选项卡视图是否具有共享的水平滚动条。|
|[CTabView：打开激活视图](#onactivateview)|当选项卡视图变为活动或非活动时，由框架调用。|

## <a name="remarks"></a>备注

此类可以轻松地将选项卡式视图放入文档/视图应用程序中。 `CTabView`是包含`CView`嵌入`CMFCTabCtrl`对象的派生类。 `CTabView`处理支持`CMFCTabCtrl`该对象所需的所有消息。 只需从`CTabView`派生类并将其插入应用程序，然后使用 方法`CView``AddView`添加派生类。 选项卡控件将这些视图显示为选项卡。

例如，您可能有一个文档可以以不同的方式表示：作为电子表格、图表、可编辑窗体等。 您可以根据需要创建绘制数据的单个视图，将它们插入到`CTabView`派生对象中，并在不进行任何其他编码的情况下对其进行选项卡化。

[选项卡式视图示例：MFC 选项卡式视图应用程序](../../overview/visual-cpp-samples.md)演示`CTabView`了 的用法。

## <a name="example"></a>示例

下面的示例显示了在`CTabView`TabbedView 示例中的使用方式。

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>要求

**标题：** afxTabView.h

## <a name="ctabviewaddview"></a><a name="addview"></a>CTabView：：添加视图

向选项卡控件添加视图。

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>参数

*pView 类*<br/>
[在]指向插入视图的运行时类的指针。

*strViewLabel*<br/>
[在]指定选项卡的文本。

*iIndex*<br/>
[在]指定要插入视图的零基位置。 如果位置为 -1，则新选项卡将插入到末尾。

*pContext*<br/>
[在]指向视图`CCreateContext`的指针。

### <a name="return-value"></a>返回值

如果此方法成功，则为视图索引。 否则，为 -1。

### <a name="remarks"></a>备注

调用此函数以向嵌入在帧中的选项卡控件添加视图。

## <a name="ctabviewfindtab"></a><a name="findtab"></a>CTabView：：查找选项卡

在选项卡控件中返回指定视图的索引。

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>参数

*hWndView*<br/>
[在]视图的句柄。

### <a name="return-value"></a>返回值

如果找到视图，则为视图的索引;否则，-1。

### <a name="remarks"></a>备注

调用此函数以检索具有指定句柄的视图的索引。

## <a name="ctabviewgetactiveview"></a><a name="getactiveview"></a>CTabView：获取活动视图

返回指向当前活动视图的指针。

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>返回值

指向活动视图的有效指针，如果没有活动视图，则指向 NULL。

### <a name="remarks"></a>备注

## <a name="ctabviewgettabcontrol"></a><a name="gettabcontrol"></a>CTabView：获取Tab控制

返回对与视图关联的选项卡控件的引用。

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>返回值

对与视图关联的选项卡控件的引用。

## <a name="ctabviewisscrollbar"></a><a name="isscrollbar"></a>CTabView：：IsScrollBar

创建选项卡视图时由框架调用，以确定选项卡视图是否具有共享的水平滚动条。

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>返回值

如果选项卡视图应与共享滚动条一起创建，则为 TRUE。 否则为 FALSE。

### <a name="remarks"></a>备注

创建*CTabView*对象时，框架调用此方法。

覆盖*CTabView*派生类中的*IsScrollBar*方法，如果要创建具有共享水平滚动条的视图，则返回 TRUE。

## <a name="ctabviewonactivateview"></a><a name="onactivateview"></a>CTabView：打开激活视图

当选项卡视图变为活动或非活动时，由框架调用。

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>参数

*视图*<br/>
[在]指向视图的指针。

### <a name="remarks"></a>备注

默认实现不执行任何操作。 重写`CTabView`派生类中的此方法以处理此通知。

## <a name="ctabviewremoveview"></a><a name="removeview"></a>CTabView：删除查看

从选项卡控件中删除视图。

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>参数

*伊塔布纳姆*<br/>
[在]要删除的视图的索引。

### <a name="return-value"></a>返回值

如果此方法成功，则删除视图的索引。 否则 -1。

### <a name="remarks"></a>备注

## <a name="ctabviewsetactiveview"></a><a name="setactiveview"></a>CTabView：设置活动视图

使视图处于活动状态。

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>参数

*伊塔布纳姆*<br/>
[在]选项卡视图的零基索引。

### <a name="return-value"></a>返回值

如果指定的视图处于活动状态，则为 TRUE;如果视图的索引无效，则 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[CMFCTabCtrl：：设置活动选项卡](../../mfc/reference/cmfctabctrl-class.md#setactivetab)。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTabCtrl](../../mfc/reference/ctabview-class.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)
