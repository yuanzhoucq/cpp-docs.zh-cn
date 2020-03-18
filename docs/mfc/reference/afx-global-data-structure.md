---
title: AFX_GLOBAL_DATA 结构
ms.date: 11/04/2016
f1_keywords:
- AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::CleanUp
- AFXGLOBALS/AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawParentBackground
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawTextOnGlass
- AFXGLOBALS/AFX_GLOBAL_DATA::ExcludeTag
- AFXGLOBALS/AFX_GLOBAL_DATA::GetColor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetDirect2dFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetHandCursor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList3
- AFXGLOBALS/AFX_GLOBAL_DATA::GetNonClientMetrics
- AFXGLOBALS/AFX_GLOBAL_DATA::GetShellAutohideBars
- AFXGLOBALS/AFX_GLOBAL_DATA::GetTextHeight
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWICFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWriteFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::InitD2D
- AFXGLOBALS/AFX_GLOBAL_DATA::Is32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::IsDwmCompositionEnabled
- AFXGLOBALS/AFX_GLOBAL_DATA::IsHighContrastMode
- AFXGLOBALS/AFX_GLOBAL_DATA::OnSettingChange
- AFXGLOBALS/AFX_GLOBAL_DATA::RegisterWindowClass
- AFXGLOBALS/AFX_GLOBAL_DATA::ReleaseTaskBarRefs
- AFXGLOBALS/AFX_GLOBAL_DATA::Resume
- AFXGLOBALS/AFX_GLOBAL_DATA::SetLayeredAttrib
- AFXGLOBALS/AFX_GLOBAL_DATA::SetMenuFont
- AFXGLOBALS/AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateFonts
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateSysColors
- AFXGLOBALS/AFX_GLOBAL_DATA::EnableAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsWindows7
- AFXGLOBALS/AFX_GLOBAL_DATA::clrActiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::clrInactiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseSystemFont
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurHand
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretch
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretchVert
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hiconTool
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
ms.openlocfilehash: 66cfb66e091d487ea9d3f563b7b6bbb9ca1ea928
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447334"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA 结构

`AFX_GLOBAL_DATA` 结构包含用于管理框架或自定义应用程序外观和行为的字段和方法。

## <a name="syntax"></a>语法

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|构造 `AFX_GLOBAL_DATA` 结构。|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[AFX_GLOBAL_DATA：：清理](#cleanup)|释放由框架（如画笔、字体和 DLL）分配的资源。|
|[AFX_GLOBAL_DATA：:D 2D1MakeRotateMatrix](#d2d1makerotatematrix)|创建以指定点为中心旋转指定角度的旋转转换。|
|[AFX_GLOBAL_DATA：:D rawParentBackground](#drawparentbackground)|在指定区域中绘制控件的父级的背景。|
|[AFX_GLOBAL_DATA：:D rawTextOnGlass](#drawtextonglass)|使用指定主题的视觉样式绘制指定的文本。|
|[AFX_GLOBAL_DATA：： ExcludeTag](#excludetag)|从指定的缓冲区中删除指定的 XML 标记对。|
|[AFX_GLOBAL_DATA：： GetColor](#getcolor)|检索指定用户界面元素的当前颜色。|
|[AFX_GLOBAL_DATA：： GetDirect2dFactory](#getdirect2dfactory)|返回一个指向存储在全局数据中的 `ID2D1Factory` 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。|
|[AFX_GLOBAL_DATA：： GetHandCursor](#gethandcursor)|检索类似于手，其标识符为 `IDC_HAND`的预定义光标。|
|[AFX_GLOBAL_DATA：： GetITaskbarList](#getitaskbarlist)|在全局数据中创建和存储指向 ITaskBarList 接口的指针。|
|[AFX_GLOBAL_DATA：： GetITaskbarList3](#getitaskbarlist3)|在全局数据中创建和存储指向 ITaskBarList3 接口的指针。|
|[AFX_GLOBAL_DATA：： GetNonClientMetrics](#getnonclientmetrics)|检索与非最小化窗口的非工作区相关联的度量值。|
|[AFX_GLOBAL_DATA：： GetShellAutohideBars](#getshellautohidebars)|确定 Shell 自动隐藏栏的位置。|
|[AFX_GLOBAL_DATA：： GetTextHeight](#gettextheight)|检索当前字体中的文本字符高度。|
|[AFX_GLOBAL_DATA：： GetWICFactory](#getwicfactory)|返回一个指向存储在全局数据中的 `IWICImagingFactory` 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。|
|[AFX_GLOBAL_DATA：： GetWriteFactory](#getwritefactory)|返回一个指向存储在全局数据中的 `IDWriteFactory` 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。|
|[AFX_GLOBAL_DATA：： InitD2D](#initd2d)|初始化 `D2D``DirectWrite` 和 `WIC` 工厂。 在初始化主窗口之前调用此方法。|
|[AFX_GLOBAL_DATA：： Is32BitIcons](#is32biticons)|指示是否支持预定义的 32 位图标。|
|[AFX_GLOBAL_DATA：： IsD2DInitialized](#isd2dinitialized)|确定是否已初始化 `D2D` 。|
|[AFX_GLOBAL_DATA：： IsDwmCompositionEnabled](#isdwmcompositionenabled)|提供了一种简单的方法来调用 Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) 方法。|
|[AFX_GLOBAL_DATA：： IsHighContrastMode](#ishighcontrastmode)|指示当前是否以高对比度显示图像。|
|[AFX_GLOBAL_DATA：： OnSettingChange](#onsettingchange)|检测桌面菜单动画和任务栏自动隐藏功能的当前状态。|
|[AFX_GLOBAL_DATA：： RegisterWindowClass](#registerwindowclass)|注册指定的 MFC 窗口类。|
|[AFX_GLOBAL_DATA：： ReleaseTaskBarRefs](#releasetaskbarrefs)|释放通过 GetITaskbarList 和 GetITaskbarList3 方法获取的接口。|
|[AFX_GLOBAL_DATA：： Resume](#resume)|重新初始化访问支持 Windows [主题和视觉样式](/windows/win32/Controls/visual-styles-overview)的方法的内部函数指针。|
|[AFX_GLOBAL_DATA：： SetLayeredAttrib](#setlayeredattrib)|提供了一种简单的方法来调用 Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) 方法。|
|[AFX_GLOBAL_DATA：： SetMenuFont](#setmenufont)|创建指定的逻辑字体。|
|[AFX_GLOBAL_DATA：： ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|创建并初始化分析名称中的 Shell 项对象。|
|[AFX_GLOBAL_DATA：： UpdateFonts](#updatefonts)|重新初始化框架使用的逻辑字体。|
|[AFX_GLOBAL_DATA：： UpdateSysColors](#updatesyscolors)|初始化框架使用的颜色、颜色深度、画笔、笔和图像。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[AFX_GLOBAL_DATA：： EnableAccessibilitySupport](#enableaccessibilitysupport)|启用或禁用 Microsoft Active Accessibility 支持。 Active Accessibility 提供了可靠的方式来公开与用户界面元素有关的信息。|
|[AFX_GLOBAL_DATA：： IsAccessibilitySupport](#isaccessibilitysupport)|指示是否启用了 Microsoft Active Accessibility 支持。|
|[AFX_GLOBAL_DATA：： IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|指示操作系统是否支持分层的窗口。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[AFX_GLOBAL_DATA：： bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|指示当前操作系统是否支持 alpha 值混合处理。|
|[AFX_GLOBAL_DATA：： bIsWindows7](#biswindows7)|指示应用程序在 Windows 7 OS 还是更高版本下执行|
|[AFX_GLOBAL_DATA：： clrActiveCaptionGradient](#clractivecaptiongradient)|指定活动标题的渐变颜色。 通常用于停靠窗格。|
|[AFX_GLOBAL_DATA：： clrInactiveCaptionGradient](#clrinactivecaptiongradient)|指定非活动标题的渐变颜色。 通常用于停靠窗格。|
|[AFX_GLOBAL_DATA：： m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|指示框架是否使用预定义的 32 位颜色图标或分辨率较低的图标。|
|[AFX_GLOBAL_DATA：： m_bUseSystemFont](#m_busesystemfont)|指示系统字体是否用于菜单、工具栏和功能区。|
|[AFX_GLOBAL_DATA：： m_hcurHand](#m_hcurhand)|存储手形光标的句柄。|
|[AFX_GLOBAL_DATA：： m_hcurStretch](#m_hcurstretch)|存储水平拉伸光标的句柄。|
|[AFX_GLOBAL_DATA：： m_hcurStretchVert](#m_hcurstretchvert)|存储垂直拉伸光标的句柄。|
|[AFX_GLOBAL_DATA：： m_hiconTool](#m_hicontool)|存储工具图标的句柄。|
|[AFX_GLOBAL_DATA：： m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|指定从自动隐藏工具栏最左侧到停靠栏左侧的偏移量。|
|[AFX_GLOBAL_DATA：： m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|指定自动隐藏工具栏之间的间距。|
|[AFX_GLOBAL_DATA：： m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|指定用于传达停靠状态的拖动框架的粗细。|
|[AFX_GLOBAL_DATA：： m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|指定用于传达浮动状态的拖动框架的粗细。|

### <a name="remarks"></a>备注

应用程序启动时， `AFX_GLOBAL_DATA` 结构中的大多数数据被初始化。

### <a name="inheritance-hierarchy"></a>继承层次结构

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>要求

**标头：** afxglobals.h

## <a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA：： bIsOSAlphaBlendingSupport

指示操作系统是否支持 alpha 混合。

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>备注

TRUE 表示支持 alpha 混合;否则为 FALSE。

## <a name="cleanup"></a>AFX_GLOBAL_DATA：：清理

释放由框架（如画笔、字体和 DLL）分配的资源。

```
void CleanUp();
```

## <a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA：:D 2D1MakeRotateMatrix

创建以指定点为中心旋转指定角度的旋转转换。

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>参数

*夹角*<br/>
顺时针旋转角度，以度为单位。

*center*<br/>
要旋转的点。

*矩阵*<br/>
此方法返回时，将包含新的旋转转换。 必须为此参数分配存储空间。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误值。

## <a name="drawparentbackground"></a>AFX_GLOBAL_DATA：:D rawParentBackground

在指定区域中绘制控件的父级的背景。

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中指向控件窗口的指针。

*pDC*<br/>
中指向设备上下文的指针。

*lpRect*<br/>
中一个指针，指向限定要绘制的区域的矩形。 默认值为 NULL。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

## <a name="drawtextonglass"></a>AFX_GLOBAL_DATA：:D rawTextOnGlass

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

*hTheme*<br/>
中窗口主题数据的句柄，或为 NULL。 如果此参数不为 NULL 并且支持主题，框架将使用指定的主题绘制文本。 否则，该框架将不使用主题来绘制文本。

使用[OpenThemeData](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata)方法创建 HTHEME。

*pDC*<br/>
中指向设备上下文的指针。

*iPartId*<br/>
中具有所需文本外观的控件部件。 有关详细信息，请参阅 [部件和状态](/windows/win32/controls/parts-and-states)中表格的“部件”列。 如果此值为 0，则会使用默认字体或在设备上下文中选择的字体绘制文本。

*iStateId*<br/>
中具有所需文本外观的控件状态。 有关详细信息，请参阅 [部件和状态](/windows/win32/controls/parts-and-states)中表格的“状态”列。

*strText*<br/>
中要绘制的文本。

*rect*<br/>
中在其中绘制指定文本的区域的边界。

dwFlags<br/>
中指定如何绘制指定文本的标志的按位组合（OR）。

如果*hTheme*参数 `NULL`，或者如果不支持和启用主题，则[CDC：:D Rawtext](../../mfc/reference/cdc-class.md#drawtext)方法的*nFormat*参数将描述有效的标志。 如果支持主题，则[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)方法的*dwFlags*参数将描述有效的标志。

*nGlowSize*<br/>
中绘制指定的文本之前在背景上绘制的发光效果的大小。 默认值为 0。

*clrText*<br/>
中在其中绘制指定文本的颜色。 默认值为默认颜色。

### <a name="return-value"></a>返回值

如果主题用于绘制指定的文本，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

主题定义应用程序的视觉样式。 如果*hTheme*参数为 NULL，或者不支持[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)方法，或者如果禁用[桌面窗口管理器](/windows/win32/dwm/dwm-overview)（DWM）组合，则不使用主题来绘制文本。

## <a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA：： EnableAccessibilitySupport

启用或禁用 Microsoft Active Accessibility 支持。

```
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
中TRUE 表示启用辅助功能支持;禁用辅助功能支持的 FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

Active Accessibility 是基于 COM 的技术，其使用辅助技术产品改进了程序和 Windows 操作系统一起工作的方式。 它提供了可靠的方式来公开与用户界面元素有关的信息。 但是，称为 Microsoft UI 自动化的更新辅助功能现已可用。 有关这两种技术的比较，请参阅[UI 自动化和 Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)。

使用[AFX_GLOBAL_DATA：： IsAccessibilitySupport](#isaccessibilitysupport)方法来确定是否启用了 Microsoft Active Accessibility 支持。

## <a name="excludetag"></a>AFX_GLOBAL_DATA：： ExcludeTag

从指定的缓冲区中删除指定的 XML 标记对。

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>参数

*strBuffer*<br/>
中文本缓冲区。

*lpszTag*<br/>
中一对开始和结束 XML 标记的名称。

*strTag*<br/>
弄此方法返回时， *strTag*参数包含*lpszTag*参数命名的开始和结束 XML 标记之间的文本。 任何前导空格或尾随空格都将从结果中去除。

*bIsCharsList*<br/>
中如果为 TRUE，则将*strTag*参数中的转义符符号转换为实际转义字符;若为 FALSE，则不执行转换。默认值为 FALSE。 有关详细信息，请参阅备注。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

XML 标记对包含命名的开始标记和结束标记，这些标记指示指定缓冲区中的文本运行的开始和结束。 *StrBuffer*参数指定缓冲区， *LPSZTAG*参数指定 XML 标记的名称。

使用下表中的符号对指定缓冲区中的一组转义符进行编码。 将*bIsCharsList*参数指定为 TRUE 可将*strTag*参数中的符号转换为实际转义字符。 下表使用[_T （）](../../c-runtime-library/data-type-mappings.md)宏指定符号和转义字符串。

|符号|转义符|
|------------|----------------------|
|_T （"\\\t"）|_T("\t")|
|_T （"\\\n"）|_T （"\n"）|
|_T （"\\\r"）|_T （"\r"）|
|_T （"\\\b"）|_T （"\b"）|
|_T("LT")|_T （"\<"）|
|_T （"G"）|_T(">")|
|_T （"AMP"）|_T （"&"）|

## <a name="getcolor"></a>AFX_GLOBAL_DATA：： GetColor

检索指定用户界面元素的当前颜色。

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>参数

*nColor*<br/>
中一个值，该值指定要检索其颜色的用户界面元素。 有关有效值的列表，请参阅[GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor)方法的*nIndex*参数。

### <a name="return-value"></a>返回值

指定的用户界面元素的 RGB 颜色值。 有关详细信息，请参阅备注。

### <a name="remarks"></a>备注

如果*nColor*参数超出范围，则返回值为零。 由于零也是有效的 RGB 值，因此您不能使用此方法来确定当前操作系统是否支持系统颜色。 改为使用[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)方法，如果不支持该颜色，该方法将返回 NULL。

## <a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA：： GetDirect2dFactory

返回一个指向存储在全局数据中的 ID2D1Factory 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>返回值

如果创建工厂成功，则为指向 ID2D1Factory 接口的指针; 如果创建失败或当前操作系统不支持 D2D，则为 NULL。

## <a name="gethandcursor"></a>AFX_GLOBAL_DATA：： GetHandCursor

检索类似于手型并 IDC_HAND 其标识符的预定义游标。

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>返回值

获取手形光标的句柄。

## <a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA：： GetNonClientMetrics

检索与非最小化窗口的非工作区相关联的度量值。

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>参数

info<br/>
[in，out][NONCLIENTMETRICS](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)结构，其中包含与非最小化窗口的非工作区相关联的可缩放指标。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

## <a name="gettextheight"></a>AFX_GLOBAL_DATA：： GetTextHeight

检索当前字体中的文本字符高度。

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>参数

*bHorz*<br/>
中若要在文本水平运行时检索字符的高度，则为 TRUE;若为 FALSE，则在文本垂直运行时检索字符的高度。 默认值为 TRUE。

### <a name="return-value"></a>返回值

当前字体的高度，从字体上缘往字体下缘测量。

## <a name="getwicfactory"></a>AFX_GLOBAL_DATA：： GetWICFactory

返回一个指向存储在全局数据中的 IWICImagingFactory 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>返回值

如果创建工厂成功，则为指向 IWICImagingFactory 接口的指针; 如果创建失败或当前操作系统不支持 WIC，则为 NULL。

## <a name="getwritefactory"></a>AFX_GLOBAL_DATA：： GetWriteFactory

返回一个指向存储在全局数据中的 IDWriteFactory 接口的指针。 如果接口未初始化，则创建具有默认参数的接口。

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>返回值

如果创建工厂成功，则为指向 IDWriteFactory 接口的指针; 如果创建失败或当前操作系统不支持 DirectWrite，则为 NULL。

## <a name="initd2d"></a>AFX_GLOBAL_DATA：： InitD2D

初始化 D2D、DirectWrite 和 WIC 工厂。 在初始化主窗口之前调用此方法。

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>参数

*d2dFactoryType*<br/>
D2D 工厂及其创建的资源的线程模型。

*writeFactoryType*<br/>
一个值，该值指定是共享还是隔离写入工厂对象

### <a name="return-value"></a>返回值

如果工厂为 intilalizrd，则返回 TRUE，否则返回 FALSE。

## <a name="is32biticons"></a>AFX_GLOBAL_DATA：： Is32BitIcons

指示是否支持预定义的 32 位图标。

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>返回值

如果支持预定义的32位图标，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果框架支持32位内置图标，则此方法返回 TRUE; 如果操作系统支持每像素16位或更大，则返回 TRUE; 如果图像未以高对比度显示，则返回 TRUE。

## <a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA：： IsAccessibilitySupport

指示是否启用了 Microsoft Active Accessibility 支持。

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>返回值

如果启用辅助功能支持，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

Microsoft Active Accessibility 是使应用程序可访问的早期解决方案。 Microsoft UI Automation 是 Microsoft Windows 的新的可访问性模型，旨在满足对辅助技术产品和自动测试工具的需求。

使用[AFX_GLOBAL_DATA：： EnableAccessibilitySupport](#enableaccessibilitysupport)方法可启用或禁用 Active Accessibility 支持。

## <a name="isd2dinitialized"></a>AFX_GLOBAL_DATA：： IsD2DInitialized

确定是否已初始化 D2D

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>返回值

如果已初始化 D2D，则为 TRUE;否则为 FALSE。

## <a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA：： IsDwmCompositionEnabled

提供了一种简单的方法来调用 Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) 方法。

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>返回值

如果启用[桌面窗口管理器](/windows/win32/dwm/dwm-overview)（DWM）组合，则为 TRUE;否则为 FALSE。

## <a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA：： IsHighContrastMode

指示当前是否以高对比度显示图像。

```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>返回值

如果图像当前以黑色或白色高对比度模式显示，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

在黑色高对比度模式下，光线正面为白色，背景为黑色。 在白色的高对比度模式下，光线的边缘为黑色，背景为白色。

## <a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA：： IsWindowsLayerSupportAvailable

指示操作系统是否支持分层的窗口。

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>返回值

如果支持分层窗口，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果支持分层窗口，*智能停靠*标记将使用分层窗口。

## <a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA：： m_bUseBuiltIn32BitIcons

指示框架是否使用预定义的 32 位颜色图标或分辨率较低的图标。

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>备注

如果为 TRUE，则指定框架使用32位颜色图标;FALSE 指定分辨率较低的图标。 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 构造函数将此成员初始化为 TRUE。

必须在应用程序启动时设置此成员。

## <a name="m_busesystemfont"></a>AFX_GLOBAL_DATA：： m_bUseSystemFont

指示系统字体是否用于菜单、工具栏和功能区。

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>备注

如果为 TRUE，则指定使用系统字体;否则为 FALSE。 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 构造函数将此成员初始化为 FALSE。

测试此成员不是框架确定要使用的字体的唯一方法。 `AFX_GLOBAL_DATA::UpdateFonts` 方法还会测试默认字体和备用字体，以确定哪些视觉样式可应用于菜单、工具栏和功能区。

## <a name="m_hcurhand"></a>AFX_GLOBAL_DATA：： m_hcurHand

存储手形光标的句柄。

```
HCURSOR m_hcurHand;
```

## <a name="m_hcurstretch"></a>AFX_GLOBAL_DATA：： m_hcurStretch

存储水平拉伸光标的句柄。

```
HCURSOR m_hcurStretch;
```

## <a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA：： m_hcurStretchVert

存储垂直拉伸光标的句柄。

```
HCURSOR m_hcurStretchVert;
```

## <a name="m_hicontool"></a>AFX_GLOBAL_DATA：： m_hiconTool

存储工具图标的句柄。

```
HICON m_hiconTool;
```

## <a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA：： m_nAutoHideToolBarMargin

指定从最左侧的自动隐藏工具栏到停靠栏左侧的偏移量。

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>备注

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 构造函数将此成员初始化为 4 像素。

## <a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA：： m_nAutoHideToolBarSpacing

指定自动隐藏工具栏之间的间距。

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>备注

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 构造函数将此成员初始化为14像素。

## <a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA：： m_nDragFrameThicknessDock

指定用于指示停靠状态的拖动框架的粗细。

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>备注

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 构造函数将此成员初始化为三个像素。

## <a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA：： m_nDragFrameThicknessFloat

指定用于指示浮动状态的拖动框架的粗细。

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>备注

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 构造函数将此成员初始化为 4 像素。

## <a name="onsettingchange"></a>AFX_GLOBAL_DATA：： OnSettingChange

检测桌面菜单动画和任务栏自动隐藏功能的当前状态。

```
void OnSettingChange();
```

### <a name="remarks"></a>备注

此方法将框架变量设置为用户桌面的某些属性的状态。 此方法检测菜单动画、菜单淡化和任务栏自动隐藏功能的当前状态。

## <a name="registerwindowclass"></a>AFX_GLOBAL_DATA：： RegisterWindowClass

注册指定的 MFC 窗口类。

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>参数

*lpszClassNamePrefix*<br/>
中要注册的窗口类的名称。

### <a name="return-value"></a>返回值

如果此方法成功，则为注册类的限定名称;否则为[资源异常](exception-processing.md#afxthrowresourceexception)。

### <a name="remarks"></a>备注

返回值是*lpszClassNamePrefix*参数字符串的以冒号分隔的列表，以及当前应用程序实例的句柄的十六进制文本表示形式;应用程序光标，它是标识符 IDC_ARROW 的箭头光标;和背景画笔。 有关注册 MFC 窗口类的详细信息，请参阅[AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)。

## <a name="resume"></a>AFX_GLOBAL_DATA：： Resume

重新初始化访问支持 Windows 主题和视觉样式的方法的内部函数指针。

```
BOOL Resume();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。 在调试模式下，此方法将断言此方法是否失败。

### <a name="remarks"></a>备注

当框架收到[WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast)消息时，将调用此方法。

## <a name="setlayeredattrib"></a>AFX_GLOBAL_DATA：： SetLayeredAttrib

提供了一种简单的方法来调用 Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) 方法。

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
中分层窗口的句柄。

*crKey*<br/>
中[桌面窗口管理器](/windows/win32/dwm/dwm-overview)用于撰写分层窗口的透明度颜色键。

*bAlpha*<br/>
中用于描述分层窗口的不透明度的 alpha 值。

dwFlags<br/>
中标志的按位组合（OR），指定要使用的方法参数。 指定 LWA_COLORKEY 使用*crKey*参数作为透明度颜色。 指定 LWA_ALPHA 使用*bAlpha*参数确定分层窗口的不透明度。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

## <a name="setmenufont"></a>AFX_GLOBAL_DATA：： SetMenuFont

创建指定的逻辑字体。

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

*lpLogFont*<br/>
中指向一个结构的指针，该结构包含字体的特性。

*bHorz*<br/>
中若要指定文本水平运行，则为 TRUE;若为 FALSE，则指定文本垂直运行。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。 在调试模式下，此方法将断言此方法是否失败。

### <a name="remarks"></a>备注

此方法创建一个水平普通字体、一个带下划线的字体以及在默认菜单项中使用的粗体字体。 此方法可选择创建常规竖线。 有关逻辑字体的详细信息，请参阅[CFont：： CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect)。

## <a name="updatefonts"></a>AFX_GLOBAL_DATA：： UpdateFonts

重新初始化框架使用的逻辑字体。

```
void UpdateFonts();
```

### <a name="remarks"></a>备注

有关逻辑焦点详细信息，请参阅 `CFont::CreateFontIndirect`。

## <a name="updatesyscolors"></a>AFX_GLOBAL_DATA：： UpdateSysColors

初始化框架使用的颜色、颜色深度、画笔、笔和图像。

```
void UpdateSysColors();
```

## <a name="biswindows7"></a>AFX_GLOBAL_DATA：： bIsWindows7

指示应用程序在 Windows 7 还是更高版本下执行。

```
BOOL bIsWindows7;
```

## <a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA：： clrActiveCaptionGradient

指定活动标题的渐变颜色。 通常用于停靠窗格。

```
COLORREF clrActiveCaptionGradient;
```

## <a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA：： clrInactiveCaptionGradient

指定非活动标题的渐变颜色。 通常用于停靠窗格。

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="getitaskbarlist"></a>AFX_GLOBAL_DATA：： GetITaskbarList

在全局数据中创建和存储指向 `ITaskBarList` 接口的指针。

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>返回值

如果创建任务栏列表对象成功，则为指向 `ITaskbarList` 接口的指针;如果创建失败或当前操作系统小于 Windows 7，则为 NULL。

## <a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA：： GetITaskbarList3

在全局数据中创建和存储指向 `ITaskBarList3` 接口的指针。

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>返回值

如果创建任务栏列表对象成功，则为指向 `ITaskbarList3` 接口的指针;如果创建失败或当前操作系统小于 Windows 7，则为 NULL。

## <a name="getshellautohidebars"></a>AFX_GLOBAL_DATA：： GetShellAutohideBars

确定 Shell 自动隐藏栏的位置。

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>返回值

一个整数值，它具有指定自动隐藏栏的位置的编码标志。 它可能会组合以下值： AFX_AUTOHIDE_BOTTOM、AFX_AUTOHIDE_TOP、AFX_AUTOHIDE_LEFT AFX_AUTOHIDE_RIGHT。

## <a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA：： ReleaseTaskBarRefs

释放通过 `GetITaskbarList` 和 `GetITaskbarList3` 方法获取的接口。

```
void ReleaseTaskBarRefs();
```

## <a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA：： ShellCreateItemFromParsingName

创建并初始化分析名称中的 Shell 项对象。

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>参数

*pszPath*<br/>
中指向显示名称的指针。

*pbc*<br/>
指向控制分析操作的绑定上下文的指针。

*riid*<br/>
对接口 ID 的引用。

*ppv*<br/>
弄如果此函数返回，则包含在*riid*中请求的接口指针。 这通常将 `IShellItem` 或 `IShellItem2`。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK;否则为错误值。

## <a name="see-also"></a>另请参阅

[层次结构图](../hierarchy-chart.md)<br/>
[结构、样式、回调和消息映射](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[部件和状态](/windows/win32/controls/parts-and-states)<br/>
[CDC：:D rawText](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[桌面窗口管理器](/windows/win32/dwm/dwm-overview)<br/>
[启用和控制 DWM 组合](/windows/win32/dwm/composition-ovw)<br/>
[UI 自动化和 Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[GetSysColor 函数](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[NONCLIENTMETRICS 结构](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
