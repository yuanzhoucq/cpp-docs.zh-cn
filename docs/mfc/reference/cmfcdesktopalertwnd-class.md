---
title: "CMFCDesktopAlertWnd 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWnd class
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
caps.latest.revision: 33
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
ms.openlocfilehash: be9d81ffff003119aa7ff9e0cd100c575bd82d36
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class
`CMFCDesktopAlertWnd`类有关的事件通知用户在屏幕上实现的无模式对话框会显示此功能。  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>语法  
  
```  
class CMFCDesktopAlertWnd : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCDesktopAlertWnd::Create](#create)|创建并初始化在桌面警报窗口。|  
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|返回动画速度。|  
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|返回的动画类型。|  
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|返回自动关闭超时值。|  
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|返回的标题高度。|  
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||  
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|在屏幕上返回在桌面警报窗口的最后一个有效位置。|  
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|返回的透明度级别。|  
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|确定是否用小标题显示在桌面警报窗口。|  
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||  
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|由框架调用，当用户单击位于桌面警报菜单上的链接按钮。|  
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|当用户从菜单中，选择一个项，当子控件将发送一条通知消息，或者当转换加速器击键，框架将调用此成员函数。 (重写[CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand)。)|  
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||  
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||  
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|设置新的动画速度。|  
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|设置的动画类型。|  
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|设置自动关闭超时值。|  
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|小型和正常字幕之间切换。|  
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|设置的透明度级别。|  
  
## <a name="remarks"></a>备注  
 桌面警报窗口可以是透明的它可以出现的动画效果，（指定延迟后或当用户关闭它通过单击关闭按钮时），它就可能会消失。  
  
 桌面警报窗口还可以包含又包含一个图标、 消息文本 （标签） 和一个链接默认对话框。 或者，桌面警报窗口可包含从应用程序的资源的自定义对话框。  
  
 在两个步骤中创建桌面警报窗口。 首先，调用构造函数来构造`CMFCDesktopAlertWnd`对象。 其次，调用[CMFCDesktopAlertWnd::Create](#create)成员函数以创建窗口，然后将其附加到`CMFCDesktopAlertWnd`对象。  
  
 `CMFCDesktopAlertWnd`对象创建填充在桌面警报窗口的客户端区域的特殊子对话框。 对话框中拥有定位在其的所有控件。  
  
 若要在弹出窗口上显示一个自定义对话框，请按照下列步骤︰  
  
1.  从 `CMFCDesktopAlertDialog` 派生一个类。  
  
2.  创建子对话框模板资源中。  
  
3.  调用[CMFCDesktopAlertWnd::Create](#create)使用对话框模板和指向派生类的运行时类信息的资源 ID。  
  
4.  自定义对话框来处理来自托管控件的所有通知的程序或程序所承载的控件，可以直接都处理这些通知。  
  
 使用以下函数来控制在桌面警报窗口的行为︰  
  
-   通过调用设置动画类型[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)。 有效选项包括展开、 幻灯片，并淡入淡出。  
  
-   通过调用设置动画帧速度[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)。  
  
-   通过调用设置的透明度级别[CMFCDesktopAlertWnd::SetTransparency](#settransparency)。  
  
-   将标题的大小更改为小，通过调用[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)。 小标题为 7 像素高。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCDesktopAlertWnd`用于配置类`CMFCDesktopAlertWnd`对象。 该示例演示如何设置动画类型、 将弹出窗口的透明度设置、 指定警报窗口中显示的小标题和设置超时通知窗口会自动关闭之前经过的时间。 该示例还演示如何创建和初始化在桌面警报窗口。 此代码段属于[桌面警报演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo #&1;](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxDesktopAlertWnd.h  
  
##  <a name="create"></a>CMFCDesktopAlertWnd::Create  
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
 指定通知窗口的所有者。 该所有者将收到有关在桌面警报窗口的所有通知。 此值不能为 `NULL`。  
  
 [in] `uiDlgResID`  
 指定警报窗口中的资源 ID。  
  
 [in] `hMenu`  
 指定当用户单击菜单按钮时显示的菜单。 如果`NULL`，不显示菜单按钮。  
  
 [in] `ptPos`  
 指定通知窗口的显示位置的初始位置，请使用屏幕坐标。 如果此参数为 （-1，则为-1），通知窗口被显示在屏幕的右下角。  
  
 [in] `pRTIDlgBar`  
 介绍通知窗口的工作区的自定义对话框类的运行时类信息。  
  
 [in] `params`  
 指定用于创建警报的窗口的参数。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则创建的通知窗口否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以创建警报的窗口。 通知窗口的工作区包含承载向用户显示的所有控件的子对话框。  
  
 第一个方法重载创建一个警报窗口，其中包含从应用程序的资源加载的子对话框。 第一个方法重载还可以指定自定义对话框类的运行时类信息。  
  
 第二个方法重载将创建一个警报窗口，其中包含默认控件。 您可以指定哪些控件以显示通过修改[CMFCDesktopAlertWndInfo 类](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)。  
  
##  <a name="getanimationspeed"></a>CMFCDesktopAlertWnd::GetAnimationSpeed  
 返回动画速度。  
  
```  
UINT GetAnimationSpeed() const;  
```  
  
### <a name="return-value"></a>返回值  
 通知窗口，以毫秒为单位的动画速度。  
  
### <a name="remarks"></a>备注  
 动画速度介绍通知窗口打开和关闭的速度。  
  
##  <a name="getanimationtype"></a>CMFCDesktopAlertWnd::GetAnimationType  
 返回的动画类型。  
  
```  
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```  
  
### <a name="return-value"></a>返回值  
 下面的动画类型之一︰  
  
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
 时间 （毫秒），其后通知窗口将自动关闭。  
  
### <a name="remarks"></a>备注  
 使用此方法以确定要通知窗口将自动关闭之前，应经过多长时间。  
  
##  <a name="getcaptionheight"></a>CMFCDesktopAlertWnd::GetCaptionHeight  
 返回的标题高度。  
  
```  
virtual int GetCaptionHeight();
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位的标题的高度。  
  
### <a name="remarks"></a>备注  
 可以在派生类中重写此方法。 默认实现是︰ 如果弹出项窗口中应显示小标题或从 Windows API 函数获取的值，则返回的小标题高度值 （7 像素为单位） `GetSystemMetrics(SM_CYSMCAPTION)`。  
  
##  <a name="getlastpos"></a>CMFCDesktopAlertWnd::GetLastPos  
 在屏幕上返回在桌面警报窗口的最后一个位置。  
  
```  
CPoint GetLastPos() const;  
```  
  
### <a name="return-value"></a>返回值  
 屏幕坐标中的点。  
  
### <a name="remarks"></a>备注  
 此方法返回在屏幕上的警报窗口中的最后一个有效位置。  
  
##  <a name="gettransparency"></a>CMFCDesktopAlertWnd::GetTransparency  
 返回的透明度级别。  
  
```  
BYTE GetTransparency() const;  
```  
  
### <a name="return-value"></a>返回值  
 0 和 255 之间 （含） 之间的透明度级别。 值越大，更多的不透明窗口。  
  
### <a name="remarks"></a>备注  
 使用此方法可检索当前的通知窗口的透明度级别。  
  
##  <a name="hassmallcaption"></a>CMFCDesktopAlertWnd::HasSmallCaption  
 确定在桌面警报窗口具有小型标题或常规大小标题。  
  
```  
BOOL HasSmallCaption() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果弹出式窗口显示与小标题;`FALSE`如果弹出式窗口显示与普通大小的标题。  
  
### <a name="remarks"></a>备注  
 使用此方法以确定的弹出窗口的小型标题或常规大小标题。 默认情况下，小型标题为 7 个像素高。 通过调用 Windows API 函数获取的常规大小标题的高度`GetSystemMetrics(SM_CYCAPTION)`。  
  
##  <a name="onbeforeshow"></a>CMFCDesktopAlertWnd::OnBeforeShow  

  
```  
virtual BOOL OnBeforeShow(CPoint&);
```  
  
### <a name="parameters"></a>参数  
 [in] `CPoint&`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onclicklinkbutton"></a>CMFCDesktopAlertWnd::OnClickLinkButton  
 由框架调用，当用户单击位于桌面警报菜单上的链接按钮。  
  
```  
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 未使用此参数。  
  
### <a name="return-value"></a>返回值  
 总是为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 如果您想要被通知用户单击通知窗口上的链接时，重写此方法在派生类中。  
  
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
 设置新的动画速度。  
  
```  
void SetAnimationSpeed(UINT nSpeed);
```  
  
### <a name="parameters"></a>参数  
 [in] `nSpeed`  
 指定新的动画速度，以毫秒为单位。  
  
### <a name="remarks"></a>备注  
 调用此方法以设置通知窗口的动画速度。 默认值动画速度为 30 毫秒。  
  
##  <a name="setanimationtype"></a>CMFCDesktopAlertWnd::SetAnimationType  
 设置的动画类型。  
  
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
 间隔警报窗口中自动关闭前的时间，以毫秒为单位。  
  
### <a name="remarks"></a>备注  
 如果用户不会交互使用窗口中指定的时间后自动关闭通知窗口。  
  
##  <a name="setsmallcaption"></a>CMFCDesktopAlertWnd::SetSmallCaption  
 小型和常规大小字幕之间切换。  
  
```  
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSmallCaption`  
 `TRUE`若要指定通知窗口显示小标题;否则为`FALSE`若要指定警报窗口中显示的常规大小的标题。  
  
### <a name="remarks"></a>备注  
 调用此方法以显示小型或常规大小标题。 默认情况下，小型标题为 7 个像素高。 通过调用 Windows API 函数获取的正则标题大小`GetSystemMetrics(SM_CYCAPTION)`。  
  
##  <a name="settransparency"></a>CMFCDesktopAlertWnd::SetTransparency  
 设置弹出窗口的透明度级别。  
  
```  
void SetTransparency(BYTE nTransparency);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTransparency`  
 指定透明度级别。 此值必须是 0 和 255 之间 （含） 之间。 值越大，更多的不透明窗口。  
  
### <a name="remarks"></a>备注  
 调用此函数可设置弹出窗口的透明度级别。  
  
##  <a name="getdialogsize"></a>CMFCDesktopAlertWnd::GetDialogSize  

  
```  
virtual CSize GetDialogSize();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWndInfo 类](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [CMFCDesktopAlertDialog 类](../../mfc/reference/cmfcdesktopalertdialog-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)

