---
title: "CMFCDesktopAlertWnd 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
dev_langs: C++
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cfebb488921d81c36f842885ad49eae3f40a37fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class
`CMFCDesktopAlertWnd`类实现的无模式对话框中显示的功能在屏幕上以通知用户有关的事件。  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>语法  
  
```  
class CMFCDesktopAlertWnd : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Cmfcdesktopalertwnd:: Create](#create)|创建并初始化在桌面警报窗口。|  
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|返回动画速度。|  
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|返回的动画类型。|  
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|返回自动关闭超时值。|  
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|返回标题的高度。|  
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||  
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|在屏幕上返回在桌面警报窗口的最后一个有效位置。|  
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|返回的透明度级别。|  
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|确定是否使用小标题显示在桌面警报窗口。|  
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||  
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|当用户单击链接按钮位于在桌面警报菜单上，由框架调用。|  
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|当用户从菜单中，选择一个项，子控件将发送一条通知消息，或转换快捷键击键时，框架将调用此成员函数。 (重写[CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand)。)|  
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||  
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||  
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|设置新动画速度。|  
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|将动画类型设置。|  
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|设置自动关闭超时值。|  
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|小型和正常标题之间切换。|  
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|设置的透明度级别。|  
  
## <a name="remarks"></a>备注  
 桌面警报窗口可以是透明的它可以显示的动画效果，它可能会消失 （指定延迟后或通过单击关闭按钮，用户就可以关闭它时）。  
  
 桌面警报窗口还可以包含一个默认对话框，其中又包含一个图标、 消息文本 （标签） 和链接。 或者，桌面警报窗口可以包含自定义对话框从应用程序的资源。  
  
 在两个步骤中创建桌面警报窗口。 首先，调用的构造函数来构造`CMFCDesktopAlertWnd`对象。 其次，调用[cmfcdesktopalertwnd:: Create](#create)成员函数以创建窗口并将其附加到`CMFCDesktopAlertWnd`对象。  
  
 `CMFCDesktopAlertWnd`对象创建填满在桌面警报窗口工作区的特殊子对话框框。 对话框拥有定位于它的所有控件。  
  
 若要在弹出窗口中显示自定义对话框中，请按照下列步骤：  
  
1.  从 `CMFCDesktopAlertDialog` 派生一个类。  
  
2.  在资源中创建子对话框模板。  
  
3.  调用[cmfcdesktopalertwnd:: Create](#create)使用对话框模板和指向派生类的运行时类信息的资源 ID。  
  
4.  程序自定义对话框中，以处理来自托管控件中，所有通知或对托管的控件进行编程直接都处理这些通知。  
  
 使用以下函数来控制在桌面警报窗口的行为：  
  
-   通过调用设置动画类型[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)。 有效选项包括展开、 幻灯片，和淡入淡出。  
  
-   通过调用设置动画帧速度[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)。  
  
-   通过调用设置透明度级别[CMFCDesktopAlertWnd::SetTransparency](#settransparency)。  
  
-   通过调用将标题的大小更改为小[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)。 小标题为 7 像素高。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCDesktopAlertWnd`用于配置类`CMFCDesktopAlertWnd`对象。 该示例演示如何将动画类型，将弹出窗口的透明度设置、 指定通知窗口显示小标题，并将通知窗口会自动关闭之前经过的时间。 该示例还演示如何创建和初始化在桌面警报窗口。 此代码片段属于[桌面警报演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxDesktopAlertWnd.h  
  
##  <a name="create"></a>Cmfcdesktopalertwnd:: Create  
 创建并初始化在桌面警报窗口。  
  
```  
virtual BOOL Create(
    CWnd* pWndOwner,  
    UINT uiDlgResID,  
    HMENU hMenu = NULL,  
    CPoint ptPos = CPoint(-1,-1),  
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));

 
virtual BOOL Create(
    CWnd* pWndOwner,  
    CMFCDesktopAlertWndInfo& params,  
    HMENU hMenu = NULL,  
    CPoint ptPos = CPoint(-1,-1));
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pWndOwner`  
 指定的通知窗口的所有者。 然后，该所有者将收到在桌面警报窗口的所有的通知。 此值不能为 `NULL`。  
  
 [in] `uiDlgResID`  
 指定通知窗口的资源的 ID。  
  
 [in] `hMenu`  
 指定当用户单击的菜单按钮时显示的菜单。 如果`NULL`，不显示的菜单按钮。  
  
 [in] `ptPos`  
 指定通知窗口的显示位置的初始位置，则使用屏幕坐标。 如果此参数为 （-1，则为-1），通知窗口被显示在屏幕右下角。  
  
 [in] `pRTIDlgBar`  
 介绍通知窗口的工作区的自定义的对话框类的运行时类信息。  
  
 [in] `params`  
 指定用于创建警报的窗口的参数。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则创建通知窗口否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以创建警报的窗口。 通知窗口的工作区包含承载向用户显示的所有控件的子对话框。  
  
 第一个方法重载创建警报的窗口，其中包含从应用程序的资源加载一个子对话框。 第一个方法重载还可以指定的自定义对话框类的运行时类信息。  
  
 第二个方法重载创建警报的窗口，其中包含默认控件。 你可以指定它可以控制要显示通过修改[CMFCDesktopAlertWndInfo 类](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)。  
  
##  <a name="getanimationspeed"></a>CMFCDesktopAlertWnd::GetAnimationSpeed  
 返回动画速度。  
  
```  
UINT GetAnimationSpeed() const;  
```  
  
### <a name="return-value"></a>返回值  
 通知窗口，以毫秒为单位动画速度。  
  
### <a name="remarks"></a>备注  
 动画速度描述通知窗口打开和关闭的速度。  
  
##  <a name="getanimationtype"></a>CMFCDesktopAlertWnd::GetAnimationType  
 返回的动画类型。  
  
```  
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```  
  
### <a name="return-value"></a>返回值  
 以下的动画类型之一：  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="getautoclosetime"></a>CMFCDesktopAlertWnd::GetAutoCloseTime  
 返回自动关闭超时值。  
  
```  
int GetAutoCloseTime() const;  
```  
  
### <a name="return-value"></a>返回值  
 时间，以毫秒为单位，此后通知窗口将自动关闭。  
  
### <a name="remarks"></a>备注  
 使用此方法以确定要通知窗口将自动关闭之前，应经过多长时间。  
  
##  <a name="getcaptionheight"></a>CMFCDesktopAlertWnd::GetCaptionHeight  
 返回标题的高度。  
  
```  
virtual int GetCaptionHeight();
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位的标题高度。  
  
### <a name="remarks"></a>备注  
 可以在派生类中重写此方法。 默认实现任一： 返回的小标题高度值 （7 像素为单位），如果小标题或从 Windows API 函数获取的值，应显示弹出窗口`GetSystemMetrics(SM_CYSMCAPTION)`。  
  
##  <a name="getlastpos"></a>CMFCDesktopAlertWnd::GetLastPos  
 在屏幕上返回在桌面警报窗口的最后一个位置。  
  
```  
CPoint GetLastPos() const;  
```  
  
### <a name="return-value"></a>返回值  
 屏幕坐标中的点。  
  
### <a name="remarks"></a>备注  
 此方法返回在屏幕上的通知窗口的最后一个有效位置。  
  
##  <a name="gettransparency"></a>CMFCDesktopAlertWnd::GetTransparency  
 返回的透明度级别。  
  
```  
BYTE GetTransparency() const;  
```  
  
### <a name="return-value"></a>返回值  
 介于 0 和 255，非独占透明度级别。 值越大，详细的不透明窗口。  
  
### <a name="remarks"></a>备注  
 使用此方法来检索当前的通知窗口的透明度级别。  
  
##  <a name="hassmallcaption"></a>CMFCDesktopAlertWnd::HasSmallCaption  
 确定在桌面警报窗口是否具有一个小的标题或常规大小标题。  
  
```  
BOOL HasSmallCaption() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果弹出窗口显示与小标题;`FALSE`如果带有常规大小标题显示弹出窗口。  
  
### <a name="remarks"></a>备注  
 使用此方法以确定弹出窗口的一个小的标题或常规大小标题。 默认情况下，小标题是 7 像素高。 你可以通过调用 Windows API 函数获取常规大小标题的高度`GetSystemMetrics(SM_CYCAPTION)`。  
  
##  <a name="onbeforeshow"></a>CMFCDesktopAlertWnd::OnBeforeShow  

  
```  
virtual BOOL OnBeforeShow(CPoint&);
```  
  
### <a name="parameters"></a>参数  
 [in] `CPoint&`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onclicklinkbutton"></a>CMFCDesktopAlertWnd::OnClickLinkButton  
 当用户单击链接按钮位于在桌面警报菜单上，由框架调用。  
  
```  
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 未使用此参数。  
  
### <a name="return-value"></a>返回值  
 总是为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 如果你想要被通知用户单击通知窗口上的链接时，重写此方法在派生类。  
  
##  <a name="oncommand"></a>CMFCDesktopAlertWnd::OnCommand  

  
```  
virtual BOOL OnCommand(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 [in] `wParam`  
 [in] `lParam`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondraw"></a>CMFCDesktopAlertWnd::OnDraw  

  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="remarks"></a>备注  
  
##  <a name="processcommand"></a>CMFCDesktopAlertWnd::ProcessCommand  

  
```  
BOOL ProcessCommand(HWND hwnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `hwnd`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="setanimationspeed"></a>CMFCDesktopAlertWnd::SetAnimationSpeed  
 设置新动画速度。  
  
```  
void SetAnimationSpeed(UINT nSpeed);
```  
  
### <a name="parameters"></a>参数  
 [in] `nSpeed`  
 指定新动画速度，以毫秒为单位。  
  
### <a name="remarks"></a>备注  
 调用此方法以设置通知窗口的动画速度。 默认动画速度为 30 毫秒。  
  
##  <a name="setanimationtype"></a>CMFCDesktopAlertWnd::SetAnimationType  
 将动画类型设置。  
  
```  
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```  
  
### <a name="parameters"></a>参数  
 [in] `type`  
 指定动画类型。  
  
### <a name="remarks"></a>备注  
 调用此方法以设置动画类型。 可以指定以下值之一：  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="setautoclosetime"></a>CMFCDesktopAlertWnd::SetAutoCloseTime  
 设置自动关闭超时值。  
  
```  
void SetAutoCloseTime(int nTime);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTime`  
 经过通知窗口自动关闭之前的时间，以毫秒为单位。  
  
### <a name="remarks"></a>备注  
 如果用户不进行交互的窗口在指定时间后自动关闭通知窗口。  
  
##  <a name="setsmallcaption"></a>CMFCDesktopAlertWnd::SetSmallCaption  
 小型和常规大小标题之间切换。  
  
```  
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSmallCaption`  
 `TRUE`若要指定通知窗口显示小标题;否则为`FALSE`指定通知窗口显示常规大小标题。  
  
### <a name="remarks"></a>备注  
 调用此方法以显示小型或常规大小标题。 默认情况下，小标题是 7 像素高。 你可以通过调用 Windows API 函数获取的正则标题大小`GetSystemMetrics(SM_CYCAPTION)`。  
  
##  <a name="settransparency"></a>CMFCDesktopAlertWnd::SetTransparency  
 设置弹出窗口的透明度级别。  
  
```  
void SetTransparency(BYTE nTransparency);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTransparency`  
 指定透明度级别。 此值必须介于 0 和 255，（含) 之间。 值越大，详细的不透明窗口。  
  
### <a name="remarks"></a>备注  
 调用此函数可设置弹出窗口的透明度级别。  
  
##  <a name="getdialogsize"></a>CMFCDesktopAlertWnd::GetDialogSize  

  
```  
virtual CSize GetDialogSize();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWndInfo 类](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [CMFCDesktopAlertDialog 类](../../mfc/reference/cmfcdesktopalertdialog-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)
