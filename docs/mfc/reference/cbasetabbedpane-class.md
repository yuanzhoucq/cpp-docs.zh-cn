---
title: "CBaseTabbedPane 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBaseTabbedPane
dev_langs:
- C++
helpviewer_keywords:
- CBaseTabbedPane class
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b72804dd8b2ca2253caff4cebf5b0631ae6040c6
ms.lasthandoff: 02/24/2017

---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane 类
扩展功能的[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)以支持创建选项卡式窗口。  
  
## <a name="syntax"></a>语法  
  
```  
class CBaseTabbedPane : public CDockablePane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CBaseTabbedPane::CBaseTabbedPane`|默认构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CBaseTabbedPane::AddTab](#addtab)|选项卡式窗格中添加一个新选项卡。|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可销毁一个空的选项卡式的窗格。|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|将从注册表中，加载到选项卡式窗格中的选项卡上设置应用。|  
|[CBaseTabbedPane::CanFloat](#canfloat)|确定是否可以浮动窗格。 (重写[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|确定选项卡式窗格的标题是否应为活动选项卡显示相同的文本。|  
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(重写[CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。)|  
|[CBaseTabbedPane::DetachPane](#detachpane)|将一个或多个可停靠窗格转换为 MDI 选项卡式文档。|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|启用或禁用选项卡式窗格中的活动选项卡上的标签文本同步标题文本的能力。|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|将内部的 tab 键顺序还原到默认状态。|  
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|返回所在的选项卡中，当按从零开始的 tab 键索引标识选项卡的窗格。|  
|||  
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|返回由窗格 ID 标识的窗格|  
|[CBaseTabbedPane::FloatTab](#floattab)|仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。|  
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|在窗格中返回选项卡的默认顺序。|  
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|检索指向第一个显示的选项卡。|  
|[CBaseTabbedPane::GetMinSize](#getminsize)|检索允许大小为窗格中的最小。 (重写[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。)|  
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|返回窗格中图标的句柄。 (重写[CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon)。)|  
|[CBaseTabbedPane::GetPaneList](#getpanelist)|在选项卡式窗格中返回所包含的窗格的列表。|  
|[CBaseTabbedPane::GetTabArea](#gettabarea)|返回的顶部和底部的选项卡区域的边界矩形。|  
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|在选项卡上的窗口中返回的选项卡的计数。|  
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|获取基础 （包装） 选项卡窗口。|  
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|返回显示的标签的计数。|  
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|确定是否可以为自动隐藏模式切换选项卡式窗格。|  
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|确定是否选项卡式窗格中处于隐藏状态，如果只显示一个选项卡。|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|在序列化期间在内部使用。|  
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|重新计算窗格中的布局信息。 (重写[CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout)。)|  
|[CBaseTabbedPane::RemovePane](#removepane)|从选项卡式窗格中删除一个窗格。|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|在序列化期间在内部使用。|  
|`CBaseTabbedPane::Serialize`|(重写[CDockablePane::Serialize](http://msdn.microsoft.com/en-us/09787e59-e446-4e76-894b-206d303dcfd6)。)|  
|`CBaseTabbedPane::SerializeTabWindow`|在序列化期间在内部使用。|  
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|确定是否将自动销毁选项卡式的控件条。|  
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|切换停靠窗格之间显示和自动隐藏模式。 (重写[CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)。)|  
|[CBaseTabbedPane::ShowTab](#showtab)|显示或隐藏选项卡。|  
  
## <a name="remarks"></a>备注  
 此类是一个抽象类，不能实例化。 它实现的服务所共有的所有类型的选项卡式窗格。  
  
 目前，该库中包括两个选项卡式的窗格派生的类︰ [CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 一个`CBaseTabbedPane`对象包装到指针[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)对象。 [CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)随后将成为选项卡式窗格中的子窗口。  
  
 有关如何创建选项卡式的窗格的详细信息，请参阅[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)， [CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)，和[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 `CBaseTabbedPane`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxBaseTabbedPane.h  
  
##  <a name="a-nameaddtaba--cbasetabbedpaneaddtab"></a><a name="addtab"></a>CBaseTabbedPane::AddTab  
 选项卡式窗格中添加一个新选项卡。  
  
```  
virtual BOOL AddTab(
    CWnd* pNewBar,  
    BOOL bVisible = TRUE,  
    BOOL bSetActive = TRUE,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pNewBar`  
 指向添加窗格中的指针。 在调用此方法后，该指针可能会失效。 有关详细信息，请参阅“备注”部分。  
  
 [in] `bVisible`  
 `TRUE`若要使选项卡可见;否则为`FALSE`。  
  
 [in] `bSetActive`  
 `TRUE`若要使活动选项卡; 选项卡否则为`FALSE`。  
  
 [in] `bDetachable`  
 `TRUE`若要使选项卡可插拔;否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中已成功添加为一个选项卡，并不被销毁过程中。 `FALSE`如果添加窗格中是一个对象类型的`CBaseTabbedPane`。 有关详细信息，请参阅“备注”部分。  
  
### <a name="remarks"></a>备注  
 调用此方法可作为新的选项卡上选项卡式窗格中添加一个窗格。 如果`pNewBar`指向类型的对象`CBaseTabbedPane`，所有选项卡都已复制到选项卡式窗格中，然后`pNewBar`被销毁。 因此，`pNewBar`变为无效指针，不应使用。  
  
##  <a name="a-nameallowdestroyemptytabbedpanea--cbasetabbedpaneallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane  
 指定是否可销毁一个空的选项卡式的窗格。  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可销毁一个空的选项卡式的窗格;否则为`FALSE`。 默认实现始终返回`TRUE`。  
  
### <a name="remarks"></a>备注  
 如果不允许空的选项卡式窗格中，将其销毁，框架隐藏窗格。  
  
##  <a name="a-nameapplyrestoredtabinfoa--cbasetabbedpaneapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo  
 从注册表加载选项卡上的设置，并将其应用到选项卡式窗格。  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bUseTabIndexes`  
 框架在内部使用此参数。  
  
### <a name="remarks"></a>备注  
 重新停靠状态信息从注册表加载时，将由框架调用此方法。 此方法获取有关 tab 键顺序和选项卡式窗格中的选项卡名称的信息。  
  
##  <a name="a-namecanfloata--cbasetabbedpanecanfloat"></a><a name="canfloat"></a>CBaseTabbedPane::CanFloat  
 指定是否可以浮动选项卡式的窗格。  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格可以浮动;，否则为`FALSE`。  
  
##  <a name="a-namecansetcaptiontexttotabnamea--cbasetabbedpanecansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName  
 确定选项卡式窗格的标题是否应为活动选项卡显示相同的文本。  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果将选项卡式窗格中的标题文本设置为活动选项卡; 的文本否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 该方法用于确定是否显示的文本上的选项卡式的窗格标题重复项的标签的活动选项卡。 您可以启用或禁用此功能通过调用[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)。  
  
##  <a name="a-nameconverttotabbeddocumenta--cbasetabbedpaneconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument  
 将一个或多个可停靠窗格转换为 MDI 选项卡式文档。  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bActiveTabOnly`  
 当转换选项卡式窗格中时，指定`TRUE`转换仅活动选项卡。 指定`FALSE`要转换的窗格中的所有选项卡。  
  
##  <a name="a-namedetachpanea--cbasetabbedpanedetachpane"></a><a name="detachpane"></a>CBaseTabbedPane::DetachPane  
 分离一个窗格从选项卡式窗格。  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指针，指向分离窗格中。  
  
 [in] `bHide`  
 指定它分离之后，该框架是否隐藏窗格中的布尔型参数。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果框架成功分离窗格中;`FALSE`如果`pBar`是`NULL`或引用了不在选项卡式窗格中的窗格。  
  
### <a name="remarks"></a>备注  
 框架尽可能浮动分离窗格。 有关详细信息，请参阅[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。  
  
##  <a name="a-nameenablesetcaptiontexttotabnamea--cbasetabbedpaneenablesetcaptiontexttotabname"></a><a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName  
 启用或禁用选项卡式窗格中的活动选项卡上的标签文本同步标题文本的能力。  
  
```  
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要与活动选项卡标题; 同步的选项卡式的窗格标题否则为`FALSE`。  
  
##  <a name="a-namefilldefaulttabsorderarraya--cbasetabbedpanefilldefaulttabsorderarray"></a><a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray  
 将内部的 tab 键顺序还原到默认状态。  
  
```  
void FillDefaultTabsOrderArray();
```  
  
### <a name="remarks"></a>备注  
 在该框架将 Outlook 栏还原到初始状态时，调用此方法。  
  
##  <a name="a-namefindpanebyida--cbasetabbedpanefindpanebyid"></a><a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID  
 返回由窗格 ID 标识的窗格  
  
```  
virtual CWnd* FindPaneByID(UINT uBarID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uBarID`  
 指定要查找窗格中的 ID。  
  
### <a name="return-value"></a>返回值  
 指向如果它; 如果未找到窗格中的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 此方法将在窗格中的所有选项卡，并返回具有指定 ID 的一个`uBarID`参数。  
  
##  <a name="a-namefindbarbytabnumbera--cbasetabbedpanefindbarbytabnumber"></a><a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber  
 返回驻留在一个选项卡的窗格。  
  
```  
virtual CWnd* FindBarByTabNumber(
    int nTabNum,  
    BOOL bGetWrappedBar = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTabNum`  
 指定要检索的选项卡的从零开始索引。  
  
 [in] `bGetWrappedBar`  
 `TRUE`若要返回而不是重试。 窗格中窗格中的基础 （包装） 窗口否则为`FALSE`。 这仅适用于派生自的窗格[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)。  
  
### <a name="return-value"></a>返回值  
 如果找到窗格中，则返回到要搜索窗格中的有效指针;否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索位于指定的选项卡的窗格`nTabNum`参数。  
  
##  <a name="a-namefloattaba--cbasetabbedpanefloattab"></a><a name="floattab"></a>CBaseTabbedPane::FloatTab  
 仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pBar`  
 指向为浮点型窗格中的指针。  
  
 [in] `nTabID`  
 指定为 float 选项卡的从零开始索引。  
  
 [in] `dockMethod`  
 指定要用于使窗格浮动的方法。 有关详细信息，请参阅“备注”部分。  
  
 [in] `bHide`  
 `TRUE`若要在浮动; 之前隐藏窗格否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中浮动。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以浮动窗格当前所驻留的可拆分选项卡中。  
  
 如果您想要以编程方式分离窗格中，指定`DM_SHOW`为`dockMethod`参数。 如果您想要 float 以前浮动的同一位置中窗格中，指定`DM_DBL_CLICK`作为`dockMethod`参数。  
  
##  <a name="a-namegetdefaulttabsordera--cbasetabbedpanegetdefaulttabsorder"></a><a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder  
 在窗格中返回选项卡的默认顺序。  
  
```  
const CArray<int,int>& GetDefaultTabsOrder();
```  
  
### <a name="return-value"></a>返回值  
 一个`CArray`对象，它指定在窗格中的选项卡的默认顺序。  
  
### <a name="remarks"></a>备注  
 Outlook 栏重置为初始状态时，框架将调用此方法。  
  
##  <a name="a-namegetfirstvisibletaba--cbasetabbedpanegetfirstvisibletab"></a><a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab  
 检索指向第一个显示的选项卡。  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTabNum`  
 对整数的引用。 此方法将第一个显示的选项卡的从零开始索引写入此参数，则为-1 如果不需要显示选项卡上找到。  
  
### <a name="return-value"></a>返回值  
 如果成功，指向第一个显示选项卡;否则为`NULL`。  
  
##  <a name="a-namegetminsizea--cbasetabbedpanegetminsize"></a><a name="getminsize"></a>CBaseTabbedPane::GetMinSize  
 检索允许大小为窗格中的最小。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `size`  
 一个`CSize`用允许的大小的最小填充的对象。  
  
### <a name="remarks"></a>备注  
 如果最小窗格大小的统一管理处于活动状态 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，`size`用允许的活动选项卡大小的最小填充。 否则为`size`的返回值填充[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。  
  
##  <a name="a-namegetpaneicona--cbasetabbedpanegetpaneicon"></a><a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon  
 检索允许大小为窗格中的最小。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `size`  
 一个`CSize`用允许的大小的最小填充的对象。  
  
### <a name="remarks"></a>备注  
 如果最小窗格大小的统一管理处于活动状态 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，`size`用允许的活动选项卡大小的最小填充。 否则为`size`的返回值填充[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。  
  
##  <a name="a-namegetpanelista--cbasetabbedpanegetpanelist"></a><a name="getpanelist"></a>CBaseTabbedPane::GetPaneList  
 在选项卡式窗格中返回所包含的窗格的列表。  
  
```  
virtual void GetPaneList(
    CObList& lst,  
    CRuntimeClass* pRTCFilter = NULL);
```  
  
### <a name="parameters"></a>参数  
 [out] `lst`  
 一个`CObList`充满窗格，其中包含在选项卡式窗格中。  
  
 [in] `pRTCFilter`  
 如果不是`NULL`，返回的列表包含均属于指定的运行时类的窗格。  
  
##  <a name="a-namegettabareaa--cbasetabbedpanegettabarea"></a><a name="gettabarea"></a>CBaseTabbedPane::GetTabArea  
 返回的顶部和底部的选项卡区域的边界矩形。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>参数  
 [out] `rectTabAreaTop`  
 接收的上部选项卡区域的屏幕坐标。  
  
 [out] `rectTabAreaBottom`  
 接收较低的选项卡区域的屏幕坐标。  
  
### <a name="remarks"></a>备注  
 调用此方法来确定的上限和下限的选项卡区域的屏幕坐标中的边界矩形。  
  
##  <a name="a-namegettabsnuma--cbasetabbedpanegettabsnum"></a><a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum  
 在选项卡上的窗口中返回的选项卡的计数。  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>返回值  
 在选项卡式窗格中的选项卡的数目。  
  
##  <a name="a-namegetunderlyingwindowa--cbasetabbedpanegetunderlyingwindow"></a><a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow  
 获取基础 （包装） 选项卡窗口。  
  
```  
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```  
  
### <a name="return-value"></a>返回值  
 指向基础选项卡窗口的指针。  
  
##  <a name="a-namegetvisibletabsnuma--cbasetabbedpanegetvisibletabsnum"></a><a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum  
 返回可见选项卡的计数。  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>返回值  
 可见选项卡，将大于或等于零的数目。  
  
### <a name="remarks"></a>备注  
 调用此方法以确定在选项卡式窗格中可见选项卡的数目。  
  
##  <a name="a-namehasautohidemodea--cbasetabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode  
 确定选项卡式窗格是否可以切换为自动隐藏模式。  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中可以切换到自动隐藏模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果禁用了自动隐藏模式下，没有 pin 按钮将显示在选项卡式的窗格标题。  
  
##  <a name="a-nameishidesingletaba--cbasetabbedpaneishidesingletab"></a><a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab  
 确定是否选项卡式窗格中处于隐藏状态，如果只显示一个选项卡。  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果只有一个可见选项卡; 时未显示选项卡窗口否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果窗格中将不显示，因为只有一个选项卡处于打开状态，可以调用此方法以确定是否正常工作选项卡式窗格。  
  
##  <a name="a-nameremovepanea--cbasetabbedpaneremovepane"></a><a name="removepane"></a>CBaseTabbedPane::RemovePane  
 从选项卡式窗格中删除一个窗格。  
  
```  
virtual BOOL RemovePane(CWnd* pBar);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pBar`  
 指向删除选项卡式窗格中窗格中的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功从选项卡式窗格中删除窗格中，并且选项卡式窗格中是否仍然有效。 `FALSE`如果已从选项卡式窗格和选项卡式窗格中删除最后一个窗格，是即将销毁。 如果返回值是`FALSE`，不要再使用选项卡式窗格。  
  
### <a name="remarks"></a>备注  
 调用此方法以删除指定的窗格`pBar`从选项卡式窗格中的参数。  
  
##  <a name="a-namesetautodestroya--cbasetabbedpanesetautodestroy"></a><a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy  
 确定是否将自动销毁选项卡式的控件条。  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bAutoDestroy`  
 `TRUE`如果动态创建的选项卡式窗格中，您不控制其生命周期。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 设置自动销毁模式设置为`TRUE`如果动态创建选项卡式窗格中，并且您不控制其生存期。 如果自动销毁模式是`TRUE`，框架将自动销毁选项卡式的窗格。  
  
##  <a name="a-nameshowtaba--cbasetabbedpaneshowtab"></a><a name="showtab"></a>CBaseTabbedPane::ShowTab  
 显示或隐藏选项卡。  
  
```  
virtual BOOL ShowTab(
    CWnd* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向以显示或隐藏窗格中的指针。  
  
 [in] `bShow`  
 `TRUE`若要显示窗格;`FALSE`要隐藏窗格。  
  
 [in] `bDelay`  
 `TRUE`若要延迟的选项卡布局中; 调整否则为`FALSE`。  
  
 [in] `bActivate`  
 `TRUE`若要使活动选项卡; 选项卡否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果选项卡已显示或隐藏成功，则，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当调用此方法时，一个窗格所示，或者隐藏的具体取决于值`bShow`参数。 如果隐藏选项卡，并且它是基本选项卡窗口中的最后一个可见选项卡，则隐藏选项卡式窗格。 如果没有以前没有的选项卡可见时显示一个选项卡，将显示选项卡式窗格。  
  
##  <a name="a-namerecalclayouta--cbasetabbedpanerecalclayout"></a><a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout  
 重新计算窗格中的布局信息。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>备注  
 如果浮动的窗格中，此方法通知框架，以调整到最小化框架的当前大小窗格的大小。  
  
 如果停靠窗格中，此方法没有任何效果。  
  
##  <a name="a-namesetautohidemodea--cbasetabbedpanesetautohidemode"></a><a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode  
 在选项卡式窗格中的可插拔窗格的设置自动隐藏模式。  
  
```  
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bMode`  
 `TRUE`若要启用自动隐藏模式;`FALSE`若要启用正则停靠模式。  
  
 [in] `dwAlignment`  
 指定要创建自动隐藏窗格中的对齐方式。 有关可能的值的列表，请参阅[CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment)。  
  
 [in][out]`pCurrAutoHideBar`  
 指向当前自动隐藏工具栏上的指针。 可以是`NULL`。  
  
 [in] `bUseTimer`  
 指定是否使用自动隐藏效果，当用户切换窗格中，为自动隐藏模式，或立即隐藏窗格。  
  
### <a name="return-value"></a>返回值  
 切换到自动隐藏模式时创建的自动隐藏工具栏的指针或`NULL`如果创建没有工具栏。  
  
### <a name="remarks"></a>备注  
 当用户选择 pin 按钮以切换到自动隐藏模式或正则停靠模式下的选项卡式窗格中，框架将调用此方法。  
  
 自动隐藏模式设置为在选项卡式窗格中每个可插拔窗格中。 非可拆分的窗格将被忽略。 有关详细信息，请参阅[CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)。  
  
 调用此方法以编程方式切换到自动隐藏模式的选项卡式的窗格。 窗格中必须停靠到主框架窗口 ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider)必须返回到的有效指针[CPaneDivider](../../mfc/reference/cpanedivider-class.md))。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)

