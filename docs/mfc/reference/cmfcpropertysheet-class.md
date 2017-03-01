---
title: "CMFCPropertySheet 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertySheet
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertySheet::PreTranslateMessage method
- CMFCPropertySheet::OnInitDialog method
- CMFCPropertySheet class
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
caps.latest.revision: 35
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a157a0afa4542bc023ba4d7149e78a71bbd56e74
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[Cmfcpropertysheet:: Addpage](#addpage)|向属性表添加页面。|  
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|向树控件添加新的属性页。|  
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|向树控件添加新节点。|  
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|在每个页面顶部保留一定空间，用于绘制自定义页眉。|  
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|检索当前页眉的高度。|  
|[CMFCPropertySheet::GetLook](#getlook)|检索一个枚举值，该值指定当前属性表的外观。|  
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|检索导航栏的宽度（以像素为单位）。|  
|[CMFCPropertySheet::GetTab](#gettab)|检索支持当前属性表控件的内部选项卡控件对象。|  
|`CMFCPropertySheet::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|初始化当前属性表控件的外观。|  
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|当属性页处于启用状态时由框架调用。|  
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|由框架调用，用于绘制自定义属性页页眉。|  
|`CMFCPropertySheet::OnInitDialog`|处理[WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428)消息。 (重写[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。)|  
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|由框架调用，用于从树控件中删除属性页。|  
|`CMFCPropertySheet::PreTranslateMessage`|翻译窗口消息之前被发送到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 （重写 `CPropertySheet::PreTranslateMessage`。）|  
|[CMFCPropertySheet::RemoveCategory](#removecategory)|从树控件中删除节点。|  
|[CMFCPropertySheet::RemovePage](#removepage)|从属性表中删除属性页。|  
|[CMFCPropertySheet::SetIconsList](#seticonslist)|指定用于 Outlook 窗格的导航控件的图像列表。|  
|[Cmfcpropertysheet:: Setlook](#setlook)|指定属性表的外观。|  
  
## <a name="remarks"></a>备注  
 `CMFCPropertySheet` 类表示属性表，也称为选项卡对话框。 `CMFCPropertySheet` 类可以用多种方式显示属性页。  
  
 执行以下步骤，以便在应用程序中使用 `CMFCPropertySheet` 类：  
  
1.  从 `CMFCPropertySheet` 类派生一个类，并对其命名，例如，CMyPropertySheet。  
  
2.  构造[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)每个属性页面的对象。  
  
3.  调用[cmfcpropertysheet:: Setlook](#setlook) CMyPropertySheet 构造函数中的方法。 该方法的参数指定属性页的显示方式：属性表顶部或左侧的选项卡；Microsoft OneNote 属性表样式的选项卡；Microsoft Outlook 工具栏控件上的按钮；树控件上的节点；或属性表左侧的项列表。  
  
4.  如果在 Microsoft Outlook 工具栏样式的中创建属性表，则调用[CMFCPropertySheet::SetIconsList](#seticonslist)方法将一个图像列表与属性页关联起来。  
  
5.  调用[cmfcpropertysheet:: Addpage](#addpage)每个属性页面的方法。  
  
6.  创建 `CMFCPropertySheet` 控件并调用其 `DoModal` 方法。  
  
## <a name="illustrations"></a>图示  
 下图描绘了一个采用嵌入式 Microsoft Outlook 工具栏样式的属性表。 该 Outlook 工具栏显示在属性表左侧。  
  
 ![CMFCPropertySheet 颜色控件](../../mfc/reference/media/cmfcpropertysheet_color.png "cmfcpropertysheet_color")  
  
 下图描绘了一个包含的属性表[CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)对象。 该对象是一个采用标准常用控件属性表样式的属性表。  
  
 ![CMFCPropertySheet 列表和属性控件](../../mfc/reference/media/cmfcpropertysheet_list.png "cmfcpropertysheet_list")  
  
 下图描绘了一个采用树控件样式的属性表。  
  
 ![属性树](../../mfc/reference/media/proptree.png "proptree")  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxpropertysheet.h  
  
##  <a name="a-nameaddpagea--cmfcpropertysheetaddpage"></a><a name="addpage"></a>Cmfcpropertysheet:: Addpage  
 向属性表添加页面。  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 [in] `pPage`  
 Page 对象的指针。 此参数不能为`NULL`。  
  
### <a name="remarks"></a>备注  
 此方法将指定的属性页添加为属性表中最右侧的选项卡。 因此，使用此方法以从左到右的顺序添加页面。  
  
 如果属性表样式的 Microsoft Outlook，框架将显示属性表左侧的导航按钮的列表。 此方法将添加属性页后，它会将相应的按钮添加到列表中。 若要显示属性页上，单击其对应的按钮。 属性表样式的详细信息，请参阅[cmfcpropertysheet:: Setlook](#setlook)。  
  
##  <a name="a-nameaddpagetotreea--cmfcpropertysheetaddpagetotree"></a><a name="addpagetotree"></a>CMFCPropertySheet::AddPageToTree  
 向树控件添加新的属性页。  
  
```  
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,  
    CMFCPropertyPage* pPage,  
    int nIconNum=-1,  
    int nSelIconNum=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `pCategory`  
 指向父树节点或`NULL`将指定的页的顶级节点与相关联。 调用[CMFCPropertySheet::AddTreeCategory](#addtreecategory)方法来获取该指针。  
  
 [in] `pPage`  
 为属性页上对象的指针。  
  
 [in] `nIconNum`  
 一个图标，则为-1 如果使用无图标的从零开始索引。 如果未选择页上，树控件属性页旁边显示此图标。 默认值为 -1。  
  
 [in] `nSelIconNum`  
 一个图标，则为-1 如果使用无图标的从零开始索引。 在页处于选定状态时，树控件属性页旁边显示此图标。 默认值为 -1。  
  
### <a name="remarks"></a>备注  
 此方法为叶树控件中添加属性页。 若要添加的属性页，创建`CMFCPropertySheet`对象，请调用[cmfcpropertysheet:: Setlook](#setlook)方法`look`参数设置为`CMFCPropertySheet::PropSheetLook_Tree`，然后使用此方法中添加属性页。  
  
##  <a name="a-nameaddtreecategorya--cmfcpropertysheetaddtreecategory"></a><a name="addtreecategory"></a>CMFCPropertySheet::AddTreeCategory  
 向树控件添加新节点。  
  
```  
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,  
    int nIconNum=-1,  
    int nSelectedIconNum=-1,  
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 节点的名称。  
  
 [in] `nIconNum`  
 一个图标，则为-1 如果使用无图标的从零开始索引。 如果未选择页上，树控件属性页旁边显示此图标。 默认值为 -1。  
  
 [in] `nSelectedIconNum`  
 一个图标，则为-1 如果使用无图标的从零开始索引。 在页处于选定状态时，树控件属性页旁边显示此图标。 默认值为 -1。  
  
 [in] `pParentCategory`  
 指向父树节点或`NULL`将指定的页的顶级节点与相关联。 设置此参数与[CMFCPropertySheet::AddTreeCategory](#addtreecategory)方法。  
  
### <a name="return-value"></a>返回值  
 指向目录树控件中的新节点的指针。  
  
### <a name="remarks"></a>备注  
 使用此方法将也称为一个类别，一个新节点添加到树控件。 若要添加节点时，创建`CMFCPropertySheet`对象，请调用[cmfcpropertysheet:: Setlook](#setlook)方法`look`参数设置为`CMFCPropertySheet::PropSheetLook_Tree`，然后使用此方法将节点添加。  
  
 在后续调用中使用此方法的返回值[CMFCPropertySheet::AddPageToTree](#addpagetotree)和[CMFCPropertySheet::AddTreeCategory](#addtreecategory)。  
  
##  <a name="a-namecmfcpropertysheeta--cmfcpropertysheetcmfcpropertysheet"></a><a name="cmfcpropertysheet"></a>CMFCPropertySheet::CMFCPropertySheet  
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
 [in] `pszCaption`  
 一个包含属性表标题的字符串。 不能为`NULL`。  
  
 [in] `nIDCaption`  
 一个包含属性表标题的资源 ID。  
  
 [in] `pParentWnd`  
 向属性表中，其父窗口的指针或`NULL`如果父窗口是应用程序的主窗口。 默认值为 `NULL`。  
  
 [in] `iSelectPage`  
 Top 属性页的从零开始索引。 默认值为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅为参数[CPropertySheet::CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)构造函数。  
  
##  <a name="a-nameenablepageheadera--cmfcpropertysheetenablepageheader"></a><a name="enablepageheader"></a>CMFCPropertySheet::EnablePageHeader  
 在每个页面顶部保留一定空间，用于绘制自定义页眉。  
  
```  
void EnablePageHeader(int nHeaderHeight);
```  
  
### <a name="parameters"></a>参数  
 [in] `nHeaderHeight`  
 标头，以像素为单位的高度。  
  
### <a name="remarks"></a>备注  
 若要使用的值`nHeaderHeight`参数来绘制自定义标头，重写[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)方法。  
  
##  <a name="a-namegetheaderheighta--cmfcpropertysheetgetheaderheight"></a><a name="getheaderheight"></a>CMFCPropertySheet::GetHeaderHeight  
 检索当前页眉的高度。  
  
```  
int GetHeaderHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 标头，以像素为单位的高度。  
  
### <a name="remarks"></a>备注  
 调用[CMFCPropertySheet::EnablePageHeader](#enablepageheader)方法之前调用此方法。  
  
##  <a name="a-namegetlooka--cmfcpropertysheetgetlook"></a><a name="getlook"></a>CMFCPropertySheet::GetLook  
 检索一个枚举值，该值指定当前属性表的外观。  
  
```  
PropSheetLook GetLook() const;  
```  
  
### <a name="return-value"></a>返回值  
 指定的属性表的外观的枚举值之一。 有关可能的值的列表，请参阅中的备注部分的枚举表[cmfcpropertysheet:: Setlook](#setlook)。  
  
##  <a name="a-namegetnavbarwidtha--cmfcpropertysheetgetnavbarwidth"></a><a name="getnavbarwidth"></a>CMFCPropertySheet::GetNavBarWidth  
 获取导航栏的宽度。  
  
```  
int GetNavBarWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 导航栏的宽度（以像素为单位）。  
  
##  <a name="a-namegettaba--cmfcpropertysheetgettab"></a><a name="gettab"></a>CMFCPropertySheet::GetTab  
 检索支持当前属性表控件的内部选项卡控件对象。  
  
```  
CMFCTabCtrl& GetTab() const;  
```  
  
### <a name="return-value"></a>返回值  
 内部选项卡控件对象。  
  
### <a name="remarks"></a>备注  
 您可以设置属性表，以使其显示在不同的样式，例如树控件中，导航按钮或一组选项卡式页的列表。  
  
 在调用此方法之前，调用[cmfcpropertysheet:: Setlook](#setlook)方法设置的属性表控件的外观。 然后，调用[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)方法以初始化内部的选项卡控件对象。 使用此方法来检索选项卡控件对象，然后使用该对象为适用于选项卡上的属性表。  
  
 此方法断言在调试模式下，如果未设置属性表控件才会显示在 Microsoft OneNote 的样式。  
  
##  <a name="a-nameinitnavigationcontrola--cmfcpropertysheetinitnavigationcontrol"></a><a name="initnavigationcontrol"></a>CMFCPropertySheet::InitNavigationControl  
 初始化当前属性表控件的外观。  
  
```  
virtual CWnd* InitNavigationControl();
```  
  
### <a name="return-value"></a>返回值  
 指向窗口中的属性表控件的指针。  
  
### <a name="remarks"></a>备注  
 属性表控件可以出现在多个不同的形式，如一组选项卡式的页面、 树控件中或导航按钮的列表。 使用[cmfcpropertysheet:: Setlook](#setlook)方法，以指定的属性表控件的外观。  
  
##  <a name="a-nameonactivatepagea--cmfcpropertysheetonactivatepage"></a><a name="onactivatepage"></a>CMFCPropertySheet::OnActivatePage  
 当属性页处于启用状态时由框架调用。  
  
```  
virtual void OnActivatePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 [in] `pPage`  
 为属性页对象表示已启用的属性页的指针。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法可以确保 enabled 的属性页上，滚动到视图。 如果当前属性表样式包含 Microsoft Outlook 窗格中，此方法设置相应的 Outlook 按钮为选中状态。  
  
##  <a name="a-nameondrawpageheadera--cmfcpropertysheetondrawpageheader"></a><a name="ondrawpageheader"></a>CMFCPropertySheet::OnDrawPageHeader  
 由框架用于绘制自定义属性页的标头调用。  
  
```  
virtual void OnDrawPageHeader(
    CDC* pDC,  
    int nPage,  
    CRect rectHeader);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `nPage`  
 从零开始的属性页号。  
  
 [in] `rectHeader`  
 指定要绘制标题的边框。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法没有任何效果。 如果重写此方法，调用[CMFCPropertySheet::EnablePageHeader](#enablepageheader)方法之前框架将调用此方法。  
  
##  <a name="a-nameonremovetreepagea--cmfcpropertysheetonremovetreepage"></a><a name="onremovetreepage"></a>CMFCPropertySheet::OnRemoveTreePage  
 由框架调用，用于从树控件中删除属性页。  
  
```  
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 [in] `pPage`  
 表示属性页上，要删除的属性页上对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `TRUE`；否则为 `FALSE`。  
  
##  <a name="a-nameremovecategorya--cmfcpropertysheetremovecategory"></a><a name="removecategory"></a>CMFCPropertySheet::RemoveCategory  
 从树控件中删除节点。  
  
```  
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```  
  
### <a name="parameters"></a>参数  
 [in] `pCategory`  
 指针，指向要删除的类别 （节点）。  
  
### <a name="remarks"></a>备注  
 使用此方法中删除节点，这也称为为类别，从树控件。 使用[CMFCPropertySheet::AddTreeCategory](#addtreecategory)方法将节点添加到树控件。  
  
##  <a name="a-nameremovepagea--cmfcpropertysheetremovepage"></a><a name="removepage"></a>CMFCPropertySheet::RemovePage  
 从属性表中删除属性页。  
  
```  
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>参数  
 [in] `pPage`  
 为表示属性页上，要删除的属性页上对象的指针。 不能为`NULL`。  
  
 [in] `nPage`  
 要删除的页的从零开始索引。  
  
### <a name="remarks"></a>备注  
 此方法中删除指定的属性页和销毁其关联的窗口。 属性页上对象`pPage`参数指定不会被破坏之前[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)窗口处于关闭状态。  
  
##  <a name="a-nameseticonslista--cmfcpropertysheetseticonslist"></a><a name="seticonslist"></a>CMFCPropertySheet::SetIconsList  
 指定用于 Outlook 窗格的导航控件的图像列表。  
  
```  
BOOL SetIconsList(
    UINT uiImageListResID,  
    int cx,  
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiImageListResID`  
 图像列表资源 ID。  
  
 [in] `cx`  
 以像素为单位的图像列表中的图标的宽度。  
  
 [in] `clrTransparent`  
 透明图像颜色。 是这种颜色的图像的部分将是透明的。 默认值为颜色洋红 RGB(255,0,255)。  
  
 [in] `hIcons`  
 指向现有图像列表的句柄。  
  
### <a name="return-value"></a>返回值  
 第一种方法重载的语法中，`TRUE`如果此方法成功，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果属性表样式的 Microsoft Outlook，框架显示导航按钮，称为 Outlook 窗格控件中，属性表左侧的列表。 此方法用于设置要由 Outlook 窗格控件的图像列表。  
  
 有关支持此方法的方法的详细信息，请参阅[CImageList::Create](../../mfc/reference/cimagelist-class.md#create)和[CImageList::Add](../../mfc/reference/cimagelist-class.md#add)。 有关如何设置的属性表样式的详细信息，请参阅[cmfcpropertysheet:: Setlook](#setlook)。  
  
##  <a name="a-namesetlooka--cmfcpropertysheetsetlook"></a><a name="setlook"></a>Cmfcpropertysheet:: Setlook  
 指定属性表的外观。  
  
```  
void SetLook(
    PropSheetLook look,  
    int nNavControlWidth=100);
```  
  
### <a name="parameters"></a>参数  
 [in] `look`  
 指定的属性表的外观的枚举值之一。 属性表的默认样式为`CMFCPropertySheet::PropSheetLook_Tabs`。 有关详细信息，请参阅本主题的备注部分中的表。  
  
 [in] `nNavControlWidth`  
 导航控件，以像素为单位的宽度。 默认值为 100。  
  
### <a name="remarks"></a>备注  
 若要显示属性表中而不是默认样式，请在创建属性表窗口之前调用此方法。  
  
 下表列出了可以在中指定的枚举值`look`参数。  
  
|值|说明|  
|-----------|-----------------|  
|`CMFCPropertySheet::PropSheetLook_Tabs`|（默认值）显示每个属性页面选项卡。 选项卡显示在属性表的顶部，并具有堆积，如果有多个选项卡的单个行中放不下。|  
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|显示样式的 Microsoft Outlook 栏中，属性表左侧的导航按钮的列表。 在列表中的每个按钮对应于属性页。 如果有更多按钮在列表的可见区域中放不下，框架将显示滚动箭头。|  
|`CMFCPropertySheet::PropSheetLook_Tree`|属性表的左侧显示一个树控件。 树控件的每个父或子节点对应的属性页。 如果有多个节点的树控件的可视区域中放不下，框架将显示滚动箭头。|  
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|显示一个选项卡，在 Microsoft onenote 样式中每个属性页。 框架在属性表的顶部显示选项卡并滚动箭头比更多选项卡是否适合单个行中。|  
|`CMFCPropertySheet::PropSheetLook_List`|显示属性表左侧的列表。 每个列表项对应于属性页。 如果有多个列表项列表的可见区域中放不下，框架将显示滚动箭头。|  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyPage 类](../../mfc/reference/cmfcpropertypage-class.md)   
 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)

