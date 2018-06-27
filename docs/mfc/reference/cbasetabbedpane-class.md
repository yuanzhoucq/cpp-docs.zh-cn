---
title: CBaseTabbedPane 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
dev_langs:
- C++
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edb9fe1942f9fe8b462ce9fc6a56e37538866174
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954983"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane 类
扩展 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 的功能以支持创建选项卡式窗口。  
  
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
|[Cbasetabbedpane:: Addtab](#addtab)|将一个新选项卡添加到选项卡式窗格。|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可以销毁空的选项卡式的窗格。|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|将从注册表中，加载到选项卡式窗格的选项卡上设置应用。|  
|[CBaseTabbedPane::CanFloat](#canfloat)|确定是否可以浮动窗格。 (重写[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|确定选项卡式窗格的标题是否应显示为活动选项卡上的相同的文本。|  
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(重写[CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。)|  
|[Cbasetabbedpane:: Detachpane](#detachpane)|将一个或多个可停靠窗格转换为 MDI 选项卡式文档。|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|启用或禁用选项卡式窗格与活动选项卡上的标签文本同步标题文本的能力。|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|将内部 tab 键顺序还原为默认状态。|  
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|返回从零开始的选项卡索引标识选项卡位于选项卡中的窗格。|  
|||  
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|返回由窗格 ID 标识的窗格|  
|[Cbasetabbedpane:: Floattab](#floattab)|仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。|  
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|在窗格中返回选项卡的默认顺序。|  
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|检索指向第一个显示的选项卡。|  
|[CBaseTabbedPane::GetMinSize](#getminsize)|检索允许窗格的大小的最小。 (重写[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。)|  
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|返回窗格图标的句柄。 (重写[CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon)。)|  
|[CBaseTabbedPane::GetPaneList](#getpanelist)|在选项卡式窗格中返回包含的窗格的列表。|  
|[CBaseTabbedPane::GetTabArea](#gettabarea)|返回适用于顶部和底部的选项卡区域的边界矩形。|  
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|在选项卡窗口中返回的选项卡的计数。|  
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|获取基础 （包装） 选项卡窗口。|  
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|返回的显示选项卡的计数。|  
|[Cbasetabbedpane:: Hasautohidemode](#hasautohidemode)|确定是否可以将选项卡式的窗格切换到自动隐藏模式。|  
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|确定如果只显示一个选项卡是否隐藏选项卡式的窗格。|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|在序列化过程内部使用。|  
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|重新计算该窗格的布局信息。 (重写[cpane:: Recalclayout](../../mfc/reference/cpane-class.md#recalclayout)。)|  
|[CBaseTabbedPane::RemovePane](#removepane)|从选项卡式窗格中删除窗格。|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|在序列化过程内部使用。|  
|`CBaseTabbedPane::Serialize`|(重写[cdockablepane:: Serialize](http://msdn.microsoft.com/en-us/09787e59-e446-4e76-894b-206d303dcfd6)。)|  
|`CBaseTabbedPane::SerializeTabWindow`|在序列化过程内部使用。|  
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|确定是否将自动销毁选项卡式的控件条。|  
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|停靠的窗格之间显示的开关和自动隐藏模式。 (重写[CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)。)|  
|[CBaseTabbedPane::ShowTab](#showtab)|显示或隐藏选项卡。|  
  
## <a name="remarks"></a>备注  
 此类是一个抽象类，并不能实例化。 它实现所共有的所有类型的选项卡式窗格的服务。  
  
 目前，库包括两个选项卡式的窗格派生的类： [CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 A`CBaseTabbedPane`对象包装到指针[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)对象。 [CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)随后将成为子窗口的选项卡式窗格。  
  
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
 **标头：** afxBaseTabbedPane.h  
  
##  <a name="addtab"></a>  Cbasetabbedpane:: Addtab  
 将一个新选项卡添加到选项卡式窗格。  
  
```  
virtual BOOL AddTab(
    CWnd* pNewBar,  
    BOOL bVisible = TRUE,  
    BOOL bSetActive = TRUE,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in][out]*pNewBar*  
 指向添加窗格的指针。 此指针可能会变得无效后调用此方法。 有关详细信息，请参阅“备注”部分。  
  
 [in]*bVisible*  
 `TRUE` 若要使选项卡可见;否则为`FALSE`。  
  
 [in]*bSetActive*  
 `TRUE` 若要使活动选项卡; 的选项卡否则为`FALSE`。  
  
 [in]*bDetachable*  
 `TRUE` 若要使选项卡的可拆分;否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格已成功添加为一个选项卡，并已不在过程中会被销毁。 `FALSE` 如果要添加在窗格中，类型的对象`CBaseTabbedPane`。 有关详细信息，请参阅“备注”部分。  
  
### <a name="remarks"></a>备注  
 调用此方法以添加作为选项卡式窗格上的新选项卡的窗格。 如果*pNewBar*指向类型的对象`CBaseTabbedPane`，所有选项卡复制到选项卡式窗格，然后*pNewBar*被销毁。 因此， *pNewBar*变为无效指针和不应使用。  
  
##  <a name="allowdestroyemptytabbedpane"></a>  CBaseTabbedPane::AllowDestroyEmptyTabbedPane  
 指定是否可以销毁空的选项卡式的窗格。  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果可以销毁空的选项卡式的窗格;否则为`FALSE`。 默认实现始终返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 如果不允许空的选项卡式窗格中，将其销毁，框架隐藏窗格。  
  
##  <a name="applyrestoredtabinfo"></a>  CBaseTabbedPane::ApplyRestoredTabInfo  
 从注册表加载选项卡上设置并将其应用到选项卡式窗格。  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bUseTabIndexes*  
 框架内部使用此参数。  
  
### <a name="remarks"></a>备注  
 重新加载注册表中的停靠状态信息时，将由框架调用此方法。 此方法获取有关 tab 键顺序和选项卡式窗格的选项卡名称的信息。  
  
##  <a name="canfloat"></a>  CBaseTabbedPane::CanFloat  
 指定是否可以浮动选项卡式的窗格。  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格可以浮动;，否则为`FALSE`。  
  
##  <a name="cansetcaptiontexttotabname"></a>  CBaseTabbedPane::CanSetCaptionTextToTabName  
 确定选项卡式窗格的标题是否应显示为活动选项卡上的相同的文本。  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果选项卡式窗格的标题文本设置为活动选项卡; 的文本否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 该方法用于确定是否显示的文本上选项卡式的窗格标题重复项的活动选项卡标签。你可以启用或禁用此功能通过调用[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)。  
  
##  <a name="converttotabbeddocument"></a>  CBaseTabbedPane::ConvertToTabbedDocument  
 将一个或多个可停靠窗格转换为 MDI 选项卡式文档。  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bActiveTabOnly*  
 在转换选项卡式的窗格时，指定`TRUE`要转换仅是活动的选项卡。指定`FALSE`要转换的窗格中的所有选项卡。  
  
##  <a name="detachpane"></a>  Cbasetabbedpane:: Detachpane  
 分离从选项卡式窗格中的窗格。  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in]*pBar*  
 指向要分离的窗格的指针。  
  
 [in]*bHide*  
 布尔参数可指定它分离之后，框架是否隐藏窗格。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果框架成功分离窗格;`FALSE`如果*pBar*是`NULL`指不在选项卡式窗格中的窗格。  
  
### <a name="remarks"></a>备注  
 框架尽可能浮动分离窗格。 有关详细信息，请参阅[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。  
  
##  <a name="enablesetcaptiontexttotabname"></a>  CBaseTabbedPane::EnableSetCaptionTextToTabName  
 启用或禁用选项卡式窗格与活动选项卡上的标签文本同步标题文本的能力。  
  
```  
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in]*bEnable*  
 `TRUE` 若要与活动选项卡标题; 同步选项卡式的窗格标题否则为`FALSE`。  
  
##  <a name="filldefaulttabsorderarray"></a>  CBaseTabbedPane::FillDefaultTabsOrderArray  
 将内部 tab 键顺序还原为默认状态。  
  
```  
void FillDefaultTabsOrderArray();
```  
  
### <a name="remarks"></a>备注  
 框架将 Outlook 栏还原到初始状态时调用此方法。  
  
##  <a name="findpanebyid"></a>  CBaseTabbedPane::FindPaneByID  
 返回由窗格 ID 标识的窗格  
  
```  
virtual CWnd* FindPaneByID(UINT uBarID);
```  
  
### <a name="parameters"></a>参数  
 [in]*uBarID*  
 指定要查找的窗格中的 ID。  
  
### <a name="return-value"></a>返回值  
 指向的窗格中，如果它; 如果未找到否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 此方法将在窗格中的所有选项卡，并返回一个具有指定 ID *uBarID*参数。  
  
##  <a name="findbarbytabnumber"></a>  CBaseTabbedPane::FindBarByTabNumber  
 返回位于选项卡的窗格。  
  
```  
virtual CWnd* FindBarByTabNumber(
    int nTabNum,  
    BOOL bGetWrappedBar = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in]*nTabNum*  
 指定要检索的选项卡的从零开始索引。  
  
 [in]*bGetWrappedBar*  
 `TRUE` 若要返回的而不是窗格本身; 窗格基础 （包装） 的窗口否则为`FALSE`。 这仅适用于派生自的窗格[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)。  
  
### <a name="return-value"></a>返回值  
 如果找到窗格中，则返回指向要搜索的窗格中的有效指针;否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索位于指定的选项卡的窗格*nTabNum*参数。  
  
##  <a name="floattab"></a>  Cbasetabbedpane:: Floattab  
 仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in][out]*pBar*  
 指向为浮动窗格的指针。  
  
 [in]*nTabID*  
 指定为浮动选项卡的从零开始索引。  
  
 [in]*dockMethod*  
 指定要使用可使窗格浮动的方法。 有关详细信息，请参阅“备注”部分。  
  
 [in]*bHide*  
 `TRUE` 若要隐藏浮点; 之前的窗格否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格浮动;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以 float 当前驻留在拆离的选项卡的窗格。  
  
 如果你想要以编程方式分离窗格中，指定`DM_SHOW`为*dockMethod*参数。 如果你想要 float 浮动以前的相同位置中的窗格中，指定`DM_DBL_CLICK`作为*dockMethod*参数。  
  
##  <a name="getdefaulttabsorder"></a>  CBaseTabbedPane::GetDefaultTabsOrder  
 在窗格中返回选项卡的默认顺序。  
  
```  
const CArray<int,int>& GetDefaultTabsOrder();
```  
  
### <a name="return-value"></a>返回值  
 A`CArray`指定选项卡的默认顺序窗格中的对象。  
  
### <a name="remarks"></a>备注  
 Outlook 栏重置为初始状态时，框架将调用此方法。  
  
##  <a name="getfirstvisibletab"></a>  CBaseTabbedPane::GetFirstVisibleTab  
 检索指向第一个显示的选项卡。  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>参数  
 [in]*iTabNum*  
 对整数的引用。 此方法将第一个显示的选项卡的从零开始索引写入此参数，则为-1 如果未显示找到选项卡。  
  
### <a name="return-value"></a>返回值  
 如果成功，指向第一个显示的选项卡;否则为`NULL`。  
  
##  <a name="getminsize"></a>  CBaseTabbedPane::GetMinSize  
 检索允许窗格的大小的最小。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>参数  
 [out]*大小*  
 A`CSize`填入允许大小的最小的对象。  
  
### <a name="remarks"></a>备注  
 如果最小窗格大小的统一管理处于活动状态 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，*大小*填入允许活动选项卡大小的最小。否则为*大小*的返回值填充[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。  
  
##  <a name="getpaneicon"></a>  CBaseTabbedPane::GetPaneIcon  
 检索允许窗格的大小的最小。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>参数  
 [out]*大小*  
 A`CSize`填入允许大小的最小的对象。  
  
### <a name="remarks"></a>备注  
 如果最小窗格大小的统一管理处于活动状态 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，*大小*填入允许活动选项卡大小的最小。否则为*大小*的返回值填充[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。  
  
##  <a name="getpanelist"></a>  CBaseTabbedPane::GetPaneList  
 在选项卡式窗格中返回包含的窗格的列表。  
  
```  
virtual void GetPaneList(
    CObList& lst,  
    CRuntimeClass* pRTCFilter = NULL);
```  
  
### <a name="parameters"></a>参数  
 [out]*lst*  
 A`CObList`充满选项卡式窗格中包含的窗格。  
  
 [in]*pRTCFilter*  
 如果不是`NULL`，返回的列表包含属于指定的运行时类的窗格。  
  
##  <a name="gettabarea"></a>  CBaseTabbedPane::GetTabArea  
 返回适用于顶部和底部的选项卡区域的边界矩形。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>参数  
 [out]*rectTabAreaTop*  
 接收左上的选项卡区域的屏幕坐标。  
  
 [out]*rectTabAreaBottom*  
 接收较低的选项卡区域的屏幕坐标。  
  
### <a name="remarks"></a>备注  
 调用此方法以确定在屏幕坐标中，适用于的上限和下限的选项卡区域的边界矩形。  
  
##  <a name="gettabsnum"></a>  CBaseTabbedPane::GetTabsNum  
 在选项卡窗口中返回的选项卡的计数。  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>返回值  
 在选项卡式窗格中的选项卡的数目。  
  
##  <a name="getunderlyingwindow"></a>  CBaseTabbedPane::GetUnderlyingWindow  
 获取基础 （包装） 选项卡窗口。  
  
```  
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```  
  
### <a name="return-value"></a>返回值  
 指向基础的选项卡窗口的指针。  
  
##  <a name="getvisibletabsnum"></a>  CBaseTabbedPane::GetVisibleTabsNum  
 返回可见选项卡的计数。  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>返回值  
 可见选项卡，将大于或等于零的数目。  
  
### <a name="remarks"></a>备注  
 调用此方法以确定在选项卡式窗格中的可见选项卡的数目。  
  
##  <a name="hasautohidemode"></a>  Cbasetabbedpane:: Hasautohidemode  
 确定选项卡式窗格是否可以切换为自动隐藏模式。  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格可以切换为自动隐藏模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果禁用自动隐藏模式，则没有 pin 按钮被显示在选项卡式的窗格标题。  
  
##  <a name="ishidesingletab"></a>  CBaseTabbedPane::IsHideSingleTab  
 确定如果只显示一个选项卡是否隐藏选项卡式的窗格。  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果只有一个可见选项卡; 时不会显示选项卡窗口否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果因为只有一个选项卡处于打开状态，不显示的窗格，可以调用此方法以确定是否选项卡式的窗格是否正常工作。  
  
##  <a name="removepane"></a>  CBaseTabbedPane::RemovePane  
 从选项卡式窗格中删除窗格。  
  
```  
virtual BOOL RemovePane(CWnd* pBar);
```  
  
### <a name="parameters"></a>参数  
 [in][out]*pBar*  
 指向窗格从选项卡式窗格中移除的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果已成功从选项卡式窗格中删除窗格，和选项卡式的窗格是否仍然有效。 `FALSE` 如果从选项卡式的窗格和选项卡式的窗格中删除的最后一个窗格，是即将销毁。 如果返回值为`FALSE`，更不使用选项卡式的窗格。  
  
### <a name="remarks"></a>备注  
 调用此方法以删除指定的窗格*pBar*从选项卡式窗格中的参数。  
  
##  <a name="setautodestroy"></a>  CBaseTabbedPane::SetAutoDestroy  
 确定是否将自动销毁选项卡式的控件条。  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bAutoDestroy*  
 `TRUE` 如果动态创建选项卡式窗格中，并且您不控制其生命周期。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 设置自动销毁模式设置为`TRUE`如果动态创建选项卡式窗格中，并且您不控制其生存期。 如果自动销毁模式是`TRUE`，将被框架自动销毁选项卡式的窗格。  
  
##  <a name="showtab"></a>  CBaseTabbedPane::ShowTab  
 显示或隐藏选项卡。  
  
```  
virtual BOOL ShowTab(
    CWnd* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>参数  
 [in]*pBar*  
 指向以显示或隐藏的窗格的指针。  
  
 [in]*bShow*  
 `TRUE` 若要显示窗格;`FALSE`若要隐藏窗格。  
  
 [in]*bDelay*  
 `TRUE` 对延迟的选项卡布局; 调整否则为`FALSE`。  
  
 [in]*bActivate*  
 `TRUE` 若要使活动选项卡; 的选项卡否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果选项卡已显示或隐藏成功，则，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在调用此方法时，一个窗格所示，或者隐藏，具体取决于值*bShow*参数。 如果隐藏选项卡，并且它是基础的选项卡窗口中的最后一个可见选项卡，则会隐藏选项卡式的窗格。 如果没有以前没有选项卡可见时显示一个选项卡，将显示选项卡式的窗格。  
  
##  <a name="recalclayout"></a>  CBaseTabbedPane::RecalcLayout  
 重新计算该窗格的布局信息。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>备注  
 如果窗格浮动的此方法会通知框架，若要调整大小的微型框架的当前大小的窗格。  
  
 如果窗格停靠，则此方法没有任何影响。  
  
##  <a name="setautohidemode"></a>  CBaseTabbedPane::SetAutoHideMode  
 在选项卡式窗格中的可插拔窗格的设置自动隐藏模式。  
  
```  
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bMode*  
 `TRUE` 若要启用自动隐藏模式;`FALSE`若要启用正则停靠模式。  
  
 [in]*dwAlignment*  
 指定要创建的自动隐藏窗格中的对齐方式。 有关可能的值的列表，请参阅[CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment)。  
  
 [in][out]*pCurrAutoHideBar*  
 指向当前的自动隐藏工具栏的指针。 可以是`NULL`。  
  
 [in]*bUseTimer*  
 指定是否若要使用自动隐藏效果，当用户切换为自动隐藏模式下，窗格中，或若要立即隐藏窗格。  
  
### <a name="return-value"></a>返回值  
 指向自动隐藏工具栏切换为自动隐藏模式时创建的或`NULL`如果创建没有工具栏。  
  
### <a name="remarks"></a>备注  
 当用户选择 pin 按钮以切换到自动隐藏模式或正则停靠模式的选项卡式的窗格，框架将调用此方法。  
  
 自动隐藏模式设置为在选项卡式窗格中的每个可拆分窗格中。 是非可拆分的窗格将被忽略。 有关详细信息，请参阅[CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)。  
  
 调用此方法以编程方式切换到自动隐藏模式的选项卡式的窗格。 必须将窗格停靠到主框架窗口 ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider)必须返回到的有效指针[CPaneDivider](../../mfc/reference/cpanedivider-class.md))。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)
