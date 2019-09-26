---
title: CMFCPropertySheet 类
ms.date: 11/19/2018
f1_keywords:
- CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPage
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPageToTree
- AFXPROPERTYSHEET/CMFCPropertySheet::AddTreeCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::EnablePageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::GetHeaderHeight
- AFXPROPERTYSHEET/CMFCPropertySheet::GetLook
- AFXPROPERTYSHEET/CMFCPropertySheet::GetNavBarWidth
- AFXPROPERTYSHEET/CMFCPropertySheet::GetTab
- AFXPROPERTYSHEET/CMFCPropertySheet::InitNavigationControl
- AFXPROPERTYSHEET/CMFCPropertySheet::OnActivatePage
- AFXPROPERTYSHEET/CMFCPropertySheet::OnDrawPageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::OnRemoveTreePage
- AFXPROPERTYSHEET/CMFCPropertySheet::RemoveCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::RemovePage
- AFXPROPERTYSHEET/CMFCPropertySheet::SetIconsList
- AFXPROPERTYSHEET/CMFCPropertySheet::SetLook
helpviewer_keywords:
- CMFCPropertySheet [MFC], CMFCPropertySheet
- CMFCPropertySheet [MFC], AddPage
- CMFCPropertySheet [MFC], AddPageToTree
- CMFCPropertySheet [MFC], AddTreeCategory
- CMFCPropertySheet [MFC], EnablePageHeader
- CMFCPropertySheet [MFC], GetHeaderHeight
- CMFCPropertySheet [MFC], GetLook
- CMFCPropertySheet [MFC], GetNavBarWidth
- CMFCPropertySheet [MFC], GetTab
- CMFCPropertySheet [MFC], InitNavigationControl
- CMFCPropertySheet [MFC], OnActivatePage
- CMFCPropertySheet [MFC], OnDrawPageHeader
- CMFCPropertySheet [MFC], OnRemoveTreePage
- CMFCPropertySheet [MFC], RemoveCategory
- CMFCPropertySheet [MFC], RemovePage
- CMFCPropertySheet [MFC], SetIconsList
- CMFCPropertySheet [MFC], SetLook
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
ms.openlocfilehash: f7c9d2b472a443d8bf556d0b12dfe202ea8607a1
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2019
ms.locfileid: "69505061"
---
# <a name="cmfcpropertysheet-class"></a>CMFCPropertySheet 类

`CMFCPropertySheet` 类支持每个属性页由页选项卡、工具栏按钮、树控件节点或列表项表示的属性表。

## <a name="syntax"></a>语法

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|构造 `CMFCPropertySheet` 对象。|
|`CMFCPropertySheet::~CMFCPropertySheet`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCPropertySheet::AddPage](#addpage)|向属性表添加页面。|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|向树控件添加新的属性页。|
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|向树控件添加新节点。|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|在每个页面顶部保留一定空间，用于绘制自定义页眉。|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|检索当前页眉的高度。|
|[CMFCPropertySheet::GetLook](#getlook)|检索一个枚举值，该值指定当前属性表的外观。|
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|检索导航栏的宽度（以像素为单位）。|
|[CMFCPropertySheet::GetTab](#gettab)|检索支持当前属性表控件的内部选项卡控件对象。|
|`CMFCPropertySheet::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|初始化当前属性表控件的外观。|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|当属性页处于启用状态时由框架调用。|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|由框架调用，用于绘制自定义属性页页眉。|
|`CMFCPropertySheet::OnInitDialog`|处理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)消息。 （重写[CPropertySheet：： OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。）|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|由框架调用，用于从树控件中删除属性页。|
|`CMFCPropertySheet::PreTranslateMessage`|转换窗口消息，然后将其调度到[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函数。 （重写 `CPropertySheet::PreTranslateMessage`。）|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|从树控件中删除节点。|
|[CMFCPropertySheet::RemovePage](#removepage)|从属性表中删除属性页。|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|指定用于 Outlook 窗格的导航控件的图像列表。|
|[CMFCPropertySheet::SetLook](#setlook)|指定属性表的外观。|

## <a name="remarks"></a>备注

`CMFCPropertySheet` 类表示属性表，也称为选项卡对话框。 `CMFCPropertySheet` 类可以用多种方式显示属性页。

执行以下步骤，以便在应用程序中使用 `CMFCPropertySheet` 类：

1. 从 `CMFCPropertySheet` 类派生一个类，并对其命名，例如，CMyPropertySheet。

1. 为每个属性页构造一个[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)对象。

1. 调用 CMyPropertySheet 构造函数中的[CMFCPropertySheet：： SetLook](#setlook)方法。 该方法的参数指定属性页的显示方式：属性表顶部或左侧的选项卡；Microsoft OneNote 属性表样式的选项卡；Microsoft Outlook 工具栏控件上的按钮；树控件上的节点；或属性表左侧的项列表。

1. 如果以 Microsoft Outlook 工具栏的样式创建属性表，请调用[CMFCPropertySheet：： SetIconsList](#seticonslist)方法将图像列表与属性页关联起来。

1. 为每个属性页调用[CMFCPropertySheet：： AddPage](#addpage)方法。

1. 创建 `CMFCPropertySheet` 控件并调用其 `DoModal` 方法。

## <a name="illustrations"></a>图示

下图描绘了一个采用嵌入式 Microsoft Outlook 工具栏样式的属性表。 该 Outlook 工具栏显示在属性表左侧。

![CMFCPropertySheet 颜色控件](../../mfc/reference/media/cmfcpropertysheet_color.png "CMFCPropertySheet 颜色控件")

下图描绘了包含[CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)对象的属性表。 该对象是一个采用标准常用控件属性表样式的属性表。

![CMFCPropertySheet 列表和属性控件](../../mfc/reference/media/cmfcpropertysheet_list.png "CMFCPropertySheet 列表和属性控件")

下图描绘了一个采用树控件样式的属性表。

![属性树](../../mfc/reference/media/proptree.png "属性树")

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>要求

**标头：** afxpropertysheet

##  <a name="addpage"></a>CMFCPropertySheet：： AddPage

向属性表添加页面。

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>参数

*pPage*<br/>
中指向页面对象的指针。 此参数不能为 NULL。

### <a name="remarks"></a>备注

此方法添加指定的属性页作为属性表中最右边的选项卡。 因此，请使用此方法以从左到右的顺序添加页。

如果属性表的样式为 Microsoft Outlook，则该框架将在属性表的左侧显示导航按钮列表。 此方法在添加属性页后，将相应的按钮添加到该列表中。 若要显示属性页，请单击其对应的按钮。 有关属性表样式的详细信息，请参阅[CMFCPropertySheet：： SetLook](#setlook)。

##  <a name="addpagetotree"></a>CMFCPropertySheet：： AddPageToTree

向树控件添加新的属性页。

```
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>参数

*pCategory*<br/>
中指向父树节点的指针; 如果为 NULL，则将指定的页与顶级节点关联。 调用[CMFCPropertySheet：： AddTreeCategory](#addtreecategory)方法获取此指针。

*pPage*<br/>
中指向属性页对象的指针。

*nIconNum*<br/>
中图标的从零开始的索引; 如果未使用图标，则为-1。 如果未选择该页面，则图标将显示在树控件属性页旁。 默认值为 -1。

*nSelIconNum*<br/>
中图标的从零开始的索引; 如果未使用图标，则为-1。 选择该页面时，该图标将显示在树控件属性页旁。 默认值为 -1。

### <a name="remarks"></a>备注

此方法将属性页添加为树控件的叶。 若要添加属性页，请创建`CMFCPropertySheet`一个对象，调用[CMFCPropertySheet：： SetLook](#setlook)方法，并将*look*参数设置`CMFCPropertySheet::PropSheetLook_Tree`为，然后使用此方法添加属性页。

##  <a name="addtreecategory"></a>CMFCPropertySheet：： AddTreeCategory

向树控件添加新节点。

```
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,
    int nIconNum=-1,
    int nSelectedIconNum=-1,
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
中节点的名称。

*nIconNum*<br/>
中图标的从零开始的索引; 如果未使用图标，则为-1。 如果未选择该页面，则图标将显示在树控件属性页旁。 默认值为 -1。

*nSelectedIconNum*<br/>
中图标的从零开始的索引; 如果未使用图标，则为-1。 选择该页面时，该图标将显示在树控件属性页旁。 默认值为 -1。

*pParentCategory*<br/>
中指向父树节点的指针; 如果为 NULL，则将指定的页与顶级节点关联。 请将此参数设置为[CMFCPropertySheet：： AddTreeCategory](#addtreecategory)方法。

### <a name="return-value"></a>返回值

指向树控件中的新节点的指针。

### <a name="remarks"></a>备注

使用此方法可将新节点（也称为类别）添加到树控件。 若要添加一个节点，请`CMFCPropertySheet`创建一个对象，调用[CMFCPropertySheet：： SetLook](#setlook)方法，并将*look*参数`CMFCPropertySheet::PropSheetLook_Tree`设置为，然后使用此方法添加节点。

在对[CMFCPropertySheet：： AddPageToTree](#addpagetotree)和[CMFCPropertySheet：： AddTreeCategory](#addtreecategory)的后续调用中使用此方法的返回值。

##  <a name="cmfcpropertysheet"></a>CMFCPropertySheet：： CMFCPropertySheet

构造 `CMFCPropertySheet` 对象。

```
CMFCPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);

CMFCPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);
```

### <a name="parameters"></a>参数

*pszCaption*<br/>
中一个包含属性表标题的字符串。 不能为 NULL。

*nIDCaption*<br/>
中包含属性表标题的资源 ID。

*pParentWnd*<br/>
中指向属性表的父窗口的指针; 如果父窗口是应用程序的主窗口，则为 NULL。 默认值为 NULL。

*iSelectPage*<br/>
中顶部属性页的从零开始的索引。 默认值为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅[CPropertySheet：： CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)构造函数的参数。

##  <a name="enablepageheader"></a>CMFCPropertySheet：： EnablePageHeader

在每个页面顶部保留一定空间，用于绘制自定义页眉。

```
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>参数

*nHeaderHeight*<br/>
中标头的高度（以像素为单位）。

### <a name="remarks"></a>备注

若要使用*nHeaderHeight*参数的值绘制自定义标头，请重写[CMFCPropertySheet：： OnDrawPageHeader](#ondrawpageheader)方法。

##  <a name="getheaderheight"></a>CMFCPropertySheet：： GetHeaderHeight

检索当前页眉的高度。

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>返回值

标头的高度（以像素为单位）。

### <a name="remarks"></a>备注

调用此方法之前调用[CMFCPropertySheet：： EnablePageHeader](#enablepageheader)方法。

##  <a name="getlook"></a>CMFCPropertySheet：： GetLook

检索一个枚举值，该值指定当前属性表的外观。

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>返回值

枚举值之一，指定属性表的外观。 有关可能值的列表，请参见[CMFCPropertySheet：： SetLook](#setlook)的 "备注" 部分中的枚举表。

##  <a name="getnavbarwidth"></a>CMFCPropertySheet：： GetNavBarWidth

获取导航栏的宽度。

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>返回值

导航栏的宽度（以像素为单位）。

##  <a name="gettab"></a>CMFCPropertySheet：： GetTab

检索支持当前属性表控件的内部选项卡控件对象。

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>返回值

内部选项卡控件对象。

### <a name="remarks"></a>备注

可以设置属性表，使其显示在不同的样式中，如树控件、导航按钮列表或一组选项卡式页面。

在调用此方法之前，请调用[CMFCPropertySheet：： SetLook](#setlook)方法来设置属性表控件的外观。 然后调用[CMFCPropertySheet：： InitNavigationControl](#initnavigationcontrol)方法来初始化内部选项卡控件对象。 使用此方法可检索选项卡控件对象，然后使用该对象处理属性表中的选项卡。

如果属性表控件未设置为以 Microsoft OneNote 样式显示，则此方法将断言处于调试模式。

##  <a name="initnavigationcontrol"></a>CMFCPropertySheet：： InitNavigationControl

初始化当前属性表控件的外观。

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>返回值

指向属性表控件的窗口的指针。

### <a name="remarks"></a>备注

属性表控件可以出现在多个不同的窗体中，例如一组选项卡式页、一个树控件或一个导航按钮列表。 使用[CMFCPropertySheet：： SetLook](#setlook)方法指定属性表控件的外观。

##  <a name="onactivatepage"></a>CMFCPropertySheet：： OnActivatePage

当属性页处于启用状态时由框架调用。

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>参数

*pPage*<br/>
中一个指针，指向表示 "已启用" 属性页的属性页对象。

### <a name="remarks"></a>备注

默认情况下，此方法可确保 "已启用" 属性页滚动到视图中。 如果当前属性表的样式包含 Microsoft Outlook 窗格，则此方法会将相应的 Outlook 按钮设置为选中状态。

##  <a name="ondrawpageheader"></a>CMFCPropertySheet：： OnDrawPageHeader

由框架调用，用于绘制自定义属性页的标头。

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向设备上下文的指针。

*nPage*<br/>
中从零开始的属性页码。

*rectHeader*<br/>
中指定页眉绘制位置的边框。

### <a name="remarks"></a>备注

默认情况下，此方法不执行任何操作。 如果重写此方法，则在框架调用此方法之前调用[CMFCPropertySheet：： EnablePageHeader](#enablepageheader)方法。

##  <a name="onremovetreepage"></a>CMFCPropertySheet：： OnRemoveTreePage

由框架调用，用于从树控件中删除属性页。

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>参数

*pPage*<br/>
中指向属性页对象的指针，该对象表示要移除的属性页。

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

##  <a name="removecategory"></a>CMFCPropertySheet：： RemoveCategory

从树控件中删除节点。

```
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>参数

*pCategory*<br/>
中指向要删除的类别（节点）的指针。

### <a name="remarks"></a>备注

使用此方法可从树控件中删除节点，该节点也称为类别。 使用[CMFCPropertySheet：： AddTreeCategory](#addtreecategory)方法将节点添加到树控件。

##  <a name="removepage"></a>CMFCPropertySheet：： RemovePage

从属性表中删除属性页。

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>参数

*pPage*<br/>
中指向属性页对象的指针，该对象表示要移除的属性页。 不能为 NULL。

*nPage*<br/>
中要移除的页的从零开始的索引。

### <a name="remarks"></a>备注

此方法删除指定的属性页并销毁其关联的窗口。 在关闭[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)窗口之前， *pPage*参数指定的属性页对象不会被销毁。

##  <a name="seticonslist"></a>CMFCPropertySheet：： SetIconsList

指定用于 Outlook 窗格的导航控件的图像列表。

```
BOOL SetIconsList(
    UINT uiImageListResID,
    int cx,
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```

### <a name="parameters"></a>参数

*uiImageListResID*<br/>
中图像列表的资源 ID。

*cx*<br/>
中图像列表中图标的宽度（以像素为单位）。

*clrTransparent*<br/>
中透明图像颜色。 此颜色的图像部分将是透明的。 默认值为洋红色、RGB （255、0255）。

*hIcons*<br/>
中现有图像列表的句柄。

### <a name="return-value"></a>返回值

在第一个方法重载语法中，如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果属性表的样式为 Microsoft Outlook，则该框架将在属性表的左侧显示导航按钮列表（称为 Outlook 窗格控件）。 使用此方法可设置 Outlook 窗格控件要使用的图像列表。

有关支持此方法的方法的详细信息，请参阅[CImageList：： Create](../../mfc/reference/cimagelist-class.md#create)和[CImageList：： Add](../../mfc/reference/cimagelist-class.md#add)。 有关如何设置属性表样式的详细信息，请参阅[CMFCPropertySheet：： SetLook](#setlook)。

##  <a name="setlook"></a>CMFCPropertySheet：： SetLook

指定属性表的外观。

```
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>参数

*look*<br/>
中枚举值之一，指定属性表的外观。 属性表的默认样式是`CMFCPropertySheet::PropSheetLook_Tabs`。 有关详细信息，请参阅本主题的 "备注" 部分中的表。

*nNavControlWidth*<br/>
中导航控件的宽度（以像素为单位）。 默认值为 100。

### <a name="remarks"></a>备注

若要以默认样式以外的样式显示属性表，请在创建属性表窗口之前调用此方法。

下表列出了可在 "*查找*" 参数中指定的枚举值。

|值|描述|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|缺省值显示每个属性页的选项卡。 选项卡显示在属性表的顶部，如果有更多的选项卡可容纳在单个行中，则该选项卡将堆积。|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|在属性表的左侧显示导航按钮列表，其样式为 Microsoft Outlook bar。 列表中的每个按钮都对应一个属性页。 如果列表的可见区域中的按钮数超出了可容纳的数目，框架将显示滚动箭头。|
|`CMFCPropertySheet::PropSheetLook_Tree`|显示属性表左侧的树控件。 树控件的每个父节点或子节点都对应一个属性页。 如果树控件的可视区域中的节点数超出了所能容纳的数目，框架将显示滚动箭头。|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|为每个属性页显示一个选项卡，样式为 Microsoft OneNote。 框架将在属性表顶部显示选项卡，并在多个选项卡超过单个行时滚动箭头。|
|`CMFCPropertySheet::PropSheetLook_List`|显示属性表左侧的列表。 每个列表项对应于一个属性页。 如果列表中的列表项超出了列表的可见区域，框架将显示滚动箭头。|

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyPage 类](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)
