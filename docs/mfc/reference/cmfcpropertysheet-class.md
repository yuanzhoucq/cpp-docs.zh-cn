---
title: CMFC属性表类
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
ms.openlocfilehash: 9b1bb2ce9a957b9cd9f7add983b4da7a228d7a1d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750060"
---
# <a name="cmfcpropertysheet-class"></a>CMFC属性表类

`CMFCPropertySheet` 类支持每个属性页由页选项卡、工具栏按钮、树控件节点或列表项表示的属性表。

## <a name="syntax"></a>语法

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|构造 `CMFCPropertySheet` 对象。|
|`CMFCPropertySheet::~CMFCPropertySheet`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCPropertySheet::AddPage](#addpage)|向属性表添加页面。|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|向树控件添加新的属性页。|
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|向树控件添加新节点。|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|在每个页面顶部保留一定空间，用于绘制自定义页眉。|
|[CMFC 属性表：获取标题高度](#getheaderheight)|检索当前页眉的高度。|
|[CMFC属性表：获取查看](#getlook)|检索一个枚举值，该值指定当前属性表的外观。|
|[CMFC属性表：获取导航栏宽度](#getnavbarwidth)|检索导航栏的宽度（以像素为单位）。|
|[CMFC财产表：GetTab](#gettab)|检索支持当前属性表控件的内部选项卡控件对象。|
|`CMFCPropertySheet::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|初始化当前属性表控件的外观。|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|当属性页处于启用状态时由框架调用。|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|由框架调用，用于绘制自定义属性页页眉。|
|`CMFCPropertySheet::OnInitDialog`|处理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)消息。 （覆盖[C 属性表：oninitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).）|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|由框架调用，用于从树控件中删除属性页。|
|`CMFCPropertySheet::PreTranslateMessage`|在窗口消息发送到[翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)窗口功能之前进行翻译。 （重写 `CPropertySheet::PreTranslateMessage`。）|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|从树控件中删除节点。|
|[CMFCPropertySheet::RemovePage](#removepage)|从属性表中删除属性页。|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|指定用于 Outlook 窗格的导航控件的图像列表。|
|[CMFCPropertySheet::SetLook](#setlook)|指定属性表的外观。|

## <a name="remarks"></a>备注

`CMFCPropertySheet` 类表示属性表，也称为选项卡对话框。 `CMFCPropertySheet` 类可以用多种方式显示属性页。

执行以下步骤，以便在应用程序中使用 `CMFCPropertySheet` 类：

1. 从 `CMFCPropertySheet` 类派生一个类，并对其命名，例如，CMyPropertySheet。

1. 为每个属性页构造一个[CMFC 属性页](../../mfc/reference/cmfcpropertypage-class.md)对象。

1. 调用[CMFC 属性表：：](#setlook)在 CMyPropertySheet 构造函数中设置查找方法。 该方法的参数指定属性页的显示方式：属性表顶部或左侧的选项卡；Microsoft OneNote 属性表样式的选项卡；Microsoft Outlook 工具栏控件上的按钮；树控件上的节点；或属性表左侧的项列表。

1. 如果在 Microsoft Outlook 工具栏的样式中创建属性表，请调用[CMFC 属性表：setIconsList](#seticonslist)方法将图像列表与属性页相关联。

1. 调用[CMFC 属性表：：](#addpage)为每个属性页添加页方法。

1. 创建 `CMFCPropertySheet` 控件并调用其 `DoModal` 方法。

## <a name="illustrations"></a>图示

下图描绘了一个采用嵌入式 Microsoft Outlook 工具栏样式的属性表。 该 Outlook 工具栏显示在属性表左侧。

![CMFCPropertySheet 颜色控件](../../mfc/reference/media/cmfcpropertysheet_color.png "CMFCPropertySheet 颜色控件")

下图描述了包含[CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)对象的属性表。 该对象是一个采用标准常用控件属性表样式的属性表。

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

**标题：** afx属性表.h

## <a name="cmfcpropertysheetaddpage"></a><a name="addpage"></a>CMFC属性表：添加页

向属性表添加页面。

```cpp
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>参数

*pPage*<br/>
[在]指向页面对象的指针。 此参数不能为 NULL。

### <a name="remarks"></a>备注

此方法将指定的属性页添加为属性表中最右侧的选项卡。 因此，使用此方法按从左到右的顺序添加页面。

如果属性表以 Microsoft Outlook 样式显示，则框架将在属性表的左侧显示导航按钮的列表。 此方法添加属性页后，它将相应的按钮添加到列表中。 要显示属性页，请单击其相应的按钮。 有关属性表样式的详细信息，请参阅[CMFC 属性表：：：SetLook](#setlook)。

## <a name="cmfcpropertysheetaddpagetotree"></a><a name="addpagetotree"></a>CMFC属性表：：添加页面到树

向树控件添加新的属性页。

```cpp
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>参数

*p 类别*<br/>
[在]指向父树节点的指针，或 NULL 将指定的页面与顶级节点相关联。 调用[CMFC 属性表：addTree 类别](#addtreecategory)方法以获取此指针。

*pPage*<br/>
[在]指向属性页对象的指针。

*nIconNum*<br/>
[在]图标的零索引，如果未使用图标，则为 -1。 未选择该页时，该图标将显示在树控件属性页旁边。 默认值为 -1。

*恩塞尔克尼纳姆*<br/>
[在]图标的零索引，如果未使用图标，则为 -1。 选择页面时，该图标将显示在树控件属性页旁边。 默认值为 -1。

### <a name="remarks"></a>备注

此方法将属性页添加为树控件的叶。 要添加属性页，请创建一`CMFCPropertySheet`个对象，请调用[CMFC属性表：：SetLook](#setlook)方法，*外观参数设置为*`CMFCPropertySheet::PropSheetLook_Tree`，然后使用此方法添加属性页。

## <a name="cmfcpropertysheetaddtreecategory"></a><a name="addtreecategory"></a>CMFC 属性表：：添加树类别

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
[在]节点的名称。

*nIconNum*<br/>
[在]图标的零索引，如果未使用图标，则为 -1。 未选择该页时，该图标将显示在树控件属性页旁边。 默认值为 -1。

*n选择图标*<br/>
[在]图标的零索引，如果未使用图标，则为 -1。 选择页面时，该图标将显示在树控件属性页旁边。 默认值为 -1。

*p 父项*<br/>
[在]指向父树节点的指针，或 NULL 将指定的页面与顶级节点相关联。 使用[CMFC 属性表设置此参数：addTree 类别](#addtreecategory)方法。

### <a name="return-value"></a>返回值

指向树控件中的新节点的指针。

### <a name="remarks"></a>备注

使用此方法向树控件添加新节点（也称为类别）。 要添加节点，请创建一`CMFCPropertySheet`个对象，请调用[CMFC属性表：：SetLook](#setlook)方法，*外观参数设置为*`CMFCPropertySheet::PropSheetLook_Tree`，然后使用此方法添加节点。

在后续调用 CMFC 属性表时使用此方法的返回值[：：AddPageTotree](#addpagetotree)和[CMFC 属性表：：添加树类别](#addtreecategory)。

## <a name="cmfcpropertysheetcmfcpropertysheet"></a><a name="cmfcpropertysheet"></a>CMFC财产表：CMFC财产表

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
[在]包含属性工作表标题的字符串。 不能为 NULL。

*nIDCaption*<br/>
[在]包含属性表标题的资源 ID。

*pparentwnd*<br/>
[在]指针指向属性表的父窗口，如果父窗口是应用程序的主窗口，则指向 NULL。 默认值为 NULL。

*iSelectPage*<br/>
[在]顶部属性页的零基索引。 默认值为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅[CPropertySheet：cPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)构造函数的参数。

## <a name="cmfcpropertysheetenablepageheader"></a><a name="enablepageheader"></a>CMFC 属性表：启用页眉

在每个页面顶部保留一定空间，用于绘制自定义页眉。

```cpp
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>参数

*nHeaderHeight*<br/>
[在]标头的高度（以像素为单位）。

### <a name="remarks"></a>备注

要使用*nHeaderHeight*参数的值绘制自定义标头，要重写[CMFC 属性表：：OnDrawPageHeader](#ondrawpageheader)方法。

## <a name="cmfcpropertysheetgetheaderheight"></a><a name="getheaderheight"></a>CMFC 属性表：获取标题高度

检索当前页眉的高度。

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>返回值

标头的高度（以像素为单位）。

### <a name="remarks"></a>备注

调用[CMFC 属性表：启用PageHeader](#enablepageheader)方法，然后再调用此方法。

## <a name="cmfcpropertysheetgetlook"></a><a name="getlook"></a>CMFC属性表：获取查看

检索一个枚举值，该值指定当前属性表的外观。

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>返回值

指定属性表外观的枚举值之一。 有关可能值的列表，请参阅 CMFC属性表注释部分中的枚举表[：：SetLook](#setlook)。

## <a name="cmfcpropertysheetgetnavbarwidth"></a><a name="getnavbarwidth"></a>CMFC属性表：获取导航栏宽度

获取导航栏的宽度。

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>返回值

导航栏的宽度（以像素为单位）。

## <a name="cmfcpropertysheetgettab"></a><a name="gettab"></a>CMFC财产表：GetTab

检索支持当前属性表控件的内部选项卡控件对象。

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>返回值

内部选项卡控件对象。

### <a name="remarks"></a>备注

您可以设置属性表，使其以不同的样式显示，例如树控件、导航按钮列表或一组选项卡式页面。

在调用此方法之前，调用[CMFC 属性表：：SetLook](#setlook)方法来设置属性表控件的外观。 然后调用[CMFC 属性表：init导航控制](#initnavigationcontrol)方法以初始化内部选项卡控制对象。 使用此方法检索选项卡控件对象，然后使用该对象处理属性表上的选项卡。

如果属性表控件未设置为以 Microsoft OneNote 的样式显示，则此方法在调试模式下断言。

## <a name="cmfcpropertysheetinitnavigationcontrol"></a><a name="initnavigationcontrol"></a>CMFC 属性表：init 导航控制

初始化当前属性表控件的外观。

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>返回值

指向属性工作表控件窗口的指针。

### <a name="remarks"></a>备注

属性表控件可以以几种不同形式显示，例如一组选项卡式页面、树控件或导航按钮列表。 使用[CMFC 属性表：：SetLook](#setlook)方法指定属性表控件的外观。

## <a name="cmfcpropertysheetonactivatepage"></a><a name="onactivatepage"></a>CMFC 属性表：打开 Activatepage

当属性页处于启用状态时由框架调用。

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>参数

*pPage*<br/>
[在]指向表示启用的属性页的属性页对象的指针。

### <a name="remarks"></a>备注

默认情况下，此方法可确保启用的属性页滚动到视图中。 如果当前属性表的样式包含 Microsoft Outlook 窗格，则此方法将相应的 Outlook 按钮设置为选中的状态。

## <a name="cmfcpropertysheetondrawpageheader"></a><a name="ondrawpageheader"></a>CMFC 属性表：在绘制页眉

由框架调用以绘制自定义属性页的标头。

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*nPage*<br/>
[在]零基属性页码。

*整流头*<br/>
[在]指定绘制标题的位置的边界矩形。

### <a name="remarks"></a>备注

默认情况下，此方法不执行任何操作。 如果重写此方法，请调用[CMFC 属性表：：启用PageHeader](#enablepageheader)方法，然后框架调用此方法。

## <a name="cmfcpropertysheetonremovetreepage"></a><a name="onremovetreepage"></a>CMFC属性表：：删除树页

由框架调用，用于从树控件中删除属性页。

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>参数

*pPage*<br/>
[在]指向表示要删除的属性页的属性页对象的指针。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

## <a name="cmfcpropertysheetremovecategory"></a><a name="removecategory"></a>CMFC 属性表：删除类别

从树控件中删除节点。

```cpp
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>参数

*p 类别*<br/>
[在]指向要删除的类别（节点）的指针。

### <a name="remarks"></a>备注

使用此方法从树控件中删除节点（也称为类别）。 使用[CMFC 属性表：addTreeCategory](#addtreecategory)方法将节点添加到树控件。

## <a name="cmfcpropertysheetremovepage"></a><a name="removepage"></a>CMFC 属性表：删除页

从属性表中删除属性页。

```cpp
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>参数

*pPage*<br/>
[在]指向表示要删除的属性页的属性页对象的指针。 不能为 NULL。

*nPage*<br/>
[在]要删除的页面的从零开始索引。

### <a name="remarks"></a>备注

此方法删除指定的属性页并销毁其关联的窗口。 在[关闭 CMFC属性表](../../mfc/reference/cmfcpropertysheet-class.md)窗口之前，pPage 参数指定的属性页对象不会销毁。 *pPage*

## <a name="cmfcpropertysheetseticonslist"></a><a name="seticonslist"></a>CMFC 属性表：设置图标列表

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
[在]映像列表的资源 ID。

*残雪*<br/>
[在]图像列表中图标的宽度（以像素为单位）。

*clr透明*<br/>
[在]透明图像颜色。 此颜色的图像部分将是透明的。 默认值是色品红色，RGB（255，0，255）。

*h图标*<br/>
[在]现有图像列表的句柄。

### <a name="return-value"></a>返回值

在第一个方法重载语法中，如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

如果属性表以 Microsoft Outlook 样式显示，则框架将在属性表的左侧显示导航按钮列表，称为 Outlook 窗格控件。 使用此方法可设置要由 Outlook 窗格控件使用的图像列表。

有关支持此方法的方法的详细信息，请参阅[CImageList：：创建](../../mfc/reference/cimagelist-class.md#create)和[CImageList：：添加](../../mfc/reference/cimagelist-class.md#add)。 有关如何设置属性表样式的详细信息，请参阅[CMFC属性表：：：SetLook](#setlook)。

## <a name="cmfcpropertysheetsetlook"></a><a name="setlook"></a>CMFC 属性表：设置查看

指定属性表的外观。

```cpp
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>参数

*看*<br/>
[在]指定属性表外观的枚举值之一。 属性表的默认样式为`CMFCPropertySheet::PropSheetLook_Tabs`。 有关详细信息，请参阅本主题的备注部分中的表。

*nNavControl 宽度*<br/>
[在]导航控件的宽度（以像素为单位）。 默认值为 100。

### <a name="remarks"></a>备注

要在默认值以外的样式中显示属性表，请先在创建属性工作表窗口之前调用此方法。

下表列出了可在*look*参数中指定的枚举值。

|“值”|说明|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|（默认）显示每个属性页的选项卡。 选项卡显示在属性表的顶部，如果选项卡数多于单个行中容纳的选项卡数，则选项卡将被堆叠。|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|在属性表的左侧显示 Microsoft Outlook 栏样式中的导航按钮列表。 列表中的每个按钮都对应于属性页。 如果按钮数超过列表的可见区域，则框架将显示滚动箭头。|
|`CMFCPropertySheet::PropSheetLook_Tree`|在属性手册的左侧显示树控件。 树控件的每个父节点或子节点对应于属性页。 如果节点数多于树控件的可见区域，则框架将显示滚动箭头。|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|为每个属性页显示一个选项卡，以 Microsoft OneNote 的样式显示。 如果选项卡数多于单行中容纳的选项卡数，则框架在属性表顶部显示选项卡，并滚动箭头。|
|`CMFCPropertySheet::PropSheetLook_List`|在属性表的左侧显示一个列表。 每个列表项对应于属性页。 如果列表项数多于列表的可见区域，则框架将显示滚动箭头。|

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyPage 类](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)
