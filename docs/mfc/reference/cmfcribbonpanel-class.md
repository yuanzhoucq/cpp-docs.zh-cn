---
title: "CMFCRibbonPanel 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonPanel
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonPanel class
ms.assetid: 51d70749-1140-4386-b103-f14082049ba6
caps.latest.revision: 34
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
ms.openlocfilehash: 1f833e1fa59f733734da321718d5db73377fa4bd
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonpanel-class"></a>CMFCRibbonPanel 类
实现包含一组功能区元素的面板。 在绘制面板时，系统将根据面板的大小显示尽可能多的元素。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonPanel : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonPanel::CMFCRibbonPanel](#cmfcribbonpanel)|构造并初始化一个 `CMFCRibbonPanel` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonPanel::Add](#add)|向面板中添加功能区元素。|  
|[CMFCRibbonPanel::AddSeparator](#addseparator)|向功能区面板添加分隔符。|  
|[CMFCRibbonPanel::AddToolBar](#addtoolbar)|将工具栏添加到功能区面板。|  
|[CMFCRibbonPanel::FindByData](#findbydata)||  
|[CMFCRibbonPanel::FindByID](#findbyid)|返回由指定的命令 ID 来标识元素。|  
|[CMFCRibbonPanel::GetCaptionHeight](#getcaptionheight)||  
|[CMFCRibbonPanel::GetCount](#getcount)|在功能区面板中返回元素的数。|  
|[CMFCRibbonPanel::GetData](#getdata)|返回与面板相关联的用户定义数据。|  
|[CMFCRibbonPanel::GetDefaultButton](#getdefaultbutton)||  
|[CMFCRibbonPanel::GetDroppedDown](#getdroppeddown)||  
|[CMFCRibbonPanel::GetElement](#getelement)|返回位于指定索引处的功能区元素。|  
|[CMFCRibbonPanel::GetElements](#getelements)|检索包含在功能区面板中的所有元素。|  
|[CMFCRibbonPanel::GetElementsByID](#getelementsbyid)||  
|[CMFCRibbonPanel::GetFocused](#getfocused)|返回焦点元素。|  
|[CMFCRibbonPanel::GetGalleryRect](#getgalleryrect)|返回库元素的绑定矩形。|  
|[CMFCRibbonPanel::GetHighlighted](#gethighlighted)||  
|[CMFCRibbonPanel::GetIndex](#getindex)||  
|[CMFCRibbonPanel::GetItemIDsList](#getitemidslist)||  
|[CMFCRibbonPanel::GetName](#getname)||  
|[CMFCRibbonPanel::GetParentButton](#getparentbutton)||  
|[CMFCRibbonPanel::GetParentCategory](#getparentcategory)|返回功能区面板的父类别。|  
|[CMFCRibbonPanel::GetParentMenuBar](#getparentmenubar)||  
|[CMFCRibbonPanel::GetPreferedMenuLocation](#getpreferedmenulocation)||  
|[CMFCRibbonPanel::GetPressed](#getpressed)||  
|[CMFCRibbonPanel::GetRect](#getrect)||  
|[CMFCRibbonPanel::GetVisibleElements](#getvisibleelements)|获取可见元素的数组。|  
|[CMFCRibbonPanel::HasElement](#haselement)||  
|[CMFCRibbonPanel::HitTest](#hittest)||  
|[CMFCRibbonPanel::HitTestEx](#hittestex)||  
|[CMFCRibbonPanel::Insert](#insert)|给定位置处插入的功能区元素。|  
|[CMFCRibbonPanel::InsertSeparator](#insertseparator)|在指定的位置插入分隔符。|  
|[CMFCRibbonPanel::IsCenterColumnVert](#iscentercolumnvert)|指定是否所有面板元素应该都居中 （对齐） 设为垂直列。|  
|[CMFCRibbonPanel::IsCollapsed](#iscollapsed)||  
|[CMFCRibbonPanel::IsHighlighted](#ishighlighted)||  
|[CMFCRibbonPanel::IsJustifyColumns](#isjustifycolumns)|指定面板的所有列是否都具有相同的宽度。|  
|[CMFCRibbonPanel::IsMainPanel](#ismainpanel)||  
|[CMFCRibbonPanel::IsMenuMode](#ismenumode)||  
|[CMFCRibbonPanel::MakeGalleryItemVisible](#makegalleryitemvisible)|执行滚动操作使得库以使指定的功能区元素可见。|  
|[CMFCRibbonPanel::OnKey](#onkey)||  
|[CMFCRibbonPanel::RecalcWidths](#recalcwidths)||  
|[CMFCRibbonPanel::Remove](#remove)|删除并根据需要删除位于指定索引处的元素。|  
|[CMFCRibbonPanel::RemoveAll](#removeall)|从功能区面板中移除所有元素。|  
|[CMFCRibbonPanel::Replace](#replace)|将一个元素替换与另一个基于其各自的索引值。|  
|[CMFCRibbonPanel::ReplaceByID](#replacebyid)|一个元素替换为另一个基于指定的命令 id。|  
|[CMFCRibbonPanel::SetCenterColumnVert](#setcentercolumnvert)|要按列设为垂直对齐的元素的面板进行排序。|  
|[CMFCRibbonPanel::SetData](#setdata)|将用户定义数据，功能区面板。|  
|[CMFCRibbonPanel::SetElementMenu](#setelementmenu)|将具有给定的命令 ID 的元素的弹出菜单|  
|[CMFCRibbonPanel::SetElementRTC](#setelementrtc)|将添加到功能区面板提供运行时类信息由指定的功能区元素。|  
|[CMFCRibbonPanel::SetElementRTCByID](#setelementrtcbyid)|将添加到功能区面板提供运行时类信息由指定的功能区元素。|  
|[CMFCRibbonPanel::SetFocused](#setfocused)|将焦点移到指定的功能区元素。|  
|[CMFCRibbonPanel::SetJustifyColumns](#setjustifycolumns)|启用或禁用列对齐方式。|  
|[CMFCRibbonPanel::SetKeys](#setkeys)|设置显示功能区面板的键盘快捷键。|  
|[CMFCRibbonPanel::ShowPopup](#showpopup)||  
  
## <a name="remarks"></a>备注  
 功能区面板是相关的任务在功能区类别内创建的逻辑分组。 当功能区更改容量时，面板布局会自动调整以显示尽可能多的元素。  
  
 你可以获取功能区面板，其中包含通过调用在功能区类别[CMFCRibbonCategory::GetPanel](../../mfc/reference/cmfcribboncategory-class.md#getpanel)方法。  
  
## <a name="example"></a>示例  
 下面的示例演示如何配置`CMFCRibbonPanel`使用中的各种方法的对象`CMFCRibbonPanel`类。 该示例演示如何设置键盘快捷方式，用于显示功能区面板、 垂直对齐面板中的元素，按列，以及启用列对齐方式。 此代码段属于[MS Office 2007 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&10;](../../mfc/reference/codesnippet/cpp/cmfcribbonpanel-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxRibbonPanel.h  
  
##  <a name="a-nameadda--cmfcribbonpaneladd"></a><a name="add"></a>CMFCRibbonPanel::Add  
 将指定的功能区元素追加到包含功能区面板在功能区元素的数组。  
  
```  
virtual void Add(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pElem`  
 指向功能区元素的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddseparatora--cmfcribbonpaneladdseparator"></a><a name="addseparator"></a>CMFCRibbonPanel::AddSeparator  
 向功能区面板添加分隔符。  
  
```  
virtual void AddSeparator();
```  
  
### <a name="remarks"></a>备注  
 调用此方法来将分隔条添加到功能区面板。 分隔符将被添加到前面的调用已添加的功能区元素旁边[CMFCRibbonPanel::Add](#add)。 若要指定的位置插入一个分隔符，调用[CMFCRibbonPanel::InsertSeparator](#insertseparator)。  
  
##  <a name="a-nameaddtoolbara--cmfcribbonpaneladdtoolbar"></a><a name="addtoolbar"></a>CMFCRibbonPanel::AddToolBar  
 将工具栏添加到功能区面板。  
  
```  
CMFCRibbonButtonsGroup* AddToolBar(
UINT uiToolbarResID,  
UINT uiColdResID = 0,  
UINT uiHotResID = 0,  
UINT uiDisabledResID = 0);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiToolbarResID`  
 指定要添加工具栏上的资源 ID。  
  
 [in] `uiColdResID`  
 指定工具栏的冷图像的资源 ID。  
  
 [in] `uiHotResID`  
 指定工具栏的热图像的资源 ID。  
  
 [in] `uiDisabledResID`  
 指定已禁用的工具栏图像的资源 ID。  
  
### <a name="return-value"></a>返回值  
 调用此方法以将工具栏添加到功能区面板。 工具栏将添加到以前的调用添加的功能区元素旁边[CMFCRibbonPanel::Add](#add)。  
  
### <a name="remarks"></a>备注  
 关于工具栏、 热图像、 冷图像及已禁用的映像的详细信息，请参阅[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)。  
  
##  <a name="a-namecmfcribbonpanela--cmfcribbonpanelcmfcribbonpanel"></a><a name="cmfcribbonpanel"></a>CMFCRibbonPanel::CMFCRibbonPanel  
 构造并初始化[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)对象。  
  
```  
CMFCRibbonPanel(
LPCTSTR lpszName = NULL,  
HICON hIcon = NULL);  
  
CMFCRibbonPanel(CMFCRibbonGallery* pPaletteButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszName`  
 功能区面板的名称。  
  
 [in] `hIcon`  
 功能区面板的默认按钮的图标的句柄。  
  
 [in] `pPaletteButton`  
 指针，指向功能区面板中的功能区库。  
  
##  <a name="a-namefindbydataa--cmfcribbonpanelfindbydata"></a><a name="findbydata"></a>CMFCRibbonPanel::FindByData  
 检索与指定的数据相关联的功能区元素。  
  
```  
CMFCRibbonBaseElement* FindByData(DWORD_PTR dwData) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `dwData`  
 与功能区元素关联的数据。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则为功能区元素的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namefindbyida--cmfcribbonpanelfindbyid"></a><a name="findbyid"></a>CMFCRibbonPanel::FindByID  
 检索由指定的命令 ID 标识的功能区元素  
  
```  
CMFCRibbonBaseElement* FindByID(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 功能区元素命令 ID。  
  
### <a name="return-value"></a>返回值  
 由指定的命令 ID; 标识功能区元素否则为`NULL`如果没有的功能区元素标识替换为指定的命令 id。  
  
##  <a name="a-namegetcaptionheighta--cmfcribbonpanelgetcaptionheight"></a><a name="getcaptionheight"></a>CMFCRibbonPanel::GetCaptionHeight  
 检索功能区面板的标题的高度。  
  
```  
int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位的功能区面板的标题高度。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetcounta--cmfcribbonpanelgetcount"></a><a name="getcount"></a>CMFCRibbonPanel::GetCount  
 检索包含在功能区面板中的功能区元素的数目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 功能区面板中包含的功能区元素的数目。  
  
##  <a name="a-namegetdataa--cmfcribbonpanelgetdata"></a><a name="getdata"></a>CMFCRibbonPanel::GetData  
 返回与面板相关联的用户定义数据。  
  
```  
DWORD_PTR GetData() const;  
```  
  
### <a name="return-value"></a>返回值  
 与面板相关联的用户定义的数据中。  
  
##  <a name="a-namegetdefaultbuttona--cmfcribbonpanelgetdefaultbutton"></a><a name="getdefaultbutton"></a>CMFCRibbonPanel::GetDefaultButton  
 检索功能区面板中的默认按钮。  
  
```  
CMFCRibbonButton& GetDefaultButton();
```  
  
### <a name="return-value"></a>返回值  
 功能区面板为默认按钮。  
  
### <a name="remarks"></a>备注  
 功能区面板没有足够的空间来显示其功能区元素时，将显示默认按钮。  
  
##  <a name="a-namegetdroppeddowna--cmfcribbonpanelgetdroppeddown"></a><a name="getdroppeddown"></a>CMFCRibbonPanel::GetDroppedDown  
 检索指向功能区元素的指针，如果向下删除其弹出菜单。  
  
```  
CMFCRibbonBaseElement* GetDroppedDown() const;  
```  
  
### <a name="return-value"></a>返回值  
 具有已下拉; 其弹出菜单的功能区元素的指针否则为`NULL`如果功能区元素不具有向下删除其弹出菜单。  
  
### <a name="remarks"></a>备注  
 测试包含在功能区面板中添加的功能区元素。  
  
##  <a name="a-namegetelementa--cmfcribbonpanelgetelement"></a><a name="getelement"></a>CMFCRibbonPanel::GetElement  
 返回位于指定索引处的功能区元素。  
  
```  
CMFCRibbonBaseElement* GetElement(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定要检索的元素的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指向的基本功能区元素的有效指针位于位置`nIndex`在功能区面板中，或`NULL`如果没有任何元素的指定索引处。  
  
##  <a name="a-namegetelementsa--cmfcribbonpanelgetelements"></a><a name="getelements"></a>CMFCRibbonPanel::GetElements  
 检索包含在功能区面板中的所有功能区元素。  
  
```  
void GetElements(CArray<CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>参数  
 [out] `arElements`  
 用于填充功能区面板中包含的所有功能区元素的数组。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetelementsbyida--cmfcribbonpanelgetelementsbyid"></a><a name="getelementsbyid"></a>CMFCRibbonPanel::GetElementsByID  
 添加具有指定的命令 ID 到指定的数组的功能区元素。  
  
```  
void GetElementsByID(
UINT uiCmdID,  
CArray<CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 功能区元素的命令 ID。  
  
 [in] `arElements`  
 功能区元素的数组。  
  
### <a name="remarks"></a>备注  
 测试包含在功能区面板中添加的功能区元素。  
  
##  <a name="a-namegethighlighteda--cmfcribbonpanelgethighlighted"></a><a name="gethighlighted"></a>CMFCRibbonPanel::GetHighlighted  
 检索在功能区面板突出显示的功能区元素。  
  
```  
CMFCRibbonBaseElement* GetHighlighted() const;  
```  
  
### <a name="return-value"></a>返回值  
 在功能区面板上突出显示的功能区元素的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetindexa--cmfcribbonpanelgetindex"></a><a name="getindex"></a>CMFCRibbonPanel::GetIndex  
 从功能区面板中包含的功能区元素的数组中检索指定的功能区元素的从零开始索引。  
  
```  
virtual int GetIndex(CMFCRibbonBaseElement* pElem) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pElem`  
 指向功能区元素的指针。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则指定功能区元素的从零开始的索引否则为-1。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetitemidslista--cmfcribbonpanelgetitemidslist"></a><a name="getitemidslist"></a>CMFCRibbonPanel::GetItemIDsList  
 检索功能区面板中的所有功能区元素的命令 Id。  
  
```  
void GetItemIDsList(CList<UINT, UINT>& lstItems) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `lstItems`  
 功能区面板中包含的功能区元素的命令 Id 的列表。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetnamea--cmfcribbonpanelgetname"></a><a name="getname"></a>CMFCRibbonPanel::GetName  
 检索功能区面板中的名称。  
  
```  
LPCTSTR GetName() const;  
```  
  
### <a name="return-value"></a>返回值  
 功能区面板的名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetparentbuttona--cmfcribbonpanelgetparentbutton"></a><a name="getparentbutton"></a>CMFCRibbonPanel::GetParentButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonBaseElement* GetParentButton() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetparentcategorya--cmfcribbonpanelgetparentcategory"></a><a name="getparentcategory"></a>CMFCRibbonPanel::GetParentCategory  
 返回功能区面板的父类别。  
  
```  
CMFCRibbonCategory* GetParentCategory() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向包含此功能区面板的功能区类别。  
  
##  <a name="a-namegetparentmenubara--cmfcribbonpanelgetparentmenubar"></a><a name="getparentmenubar"></a>CMFCRibbonPanel::GetParentMenuBar  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonPanelMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetpreferedmenulocationa--cmfcribbonpanelgetpreferedmenulocation"></a><a name="getpreferedmenulocation"></a>CMFCRibbonPanel::GetPreferedMenuLocation  
 检索功能区面板的弹出菜单的首选的显示矩形。  
  
```  
virtual BOOL GetPreferedMenuLocation(CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 [out] `rect`  
 未使用此参数。  
  
### <a name="return-value"></a>返回值  
 始终返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法始终返回 `FALSE`。 重写此方法以检索功能区面板的弹出菜单的首选的显示矩形。  
  
##  <a name="a-namegetpresseda--cmfcribbonpanelgetpressed"></a><a name="getpressed"></a>CMFCRibbonPanel::GetPressed  
 如果用户当前按，检索到功能区面板上的功能区元素的指针。  
  
```  
CMFCRibbonBaseElement* GetPressed() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向用户当前按下它; 如果的功能区元素的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetrecta--cmfcribbonpanelgetrect"></a><a name="getrect"></a>CMFCRibbonPanel::GetRect  
 检索功能区面板显示矩形。  
  
```  
const CRect& GetRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 功能区面板显示矩形。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namehaselementa--cmfcribbonpanelhaselement"></a><a name="haselement"></a>CMFCRibbonPanel::HasElement  
 指示功能区面板中是否包含指定的功能区元素。  
  
```  
BOOL HasElement(const CMFCRibbonBaseElement* pElem) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pElem`  
 指向功能区元素的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果功能区面板包含指定功能区元素;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namehighlighta--cmfcribbonpanelhighlight"></a><a name="highlight"></a>CMFCRibbonPanel::Highlight  
 设置为所选的功能区面板和指定的点的功能区元素的突出显示颜色。  
  
```  
virtual void Highlight(
BOOL bHighlight,  
CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `bHighlight`  
 `TRUE`若要突出显示功能区面板中;`FALSE`以 unhighlight 功能区面板。  
  
 [in] `point`  
 X 和 y 坐标相对于窗口的左上角的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namehittesta--cmfcribbonpanelhittest"></a><a name="hittest"></a>CMFCRibbonPanel::HitTest  
 如果指定的点位于它，检索的功能区元素。  
  
```  
virtual CMFCRibbonBaseElement* HitTest(
CPoint point,  
BOOL bCheckPanelCaption = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 X 和 y 坐标相对于窗口的左上角的指针。  
  
 [in] `bCheckPanelCaption`  
 `TRUE`若要测试功能区面板标题;否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 指定的点位于它; 如果的功能区元素的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 测试包含在功能区面板中添加的功能区元素。  
  
##  <a name="a-namehittestexa--cmfcribbonpanelhittestex"></a><a name="hittestex"></a>CMFCRibbonPanel::HitTestEx  
 检索具有指定的点位于它的功能区元素的从零开始索引。  
  
```  
virtual int HitTestEx(CPoint point) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 X 和 y 坐标相对于窗口的左上角的指针。  
  
### <a name="return-value"></a>返回值  
 具有位于; 的指定的点的功能区元素的从零开始的索引否则为-1。  
  
### <a name="remarks"></a>备注  
 测试包含在功能区面板中添加的功能区元素。  
  
##  <a name="a-nameinserta--cmfcribbonpanelinsert"></a><a name="insert"></a>CMFCRibbonPanel::Insert  
 指定功能区元素的位置处插入指定数组中的功能区元素包含在功能区面板。  
  
```  
virtual BOOL Insert(
CMFCRibbonBaseElement* pElem,  
int nIndex);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pElem`  
 指向功能区元素的指针。  
  
 [in] `nIndex`  
 从零开始的值，范围从-1 到数组中包含的功能区元素的数目。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则插入了功能区元素否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果值`nIndex`为-1，或者如果`nIndex`等于数组中的功能区元素的数目，则指定的功能区元素添加到该数组的末尾。 如果值`nIndex`是超出范围，该方法将失败。  
  
##  <a name="a-nameinsertseparatora--cmfcribbonpanelinsertseparator"></a><a name="insertseparator"></a>CMFCRibbonPanel::InsertSeparator  
 在指定的位置插入分隔符。  
  
```  
virtual BOOL InsertSeparator(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定分隔符插入的位置的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功，则插入分隔符否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以在指定的位置插入一个分隔符`nIndex`。 若要插入最近添加的功能区元素旁边的分隔符，请调用[CMFCRibbonPanel::AddSeparator](#addseparator)。  
  
##  <a name="a-nameiscentercolumnverta--cmfcribbonpaneliscentercolumnvert"></a><a name="iscentercolumnvert"></a>CMFCRibbonPanel::IsCenterColumnVert  
 指示是否在其显示矩形内居中垂直位置的功能区元素。  
  
```  
BOOL IsCenterColumnVert() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果垂直定位的功能区元素是在其显示矩形; 内居中否则为`FALSE`。  
  
##  <a name="a-nameiscollapseda--cmfcribbonpaneliscollapsed"></a><a name="iscollapsed"></a>CMFCRibbonPanel::IsCollapsed  
 指示是否将功能区面板的显示大小最小化在水平方向。  
  
```  
BOOL IsCollapsed() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果功能区面板的显示大小在水平方向; 最小化状态，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当功能区面板处于折叠状态时，但它仅显示其默认按钮、 其名称和下拉箭头。  
  
##  <a name="a-nameishighlighteda--cmfcribbonpanelishighlighted"></a><a name="ishighlighted"></a>CMFCRibbonPanel::IsHighlighted  
 指示是否突出显示功能区面板的显示。  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果突出显示功能区面板的显示;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当鼠标指针位于时，将突出显示功能区面板的显示。  
  
##  <a name="a-nameisjustifycolumnsa--cmfcribbonpanelisjustifycolumns"></a><a name="isjustifycolumns"></a>CMFCRibbonPanel::IsJustifyColumns  
 指示是否将功能区面板中的同一列中的功能区元素的显示尺寸设置为相同的宽度。  
  
```  
BOOL IsJustifyColumns() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果功能区面板中的同一列中的功能区元素的显示尺寸设置为相同的宽度;否则为`FALSE`。  
  
##  <a name="a-nameismainpanela--cmfcribbonpanelismainpanel"></a><a name="ismainpanel"></a>CMFCRibbonPanel::IsMainPanel  
 指示是否将功能区面板是主要的功能区面板。  
  
```  
virtual BOOL IsMainPanel() const;  
```  
  
### <a name="return-value"></a>返回值  
 始终返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法始终返回 `FALSE`。 重写此方法以指示将功能区面板是否是主要的功能区面板。  
  
 当用户选择应用程序按钮，将显示主要的功能区面板。  
  
##  <a name="a-nameismenumodea--cmfcribbonpanelismenumode"></a><a name="ismenumode"></a>CMFCRibbonPanel::IsMenuMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMenuMode() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonkeya--cmfcribbonpanelonkey"></a><a name="onkey"></a>CMFCRibbonPanel::OnKey  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>参数  
 [in] `nChar`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namerecalcwidthsa--cmfcribbonpanelrecalcwidths"></a><a name="recalcwidths"></a>CMFCRibbonPanel::RecalcWidths  
 重新计算功能区面板中的每个显示布局配置的宽度。  
  
```  
virtual void RecalcWidths(
CDC* pDC,  
int nHeight);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 功能区面板的设备上下文的指针。  
  
 [in] `nHeight`  
 功能区面板大小的高度。  
  
### <a name="remarks"></a>备注  
 功能区面板随着可用宽度的变化更改其布局配置。  
  
##  <a name="a-nameremovea--cmfcribbonpanelremove"></a><a name="remove"></a>CMFCRibbonPanel::Remove  
 删除并根据需要删除位于指定索引处的元素。  
  
```  
BOOL Remove(
int nIndex,  
BOOL bDelete = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定从功能区面板中移除的元素的从零开始索引。  
  
 [in] `bDelete`  
 `TRUE`若要删除已移除; 的元素否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果移除并删除元素 (如果`bDelete`是`TRUE`);`FALSE`如果不移除该元素，或者如果没有任何功能区元素位于`nIndex`。  
  
### <a name="remarks"></a>备注  
 调用此方法以从功能区面板中删除元素。  
  
##  <a name="a-nameremovealla--cmfcribbonpanelremoveall"></a><a name="removeall"></a>CMFCRibbonPanel::RemoveAll  
 从功能区面板中删除所有的功能区元素。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 所有功能区元素从功能区面板中删除，并销毁。  
  
##  <a name="a-namereplacea--cmfcribbonpanelreplace"></a><a name="replace"></a>CMFCRibbonPanel::Replace  
 将一个元素替换与另一个基于其索引值。  
  
```  
BOOL Replace(
int nIndex,  
CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定要替换的元素的从零开始索引。  
  
 [in][out]`pElem`  
 指向替换原始元素的元素的有效指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已由新的功能区元素; 成功替换原始的功能区元素`FALSE`如果未替换功能区元素或没有任何元素的指定索引处。  
  
### <a name="remarks"></a>备注  
 若要将功能区元素替换为命令 ID，请调用[CMFCRibbonPanel::ReplaceByID](#replacebyid)。  
  
##  <a name="a-namereplacebyida--cmfcribbonpanelreplacebyid"></a><a name="replacebyid"></a>CMFCRibbonPanel::ReplaceByID  
 一个元素替换为另一个基于指定的命令 id。  
  
```  
BOOL ReplaceByID(
UINT uiCmdID,  
CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 指定要替换该元素的命令 ID。  
  
 [in][out]`pElem`  
 指向要替换的原始元素的元素的有效指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已由新的功能区元素; 成功替换原始的功能区元素`FALSE`不替换功能区元素是否与指定的命令 ID 的元素不实际存在。  
  
### <a name="remarks"></a>备注  
 若要替换基于位置的功能区元素，请调用[CMFCRibbonPanel::Replace](#replace)。  
  
##  <a name="a-namesetcentercolumnverta--cmfcribbonpanelsetcentercolumnvert"></a><a name="setcentercolumnvert"></a>CMFCRibbonPanel::SetCenterColumnVert  
 启用或禁用使其显示矩形内的功能区元素的垂直位置内居中。  
  
```  
void SetCenterColumnVert(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 `TRUE`要使其显示矩形; 范围内的功能区元素的垂直位置居中`FALSE`禁用此功能。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetdataa--cmfcribbonpanelsetdata"></a><a name="setdata"></a>CMFCRibbonPanel::SetData  
 将用户定义数据，功能区面板。  
  
```  
void SetData(DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwData`  
 指定要设置的用户定义数据。  
  
### <a name="remarks"></a>备注  
 调用此方法以将用户定义数据与功能区面板相关联。  
  
##  <a name="a-namesetelementmenua--cmfcribbonpanelsetelementmenu"></a><a name="setelementmenu"></a>CMFCRibbonPanel::SetElementMenu  
 将具有给定的命令 ID 的元素的弹出菜单  
  
```  
BOOL SetElementMenu(
UINT uiCmdID,  
HMENU hMenu,  
BOOL bIsDefautCommand = FALSE,  
BOOL bRightAlign = FALSE);

 
BOOL SetElementMenu(
UINT uiCmdID,  
UINT uiMenuResID,  
BOOL bIsDefautCommand = FALSE,  
BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 指定菜单中的添加位置的功能区元素的命令 ID。  
  
 [in] `hMenu`  
 指定 Windows 菜单添加到功能区面板的句柄。  
  
 [in] `bIsDefautCommand`  
 `TRUE`若要指定单击功能区元素时，应执行与功能区元素关联的命令。 在这种情况下，仅打开菜单上，当用户单击功能区元素旁边的箭头。 `FALSE`若要指定单击功能区元素时不应执行与功能区元素关联的命令。 在这种情况下，弹出菜单显示而不考虑在用户单击此元素。  
  
 [in] `bRightAlign`  
 `TRUE`若要指定的弹出菜单是右对齐;否则为`FALSE`。  
  
 [in] `uiMenuResID`  
 指定要添加到功能区面板菜单上的资源 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果向功能区元素，则分配了菜单否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以分配给具有给定的命令 ID 的功能区元素的弹出菜单  
  
##  <a name="a-namesetelementrtca--cmfcribbonpanelsetelementrtc"></a><a name="setelementrtc"></a>CMFCRibbonPanel::SetElementRTC  
 将添加到功能区面板提供运行时类信息由指定的功能区元素。  
  
```  
CMFCRibbonBaseElement* SetElementRTC(
int nIndex,  
CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定要添加的功能区元素的从零开始索引。  
  
 [in][out]`pRTC`  
 指向运行时类信息以添加到功能区面板的功能区元素的指针。  
  
### <a name="return-value"></a>返回值  
 使用指定的运行时类信息创建功能区元素。  
  
### <a name="remarks"></a>备注  
 如果你想要将自定义元素 （例如，颜色按钮） 添加到功能区面板，您必须指定自定义元素的运行时类信息。 功能区存储此信息、 创建自定义的元素，并替换现有元素，它位于 （确定） 指定的命令 id。 功能区然后返回到新创建的元素的指针。  
  
##  <a name="a-namesetelementrtcbyida--cmfcribbonpanelsetelementrtcbyid"></a><a name="setelementrtcbyid"></a>CMFCRibbonPanel::SetElementRTCByID  
 将添加到功能区面板提供运行时类信息由指定的功能区元素。  
  
```  
CMFCRibbonBaseElement* SetElementRTCByID(
UINT uiCmdID,  
CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 指定要添加的功能区元素的命令 ID。  
  
 [in][out]`pRTC`  
 指向与添加到功能区面板的功能区元素关联的运行时类信息的指针。  
  
### <a name="return-value"></a>返回值  
 使用指定的运行时类信息创建功能区元素。  
  
### <a name="remarks"></a>备注  
 如果你想要将自定义元素 （例如，颜色按钮） 添加到功能区面板，您必须指定自定义元素的运行时类信息。 功能区存储此信息、 创建自定义的元素，并替换现有元素位于由指定的命令 id。 然后会将一个指针，返回新创建的元素。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`SetElementRTCByID`方法︰  
  
```  
 
// Load and add toolbar with standard buttons. This toolbar  
// should display a custom color button with id ID_CHAR_COLOR:  
 
pPanel->AddToolBar(IDR_MAINFRAME,
    IDB_MAINFRAME256);

CMFCRibbonColorButton* pColorButton = 
(CMFCRibbonColorButton*)pPanel->SetElementRTCByID(
ID_CHAR_COLOR,
    RUNTIME_CLASS (CMFCRibbonColorButton));

 
// SetElementRTCByID sets runtime class and returns a pointer  
// to the newly created custom button,
    which can be set up immediately:  
pColorButton->EnableAutomaticButton(_T("Automatic"),
    RGB (0,
    0,
    0));  
```  
  
##  <a name="a-namesetjustifycolumnsa--cmfcribbonpanelsetjustifycolumns"></a><a name="setjustifycolumns"></a>CMFCRibbonPanel::SetJustifyColumns  
 启用或禁用的同一列中的功能区元素的宽度调整。  
  
```  
void SetJustifyColumns(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 `TRUE`若要调整为宽度的列; 中的最大功能区元素的同一列中的功能区元素的宽度`FALSE`若要禁用此宽度调整。  
  
### <a name="remarks"></a>备注  
 在功能区面板中启用此功能，同一列中的功能区元素的宽度调整为同一列中的最大功能区元素的宽度。  
  
##  <a name="a-namesetkeysa--cmfcribbonpanelsetkeys"></a><a name="setkeys"></a>CMFCRibbonPanel::SetKeys  
 设置的默认按钮的功能区面板上方的键提示。  
  
```  
void SetKeys(LPCTSTR lpszKeys);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszKeys`  
 默认按钮的功能区面板快捷键提示。  
  
### <a name="remarks"></a>备注  
 功能区面板没有足够的空间来显示其功能区元素时，将显示默认按钮。  
  
##  <a name="a-nameshowpopupa--cmfcribbonpanelshowpopup"></a><a name="showpopup"></a>CMFCRibbonPanel::ShowPopup  
 创建并显示功能区面板的弹出菜单。  
  
```  
CMFCRibbonPanelMenu* ShowPopup(CMFCRibbonDefaultPanelButton* pButton = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pButton`  
 指针，指向功能区面板中的默认按钮。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则功能区面板的弹出菜单的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 功能区面板的显示未展开时，功能区面板的弹出菜单才可用。  
  
##  <a name="a-namesetfocuseda--cmfcribbonpanelsetfocused"></a><a name="setfocused"></a>CMFCRibbonPanel::SetFocused  
 将焦点移到指定的功能区元素。  
  
```  
void SetFocused(CMFCRibbonBaseElement* pNewFocus);
```  
  
### <a name="parameters"></a>参数  
 `pNewFocus`  
 指向接收到焦点的功能区元素的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namemakegalleryitemvisiblea--cmfcribbonpanelmakegalleryitemvisible"></a><a name="makegalleryitemvisible"></a>CMFCRibbonPanel::MakeGalleryItemVisible  
 执行滚动操作使得库以使指定的功能区元素可见。  
  
```  
void MakeGalleryItemVisible(CMFCRibbonBaseElement* pItem);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向要显示的功能区元素的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameiswindows7looka--cmfcribbonpaneliswindows7look"></a><a name="iswindows7look"></a>CMFCRibbonPanel::IsWindows7Look  
 指示父功能区是否有 Windows 7 查找 （矩形的小型应用程序按钮）。  
  
```  
BOOL IsWindows7Look() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果父功能区中有 Windows 7 查找;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetvisibleelementsa--cmfcribbonpanelgetvisibleelements"></a><a name="getvisibleelements"></a>CMFCRibbonPanel::GetVisibleElements  
 检索包含可见的元素的数组。  
  
```  
void GetVisibleElements(
CArray<CMFCRibbonBaseElement*,  
CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>参数  
 `arElements`  
 当函数返回时，此参数包含可见的元素的数组。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetgalleryrecta--cmfcribbonpanelgetgalleryrect"></a><a name="getgalleryrect"></a>CMFCRibbonPanel::GetGalleryRect  
 返回库元素的绑定矩形。  
  
```  
CRect GetGalleryRect();
```  
  
### <a name="return-value"></a>返回值  
 大小和此面板中的库元素的位置。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetfocuseda--cmfcribbonpanelgetfocused"></a><a name="getfocused"></a>CMFCRibbonPanel::GetFocused  
 返回焦点元素。  
  
```  
CMFCRibbonBaseElement* GetFocused() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向具有焦点的元素的指针或`NULL`。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [CMFCRibbonCategory 类](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonBaseElement 类](../../mfc/reference/cmfcribbonbaseelement-class.md)

