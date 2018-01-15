---
title: "CMFCRibbonStatusBarPane 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e3d5059adf0ebbd1ed651d57354ae73beadb919f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane 类
`CMFCRibbonStatusBarPane`类实现可添加到功能区状态栏的功能区元素。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonStatusBarPane : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|构造并初始化一个 `CMFCRibbonStatusBarPane` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|返回用于定义可以而不发生截断的窗格中显示的文本字符串最长的字符串。|  
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|返回的文本对齐方式的当前设置。|  
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|确定是否正在执行动画。|  
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|确定窗格是否位于功能区状态栏扩展区域中。|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(重写[CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder)。)|  
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(重写[CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground)。)|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|定义可以而不发生截断的窗格中显示的最长文本字符串。|  
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|将可用于动画的图像列表分配到窗格中。|  
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|设置的文本对齐方式。|  
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|启动分配给窗格动画。|  
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|停止分配给窗格动画。 .|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|当分配给窗格动画停止时，由框架调用。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 `CMFCRibbonStatusBarPane` 类中的各种方法。 该示例演示如何构造`CMFCRibbonStatusBarPane`对象，设置状态栏窗格的标签的文本对齐方式，定义可以显示在状态栏窗格中的不截断的情况下，将附加到状态栏窗格可以用于图像列表的最长文本nimation，并开始动画。  
  
 [!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxribbonstatusbarpane.h  
  
##  <a name="cmfcribbonstatusbarpane"></a>CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane  
 构造状态栏中的窗格对象。  
  
```  
CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    BOOL bIsStatic=FALSE,  
    HICON hIcon=NULL,  
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nCmdID`  
 指定的命令 ID 的窗格。  
  
 [in] `lpszText`  
 指定要在窗格中显示的文本字符串。  
  
 [in] `bIsStatic`  
 如果`TRUE`，无法突出显示或通过单击选择状态窗格。  
  
 [in] `hIcon`  
 指定要在窗格中显示的图标的句柄。  
  
 [in] `lpszAlmostLargeText`  
 指定可以在窗格中显示的最长文本字符串。  
  
 [in] `hBmpAnimationList`  
 指定用于动画的图像列表的句柄。  
  
 [in] `cxAnimation`  
 指定宽度，以像素为单位，用于动画的图像列表中的图标。  
  
 [in] `clrTrnsp`  
 用于动画的图像列表中指定图像的透明色。  
  
 [in] `uiAnimationListResID`  
 指定图像列表用于动画的资源的 ID。  
  
##  <a name="getalmostlargetext"></a>CMFCRibbonStatusBarPane::GetAlmostLargeText  
 获取状态栏窗格可以显示的最长文本字符串。  
  
```  
LPCTSTR GetAlmostLargeText() const;  
```  
  
### <a name="return-value"></a>返回值  
 状态栏窗格可以显示最长的文本字符串。  
  
##  <a name="gettextalign"></a>CMFCRibbonStatusBarPane::GetTextAlign  
 获取当前设置的状态栏窗格的标签的文本对齐方式。  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前文本对齐方式可以是下列项之一：  
  
-   TA_LEFT  
  
-   TA_CENTER  
  
-   TA_RIGHT。  
  
##  <a name="isanimation"></a>CMFCRibbonStatusBarPane::IsAnimation  
 确定是否正在执行动画。  
  
```  
BOOL IsAnimation() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果动画正在进行;`FALSE`否则为。  
  
##  <a name="isextended"></a>CMFCRibbonStatusBarPane::IsExtended  
 确定窗格是否位于功能区状态栏扩展区域中。  
  
```  
BOOL IsExtended() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格上状态栏扩展区域中。 否则为 `FALSE`。  
  
##  <a name="ondrawborder"></a>CMFCRibbonStatusBarPane::OnDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawBorder(CDC*);
```  
  
### <a name="parameters"></a>参数  
 [in] `CDC*`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onfillbackground"></a>CMFCRibbonStatusBarPane::OnFillBackground  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onfinishanimation"></a>CMFCRibbonStatusBarPane::OnFinishAnimation  
 分配给窗格动画结束时，框架将调用此方法。  
  
```  
virtual void OnFinishAnimation();
```  
  
### <a name="remarks"></a>备注  
 `StopAnimation`方法调用`OnFinishAnimation`方法，可用于动画结束时清理数据。  
  
##  <a name="setalmostlargetext"></a>CMFCRibbonStatusBarPane::SetAlmostLargeText  
 定义可以不截断的情况下的状态栏窗格中显示的最长文本。  
  
```  
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszAlmostLargeText`  
 指定可以显示在状态栏窗格而不发生截断的最长字符串。  
  
### <a name="remarks"></a>备注  
 库计算文本的大小，`lpszAlmostLargeText`指定并相应地调整窗格的大小。 如果它仍不适合在窗格中，文本将被截断。  
  
##  <a name="setanimationlist"></a>CMFCRibbonStatusBarPane::SetAnimationList  
 将附加到状态栏窗格可以用于动画的图像列表。  
  
```  
void SetAnimationList(
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```  
  
### <a name="parameters"></a>参数  
 [in] `hBmpAnimationList`  
 指定图像列表的句柄。  
  
 [in] `cxAnimation`  
 指定宽度，以像素为单位，在图像列表的框架。  
  
 [in] `clrTransp`  
 指定的图像列表的透明颜色。  
  
 [in] `uiAnimationListResID`  
 指定的图像列表的资源 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果图像列表已成功附加到状态栏窗格;`FALSE`否则为。  
  
##  <a name="settextalign"></a>CMFCRibbonStatusBarPane::SetTextAlign  
 设置状态栏窗格的标签的文本对齐方式。  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>参数  
 [in] `nAlign`  
 指定的文本对齐方式。  
  
### <a name="remarks"></a>备注  
 `nAlign`可以具有以下值之一：  
  
- `TA_LEFT`： 左对齐  
  
- `TA_CENTER:`居中对齐  
  
- `TA_RIGHT:`右对齐  
  
##  <a name="startanimation"></a>CMFCRibbonStatusBarPane::StartAnimation  
 启动分配到窗格中显示的动画。  
  
```  
void StartAnimation(
    UINT nFrameDelay=500,  
    UINT nDuration=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `nFrameDelay`  
 指定动画帧速率，单位为毫秒。  
  
 [in] `nDuration`  
 指定播放动画，以毫秒为单位的时间。 使用-1 表示无限循环。  
  
### <a name="remarks"></a>备注  
 你在调用之前，必须指定图像列表的句柄`StartAnimation`使用`SetAnimationList`。  
  
##  <a name="stopanimation"></a>CMFCRibbonStatusBarPane::StopAnimation  
 停止动画分配给状态栏窗格。  
  
```  
void StopAnimation();
```  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonStatusBar 类](../../mfc/reference/cmfcribbonstatusbar-class.md)
