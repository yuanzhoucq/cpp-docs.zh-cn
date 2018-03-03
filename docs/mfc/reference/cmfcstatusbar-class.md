---
title: "CMFCStatusBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
dev_langs:
- C++
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a235b88b676f7cf643a878e9a06408c87b20bcba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar 类
`CMFCStatusBar`类实现类似于状态栏`CStatusBar`类。 但是， `CMFCStatusBar` 类具有 `CStatusBar` 类未提供的功能，例如显示图像、动画和进度栏的功能，以及对鼠标双击作出响应的功能。 

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]   
  
## <a name="syntax"></a>语法  
  
```  
class CMFCStatusBar : public CPane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(重写[cbasepane:: Calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|  
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||  
|[CMFCStatusBar::Create](#create)|创建的控件条，并将其附加到[CPane](../../mfc/reference/cpane-class.md)对象。 (重写[cpane:: Create](../../mfc/reference/cpane-class.md#create)。)|  
|[CMFCStatusBar::CreateEx](#createex)|创建的控件条，并将其附加到[CPane](../../mfc/reference/cpane-class.md)对象。 (重写[cpane:: Createex](../../mfc/reference/cpane-class.md#createex)。)|  
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|确定是否另一个窗格可以动态地插入此窗格之间的父框架。 (重写[cbasepane:: Doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)。)|  
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|启用或禁用在状态栏双击鼠标的处理。|  
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|在指定的窗格中显示一个进度栏。|  
|[CMFCStatusBar::GetCount](#getcount)|在状态栏上返回窗格的数。|  
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||  
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||  
|[CMFCStatusBar::GetItemID](#getitemid)||  
|[CMFCStatusBar::GetItemRect](#getitemrect)||  
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||  
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||  
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|返回的窗格样式。 (重写[CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle)。)|  
|[CMFCStatusBar::GetPaneText](#getpanetext)||  
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|返回宽度，以像素为单位，指定窗格的状态栏。|  
|[CMFCStatusBar::GetTipText](#gettiptext)|返回指定的窗格的状态栏的工具提示文本。|  
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|使无效指定的窗格并重绘其内容。|  
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|由框架创建附加到此 Windows 窗口之前调用`CWnd`对象。 (重写[CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)。)|  
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||  
|[CMFCStatusBar::SetIndicators](#setindicators)||  
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|将动画分配给指定的窗格中。|  
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|设置指定的状态栏窗格的背景色。|  
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|设置状态栏的指定窗格中的指示器图标。|  
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||  
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|设置状态栏的指定窗格中的进度栏的当前进度。|  
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|设置窗格中的样式。 (重写[CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle)。)|  
|[CMFCStatusBar::SetPaneText](#setpanetext)||  
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|设置状态栏的指定窗格中的文本颜色。|  
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|以像素为单位指定窗格的状态栏设置的宽度。|  
|[CMFCStatusBar::SetTipText](#settiptext)|设置状态栏的指定窗格中的工具提示文本。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|当它重绘的状态栏窗格中时，由框架调用。|  
  
## <a name="remarks"></a>备注  
 下图显示了从状态栏的图[状态栏演示示例](../../visual-cpp-samples.md)应用程序。  
  
 ![Cmfcstatusbar 示例](../../mfc/reference/media/cmfcstatusbar.png "cmfcstatusbar")  
  
## <a name="example"></a>示例  
 下面的示例演示应用程序使用调用中的各种方法的本地变量`CMFCStatusBar`类。 StatusBarDemoView.h 中声明这些变量。 主框架在 MainFrm.h 中声明、 文档声明中 StatusBarDemoDoc.h，和在 StatusBarDemoView.h 中声明视图。 此代码片段属于[状态栏演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]  
  
## <a name="example"></a>示例  
 下面的示例演示如何获取对引用`CMFCStatusBar`对象，它引入了`GetStatusBar`方法在 MainFrm.h，然后再调用此方法从`GetStatusBar`StatusBarDemoView.h 中的方法。 此代码片段属于[状态栏演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]  
  
## <a name="example"></a>示例  
 下面的示例演示如何调用中的各种方法`CMFCStatusBar`StatusBarDemoView.cpp 中的类。 在 MainFrm.h 中声明的常量。 该示例演示如何设置图标、 设置状态栏窗格的工具提示文本，在指定的窗格中显示一个进度条、 将动画分配给指定的窗格中，设置文本和状态栏窗格的宽度以及设置 progr 的当前进度指示器状态栏窗格的 ess 栏。 此代码片段属于[状态栏演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxstatusbar.h  
  
##  <a name="calcfixedlayout"></a>CMFCStatusBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数  
 [in] `bStretch`  
 [in] `bHorz`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="commandtoindex"></a>CMFCStatusBar::CommandToIndex  

  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nIDFind`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="create"></a>CMFCStatusBar::Create  

  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParentWnd`  
 [in] `dwStyle`  
 [in] `nID`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="createex"></a>CMFCStatusBar::CreateEx  

  
```  
BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParentWnd`  
 [in] `dwCtrlStyle`  
 [in] `dwStyle`  
 [in] `nID`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="doesallowdyninsertbefore"></a>CMFCStatusBar::DoesAllowDynInsertBefore  

  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="enablepanedoubleclick"></a>CMFCStatusBar::EnablePaneDoubleClick  
 启用或禁用在状态栏双击鼠标的处理。  
  
```  
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 如果`TRUE`，启用处理鼠标双击。 否则禁用鼠标双击的处理。  
  
### <a name="remarks"></a>备注  
 如果启用了状态栏，来处理两次单击，Windows 会将发送`WM_COMMAND`用户双击状态栏窗格上每次状态栏的通知以及向所有者的资源 ID。  
  
##  <a name="enablepaneprogressbar"></a>CMFCStatusBar::EnablePaneProgressBar  
 在指定的窗格中显示一个进度条。  
  
```  
void EnablePaneProgressBar(
    int nIndex,  
    long nTotal=100,  
    BOOL bDisplayText=FALSE,  
    COLORREF clrBar=-1,  
    COLORREF clrBarDest=-1,  
    COLORREF clrProgressText=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定的窗格中的索引启用其进度栏。  
  
 [in] `nTotal`  
 指定进度栏的最大值。  
  
 [in] `bDisplayText`  
 指定进度栏是否应显示当前进度值。  
  
 [in] `clrBar`  
 指定进度栏的背景色。  
  
 [in] `clrBarDest`  
 指定进度栏背景辅助颜色。 使用不同的值`clrBar`通过融入到渐变的颜色填充。  
  
 [in] `clrProgressText`  
 指定的文本的进度栏的颜色。  
  
### <a name="remarks"></a>备注  
 如果你想要禁用进度栏调用`EnablePaneProgressBar`与`nTotal`设置为-1。 默认情况下`nTotal`将设置为 100。 因此，你不需要任何附加的计算，显示为百分比的进度。  
  
 您应为传递不同的值`clrBar`和`clrBarDest`以便进度栏的背景色显示融入到渐变颜色。 .  
  
 若要设置当前进度，调用[CMFCStatusBar::SetPaneProgress](#setpaneprogress)方法。  
  
##  <a name="getcount"></a>CMFCStatusBar::GetCount  
 检索状态栏中的窗格的数。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在状态栏中的窗格数。  
  
##  <a name="getdrawextendedarea"></a>CMFCStatusBar::GetDrawExtendedArea  

  
```  
BOOL GetDrawExtendedArea() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getextendedarea"></a>CMFCStatusBar::GetExtendedArea  

  
```  
virtual BOOL GetExtendedArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getitemid"></a>CMFCStatusBar::GetItemID  

  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getitemrect"></a>CMFCStatusBar::GetItemRect  

  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 [in] `lpRect`  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpaneinfo"></a>CMFCStatusBar::GetPaneInfo  

  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 [in] `nID`  
 [in] `nStyle`  
 [in] `cxWidth`  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpaneprogress"></a>CMFCStatusBar::GetPaneProgress  

  
```  
long GetPaneProgress(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpanestyle"></a>CMFCStatusBar::GetPaneStyle  

  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpanetext"></a>CMFCStatusBar::GetPaneText  

  
```  
void GetPaneText(
    int nIndex,  
    CString& s) const;  
  
CString GetPaneText(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 [in] `s`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpanewidth"></a>CMFCStatusBar::GetPaneWidth  
 检索的状态栏窗格的宽度。  
  
```  
int GetPaneWidth(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定状态栏窗格中的索引。  
  
### <a name="return-value"></a>返回值  
 状态栏窗格的宽度，`nIndex`指定; 否则为零如果状态栏窗格中不存在。  
  
##  <a name="gettiptext"></a>CMFCStatusBar::GetTipText  
 检索一个状态栏窗格中的工具提示文本。  
  
```  
CString GetTipText(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定为其检索工具提示文本窗格中的索引。  
  
### <a name="return-value"></a>返回值  
 状态栏窗格的工具提示文本的`nIndex`指定。 否则为空字符串如果状态栏窗格中不存在指定`nIndex`或其工具提示文本是否为空。  
  
##  <a name="invalidatepanecontent"></a>CMFCStatusBar::InvalidatePaneContent  
 使失效状态栏窗格以及重绘其内容。  
  
```  
void InvalidatePaneContent(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定其内容是失效并在重绘的窗格中的索引。  
  
### <a name="remarks"></a>备注  
 当状态栏将失效时，则将它标记为重绘。 Windows 重绘时`UpdateWindow`方法发送`WM_PAINT`消息`OnPaint`方法。  
  
##  <a name="ondrawpane"></a>CMFCStatusBar::OnDrawPane  
 重绘状态栏的窗格。  
  
```  
virtual void OnDrawPane(
    CDC* pDC,  
    CMFCStatusBarPaneInfo* pPane);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的绘图区域。  
  
 [in] `pPane`  
 指向的指针`CMFCStatusBarPaneInfo`结构，其中包含有关要重新绘制的窗格中的信息。  
  
### <a name="remarks"></a>备注  
 默认情况下，`OnDrawPane`通过使用设备上下文重绘窗格`pDC`根据窗格的样式和内容。  
  
 重写此方法在`CMFCStatusBar`-派生类以自定义窗格的外观。  
  
##  <a name="precreatewindow"></a>CMFCStatusBar::PreCreateWindow  

  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>参数  
 [in] `cs`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="setdrawextendedarea"></a>CMFCStatusBar::SetDrawExtendedArea  

  
```  
void SetDrawExtendedArea(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setindicators"></a>CMFCStatusBar::SetIndicators  

  
```  
BOOL SetIndicators(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpIDArray`  
 [in] `nIDCount`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpaneanimation"></a>CMFCStatusBar::SetPaneAnimation  
 将动画分配给指定的窗格中。  
  
```  
void SetPaneAnimation(
    int nIndex,  
    HIMAGELIST hImageList,  
    UINT nFrameRate=500,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定你想要向其分配一种动画效果的窗格中的索引。  
  
 [in] `hImageList`  
 指定包含动画帧的图像列表的句柄。  
  
 [in] `nFrameRate`  
 指定以毫秒为单位，用于动画帧速率。  
  
 [in] `bUpdate`  
 如果`TRUE`，立即更新在窗格中的内容。 否则，它失效时，被更新窗格的内容。  
  
### <a name="remarks"></a>备注  
 如果你想要禁用当前动画，调用`SetPaneAnimation`与`hImageList`设置为`NULL`。  
  
##  <a name="setpanebackgroundcolor"></a>CMFCStatusBar::SetPaneBackgroundColor  
 设置状态栏窗格的背景色。  
  
```  
void SetPaneBackgroundColor(
    int nIndex,  
    COLORREF clrBackground=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定为其设置新的背景色窗格中的索引。  
  
 [in] `clrBackground`  
 指定新的背景色。  
  
 [in] `bUpdate`  
 如果`TRUE`，立即更新在窗格中的内容。 否则前, 不会更新窗格内容窗格中失效另一种方法。  
  
##  <a name="setpaneicon"></a>CMFCStatusBar::SetPaneIcon  
 设置状态栏窗格的图标。  
  
```  
void SetPaneIcon(
    int nIndex,  
    HICON hIcon,  
    BOOL bUpdate=TRUE);

 
void SetPaneIcon(
    int nIndex,  
    HBITMAP hBmp,  
    COLORREF clrTransparent=RGB(255, 0, 255),  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定为其设置映像窗格中的索引。  
  
 [in] `hIcon`  
 指定要设置为窗格图像的图标的句柄。  
  
 [in] `bUpdate`  
 指定是否要立即更新窗格的内容。  
  
 [in] `hBmp`  
 指定要设置为窗格图像的位图的句柄。  
  
 [in] `clrTransparent`  
 指定位图的透明颜色，`hBmp`指示。  
  
### <a name="remarks"></a>备注  
 你可以传递`HICON`或`HBITMAP`以及设置窗格中的图像的透明色。 如果你不希望将不再显示图像，将传递`NULL`作为图像句柄的值。  
  
 如果没有任何正在运行的动画， [CMFCStatusBar::SetPaneAnimation](#setpaneanimation)已设置，动画将被停止。  
  
##  <a name="setpaneinfo"></a>CMFCStatusBar::SetPaneInfo  

  
```  
void SetPaneInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 [in] `nID`  
 [in] `nStyle`  
 [in] `cxWidth`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpaneprogress"></a>CMFCStatusBar::SetPaneProgress  
 设置指定的窗格中的进度栏的当前进度指示器。  
  
```  
void SetPaneProgress(
    int nIndex,  
    long nCurr,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定要更新进度指示器的窗格中的索引。  
  
 [in] `nCurr`  
 指定的进度指示器的当前值。  
  
 [in] `bUpdate`  
 指定是否应立即更新窗格。  
  
### <a name="remarks"></a>备注  
 如果你想要更新指定的窗格中的进度栏的进度指示器，请调用此方法。  
  
 若要为给定的窗格中使用此功能，必须调用[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)第一个。  
  
##  <a name="setpanestyle"></a>CMFCStatusBar::SetPaneStyle  

  
```  
void SetPaneStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 [in] `nStyle`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpanetext"></a>CMFCStatusBar::SetPaneText  

  
```  
virtual BOOL SetPaneText(
    int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bUpdate = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 [in] `lpszNewText`  
 [in] `bUpdate`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpanetextcolor"></a>CMFCStatusBar::SetPaneTextColor  
 设置指定的窗格中的文本颜色。  
  
```  
void SetPaneTextColor(
    int nIndex,  
    COLORREF clrText=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定你想要分配新的文本颜色的窗格中的索引。  
  
 [in] `clrText`  
 指定的文本颜色。  
  
 [in] `bUpdate`  
 如果`TRUE`，立即更新在窗格中的内容。 否则前, 不会更新窗格内容窗格中失效另一种方法。  
  
##  <a name="setpanewidth"></a>CMFCStatusBar::SetPaneWidth  
 设置状态栏窗格的宽度。  
  
```  
void SetPaneWidth(
    int nIndex,  
    int cx);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 为其设置新宽度状态栏窗格的索引。  
  
 [in] `cx`  
 新状态栏窗格，以像素为单位的宽度。  
  
##  <a name="settiptext"></a>CMFCStatusBar::SetTipText  
 设置状态栏窗格的工具提示文本。  
  
```  
void SetTipText(
    int nIndex,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 你想要分配的工具提示文本窗格中的索引。  
  
 [in] `pszTipText`  
 新的工具提示文本。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane 类](../../mfc/reference/cpane-class.md)   
 [CStatusBar 类](../../mfc/reference/cstatusbar-class.md)
