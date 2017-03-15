---
title: "CMFCOutlookBarPane 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCOutlookBarPane
dev_langs:
- C++
helpviewer_keywords:
- Dock method
- IsChangeState method
- SmartUpdate method
- OnBeforeFloat method
- RestoreOriginalstate method
- CMFCOutlookBarPane class
- CanBeRestored method
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
caps.latest.revision: 30
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
ms.openlocfilehash: da4fab1a6d94e962090f21414062dc2da0c9482c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane 类
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 派生的控件[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)，可以插入到 Outlook 栏 ( [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md))。 Outlook 栏窗格包含一列大按钮。 如果按钮列表大于窗格，用户可以上下滚动按钮列表。 当用户将 Outlook 栏中的一个窗格与 Outlook 栏分离时，此窗格可以浮动或停靠在主框架窗口中。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCOutlookBarPane : public CMFCToolBar  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|默认构造函数。|  
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCOutlookBarPane::AddButton](#addbutton)|将按钮添加到 Outlook 栏窗格。|  
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|确定是否可以到另一个窗格或框架窗口中停靠窗格。 (重写[CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached)。)|  
|`CMFCOutlookBarPane::CanBeRestored`|确定是否系统工具栏为其原始状态后还原自定义项。 (重写[CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。)|  
|[CMFCOutlookBarPane::ClearAll](#clearall)|释放由 Outlook 栏窗格中的图像的资源。|  
|[CMFCOutlookBarPane::Create](#create)|创建 Outlook 栏窗格。|  
|`CMFCOutlookBarPane::CreateObject`|由框架用于创建此类类型的动态实例。|  
|`CMFCOutlookBarPane::Dock`|由框架后，若要将 Outlook 栏窗格停靠调用。 （重写 `CPane::Dock`。）|  
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|指定是否在 Outlook 栏窗格上的滚动箭头前进按钮列表通过页上，或按钮。|  
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|返回 Outlook 栏窗格的常规 （非选中状态） 的文本颜色。|  
|`CMFCOutlookBarPane::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|确定是否加载 Outlook 栏窗格的背景图像。|  
|`CMFCOutlookBarPane::IsChangeState`|确定是否可以停靠浮动窗格。 （重写 `CPane::IsChangeState`。）|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|确定当按钮将突出显示，并且显示背景图像按钮边框是否为灰显。|  
|`CMFCOutlookBarPane::OnBeforeFloat`|当一个窗格处于有关为浮点数，由框架调用。 (重写[CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)。)|  
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|删除具有指定的命令 ID 的按钮|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|还原工具栏的原始状态。 (重写[CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)。)|  
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|设置背景色。|  
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|设置背景图像。|  
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|将 Outlook 栏窗格重置为按钮的原始设置。|  
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|设置在 Outlook 栏窗格中的按钮周围所用填充的像素数。|  
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Outlook 栏窗格中设置的常规和突出显示文本的颜色。|  
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|设置 Outlook 栏窗格的透明颜色。|  
|`CMFCOutlookBarPane::SmartUpdate`|内部使用，以更新 Outlook 栏。 （重写 `CMFCToolBar::SmartUpdate`。）|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|指定的快捷菜单项显示在自定义模式。|  
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|从 Outlook 栏窗格中删除所有按钮。 (重写[CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons)。)|  
  
## <a name="remarks"></a>备注  
 有关如何实现 Outlook 栏的信息，请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 Outlook 栏的示例，请参阅 OutlookDemo 示例项目。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCOutlookBarPane`类。 该示例演示如何创建 Outlook 栏窗格、 启用页滚动模式、 启用停靠，和设置 Outlook 栏的背景色。 此代码段属于[Outlook 多视图示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews #&3;](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews #&4;](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxoutlookbarpane.h  
  
##  <a name="a-nameaddbuttona--cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a>CMFCOutlookBarPane::AddButton  
 将按钮添加到 Outlook 栏窗格。  
  
```  
BOOL AddButton(
    UINT uiImage,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    UINT uiImage,  
    UINT uiLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    LPCTSTR szBmpFileName,  
    LPCTSTR szLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HBITMAP hBmp,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HICON hIcon,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1,  
    BOOL bAlphaBlend=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiImage`  
 指定位图的资源标识符。  
  
 [in] `lpszLabel`  
 指定按钮的文本。  
  
 [in] `iIdCommand`  
 指定按钮控件的 id。  
  
 [in] `iInsertAt`  
 在插入按钮从该处的 outlook 栏页上指定的从零开始的索引。  
  
 [in] `uiLabel`  
 字符串的资源 id。  
  
 [in] `szBmpFileName`  
 指定要加载的磁盘映像文件的名称。  
  
 [in] `szLabel`  
 指定按钮的文本。  
  
 [in] `hBmp`  
 指向一个按钮的位图的句柄。  
  
 [in] `hIcon`  
 为按钮的图标的句柄。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则添加一个按钮否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法用于 Outlook 栏的页面中插入一个新按钮。 从应用程序资源或磁盘文件，可以加载按钮的图像。  
  
 如果由指定的页 ID`uiPageID`为-1，按钮插入的第一页。  
  
 如果指定的索引`iInsertAt`为-1，按钮将添加到页面的末尾。  
  
##  <a name="a-namecanbeattacheda--cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameclearalla--cmfcoutlookbarpaneclearall"></a><a name="clearall"></a>CMFCOutlookBarPane::ClearAll  
 释放由 Outlook 栏窗格上的图像的资源。  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>备注  
 此方法直接调用[CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear)，该存储过程调用上使用 Outlook 栏窗格的映像。  
  
##  <a name="a-namecreatea--cmfcoutlookbarpanecreate"></a><a name="create"></a>CMFCOutlookBarPane::Create  
 创建 Outlook 栏窗格。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT uiID=(UINT)-1,  
    DWORD dwControlBarStyle=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParentWnd`  
 指定 Outlook 栏窗格控件的父窗口。 不得为 `NULL`。  
  
 [in] `dwStyle`  
 窗口样式。  窗口样式的列表，请参阅[窗口样式](../../mfc/reference/window-styles.md)。  
  
 [in] `uiID`  
 控件 id。 必须是唯一的以使保存的控件的状态。  
  
 [in] `dwControlBarStyle`  
 指定定义 Outlook 栏窗格控件的行为，从 Outlook 栏分离时的特殊样式。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 若要构造`CMFCOutlookBarPane`对象，第一次调用构造函数中，，然后调用`Create`，它创建 Outlook 栏窗格控件并将其附加到`CMFCOutlookBarPane`对象。  
  
 有关详细信息`dwControlBarStyle`请参阅[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。  
  
##  <a name="a-nameenablecontextmenuitemsa--cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems  
 指定的快捷菜单项显示在自定义模式。  
  
```  
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,  
    CMenu* pPopup);
```  
  
### <a name="parameters"></a>参数  
 [in] `pButton`  
 指向用户单击一个工具栏按钮的指针。  
  
 [in] `pPopup`  
 快捷菜单上指向的指针。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`快捷菜单上应显示; 否则为如果`FALSE`。  
  
### <a name="remarks"></a>备注  
 重写此方法来修改框架在自定义模式下显示的 framework 标准的快捷菜单。  
  
 默认实现可检查自定义模式 ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))，如果设置为`TRUE`，禁用所有快捷方式菜单项，但**删除**。 然后，它只是将传递的输入的参数`CMFCToolBar::EnableContextMenuItems`。  
  
> [!NOTE]
> *上下文菜单*是快捷菜单上的同义词。  
  
##  <a name="a-nameenablepagescrollmodea--cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode  
 指定是否在 Outlook 栏窗格上的滚动箭头前进按钮按页或按钮的按钮的列表。  
  
```  
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bPageScroll`  
 如果`TRUE`，启用页滚动模式。 如果`FALSE`，禁用页滚动模式。  
  
##  <a name="a-namegetregularcolora--cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a>CMFCOutlookBarPane::GetRegularColor  
 返回常规 (即，未选中) 的 Outlook 栏窗格的文本颜色。  
  
```  
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前为 RGB 颜色值的文本颜色。  
  
### <a name="remarks"></a>备注  
 使用[CMFCOutlookBarPane::SetTextColor](#settextcolor)设置 Outlook 栏的当前 （常规和所选） 的文本颜色。 通过调用获取默认文本颜色[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)起作用`COLOR_WINDOW`索引。  
  
##  <a name="a-nameisbackgroundtexturea--cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a>CMFCOutlookBarPane::IsBackgroundTexture  
 确定是否加载 Outlook 栏窗格的背景图像。  
  
```  
BOOL IsBackgroundTexture() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果没有要显示; 的背景图像否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 可以通过调用添加背景图像[CMFCOutlookBarPane::SetBackImage](#setbackimage)函数。  
  
 如果没有背景图像，与通过使用指定的颜色绘制背景[CMFCOutlookBarPane::SetBackColor](#setbackcolor)。  
  
##  <a name="a-nameisdrawshadedhighlighta--cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight  
 确定当按钮将突出显示，并且显示背景图像按钮边框是否为灰显。  
  
```  
BOOL IsDrawShadedHighlight() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果按钮的边框灰显;否则为`FALSE`。  
  
##  <a name="a-nameremoveallbuttonsa--cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCOutlookBarPane::RemoveAllButtons  
 从 Outlook 栏窗格中删除所有按钮。  
  
```  
virtual void RemoveAllButtons();
```  
  
##  <a name="a-nameremovebuttona--cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a>CMFCOutlookBarPane::RemoveButton  
 删除具有指定的命令 ID 的按钮  
  
```  
BOOL RemoveButton(UINT iIdCommand);
```  
  
### <a name="parameters"></a>参数  
 [in] `iIdCommand`  
 指定要删除一个按钮的命令 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功移除了按钮;`FALSE`如果指定的命令 ID 无效。  
  
##  <a name="a-namesetbackcolora--cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a>CMFCOutlookBarPane::SetBackColor  
 设置 Outlook 栏的背景色。  
  
```  
void SetBackColor(COLORREF color);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 指定新的背景色。  
  
### <a name="remarks"></a>备注  
 调用此函数可设置 Outlook 栏的当前背景色。 只有在没有背景图像，使用的背景颜色。  
  
##  <a name="a-namesetbackimagea--cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a>CMFCOutlookBarPane::SetBackImage  
 设置背景图像。  
  
```  
void SetBackImage(UINT uiImageID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiImageID`  
 指定图像的资源 id。  
  
### <a name="remarks"></a>备注  
 调用此方法可设置 Outlook 栏的背景图像。 托管的背景图像的列表由嵌入[CMFCToolBarImages 类](../../mfc/reference/cmfctoolbarimages-class.md)对象。  
  
##  <a name="a-namesetdefaultstatea--cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a>CMFCOutlookBarPane::SetDefaultState  
 将 Outlook 栏窗格重置为按钮的原始设置。  
  
```  
void SetDefaultState();
```  
  
### <a name="remarks"></a>备注  
 此方法将 Outlook 栏按钮还原为原始集。 此方法就像`CMFCOutlookBarPane::RestoreOriginalstate`，只不过它不会触发 Outlook 栏窗格重绘。  
  
##  <a name="a-namesetextraspacea--cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a>CMFCOutlookBarPane::SetExtraSpace  
 设置在 Outlook 栏窗格中的按钮周围所用填充的像素数。  
  
```  
void SetExtraSpace()  
```  
  
##  <a name="a-namesettextcolora--cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a>CMFCOutlookBarPane::SetTextColor  
 Outlook 栏窗格中设置的常规和突出显示文本的颜色。  
  
```  
void SetTextColor(
    COLORREF clrRegText,  
    COLORREF clrSelText=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `clrRegText`  
 指定未选定文本的新颜色。  
  
 [in] `clrSelText`  
 指定所选文本的新颜色。  
  
##  <a name="a-namesettransparentcolora--cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a>CMFCOutlookBarPane::SetTransparentColor  
 设置 Outlook 栏窗格的透明颜色。  
  
```  
void SetTransparentColor(COLORREF color);
```  
  
### <a name="parameters"></a>参数  
 `color`  
 指定新的透明颜色。  
  
### <a name="remarks"></a>备注  
 显示透明图像所需的透明颜色。 此颜色在映像中的所有事件，而被都绘制背景色。  没有任何混合的前景色和背景图像。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

