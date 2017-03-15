---
title: "AFX_GLOBAL_DATA 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GLOBAL_DATA
dev_langs:
- C++
helpviewer_keywords:
- AFX_GLOBAL_DATA structure
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
caps.latest.revision: 30
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f3257f165b6b3937258acc6878ca1044ea7ab31e
ms.lasthandoff: 02/24/2017

---
# <a name="afxglobaldata-structure"></a>AFX_GLOBAL_DATA 结构
`AFX_GLOBAL_DATA` 结构包含用于管理框架或自定义应用程序外观和行为的字段和方法。  
  
## <a name="syntax"></a>语法  
  
```  
struct AFX_GLOBAL_DATA  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|构造 `AFX_GLOBAL_DATA` 结构。|  
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::CleanUp](#cleanup)|释放由框架（如画笔、字体和 DLL）分配的资源。|  
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|创建以指定点为中心旋转指定角度的旋转转换。|  
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|在指定区域中绘制控件的父级的背景。|  
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|使用指定主题的视觉样式绘制指定的文本。|  
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|从指定的缓冲区中删除指定的 XML 标记对。|  
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|检索指定用户界面元素的当前颜色。|  
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|返回一个指向存储在全局数据中的 `ID2D1Factory` 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。|  
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|检索类似于手，其标识符为 `IDC_HAND`的预定义光标。|  
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|在全局数据中创建和存储指向 ITaskBarList 接口的指针。|  
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|在全局数据中创建和存储指向 ITaskBarList3 接口的指针。|  
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|检索与非最小化窗口的非工作区相关联的度量值。|  
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|确定 Shell 自动隐藏栏的位置。|  
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|检索当前字体中的文本字符高度。|  
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|返回一个指向存储在全局数据中的 `IWICImagingFactory` 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。|  
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|返回一个指向存储在全局数据中的 `IDWriteFactory` 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|初始化 `D2D``DirectWrite` 和 `WIC` 工厂。 在初始化主窗口之前调用此方法。|  
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|指示是否支持预定义的 32 位图标。|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|确定是否已初始化 `D2D` 。|  
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|提供了一种简单的方法来调用 Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) 方法。|  
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|指示当前是否以高对比度显示图像。|  
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|检测桌面菜单动画和任务栏自动隐藏功能的当前状态。|  
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|注册指定的 MFC 窗口类。|  
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|释放通过 GetITaskbarList 和 GetITaskbarList3 方法获取的接口。|  
|[AFX_GLOBAL_DATA::Resume](#resume)|重新初始化访问支持 Windows [主题和视觉样式](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx)的方法的内部函数指针。|  
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|提供了一种简单的方法来调用 Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) 方法。|  
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|创建指定的逻辑字体。|  
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|创建并初始化分析名称中的 Shell 项对象。|  
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|重新初始化框架使用的逻辑字体。|  
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|初始化框架使用的颜色、颜色深度、画笔、笔和图像。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|启用或禁用 Microsoft Active Accessibility 支持。 Active Accessibility 提供了可靠的方式来公开与用户界面元素有关的信息。|  
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|指示是否启用了 Microsoft Active Accessibility 支持。|  
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|指示操作系统是否支持分层的窗口。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|指示当前操作系统是否支持 alpha 值混合处理。|  
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|指示应用程序在 Windows 7 OS 还是更高版本下执行|  
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|指定活动标题的渐变颜色。 通常用于停靠窗格。|  
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|指定非活动标题的渐变颜色。 通常用于停靠窗格。|  
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|指示框架是否使用预定义的 32 位颜色图标或分辨率较低的图标。|  
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|指示系统字体是否用于菜单、工具栏和功能区。|  
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|存储手形光标的句柄。|  
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|存储水平拉伸光标的句柄。|  
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|存储垂直拉伸光标的句柄。|  
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|存储工具图标的句柄。|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|指定从自动隐藏工具栏最左侧到停靠栏左侧的偏移量。|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|指定自动隐藏工具栏之间的间距。|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|指定用于传达停靠状态的拖动框架的粗细。|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|指定用于传达浮动状态的拖动框架的粗细。|  
  
### <a name="remarks"></a>备注  
 应用程序启动时， `AFX_GLOBAL_DATA` 结构中的大多数数据被初始化。  
  
### <a name="inheritance-hierarchy"></a>继承层次结构  
 `AFX_GLOBAL_DATA`   
  
### <a name="requirements"></a>要求  
 **标头：** afxglobals.h  
  
### <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


## <a name="a-namebisosalphablendingsupporta-afxglobaldatabisosalphablendingsupport"></a><a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
该值指示操作系统是否支持 alpha 值混合处理。  
  
  
```  
BOOL  bIsOSAlphaBlendingSupport;  
```  
  
### <a name="remarks"></a>备注  
 `TRUE`指示支持 alpha 值混合处理;否则为`FALSE`。  
  

## <a name="a-namecleanupa-afxglobaldatacleanup"></a><a name="cleanup"></a>AFX_GLOBAL_DATA::CleanUp
释放由框架（如画笔、字体和 DLL）分配的资源。  
  
  
```  
void CleanUp();
```  
## <a name="a-named2d1makerotatematrixa-afxglobaldatad2d1makerotatematrix"></a><a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
创建以指定点为中心旋转指定角度的旋转转换。  
  
  
```  
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,  
    D2D1_POINT_2F center,  
    D2D1_MATRIX_3X2_F *matrix);
```  
  
### <a name="parameters"></a>参数   
 `angle`  
 顺时针旋转角度，以度为单位。  
  
 `center`  
 围绕其旋转的点。  
  
 `matrix`  
 此方法返回时，包含新的旋转转换。 您必须为此参数分配存储。  
  
### <a name="return-value"></a>返回值  
 否则，返回 S_OK，如果成功或一个错误值。  
  
## <a name="a-namedrawparentbackgrounda-afxglobaldatadrawparentbackground"></a><a name="drawparentbackground"></a>AFX_GLOBAL_DATA::DrawParentBackground
在指定区域中绘制控件的父级的背景。  
  
  
```  
BOOL DrawParentBackground(
    CWnd* pWnd,   
    CDC* pDC,   
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>参数   
 [in] `pWnd`  
 指向控件的窗口的指针。  
  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `lpRect`  
 指向用来限定要绘制的区域的矩形的指针。 默认值为 `NULL`。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `TRUE`；否则为 `FALSE`。  
  
## <a name="a-namedrawtextonglassa-afxglobaldatadrawtextonglass"></a><a name="drawtextonglass"></a>AFX_GLOBAL_DATA::DrawTextOnGlass
使用指定主题的视觉样式绘制指定的文本。  
  
  
```  
BOOL DrawTextOnGlass(
    HTHEME hTheme,   
    CDC* pDC,   
    int iPartId,   
    int iStateId,   
    CString strText,   
    CRect rect,   
    DWORD dwFlags,   
    int nGlowSize = 0,   
    COLORREF clrText = (COLORREF)-1);
```  
  
### <a name="parameters"></a>参数   
 [in] `hTheme`  
 窗口主题数据的句柄，或 `NULL`。 如果此参数不是 `NULL` 且支持主题，框架将使用指定的主题绘制文本。 否则，该框架将不使用主题来绘制文本。  
  
 使用 [OpenThemeData](http://msdn.microsoft.com/library/windows/desktop/bb759821) 方法创建 `HTHEME`。  
  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `iPartId`  
 具有所需文本外观的控件部件。 有关详细信息，请参阅 [部件和状态](http://msdn.microsoft.com/library/windows/desktop/bb773210)中表格的“部件”列。 如果此值为 0，则会使用默认字体或在设备上下文中选择的字体绘制文本。  
  
 [in] `iStateId`  
 具有所需文本外观的控件状态。 有关详细信息，请参阅 [部件和状态](http://msdn.microsoft.com/library/windows/desktop/bb773210)中表格的“状态”列。  
  
 [in] `strText`  
 要绘制的文本。  
  
 [in] `rect`  
 在其中绘制指定文本的区域的边界。  
  
 [in] `dwFlags`  
 指定如何绘制指定文本的标志的按位组合 (OR)。  
  
 如果`hTheme`参数是`NULL`或不受支持且启用，主题`nFormat`参数[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)方法描述有效的标志。 如果支持主题， `dwFlags` DrawThemeTextEx [方法的](http://msdn.microsoft.com/library/windows/desktop/bb773317) 参数将描述有效的标志。  
  
 [in] `nGlowSize`  
 在背景上绘制，然后指定绘制的文本之前发光效果的大小。 默认值为 0。  
  
 [in] `clrText`  
 在其中绘制指定文本的颜色。 默认值为默认颜色。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果主题用于绘制指定的文本;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 主题定义应用程序的视觉样式。 如果 `hTheme` 参数为 `NULL`，或不支持 [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317) ，或如果禁用 [桌面窗口管理器](http://msdn.microsoft.com/library/windows/desktop/aa969540) (DWM) 组合，主题不会用于绘制文本。  
  
### <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [部件和状态](http://msdn.microsoft.com/library/windows/desktop/bb773210)   
 [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)   
 [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317)   
 [桌面窗口管理器](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [启用和控制 DWM 复合](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="a-nameenableaccessibilitysupporta-afxglobaldataenableaccessibilitysupport"></a><a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA::EnableAccessibilitySupport
启用或禁用 Microsoft Active Accessibility 支持。  
  
  
```  
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数   
 [in] `bEnable`  
 `TRUE` 启用辅助功能支持；`FALSE` 禁用辅助功能支持。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 Active Accessibility 是基于 COM 的技术，其使用辅助技术产品改进了程序和 Windows 操作系统一起工作的方式。 它提供了可靠的方式来公开与用户界面元素有关的信息。 但是，称为 Microsoft UI 自动化的更新辅助功能现已可用。 这两种技术的比较，请参阅[UI 自动化和 Microsoft Active Accessibility](http://msdn.microsoft.com/library/87bee662-0a3e-4232-a421-20e7a5968321)。  
  
 使用[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)方法，以确定是否启用 Microsoft Active Accessibility 支持。  
  
 
### <a name="see-also"></a>另请参阅  
 [UI 自动化和 Microsoft Active Accessibility](http://msdn.microsoft.com/library/87bee662-0a3e-4232-a421-20e7a5968321)   
 [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)

## <a name="a-nameexcludetaga-afxglobaldataexcludetag"></a><a name="excludetag"></a>AFX_GLOBAL_DATA::ExcludeTag
从指定的缓冲区中删除指定的 XML 标记对。  
  
  
```  
BOOL ExcludeTag(
    CString& strBuffer,  
    LPCTSTR lpszTag,  
    CString& strTag,  
    BOOL bIsCharsList = FALSE);
```  
  
### <a name="parameters"></a>参数   
 [in] `strBuffer`  
 文本缓冲区。  
  
 [in] `lpszTag`  
 对开始和结束 XML 标记的名称。  
  
 [out] `strTag`  
 此方法返回时，`strTag`参数包含的文本之间的开始和结束 XML 标记由命名`lpszTag`参数。 任何前导或尾随空格的结果进行修整。  
  
 [in] `bIsCharsList`  
 `TRUE`若要将转换中的转义字符的符号`strTag`参数为实际的转义字符;`FALSE`不以执行转换。默认值是`FALSE`。 有关更多信息，请参见“备注”。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 XML 标记对名为开始和结束标记指示开始和结束位置指定的缓冲区中的文本运行的组成。 `strBuffer`参数指定的缓冲区，和`lpszTag`参数指定的 XML 标记的名称。  
  
 使用下表中的符号进行编码的一组在指定的缓冲区中的转义字符。 指定`TRUE`为`bIsCharsList`要转换中的符号参数`strTag`到实际的转义符的参数。 下表使用[_T()](../../c-runtime-library/data-type-mappings.md)宏来指定符号并转义字符串。  
  
|符号|转义字符|  
|------------|----------------------|  
|_T("\\\t")|_T("\t")|  
|_T("\\\n")|_T("\n")|  
|_T("\\\r")|_T("\r")|  
|_T("\\\b")|_T("\b")|  
|_T("LT")|_T("\<")|  
|_T("GT")|_T(">")|  
|_T("AMP")|_T("&")|  
  
## <a name="a-namegetcolora-afxglobaldatagetcolor"></a><a name="getcolor"></a>AFX_GLOBAL_DATA::GetColor
检索指定用户界面元素的当前颜色。  
  
  
```  
COLORREF GetColor(int nColor);
```  
  
### <a name="parameters"></a>参数   
 [in] `nColor`  
 指定将检索其颜色的用户界面元素的值。 有关有效值的列表，请参阅`nIndex`参数[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)方法。  
  
### <a name="return-value"></a>返回值  
 指定的用户界面元素的 RGB 颜色值。 有关更多信息，请参见“备注”。  
  
### <a name="remarks"></a>备注  
 如果 `nColor` 参数超出范围，则返回值是零。 由于零也是有效的 RGB 值，因此您不能使用此方法来确定当前操作系统是否支持系统颜色。 请改用[GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927)方法，它返回`NULL`如果颜色不受支持。  
  
### <a name="see-also"></a>另请参阅  

 [GetSysColor 函数](http://msdn.microsoft.com/library/windows/desktop/ms724371)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927)

## <a name="a-namegetdirect2dfactorya-afxglobaldatagetdirect2dfactory"></a><a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA::GetDirect2dFactory
 返回指向存储在全局数据中的 ID2D1Factory 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。  
  
  
```  
ID2D1Factory* GetDirect2dFactory();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1Factory 接口时的默认创建的工厂取得成功，或者如果创建失败，则为 NULL 或当前操作系统不具有 D2D 支持。  
  
## <a name="a-namegethandcursora--afxglobaldatagethandcursor"></a><a name="gethandcursor"></a>AFX_GLOBAL_DATA::GetHandCursor
检索类似于手，其标识符为 `IDC_HAND`的预定义光标。  
  
  
```  
HCURSOR GetHandCursor();
```  
  
### <a name="return-value"></a>返回值  
 获取手形光标的句柄。  

## <a name="a-namegetnonclientmetricsa-afxglobaldatagetnonclientmetrics"></a><a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA::GetNonClientMetrics
检索与非最小化窗口的非工作区相关联的度量值。  
  
  
```  
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```  
  
### <a name="parameters"></a>参数   
 [in, out] `info`  
 一个[NONCLIENTMETRICS](http://msdn.microsoft.com/library/windows/desktop/ff729175)结构，其中包含与非最小化窗口的非工作区相关联的可缩放度量值。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法成功，则否则为`FALSE`。  
 
  
### <a name="see-also"></a>另请参阅   
 [NONCLIENTMETRICS 结构](http://msdn.microsoft.com/library/windows/desktop/ff729175)

## <a name="a-namegettextheighta-afxglobaldatagettextheight"></a><a name="gettextheight"></a>AFX_GLOBAL_DATA::GetTextHeight
 检索当前字体中的文本字符高度。  
  
  
```  
int GetTextHeight(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>参数   
 [in] `bHorz`  
如果为  `TRUE`，则在文本水平运行时检索字符的高度；如果为 `FALSE`，则在文本垂直运行时检索字符的高度。 默认值为 `TRUE`。  
  
### <a name="return-value"></a>返回值  
 当前字体的高度，从字体上缘往字体下缘测量。  
  
## <a name="a-namegetwicfactorya-afxglobaldatagetwicfactory"></a><a name="getwicfactory"></a>AFX_GLOBAL_DATA::GetWICFactory
返回指向存储在全局数据中的 IWICImagingFactory 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。  
  
  
```  
IWICImagingFactory* GetWICFactory();
```  
  
### <a name="return-value"></a>返回值  
 如果创建的工厂取得成功，或者如果创建失败，则为 NULL 的 IWICImagingFactory 接口或当前操作系统的指针将不具有 WIC 支持。  
  
## <a name="a-namegetwritefactorya-afxglobaldatagetwritefactory"></a><a name="getwritefactory"></a>AFX_GLOBAL_DATA::GetWriteFactory
返回指向存储在全局数据中的 IDWriteFactory 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。  
  
  
```  
IDWriteFactory* GetWriteFactory();
```  
  
### <a name="return-value"></a>返回值  
 如果创建的工厂取得成功，或者如果创建失败，则为 NULL 的 IDWriteFactory 接口或当前操作系统的指针将不具有 DirectWrite 支持。  
 
## <a name="a-nameinitd2da-afxglobaldatainitd2d"></a><a name="initd2d"></a>AFX_GLOBAL_DATA::InitD2D
初始化 D2D、 DirectWrite、 和 WIC 工厂。 在初始化主窗口之前调用此方法。  
  
  
```  
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>参数   
 `d2dFactoryType`  
 它创建 D2D 工厂和资源的线程模型。  
  
 `writeFactoryType`  
 一个值，指定是否将共享或隔离写工厂对象  
  
### <a name="return-value"></a>返回值  
 工厂是否 intilalizrd，FALSE-否则将返回 TRUE  
  
## <a name="a-nameis32biticonsa-afxglobaldatais32biticons"></a><a name="is32biticons"></a>AFX_GLOBAL_DATA::Is32BitIcons
指示是否支持预定义的 32 位图标。  
  
  
```  
BOOL Is32BitIcons() const;

 
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果预定义的 32 位图标都受支持;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法返回`TRUE`如果框架支持 32 位内置图标和操作系统支持 16 位 / 像素或更多，并且图像不会显示在高对比度。  
  
## <a name="a-nameisaccessibilitysupporta-afxglobaldataisaccessibilitysupport"></a><a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA::IsAccessibilitySupport
指示是否启用了 Microsoft Active Accessibility 支持。  
  
  
```  
BOOL IsAccessibilitySupport() const; 
```  
  
### <a name="return-value"></a>返回值  
 如果启用了 Accessibility 支持，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 Microsoft Active Accessibility 是使应用程序可访问的早期解决方案。 Microsoft UI Automation 是 Microsoft Windows 的新的可访问性模型，旨在满足对辅助技术产品和自动测试工具的需求。 有关详细信息，请参阅[UI 自动化和 Microsoft Active Accessibility](http://msdn.microsoft.com/library/87bee662-0a3e-4232-a421-20e7a5968321)。  
  
 使用[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)方法来启用或禁用 Active Accessibility 支持。  
  

### <a name="see-also"></a>另请参阅  
 [UI 自动化和 Microsoft Active Accessibility](http://msdn.microsoft.com/library/87bee662-0a3e-4232-a421-20e7a5968321)

## <a name="a-nameisd2dinitializeda-afxglobaldataisd2dinitialized"></a><a name="isd2dinitialized"></a>AFX_GLOBAL_DATA::IsD2DInitialized
 确定是否已初始化 D2D  
  
  
```  
BOOL IsD2DInitialized() const; 
```  
  
### <a name="return-value"></a>返回值  
 如果已初始化 D2D; 则为 TRUE否则为 FALSE。  
  
## <a name="a-nameisdwmcompositionenableda-afxglobaldataisdwmcompositionenabled"></a><a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA::IsDwmCompositionEnabled
提供了一种简单的方法来调用 Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) 方法。  
  
  
```  
BOOL IsDwmCompositionEnabled();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果[桌面窗口管理器](http://msdn.microsoft.com/library/windows/desktop/aa969540)(DWM) 复合，则启用; 否则为`FALSE`。  
  
### <a name="see-also"></a>另请参阅    
 [桌面窗口管理器](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [启用和控制 DWM 复合](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="a-nameishighcontrastmodea-afxglobaldataishighcontrastmode"></a><a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA::IsHighContrastMode
 指示当前是否以高对比度显示图像。    
```  
BOOL IsHighContrastMode() const; 
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果图像当前显示在黑色或白色高对比度模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在黑色的高对比度模式下，背光线的边缘为白色和背景为黑色。 在白色的高对比度模式下，背光线的边缘则呈黑色和背景为白色。  
  
## <a name="a-nameiswindowslayersupportavailablea-afxglobaldataiswindowslayersupportavailable"></a><a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
指示操作系统是否支持分层的窗口。  
  
  
```  
BOOL IsWindowsLayerSupportAvailable() const; 
```  
  
### <a name="return-value"></a>返回值  
 如果支持分层窗口，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 如果支持分层的窗口，则*智能停靠*标记将使用分层的窗口。  
  
## <a name="a-namembusebuiltin32biticonsa-afxglobaldatambusebuiltin32biticons"></a><a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
指示框架是否使用预定义的 32 位颜色图标或分辨率较低的图标。  
  
  
```  
BOOL  m_bUseBuiltIn32BitIcons;  
```  
  
### <a name="remarks"></a>备注  
 `TRUE` 指定框架使用 32 位颜色图标；`FALSE` 指定较低分辨率的图标。 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 构造函数将此成员初始化为 `TRUE`。  
  
 必须在应用程序启动时设置此成员。  
  
## <a name="a-namembusesystemfonta-afxglobaldatambusesystemfont"></a><a name="m_busesystemfont"></a>AFX_GLOBAL_DATA::m_bUseSystemFont
指示系统字体是否用于菜单、工具栏和功能区。  
  
  
```  
BOOL m_bUseSystemFont;  
```  
  
### <a name="remarks"></a>备注  
 `TRUE`指定要使用系统字体;否则为`FALSE`。 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 构造函数将此成员初始化为 `FALSE`。  
  
 测试此成员不是使用框架可以确定该字体的唯一方法。 `AFX_GLOBAL_DATA::UpdateFonts`还对方法进行测试以确定哪些视觉样式可应用于菜单、 工具栏和功能区的默认和替代字体。  
  
## <a name="a-namemhcurhanda-afxglobaldatamhcurhand"></a><a name="m_hcurhand"></a>AFX_GLOBAL_DATA::m_hcurHand
存储手形光标的句柄。  
  
  
```  
HCURSOR m_hcurHand;  
```  
  
## <a name="a-namemhcurstretcha-afxglobaldatamhcurstretch"></a><a name="m_hcurstretch"></a>AFX_GLOBAL_DATA::m_hcurStretch
存储水平拉伸光标的句柄。  
  
  
```  
HCURSOR m_hcurStretch;  
```  

## <a name="a-namemhcurstretchverta-afxglobaldatamhcurstretchvert"></a><a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA::m_hcurStretchVert
存储垂直拉伸光标的句柄。  
  
  
```  
HCURSOR m_hcurStretchVert;  
```  
  
## <a name="a-namemhicontoola-afxglobaldatamhicontool"></a><a name="m_hicontool"></a>AFX_GLOBAL_DATA::m_hiconTool
存储工具图标的句柄。  
  
  
```  
HICON m_hiconTool;  
```  
## <a name="a-namemnautohidetoolbarmargina-afxglobaldatamnautohidetoolbarmargin"></a><a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
指定从最左侧的自动隐藏工具栏到停靠栏左侧的偏移量。  
  
  
```  
int  m_nAutoHideToolBarMargin;  
```  
  
### <a name="remarks"></a>备注  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 构造函数将此成员初始化为 4 像素。  
  
## <a name="a-namemnautohidetoolbarspacinga-afxglobaldatamnautohidetoolbarspacing"></a><a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
指定自动隐藏工具栏之间的间距。  
  
  
```  
int   m_nAutoHideToolBarSpacing;  
```  
  
### <a name="remarks"></a>备注  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`构造函数将初始化此成员为 14 个像素。  
  
## <a name="a-namemndragframethicknessdocka-afxglobaldatamndragframethicknessdock"></a><a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

指定用于表示停靠的状态的拖动框架的粗细。  
  
  
```  
int  m_nDragFrameThicknessDock;  
```  
  
### <a name="remarks"></a>备注  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`构造函数此成员初始化为 3 个像素。  
  
## <a name="a-namemndragframethicknessfloata-afxglobaldatamndragframethicknessfloat"></a><a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
指定用于表示浮点状态的拖动框架的粗细。  
  
  
```  
int  m_nDragFrameThicknessFloat;  
```  
  
### <a name="remarks"></a>备注  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 构造函数将此成员初始化为 4 像素。  
  
## <a name="a-nameonsettingchangea-afxglobaldataonsettingchange"></a><a name="onsettingchange"></a>AFX_GLOBAL_DATA::OnSettingChange
检测桌面菜单动画和任务栏自动隐藏功能的当前状态。  
  
  
```  
void OnSettingChange();
```  
  
### <a name="remarks"></a>备注  
 此方法将框架变量设置为用户的桌面的特定属性的状态。 此方法检测菜单动画、 菜单淡入淡出和任务栏自动隐藏功能的当前状态。  
  
## <a name="a-nameregisterwindowclassa-afxglobaldataregisterwindowclass"></a><a name="registerwindowclass"></a>AFX_GLOBAL_DATA::RegisterWindowClass
注册指定的 MFC 窗口类。  
  
  
```  
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```  
  
### <a name="parameters"></a>参数   
 [in] `lpszClassNamePrefix`  
 要注册的窗口类的名称。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则已注册类的限定的名称否则为[资源异常](http://msdn.microsoft.com/library/ddd99292-819b-4fa4-8371-b1954ed5856d)。  
  
### <a name="remarks"></a>备注  
 返回值为以下各项的冒号分隔的列表：`lpszClassNamePrefix` 参数字符串、当前应用程序实例的句柄的十六进制文本表示形式、应用程序光标（它是标识符为 IDC_ARROW 的箭头光标）和背景画笔。 有关注册 MFC 窗口类的详细信息，请参阅[AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)。  
  
### <a name="see-also"></a>另请参阅    
 [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)   
 [AfxThrowResourceException](../../mfc/reference/exception-processing.md#afxthrowresourceexception)

## <a name="a-nameresumea-afxglobaldataresume"></a><a name="resume"></a>AFX_GLOBAL_DATA::Resume
 重新初始化访问支持 Windows 主题和视觉样式的方法的内部函数指针。 
  
  
```  
BOOL Resume();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法成功，则否则为`FALSE`。 在调试模式下，此方法要声明此方法不成功。  
  
### <a name="remarks"></a>备注  
 当框架接收时调用此方法[WM_POWERBROADCAST](http://msdn.microsoft.com/library/windows/desktop/aa373247)消息。  
  
## <a name="a-namesetlayeredattriba-afxglobaldatasetlayeredattrib"></a><a name="setlayeredattrib"></a>AFX_GLOBAL_DATA::SetLayeredAttrib
提供了一种简单的方法来调用 Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) 方法。  
  
  
```  
BOOL SetLayeredAttrib(
    HWND hwnd,  
    COLORREF crKey,  
    BYTE bAlpha,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>参数   
 [in] `hwnd`  
 分层窗口的句柄。  
  
 [in] `crKey`  
 透明度颜色键[桌面窗口管理器](http://msdn.microsoft.com/library/windows/desktop/aa969540)用于组成分层的窗口。  
  
 [in] `bAlpha`  
 用于描述分层窗口的暗度的 alpha 值。  
  
 [in] `dwFlags`  
 标志的按位组合 (OR)，其指定参数要使用的方法。 指定 LWA_COLORKEY 以使用 `crKey` 参数作为透明度颜色。 指定 LWA_ALPHA 以使用 `bAlpha` 参数确定分层窗口的暗度。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法成功，则否则为`FALSE`。   
 
### <a name="see-also"></a>另请参阅   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540)

## <a name="a-namesetmenufonta-afxglobaldatasetmenufont"></a><a name="setmenufont"></a>AFX_GLOBAL_DATA::SetMenuFont
创建指定的逻辑字体。  
  
  
```  
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数   
 [in] `lpLogFont`  
 指向包含字体的属性的结构的指针。  
  
 [in] `bHorz`  
 `TRUE`若要指定水平; 运行的文本`FALSE`以指定文本垂直运行。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法成功，则否则为`FALSE`。 在调试模式下，此方法要声明此方法不成功。  
  
### <a name="remarks"></a>备注  
 此方法创建水平常规字体，则使用下划线的字体，并使用在默认菜单项是加粗字体。。 此方法 （可选） 创建常规垂直字体。 有关逻辑焦点详细信息，请参阅[cfont:: Createfontindirect](../../mfc/reference/cfont-class.md#createfontindirect)。  
  
## <a name="a-nameupdatefontsa-afxglobaldataupdatefonts"></a><a name="updatefonts"></a>AFX_GLOBAL_DATA::UpdateFonts
重新初始化框架使用的逻辑字体。  
  
  
```  
void UpdateFonts();
```  
  
### <a name="remarks"></a>备注  
 有关逻辑焦点详细信息，请参阅 `CFont::CreateFontIndirect`。  
  
## <a name="a-nameupdatesyscolorsa-afxglobaldataupdatesyscolors"></a><a name="updatesyscolors"></a>AFX_GLOBAL_DATA::UpdateSysColors
初始化框架使用的颜色、颜色深度、画笔、笔和图像。  
  
  
```  
void UpdateSysColors();
```  
  
## <a name="a-namebiswindows7a-afxglobaldatabiswindows7"></a><a name="biswindows7"></a>AFX_GLOBAL_DATA::bIsWindows7
指示应用程序在 Windows 7 还是更高版本下执行。  
  
  
```  
BOOL bIsWindows7;  
```  
  
## <a name="a-nameclractivecaptiongradienta-afxglobaldataclractivecaptiongradient"></a><a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA::clrActiveCaptionGradient
指定活动标题的渐变颜色。 通常用于停靠窗格。  
  
  
```  
COLORREF clrActiveCaptionGradient;  
```  
  
## <a name="a-nameclrinactivecaptiongradienta-afxglobaldataclrinactivecaptiongradient"></a><a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA::clrInactiveCaptionGradient
指定非活动标题的渐变颜色。 通常用于停靠窗格。  
  
  
```  
COLORREF clrInactiveCaptionGradient;  
```  
  
## <a name="a-namegetitaskbarlista-afxglobaldatagetitaskbarlist"></a><a name="getitaskbarlist"></a>AFX_GLOBAL_DATA::GetITaskbarList
在全局数据中创建和存储指向 `ITaskBarList` 接口的指针。  
  
  
```  
ITaskbarList *GetITaskbarList();
```  
  
### <a name="return-value"></a>返回值  
 如果任务栏列表对象的创建成功，则为指向 `ITaskbarList` 接口的指针；如果创建失败或者当前操作系统的版本低于 Windows 7，则为 `NULL`。  
  
## <a name="a-namegetitaskbarlist3a-afxglobaldatagetitaskbarlist3"></a><a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA::GetITaskbarList3
在全局数据中创建和存储指向 `ITaskBarList3` 接口的指针。  
  
  
```  
ITaskbarList3 *GetITaskbarList3();
```  
  
### <a name="return-value"></a>返回值  
 如果任务栏列表对象的创建成功，则为指向 `ITaskbarList3` 接口的指针；如果创建失败或者当前操作系统的版本低于 Windows 7，则为 `NULL`。  
  
## <a name="a-namegetshellautohidebarsa-afxglobaldatagetshellautohidebars"></a><a name="getshellautohidebars"></a>AFX_GLOBAL_DATA::GetShellAutohideBars
确定 Shell 自动隐藏栏的位置。  
  
  
```  
int GetShellAutohideBars();
```  
  
### <a name="return-value"></a>返回值  
 一个整数值与已编码的标志，用于指定位置的自动隐藏条形图。 它可以结合以下值︰ AFX_AUTOHIDE_BOTTOM、 AFX_AUTOHIDE_TOP、 AFX_AUTOHIDE_LEFT、 AFX_AUTOHIDE_RIGHT。  
  
## <a name="a-namereleasetaskbarrefsa-afxglobaldatareleasetaskbarrefs"></a><a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA::ReleaseTaskBarRefs
释放接口通过获取`GetITaskbarList`和`GetITaskbarList3`方法。  
  
  
```  
void ReleaseTaskBarRefs();
```  
  
## <a name="a-nameshellcreateitemfromparsingnamea-afxglobaldatashellcreateitemfromparsingname"></a><a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
创建并初始化分析名称中的 Shell 项对象。  
  
  
```  
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,  
    IBindCtx *pbc,  
    REFIID riid,  
    void **ppv);
```  
  
### <a name="parameters"></a>参数   
 `pszPath`  
 [in]指向一个显示名称的指针。  
  
 `pbc`  
 指向控制分析操作的绑定上下文的指针。  
  
 `riid`  
 参考接口 id。  
  
 `ppv`  
 [out]此函数返回时，包含在请求的接口指针`riid`。 这通常是`IShellItem`或`IShellItem2`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK 返回否则为一个错误值。  


