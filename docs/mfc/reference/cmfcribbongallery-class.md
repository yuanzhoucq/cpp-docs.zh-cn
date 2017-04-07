---
title: "CMFCRibbonGallery 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonGallery
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::CMFCRibbonGallery
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::AddGroup
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::AddSubItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::Clear
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::EnableMenuResize
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::EnableMenuSideBar
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetCompactSize
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetDroppedDown
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetGroupName
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetGroupOffset
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetIconsInRow
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetItemToolTip
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetLastSelectedItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetPaletteID
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetRegularSize
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::GetSelectedItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::HasMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsButtonMode
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsMenuResizeEnabled
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsMenuResizeVertical
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::IsMenuSideBar
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnAfterChangeRect
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnDraw
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnEnable
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnRTLChanged
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::RedrawIcons
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::RemoveItemToolTips
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SelectItem
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetACCData
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetButtonMode
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetGroupName
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetIconsInRow
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetItemToolTip
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::SetPaletteID
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGallery::OnDrawPaletteIcon
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonGallery class
ms.assetid: 9734c9c9-981c-4b3f-8c59-264fd41811b4
caps.latest.revision: 28
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
ms.openlocfilehash: c4eadb9820f2d7318131cc4d197dbe28d65491c0
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbongallery-class"></a>CMFCRibbonGallery 类
实现 Office 2007 样式功能区库。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonGallery : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonGallery::CMFCRibbonGallery](#cmfcribbongallery)|构造并初始化一个 `CMFCRibbonGallery` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonGallery::AddGroup](#addgroup)|将新的组添加到库中。|  
|[CMFCRibbonGallery::AddSubItem](#addsubitem)|将一个新菜单项添加到下拉列表菜单。|  
|[CMFCRibbonGallery::Clear](#clear)|清除库的内容。|  
|[CMFCRibbonGallery::EnableMenuResize](#enablemenuresize)|启用或禁用菜单面板大小的调整大小。|  
|[CMFCRibbonGallery::EnableMenuSideBar](#enablemenusidebar)|启用或禁用弹出菜单的左侧的侧栏。|  
|[CMFCRibbonGallery::GetCompactSize](#getcompactsize)|(重写[CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|  
|[CMFCRibbonGallery::GetDroppedDown](#getdroppeddown)|(重写[CMFCRibbonBaseElement::GetDroppedDown](../../mfc/reference/cmfcribbonbaseelement-class.md#getdroppeddown)。)|  
|[CMFCRibbonGallery::GetGroupName](#getgroupname)|返回位于指定索引处的组的名称。|  
|[CMFCRibbonGallery::GetGroupOffset](#getgroupoffset)||  
|[CMFCRibbonGallery::GetIconsInRow](#geticonsinrow)|功能区库的某一行中返回的项数。|  
|[CMFCRibbonGallery::GetItemToolTip](#getitemtooltip)|返回与库中的项相关联的工具提示文本。|  
|[CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem)|返回用户所选库中的最后一项的索引。|  
|[CMFCRibbonGallery::GetPaletteID](#getpaletteid)|返回当前库中的命令 ID。|  
|[CMFCRibbonGallery::GetRegularSize](#getregularsize)|(重写[CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|  
|[CMFCRibbonGallery::GetSelectedItem](#getselecteditem)||  
|[CMFCRibbonGallery::HasMenu](#hasmenu)|(重写[CMFCRibbonButton::HasMenu](../../mfc/reference/cmfcribbonbutton-class.md#hasmenu)。)|  
|[CMFCRibbonGallery::IsButtonMode](#isbuttonmode)|指定是否将库包含库按钮中。|  
|[CMFCRibbonGallery::IsMenuResizeEnabled](#ismenuresizeenabled)|指定启用还是禁用菜单调整大小。|  
|[CMFCRibbonGallery::IsMenuResizeVertical](#ismenuresizevertical)||  
|[CMFCRibbonGallery::IsMenuSideBar](#ismenusidebar)|指定是否启用或禁用侧栏。|  
|[CMFCRibbonGallery::OnAfterChangeRect](#onafterchangerect)|（重写 `CMFCRibbonButton::OnAfterChangeRect`。）|  
|[CMFCRibbonGallery::OnDraw](#ondraw)|(重写[CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|  
|[CMFCRibbonGallery::OnEnable](#onenable)|（重写 `CMFCRibbonBaseElement::OnEnable`。）|  
|[CMFCRibbonGallery::OnRTLChanged](#onrtlchanged)|(重写[CMFCRibbonBaseElement::OnRTLChanged](../../mfc/reference/cmfcribbonbaseelement-class.md#onrtlchanged)。)|  
|[CMFCRibbonGallery::RedrawIcons](#redrawicons)|重绘库。|  
|[CMFCRibbonGallery::RemoveItemToolTips](#removeitemtooltips)|从库中的所有项中移除工具提示。|  
|[CMFCRibbonGallery::SelectItem](#selectitem)||  
|[CMFCRibbonGallery::SetACCData](#setaccdata)|(重写[CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|  
|[CMFCRibbonGallery::SetButtonMode](#setbuttonmode)|指定是否显示功能区库作为下拉列表按钮或直接在功能区上的调色板。|  
|[CMFCRibbonGallery::SetGroupName](#setgroupname)|设置组的名称。|  
|[CMFCRibbonGallery::SetIconsInRow](#seticonsinrow)|在库中定义每个行项的数目。|  
|[CMFCRibbonGallery::SetItemToolTip](#setitemtooltip)|设置库中的项的工具提示文本。|  
|[CMFCRibbonGallery::SetPalette](#setpalette)|附加到功能区库的调色板。|  
|[CMFCRibbonGallery::SetPaletteID](#setpaletteid)|定义中发送的命令 ID`WM_COMMAND`消息时已选择某一库项。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonGallery::OnDrawPaletteIcon](#ondrawpaletteicon)|绘制库图标时，由框架调用。|  
  
## <a name="remarks"></a>备注  
 库按钮行为就像一个常规菜单按钮，只不过它将显示一个库，当用户打开它。 当在库中选择某个项目时，框架会将发送`WM_COMMAND`以及按钮的命令 ID 的消息。 在处理消息时，应调用[CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem)来确定哪一项已选定库中。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCRibbonGallery`用于配置类`CMFCRibbonGallery`对象。 该示例演示了如何在库中指定每个行项的数目，以便启用菜单面板大小的调整大小、 弹出菜单中，左侧的侧栏和并显示功能区库为直接在功能区栏上的调色板。 此代码段属于[绘制客户端示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient #&6;](../../mfc/reference/codesnippet/cpp/cmfcribbongallery-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md) [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxRibbonPaletteGallery.h  
  
##  <a name="addgroup"></a>CMFCRibbonGallery::AddGroup  
 将新的组添加到库中。  
  
```  
void AddGroup(
    LPCTSTR lpszGroupName,  
    UINT uiImagesPaletteResID,  
    int cxPaletteImage);

 
void AddGroup(
    LPCTSTR lpszGroupName,  
    CMFCToolBarImages& imagesGroup);

 
void AddGroup(
    LPCTSTR lpszGroupName,  
    int nIconsNum);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszGroupName`  
 指定组的名称。  
  
 [in] `uiImagesPaletteResID`  
 指定包含组的图像的图像列表的资源 ID。  
  
 [in] `cxPaletteImage`  
 指定以像素为单位的图像的宽度。  
  
 [in] `imagesGroup`  
 对包含组图像的图像列表的引用。  
  
 [in] `nIconsNum`  
 指定组中的图标数目。 只能为自定义 （所有者描述），应指定此参数组。  
  
### <a name="remarks"></a>备注  
 通过调用此方法，你可以将功能区库上的项目划分为多个组。 每个组可以有标题。  
  
##  <a name="addsubitem"></a>CMFCRibbonGallery::AddSubItem  
 将一个新菜单项添加到下拉列表菜单。  
  
```  
void AddSubItem(
    CMFCRibbonBaseElement* pSubItem,  
    int nIndex=-1,  
    BOOL bOnTop=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pSubItem`  
 指向要添加到菜单的项的指针。  
  
 [in] `nIndex`  
 指定位置的从零开始的索引位置插入项。  
  
 [in] `bOnTop`  
 `TRUE`若要指定应在功能区库中; 之前插入项否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 可以通过调用此方法与弹出菜单项一起组合弹出库。 可将菜单项之前或之后库。  
  
 若要插入库之前的项，设置`bOnTop`到`TRUE`。 设置`bOnTop`到`FALSE`插入下面库的项目。  
  
> [!NOTE]
>  该参数`nIndex`指定插入索引同时在库的顶部和底部的库。 例如，如果需要插入之前库项一个位置，设置`nIndex`为 1 和`bOnTop`到`TRUE`。 同样，如果需要插入下面库项的一个位置，则将设置`nIndex`为 1 和`bOnTop`到`FALSE`。  
  
##  <a name="clear"></a>CMFCRibbonGallery::Clear  
 清除库的内容。  
  
```  
virtual void Clear();
```  
  
### <a name="remarks"></a>备注  
 调用此方法以从功能区库中删除所有内容。 此操作必须执行之前将新的功能区库或系列组附加到功能区库。  
  
##  <a name="cmfcribbongallery"></a>CMFCRibbonGallery::CMFCRibbonGallery  
 构造并初始化[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)对象。  
  
```  
CMFCRibbonGallery (
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    CMFCToolBarImages& imagesPalette);

 
CMFCRibbonGallery (
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    UINT uiImagesPaletteResID=0,  
    int cxPaletteImage=0);

 
CMFCRibbonGallery (
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    CSize sizeIcon,  
    int nIconsNum,  
    BOOL bDefaultButtonStyle=TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 指定要在用户单击按钮时执行的命令的命令 ID。  
  
 `lpszText`  
 指定要在按钮上显示的文本。  
  
 `nSmallImageIndex`  
 要在按钮上显示的小图像的从零开始的索引。  
  
 `nLargeImageIndex`  
 要在按钮上显示的大图像的从零开始的索引。  
  
 `imagesPalette`  
 对引用[CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md)对象，其中包含的图像显示在库。  
  
 `uiImagesPaletteResID`  
 若要在库中显示的图像列表资源 ID。  
  
 `cxPaletteImage`  
 指定以像素为单位库上的图像的宽度。  
  
 `sizeIcon`  
 指定大小，以像素为单位的库映像。  
  
 `nIconsNum`  
 在库中指定图标的数目。  
  
 `bDefaultButtonStyle`  
 指定是否使用默认值或所有者描述的按钮样式。  
  
### <a name="remarks"></a>备注  
  
##  <a name="enablemenuresize"></a>CMFCRibbonGallery::EnableMenuResize  
 启用或禁用菜单面板大小的调整大小。  
  
```  
void EnableMenuResize(
    BOOL bEnable = TRUE,  
    BOOL bVertcalOnly = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用调整菜单;否则为`FALSE`。  
  
 [in] `bVertcalOnly`  
 `TRUE`若要指定可仅垂直; 调整库`FALSE`来指定库可以调整同时垂直和水平方向。  
  
### <a name="remarks"></a>备注  
 此方法用于启用或禁用调整大小功能区库。 当启用时调整大小时，功能区库将显示用户可以使用它来调整其大小的控制手柄。  
  
##  <a name="enablemenusidebar"></a>CMFCRibbonGallery::EnableMenuSideBar  
 启用或禁用弹出菜单的左侧的侧栏。  
  
```  
void EnablMenuSideBar(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要指定已启用的一侧栏;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以启用或禁用 Office XP 样式侧栏菜单的左侧。  
  
##  <a name="getcompactsize"></a>CMFCRibbonGallery::GetCompactSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getdroppeddown"></a>CMFCRibbonGallery::GetDroppedDown  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CMFCRibbonBaseElement* GetDroppedDown();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getgroupname"></a>CMFCRibbonGallery::GetGroupName  
 返回位于指定索引处的组的名称。  
  
```  
LPCTSTR GetGroupName(int nGroupIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nGroupIndex`  
 指定您想要检索其名称的组的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 位于指定索引处的组的名称。 传递无效的索引将导致失败的断言。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getgroupoffset"></a>CMFCRibbonGallery::GetGroupOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetGroupOffset() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="geticonsinrow"></a>CMFCRibbonGallery::GetIconsInRow  
 功能区库的某一行中返回的项数。  
  
```  
int GetIconsInRow() const;  
```  
  
### <a name="return-value"></a>返回值  
 在行中的项的数目。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getitemtooltip"></a>CMFCRibbonGallery::GetItemToolTip  
 返回与库中的项相关联的工具提示文本。  
  
```  
LPCTSTR GetItemToolTip(int nItemIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nItemIndex`  
 指定要检索的工具提示文本的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指向分配给功能区库中的项的工具提示字符串的指针。 它可以是`NULL`如果没有工具提示分配给该项目。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getlastselecteditem"></a>CMFCRibbonGallery::GetLastSelectedItem  
 返回用户所选的功能区库中的最后一项的索引。  
  
```  
static int GetLastSelectedItem(UINT uiCmdID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 指定打开功能区库的菜单项的命令 ID。  
  
### <a name="return-value"></a>返回值  
 当用户在功能区库中选择任何项时，库将发送`WM_COMMAND`的消息，同时打开功能区库的菜单按钮的命令 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpaletteid"></a>CMFCRibbonGallery::GetPaletteID  
 返回当前调色板的命令 ID。  
  
```  
int GetPaletteID() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前所选调色板命令 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getregularsize"></a>CMFCRibbonGallery::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getselecteditem"></a>CMFCRibbonGallery::GetSelectedItem  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="hasmenu"></a>CMFCRibbonGallery::HasMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isbuttonmode"></a>CMFCRibbonGallery::IsButtonMode  
 指定调色板是否包含在库按钮。  
  
```  
BOOL IsButtonMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果调色板显示为下拉列表菜单按钮;`FALSE`如果直接在功能区上显示调色板。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ismenuresizeenabled"></a>CMFCRibbonGallery::IsMenuResizeEnabled  
 指定是否启用菜单调整大小。  
  
```  
BOOL IsMenuResizeEnabled() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已启用菜单调整大小;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ismenuresizevertical"></a>CMFCRibbonGallery::IsMenuResizeVertical  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMenuResizeVertical() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ismenusidebar"></a>CMFCRibbonGallery::IsMenuSideBar  
 指定是否启用或禁用侧栏。  
  
```  
BOOL IsMenuSideBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在使用弹出菜单的左侧绘制 Office XP 样式侧栏否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onafterchangerect"></a>CMFCRibbonGallery::OnAfterChangeRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondraw"></a>CMFCRibbonGallery::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawpaletteicon"></a>CMFCRibbonGallery::OnDrawPaletteIcon  
 绘制库图标时，由框架调用。  
  
```  
virtual void OnDrawPaletteIcon(
    CDC* pDC,  
    CRect rectIcon,  
    int nIconIndex,  
    CMFCRibbonGalleryIcon* pIcon,  
    COLORREF clrText);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向用于绘图的设备上下文的指针。  
  
 [in] `rectIcon`  
 指定要绘制的图标的边框。  
  
 [in] `nIconIndex`  
 若要绘制的图标库图标的图像列表中指定的从零开始的索引。  
  
 [in] `pIcon`  
 指向要绘制的图标的指针。  
  
 [in] `clrText`  
 指定要绘制的项的文本的颜色。  
  
### <a name="remarks"></a>备注  
 您可以重写此方法在派生类自定义功能区库的外观。  
  
##  <a name="onenable"></a>CMFCRibbonGallery::OnEnable  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrtlchanged"></a>CMFCRibbonGallery::OnRTLChanged  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>参数  
 [in] `bIsRTL`  
  
### <a name="remarks"></a>备注  
  
##  <a name="redrawicons"></a>CMFCRibbonGallery::RedrawIcons  
 重绘库。  
  
```  
void RedrawIcons();
```  
  
### <a name="remarks"></a>备注  
 调用此函数进行重绘库。 如果您更改了在运行时库的内容，必须调用此方法。  
  
##  <a name="removeitemtooltips"></a>CMFCRibbonGallery::RemoveItemToolTips  
 从库中的所有项中移除工具提示。  
  
```  
void RemoveItemToolTips();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="selectitem"></a>CMFCRibbonGallery::SelectItem  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SelectItem(int nItemIndex);
```  
  
### <a name="parameters"></a>参数  
 [in] `nItemIndex`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setaccdata"></a>CMFCRibbonGallery::SetACCData  
 使用功能区库中的可访问性数据填充指定的 `CAccessibilityData` 对象。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,   
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParent`  
 功能区库窗口中的父窗口。  
  
 [out] `data`  
 一个 `CAccessibilityData` 对象，该对象从功能区库接收可访问性数据。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 如果此方法成功，则为 `TRUE`；否则为 `FALSE`。  
  
##  <a name="setbuttonmode"></a>CMFCRibbonGallery::SetButtonMode  
 确定是否显示功能区库作为下拉列表按钮或直接在功能区上的调色板。  
  
```  
void SetButtonMode(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 `TRUE`若要将功能区库显示为下拉列表菜单按钮;`FALSE`可以直接在功能区上显示的功能区库的内容。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setgroupname"></a>CMFCRibbonGallery::SetGroupName  
 设置组的名称。  
  
```  
void SetGroupName(
    int nGroupIndex,  
    LPCTSTR lpszGroupName);
```  
  
### <a name="parameters"></a>参数  
 [in] `nGroupIndex`  
 指定将名称更改的组的从零开始索引。  
  
 [in] `lpszGroupName`  
 指定组的新名称。  
  
### <a name="remarks"></a>备注  
 要更改其名称的组必须已将添加使用[CMFCRibbonGallery::AddGroup](#addgroup)方法。  
  
##  <a name="seticonsinrow"></a>CMFCRibbonGallery::SetIconsInRow  
 指定在库中的每个行项的数目。  
  
```  
void SetIconsInRow(int nIconsInRow);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIconsInRow`  
 指定库的每一行中显示的项目数。  
  
### <a name="remarks"></a>备注  
 使用此方法以指定功能区库的宽度。  
  
##  <a name="setitemtooltip"></a>CMFCRibbonGallery::SetItemToolTip  
 设置库中的项的工具提示文本。  
  
```  
void SetItemToolTip(
    int nItemIndex,  
    LPCTSTR lpszToolTip);
```  
  
### <a name="parameters"></a>参数  
 [in] `nItemIndex`  
 与之关联的工具提示调色板项的从零开始索引。  
  
 [in] `lpszToolTip`  
 要显示在工具提示的文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpalette"></a>CMFCRibbonGallery::SetPalette  
 附加到功能区库的调色板。  
  
```  
void SetPalette(CMFCToolBarImages& imagesPalette);

 
void SetPalette(
    UINT uiImagesPaletteResID,  
    int cxPaletteImage);
```  
  
### <a name="parameters"></a>参数  
 [in] `imagesPalette`  
 指定包含要在库中显示的图标的图像列表。  
  
 [in] `uiImagesPaletteResID`  
 指定包含要在库中显示的图标的图像列表的资源 ID。  
  
 [in] `cxPaletteImage`  
 指定以像素为单位库上的图像的宽度。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpaletteid"></a>CMFCRibbonGallery::SetPaletteID  
 定义中发送的命令 ID **WM_COMMAND**消息时用户选择某一库项。  
  
```  
void SetPaletteID(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 指定在发送的命令 ID **WM_COMMAND**消息时用户选择某一库项。  
  
### <a name="remarks"></a>备注  
 若要确定用户选择了库中的特定项，请调用[CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem)静态方法。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonGalleryMenuButton 类](../../mfc/reference/cmfcribbongallerymenubutton-class.md)

