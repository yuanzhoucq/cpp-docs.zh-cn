---
title: "CMFCRibbonGallery 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonGallery [MFC], CMFCRibbonGallery
- CMFCRibbonGallery [MFC], AddGroup
- CMFCRibbonGallery [MFC], AddSubItem
- CMFCRibbonGallery [MFC], Clear
- CMFCRibbonGallery [MFC], EnableMenuResize
- CMFCRibbonGallery [MFC], EnableMenuSideBar
- CMFCRibbonGallery [MFC], GetCompactSize
- CMFCRibbonGallery [MFC], GetDroppedDown
- CMFCRibbonGallery [MFC], GetGroupName
- CMFCRibbonGallery [MFC], GetGroupOffset
- CMFCRibbonGallery [MFC], GetIconsInRow
- CMFCRibbonGallery [MFC], GetItemToolTip
- CMFCRibbonGallery [MFC], GetLastSelectedItem
- CMFCRibbonGallery [MFC], GetPaletteID
- CMFCRibbonGallery [MFC], GetRegularSize
- CMFCRibbonGallery [MFC], GetSelectedItem
- CMFCRibbonGallery [MFC], HasMenu
- CMFCRibbonGallery [MFC], IsButtonMode
- CMFCRibbonGallery [MFC], IsMenuResizeEnabled
- CMFCRibbonGallery [MFC], IsMenuResizeVertical
- CMFCRibbonGallery [MFC], IsMenuSideBar
- CMFCRibbonGallery [MFC], OnAfterChangeRect
- CMFCRibbonGallery [MFC], OnDraw
- CMFCRibbonGallery [MFC], OnEnable
- CMFCRibbonGallery [MFC], OnRTLChanged
- CMFCRibbonGallery [MFC], RedrawIcons
- CMFCRibbonGallery [MFC], RemoveItemToolTips
- CMFCRibbonGallery [MFC], SelectItem
- CMFCRibbonGallery [MFC], SetACCData
- CMFCRibbonGallery [MFC], SetButtonMode
- CMFCRibbonGallery [MFC], SetGroupName
- CMFCRibbonGallery [MFC], SetIconsInRow
- CMFCRibbonGallery [MFC], SetItemToolTip
- CMFCRibbonGallery [MFC], SetPalette
- CMFCRibbonGallery [MFC], SetPaletteID
- CMFCRibbonGallery [MFC], OnDrawPaletteIcon
ms.assetid: 9734c9c9-981c-4b3f-8c59-264fd41811b4
caps.latest.revision: "28"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6cb4772f685a38db39c946a5e6f4e77df87998a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbongallery-class"></a>CMFCRibbonGallery 类
实现 Office 2007 样式功能区库。  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonGallery : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonGallery::CMFCRibbonGallery](#cmfcribbongallery)|构造并初始化一个 `CMFCRibbonGallery` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonGallery::AddGroup](#addgroup)|将新的组添加到库。|  
|[CMFCRibbonGallery::AddSubItem](#addsubitem)|将新的菜单项添加到下拉列表菜单。|  
|[CMFCRibbonGallery::Clear](#clear)|清除库的内容。|  
|[CMFCRibbonGallery::EnableMenuResize](#enablemenuresize)|启用或禁用菜单面板的调整大小。|  
|[CMFCRibbonGallery::EnableMenuSideBar](#enablemenusidebar)|启用或禁用侧栏左侧的弹出菜单。|  
|[CMFCRibbonGallery::GetCompactSize](#getcompactsize)|(重写[cmfcribbonbutton:: Getcompactsize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|  
|[CMFCRibbonGallery::GetDroppedDown](#getdroppeddown)|(重写[CMFCRibbonBaseElement::GetDroppedDown](../../mfc/reference/cmfcribbonbaseelement-class.md#getdroppeddown)。)|  
|[CMFCRibbonGallery::GetGroupName](#getgroupname)|返回位于指定索引处的组的名称。|  
|[CMFCRibbonGallery::GetGroupOffset](#getgroupoffset)||  
|[CMFCRibbonGallery::GetIconsInRow](#geticonsinrow)|返回的行的功能区库中的项的数目。|  
|[CMFCRibbonGallery::GetItemToolTip](#getitemtooltip)|返回与库中的项关联的工具提示文本。|  
|[CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem)|返回用户所选库中的最后一项的索引。|  
|[CMFCRibbonGallery::GetPaletteID](#getpaletteid)|返回当前库的命令 ID。|  
|[CMFCRibbonGallery::GetRegularSize](#getregularsize)|(重写[cmfcribbonbutton:: Getregularsize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|  
|[CMFCRibbonGallery::GetSelectedItem](#getselecteditem)||  
|[CMFCRibbonGallery::HasMenu](#hasmenu)|(重写[CMFCRibbonButton::HasMenu](../../mfc/reference/cmfcribbonbutton-class.md#hasmenu)。)|  
|[CMFCRibbonGallery::IsButtonMode](#isbuttonmode)|指定是否将库包含在库按钮。|  
|[CMFCRibbonGallery::IsMenuResizeEnabled](#ismenuresizeenabled)|指定启用还是禁用菜单调整大小。|  
|[CMFCRibbonGallery::IsMenuResizeVertical](#ismenuresizevertical)||  
|[CMFCRibbonGallery::IsMenuSideBar](#ismenusidebar)|指定是否启用或禁用侧栏。|  
|[CMFCRibbonGallery::OnAfterChangeRect](#onafterchangerect)|（重写 `CMFCRibbonButton::OnAfterChangeRect`。）|  
|[CMFCRibbonGallery::OnDraw](#ondraw)|(重写[cmfcribbonbutton:: Ondraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|  
|[CMFCRibbonGallery::OnEnable](#onenable)|（重写 `CMFCRibbonBaseElement::OnEnable`。）|  
|[CMFCRibbonGallery::OnRTLChanged](#onrtlchanged)|(重写[CMFCRibbonBaseElement::OnRTLChanged](../../mfc/reference/cmfcribbonbaseelement-class.md#onrtlchanged)。)|  
|[CMFCRibbonGallery::RedrawIcons](#redrawicons)|重绘库。|  
|[CMFCRibbonGallery::RemoveItemToolTips](#removeitemtooltips)|从库中的所有项中移除的工具提示。|  
|[CMFCRibbonGallery::SelectItem](#selectitem)||  
|[CMFCRibbonGallery::SetACCData](#setaccdata)|(重写[cmfcribbonbutton:: Setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|  
|[CMFCRibbonGallery::SetButtonMode](#setbuttonmode)|指定是否显示为下拉列表按钮或直接在功能区上的调色板的功能区库。|  
|[CMFCRibbonGallery::SetGroupName](#setgroupname)|设置组的名称。|  
|[CMFCRibbonGallery::SetIconsInRow](#seticonsinrow)|在库中定义的每行的项数。|  
|[CMFCRibbonGallery::SetItemToolTip](#setitemtooltip)|设置库中的项的工具提示文本。|  
|[CMFCRibbonGallery::SetPalette](#setpalette)|将调色板附加到功能区库。|  
|[CMFCRibbonGallery::SetPaletteID](#setpaletteid)|定义中未发送的命令 ID`WM_COMMAND`消息时已选择的库项。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonGallery::OnDrawPaletteIcon](#ondrawpaletteicon)|绘制库图标时，由框架调用。|  
  
## <a name="remarks"></a>备注  
 库按钮行为就像常规菜单按钮，只不过它将显示一个库，当用户打开它。 当在库中选择一个项时，框架会将发送`WM_COMMAND`以及按钮的命令 ID 的消息。 在处理消息时，应调用[CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem)以确定已从库选择哪一项。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCRibbonGallery`用于配置类`CMFCRibbonGallery`对象。 该示例说明如何在库中指定每个行项的数目、 启用菜单面板的调整大小、 启用弹出菜单中，左侧的栏和显示功能区库为直接在功能区栏上的调色板。 此代码片段属于 [Draw Client 示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient#6](../../mfc/reference/codesnippet/cpp/cmfcribbongallery-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md) [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxRibbonPaletteGallery.h  
  
##  <a name="addgroup"></a>CMFCRibbonGallery::AddGroup  
 将新的组添加到库。  
  
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
 指定组中的图标的数目。 应仅为自定义 （所有者描述的） 指定此参数组。  
  
### <a name="remarks"></a>备注  
 通过调用此方法，你可以将功能区库上的项划分为多个组。 每个组可以具有标题。  
  
##  <a name="addsubitem"></a>CMFCRibbonGallery::AddSubItem  
 将新的菜单项添加到下拉列表菜单。  
  
```  
void AddSubItem(
    CMFCRibbonBaseElement* pSubItem,  
    int nIndex=-1,  
    BOOL bOnTop=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pSubItem`  
 指向要添加到菜单项的指针。  
  
 [in] `nIndex`  
 指定位置的从零开始的索引位置插入项。  
  
 [in] `bOnTop`  
 `TRUE`若要指定在功能区库; 之前，应插入项否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 可以通过调用此方法与弹出菜单项一起组合弹出库。 之前或之后库，可以放置菜单项。  
  
 若要插入库之前的项，设置`bOnTop`到`TRUE`。 设置`bOnTop`到`FALSE`来插入下面库项。  
  
> [!NOTE]
>  参数`nIndex`指定插入索引在库的顶部和底部的库。 例如，如果需要插入之前库项一个位置，则设置`nIndex`为 1 和`bOnTop`到`TRUE`。 同样，如果需要插入下面库项一个位置，则设置`nIndex`为 1 和`bOnTop`到`FALSE`。  
  
##  <a name="clear"></a>CMFCRibbonGallery::Clear  
 清除库的内容。  
  
```  
virtual void Clear();
```  
  
### <a name="remarks"></a>备注  
 调用此方法以从功能区库中删除所有内容。 此操作必须执行之前将新的功能区库或组的组连接到功能区库。  
  
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
 对引用[CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md)对象，其中包含要在库上显示的图像。  
  
 `uiImagesPaletteResID`  
 要在库中显示的图像列表的资源 ID。  
  
 `cxPaletteImage`  
 指定宽度，以像素为单位，库上的映像。  
  
 `sizeIcon`  
 指定的大小，以像素为单位的库映像。  
  
 `nIconsNum`  
 在库中指定图标的数目。  
  
 `bDefaultButtonStyle`  
 指定是否使用默认值或所有者描述的按钮样式。  
  
### <a name="remarks"></a>备注  
  
##  <a name="enablemenuresize"></a>CMFCRibbonGallery::EnableMenuResize  
 启用或禁用菜单面板的调整大小。  
  
```  
void EnableMenuResize(
    BOOL bEnable = TRUE,  
    BOOL bVertcalOnly = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用调整大小菜单;否则为`FALSE`。  
  
 [in] `bVertcalOnly`  
 `TRUE`若要指定可仅垂直; 调整库`FALSE`来指定库可以调整大小同时垂直和水平方向。  
  
### <a name="remarks"></a>备注  
 此方法用于启用或禁用调整大小功能区库。 启用重设大小后，功能区库将显示用户可以使用以调整其大小的控制手柄。  
  
##  <a name="enablemenusidebar"></a>CMFCRibbonGallery::EnableMenuSideBar  
 启用或禁用侧栏左侧的弹出菜单。  
  
```  
void EnablMenuSideBar(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要指定侧栏启用了;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以启用或禁用 Office XP 样式侧栏左侧的菜单。  
  
##  <a name="getcompactsize"></a>CMFCRibbonGallery::GetCompactSize  

  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getdroppeddown"></a>CMFCRibbonGallery::GetDroppedDown  

  
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
 指定组你想要检索其名称的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 位于指定索引处的组的名称。 传递无效的索引将导致失败的断言。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getgroupoffset"></a>CMFCRibbonGallery::GetGroupOffset  

  
```  
virtual int GetGroupOffset() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="geticonsinrow"></a>CMFCRibbonGallery::GetIconsInRow  
 返回的行的功能区库中的项的数目。  
  
```  
int GetIconsInRow() const;  
```  
  
### <a name="return-value"></a>返回值  
 行中的项的数目。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getitemtooltip"></a>CMFCRibbonGallery::GetItemToolTip  
 返回与库中的项关联的工具提示文本。  
  
```  
LPCTSTR GetItemToolTip(int nItemIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nItemIndex`  
 指定为其检索工具提示文本的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指向分配给功能区库中的项的工具提示字符串的指针。 它可以是`NULL`如果没有工具提示分配给该项目。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getlastselecteditem"></a>CMFCRibbonGallery::GetLastSelectedItem  
 返回在用户选择功能区库中的最后一项的索引。  
  
```  
static int GetLastSelectedItem(UINT uiCmdID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 指定的菜单项，打开功能区库的命令 ID。  
  
### <a name="return-value"></a>返回值  
 当用户在功能区库中选择任何项时，库将发送`WM_COMMAND`以及打开功能区库菜单按钮的命令 ID 的消息。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpaletteid"></a>CMFCRibbonGallery::GetPaletteID  
 返回当前调色板的命令 ID。  
  
```  
int GetPaletteID() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前所选的调色板命令 ID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getregularsize"></a>CMFCRibbonGallery::GetRegularSize  

  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getselecteditem"></a>CMFCRibbonGallery::GetSelectedItem  

  
```  
int GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="hasmenu"></a>CMFCRibbonGallery::HasMenu  

  
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
 `TRUE`如果 Office XP 样式侧栏绘制在左侧的弹出窗口菜单中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onafterchangerect"></a>CMFCRibbonGallery::OnAfterChangeRect  

  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondraw"></a>CMFCRibbonGallery::OnDraw  

  
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
 库图标，图标以绘制的图像列表中指定的从零开始的索引。  
  
 [in] `pIcon`  
 指向正在绘制的图标的指针。  
  
 [in] `clrText`  
 指定要绘制的项文本的颜色。  
  
### <a name="remarks"></a>备注  
 你可以重写此方法在派生类自定义功能区库的外观。  
  
##  <a name="onenable"></a>CMFCRibbonGallery::OnEnable  

  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrtlchanged"></a>CMFCRibbonGallery::OnRTLChanged  

  
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
 调用此函数可重绘库。 如果您更改在运行时库的内容，必须调用此方法。  
  
##  <a name="removeitemtooltips"></a>CMFCRibbonGallery::RemoveItemToolTips  
 从库中的所有项中移除的工具提示。  
  
```  
void RemoveItemToolTips();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="selectitem"></a>CMFCRibbonGallery::SelectItem  

  
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
 确定是否显示为下拉列表按钮或直接在功能区上的调色板的功能区库。  
  
```  
void SetButtonMode(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 `TRUE`要将功能区库显示为下拉列表菜单按钮;`FALSE`直接在功能区上显示的功能区库的内容。  
  
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
 指定的名称更改的组的从零开始索引。  
  
 [in] `lpszGroupName`  
 指定组的新名称。  
  
### <a name="remarks"></a>备注  
 正在更改其名称的组必须使用添加[CMFCRibbonGallery::AddGroup](#addgroup)方法。  
  
##  <a name="seticonsinrow"></a>CMFCRibbonGallery::SetIconsInRow  
 指定在库中的每个行项的数目。  
  
```  
void SetIconsInRow(int nIconsInRow);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIconsInRow`  
 指定库的每一行中显示的项数。  
  
### <a name="remarks"></a>备注  
 使用此方法以指定的功能区库的宽度。  
  
##  <a name="setitemtooltip"></a>CMFCRibbonGallery::SetItemToolTip  
 设置库中的项的工具提示文本。  
  
```  
void SetItemToolTip(
    int nItemIndex,  
    LPCTSTR lpszToolTip);
```  
  
### <a name="parameters"></a>参数  
 [in] `nItemIndex`  
 要与关联的工具提示调色板项的从零开始索引。  
  
 [in] `lpszToolTip`  
 要在工具提示上显示的文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpalette"></a>CMFCRibbonGallery::SetPalette  
 将调色板附加到功能区库。  
  
```  
void SetPalette(CMFCToolBarImages& imagesPalette);

 
void SetPalette(
    UINT uiImagesPaletteResID,  
    int cxPaletteImage);
```  
  
### <a name="parameters"></a>参数  
 [in] `imagesPalette`  
 指定包含要在库上显示的图标的图像列表。  
  
 [in] `uiImagesPaletteResID`  
 指定包含要在库上显示的图标的图像列表的资源 ID。  
  
 [in] `cxPaletteImage`  
 指定宽度，以像素为单位库上的图像。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpaletteid"></a>CMFCRibbonGallery::SetPaletteID  
 定义中未发送的命令 ID **WM_COMMAND**消息时用户选择的库项。  
  
```  
void SetPaletteID(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 指定发送中的命令 ID **WM_COMMAND**消息时用户选择的库项。  
  
### <a name="remarks"></a>备注  
 若要确定用户选择了库中的特定项，请调用[CMFCRibbonGallery::GetLastSelectedItem](#getlastselecteditem)静态方法。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonGalleryMenuButton 类](../../mfc/reference/cmfcribbongallerymenubutton-class.md)
