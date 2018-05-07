---
title: CMFCBaseVisualManager 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawCheckBox
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboBorder
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboDropButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawPushButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawRadioButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawStatusBarProgress
- AFXVISUALMANAGER/CMFCBaseVisualManager::FillReBarPane
- AFXVISUALMANAGER/CMFCBaseVisualManager::GetStandardWindowsTheme
- AFXVISUALMANAGER/CMFCBaseVisualManager::CleanUpThemes
- AFXVISUALMANAGER/CMFCBaseVisualManager::UpdateSystemColors
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseVisualManager [MFC], CMFCBaseVisualManager
- CMFCBaseVisualManager [MFC], DrawCheckBox
- CMFCBaseVisualManager [MFC], DrawComboBorder
- CMFCBaseVisualManager [MFC], DrawComboDropButton
- CMFCBaseVisualManager [MFC], DrawPushButton
- CMFCBaseVisualManager [MFC], DrawRadioButton
- CMFCBaseVisualManager [MFC], DrawStatusBarProgress
- CMFCBaseVisualManager [MFC], FillReBarPane
- CMFCBaseVisualManager [MFC], GetStandardWindowsTheme
- CMFCBaseVisualManager [MFC], CleanUpThemes
- CMFCBaseVisualManager [MFC], UpdateSystemColors
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 496c6905276e789a72c55db1835187b0d4ab342a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager 类
派生的视觉管理器和 Windows 主题 API 之间的一层。  
  
 `CMFCBaseVisualManager` 如果可用，加载 UxTheme.dll，并管理对 Windows 主题 API 方法的访问。  
  
 此类是仅供内部使用。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCBaseVisualManager: public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|构造并初始化一个 `CMFCBaseVisualManager` 对象。|  
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|通过使用当前的 Windows 主题绘制复选框控件。|  
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|绘制使用当前的 Windows 主题的组合框边框。|  
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|绘制组合框下拉按钮使用当前的 Windows 主题。|  
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|绘制压按钮使用当前的 Windows 主题。|  
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|通过使用当前的 Windows 主题绘制单选按钮控件。|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|在状态栏控件上绘制一个进度栏 ( [CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)) 使用当前的 Windows 主题。|  
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|通过使用当前的 Windows 主题填充 rebar 控件的背景。|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|获取当前的 Windows 主题。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|调用`CloseThemeData`中获得所有句柄`UpdateSystemColors`。|  
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|调用`OpenThemeData`以获取用于绘制各种控件的句柄： windows、 工具栏、 按钮和等等。|  
  
## <a name="remarks"></a>备注  
 无需直接实例化此类的对象。  
  
 因为它是所有视觉管理器的基类，可以直接调用[CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance)、 获取指针到当前 Visual 管理器，以及访问的方法`CMFCBaseVisualManager`使用该指针。 但是，如果你必须通过使用当前的 Windows 主题显示控件，则最好使用`CMFCVisualManagerWindows`接口。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxvisualmanager.h  
  
##  <a name="cleanupthemes"></a>  CMFCBaseVisualManager::CleanUpThemes  
 调用`CloseThemeData`中获得所有句柄`UpdateSystemColors`。  
  
```  
void CleanUpThemes();
```  
  
### <a name="remarks"></a>备注  
 仅限内部使用。  
  
##  <a name="cmfcbasevisualmanager"></a>  CMFCBaseVisualManager::CMFCBaseVisualManager  
 构造并初始化一个 `CMFCBaseVisualManager` 对象。  
  
```  
CMFCBaseVisualManager();
```  
  
##  <a name="drawcheckbox"></a>  CMFCBaseVisualManager::DrawCheckBox  
 通过使用当前的 Windows 主题绘制复选框控件。  
  
```  
virtual BOOL DrawCheckBox(
    CDC* pDC,   
    CRect rect,   
    BOOL bHighlighted,   
    int nState,   
    BOOL bEnabled,   
    BOOL bPressed);

);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文  
  
 [in] `rect`  
 复选框的绑定矩形。  
  
 [in] `bHighlighted`  
 指定是否将突出显示复选框。  
  
 [in] `nState`  
 0 用于检查正常、 未选中，1  
  
 如混合的常规 2。  
  
 [in] `bEnabled`  
 指定是否启用复选框。  
  
 [in] `bPressed`  
 指定是否按下了复选框。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果启用了主题 API;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 值`nState`对应于以下的复选框样式。  
  
|nState|复选框样式|  
|------------|---------------------|  
|0|CBS_UNCHECKEDNORMAL|  
|1|CBS_CHECKEDNORMAL|  
|2|CBS_MIXEDNORMAL|  
  
##  <a name="drawcomboborder"></a>  CMFCBaseVisualManager::DrawComboBorder  
 绘制使用当前的 Windows 主题的组合框边框。  
  
```  
virtual BOOL DrawComboBorder(
    CDC* pDC,   
    CRect rect,   
    BOOL bDisabled,   
    BOOL bIsDropped,   
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 组合框边框的绑定矩形。  
  
 [in] `bDisabled`  
 指定是否禁用组合框边框。  
  
 [in] `bIsDropped`  
 指定是否向下删除组合框边框。  
  
 [in] `bIsHighlighted`  
 指定组合框边框会突出显示。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果启用了主题 API;否则为`FALSE`。  
  
##  <a name="drawcombodropbutton"></a>  CMFCBaseVisualManager::DrawComboDropButton  
 绘制组合框下拉按钮使用当前的 Windows 主题。  
  
```  
virtual BOOL DrawComboDropButton(
    CDC* pDC,   
    CRect rect,   
    BOOL bDisabled,   
    BOOL bIsDropped,   
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `pDC`|一个指向设备上下文的指针。|  
|[in] `rect`|组合框下拉按钮的边框。|  
|[in] `bDisabled`|指定组合框下拉按钮是否已禁用。|  
|[in] `bIsDropped`|指定是否向下删除组合框下拉按钮。|  
|[in] `bIsHighlighted`|指定组合框下拉按钮将突出显示。|  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果启用了主题 API;否则为`FALSE`。  
  
##  <a name="drawpushbutton"></a>  CMFCBaseVisualManager::DrawPushButton  
 绘制压按钮使用当前的 Windows 主题。  
  
```  
virtual BOOL DrawPushButton(
    CDC* pDC,   
    CRect rect,   
    CMFCButton* pButton,   
    UINT uiState);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 推送按钮的边框。  
  
 [in] `pButton`  
 指向的指针[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)要绘制的对象。  
  
 [in] `uiState`  
 已忽略。 状态取自`pButton`。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果启用了主题 API;否则为`FALSE`。  
  
##  <a name="drawradiobutton"></a>  CMFCBaseVisualManager::DrawRadioButton  
 通过使用当前的 Windows 主题绘制单选按钮控件。  
  
```  
virtual BOOL DrawRadioButton(
    CDC* pDC,   
    CRect rect,   
    BOOL bHighlighted,   
    BOOL bChecked,   
    BOOL bEnabled,   
    BOOL bPressed);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 单选按钮的边框。  
  
 [in] `bHighlighted`  
 指定的单选按钮将突出显示。  
  
 [in] `bChecked`  
 指定是否已选中的单选按钮。  
  
 [in] `bEnabled`  
 指定是否启用单选按钮。  
  
 [in] `bPressed`  
 指定是否按下了单选按钮。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果启用了主题 API;否则为`FALSE`。  
  
##  <a name="drawstatusbarprogress"></a>  CMFCBaseVisualManager::DrawStatusBarProgress  
 在状态栏控件上绘制进度栏 ( [CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)) 使用当前的 Windows 主题。  
  
```  
virtual BOOL DrawStatusBarProgress(
    CDC* pDC,   
    CMFCStatusBar* pStatusBar,   
    CRect rectProgress,   
    int nProgressTotal,   
    int nProgressCurr,  
    COLORREF clrBar,   
    COLORREF clrProgressBarDest,   
    COLORREF clrProgressText,   
    BOOL bProgressText);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pStatusBar`  
 指向状态栏的指针。 忽略此值。  
  
 [in] `rectProgress`  
 中的进度栏的边框`pDC`坐标。  
  
 [in] `nProgressTotal`  
 总进度值。  
  
 [in] `nProgressCurr`  
 当前的进度值。  
  
 [in] `clrBar`  
 开始颜色。 `CMFCBaseVisualManager` 将忽略这种情况。 派生的类可以使用它的颜色渐变。  
  
 [in] `clrProgressBarDest`  
 结束颜色。 `CMFCBaseVisualManager` 将忽略这种情况。 派生的类可以使用它的颜色渐变。  
  
 [in] `clrProgressText`  
 进度的文本颜色。 `CMFCBaseVisualManager` 将忽略这种情况。 由定义的文本颜色`afxGlobalData.clrBtnText`。  
  
 [in] `bProgressText`  
 指定是否显示进度的文本。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果启用了主题 API;否则为`FALSE`。  
  
##  <a name="fillrebarpane"></a>  CMFCBaseVisualManager::FillReBarPane  
 通过使用当前的 Windows 主题填充 rebar 控件的背景。  
  
```  
virtual void FillReBarPane(
    CDC* pDC,   
    CBasePane* pBar,   
    CRect rectClient);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pBar`  
 指向应绘制其背景的窗格的指针。  
  
 [in] `rectClient`  
 要填充的区域边界的矩形。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果启用了主题 API;否则为`FALSE`。  
  
##  <a name="getstandardwindowstheme"></a>  CMFCBaseVisualManager::GetStandardWindowsTheme  
 获取当前的 Windows 主题。  
  
```  
virtual WinXpTheme GetStandardWindowsTheme();
```  
  
### <a name="return-value"></a>返回值  
 当前所选的 Windows 主题颜色。 可以是下列枚举值之一：  
  
- `WinXpTheme_None` -没有启用无主题。  
  
- `WinXpTheme_NonStandard` -非标准主题选择 （这意味着选择一个主题，但无从下面的列表）。  
  
- `WinXpTheme_Blue` -蓝色主题 (Luna)。  
  
- `WinXpTheme_Olive` -橄榄色主题。  
  
- `WinXpTheme_Silver` -银级主题。  
  
##  <a name="updatesystemcolors"></a>  CMFCBaseVisualManager::UpdateSystemColors  
 调用`OpenThemeData`以获取用于绘制各种控件的句柄： windows、 工具栏、 按钮和等等。  
  
```  
void UpdateSystemColors();
```  
  
### <a name="remarks"></a>备注  
 仅限内部使用。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
