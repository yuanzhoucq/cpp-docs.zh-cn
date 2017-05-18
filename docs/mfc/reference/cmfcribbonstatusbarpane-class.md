---
title: "CMFCRibbonStatusBarPane 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonStatusBarPane class
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
caps.latest.revision: 31
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a101e50f55efab44e4cb66d314b2426228dbc5c0
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|返回用于定义可以不截断的情况下窗格中显示的最长的文本字符串的字符串。|  
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|返回的文本对齐方式的当前设置。|  
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|确定是否正在执行动画。|  
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|确定是否窗格中位于功能区状态栏扩展区域中。|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(重写[CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder)。)|  
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(重写[CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground)。)|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|定义可以不截断的情况下窗格中显示的最长的文本字符串。|  
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|将可用于动画的图像列表分配给窗格中。|  
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|设置文本对齐方式。|  
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|启动分配给窗格中的动画。|  
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|停止分配给窗格中的动画。 。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|当分配给窗格中的动画停止时由框架调用。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 `CMFCRibbonStatusBarPane` 类中的各种方法。 该示例演示如何构造`CMFCRibbonStatusBarPane`对象，设置状态栏窗格的标签的文本对齐方式，定义可以显示在状态栏窗格中的不截断的情况下，将可用于动画，并启动动画的图像列表附加到状态栏窗格的最长文本。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&2;](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxribbonstatusbarpane.h  
  
##  <a name="cmfcribbonstatusbarpane"></a>CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane  
 构建在状态栏中的窗格中对象。  
  
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
 指定窗格中的命令 ID。  
  
 [in] `lpszText`  
 指定要在窗格中显示的文本字符串。  
  
 [in] `bIsStatic`  
 如果`TRUE`，不能通过单击选择或突出显示状态窗格。  
  
 [in] `hIcon`  
 指定要在窗格中显示的图标的句柄。  
  
 [in] `lpszAlmostLargeText`  
 指定可以通过窗格中显示的最长的文本字符串。  
  
 [in] `hBmpAnimationList`  
 指定用于动画的图像列表的句柄。  
  
 [in] `cxAnimation`  
 指定以像素为单位用于动画的图像列表中的图标的宽度。  
  
 [in] `clrTrnsp`  
 用于动画的图像列表中指定图像的透明色。  
  
 [in] `uiAnimationListResID`  
 指定用于动画的图像列表的资源 ID。  
  
##  <a name="getalmostlargetext"></a>CMFCRibbonStatusBarPane::GetAlmostLargeText  
 获取状态栏窗格可以显示的最长的文本字符串。  
  
```  
LPCTSTR GetAlmostLargeText() const;  
```  
  
### <a name="return-value"></a>返回值  
 状态栏窗格可以显示最长的文本字符串。  
  
##  <a name="gettextalign"></a>CMFCRibbonStatusBarPane::GetTextAlign  
 获取状态栏窗格的标签的文本对齐方式的当前设置。  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前文本对齐方式可以是以下项之一︰  
  
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
 确定是否窗格中位于功能区状态栏扩展区域中。  
  
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
 分配给窗格中的动画结束时，框架将调用此方法。  
  
```  
virtual void OnFinishAnimation();
```  
  
### <a name="remarks"></a>备注  
 `StopAnimation`方法调用`OnFinishAnimation`方法，可用于动画结束时清理数据。  
  
##  <a name="setalmostlargetext"></a>CMFCRibbonStatusBarPane::SetAlmostLargeText  
 定义可以在无间断状态栏窗格中显示的最长文本。  
  
```  
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszAlmostLargeText`  
 指定可以在无间断状态栏窗格中显示的最长字符串。  
  
### <a name="remarks"></a>备注  
 该库计算文本的大小，`lpszAlmostLargeText`指定，并相应地调整窗格的大小。 如果它仍不适合在窗格中，文本将被截断。  
  
##  <a name="setanimationlist"></a>CMFCRibbonStatusBarPane::SetAnimationList  
 将可用于动画的图像列表附加到状态栏窗格。  
  
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
 指定宽度，以像素为单位的图像列表中的帧。  
  
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
 `nAlign`可以具有下列值之一︰  
  
- `TA_LEFT`︰ 左对齐  
  
- `TA_CENTER:`居中对齐  
  
- `TA_RIGHT:`右对齐  
  
##  <a name="startanimation"></a>CMFCRibbonStatusBarPane::StartAnimation  
 启动动画，您将分配给窗格中。  
  
```  
void StartAnimation(
    UINT nFrameDelay=500,  
    UINT nDuration=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `nFrameDelay`  
 指定动画帧速率，以毫秒为单位。  
  
 [in] `nDuration`  
 指定多长时间播放动画，以毫秒为单位。 使用-1 表示无限循环。  
  
### <a name="remarks"></a>备注  
 您必须指定图像列表的句柄，然后才能调用`StartAnimation`使用`SetAnimationList`。  
  
##  <a name="stopanimation"></a>CMFCRibbonStatusBarPane::StopAnimation  
 停止分配给状态栏窗格的动画。  
  
```  
void StopAnimation();
```  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonStatusBar 类](../../mfc/reference/cmfcribbonstatusbar-class.md)

