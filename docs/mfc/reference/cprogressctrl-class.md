---
title: "CProgressCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl class
- progress controls [C++], CProgressCtrl class
- Internet Explorer 4.0 common controls
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
caps.latest.revision: 25
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
ms.sourcegitcommit: 3d045736f9a54d344c67e3f7408198e65a0bc95f
ms.openlocfilehash: a5c006087cb4ca5482ed8c14750686389ddeef68
ms.contentlocale: zh-cn
ms.lasthandoff: 03/29/2017

---
# <a name="cprogressctrl-class"></a>CProgressCtrl 类
提供 Windows 公共进度栏控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CProgressCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|构造 `CProgressCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Cprogressctrl:: Create](#create)|创建进度栏控件并将其附加到`CProgressCtrl`对象。|  
|[CProgressCtrl::CreateEx](#createex)|与指定的 Windows 扩展样式创建进度控件并将其附加到`CProgressCtrl`对象。|  
|[CProgressCtrl::GetBarColor](#getbarcolor)|获取当前进度栏控件的进度指示器栏的颜色。|  
|[CProgressCtrl::GetBkColor](#getbkcolor)|获取当前进度栏的背景色。|  
|[CProgressCtrl::GetPos](#getpos)|获取进度栏的当前位置。|  
|[CProgressCtrl::GetRange](#getrange)|获取进度栏控件的范围的下限和上限限制。|  
|[Cprogressctrl:: Getstate](#getstate)|获取当前进度栏控件的状态。|  
|[CProgressCtrl::GetStep](#getstep)|检索当前进度栏控件的进度栏的步骤增量。|  
|[CProgressCtrl::OffsetPos](#offsetpos)|进度栏控件的当前位置前移以指定的增量和重绘滚动条来反映新的位置。|  
|[CProgressCtrl::SetBarColor](#setbarcolor)|设置当前进度栏控件中的进度指示器栏的颜色。|  
|[CProgressCtrl::SetBkColor](#setbkcolor)|设置进度栏的背景色。|  
|[CProgressCtrl::SetMarquee](#setmarquee)|关闭当前进度栏控件的字幕模式打开或关闭。|  
|[CProgressCtrl::SetPos](#setpos)|设置当前进度栏控件位置和重绘滚动条来反映新的位置。|  
|[CProgressCtrl::SetRange](#setrange)|设置进度栏控件的最小和最大范围和重绘滚动条来反映新的范围。|  
|[CProgressCtrl::SetState](#setstate)|设置当前进度栏控件的状态。|  
|[CProgressCtrl::SetStep](#setstep)|指定进度栏控件的步骤增量。|  
|[CProgressCtrl::StepIt](#stepit)|进度栏控件的当前位置前移步骤增量 (请参阅[SetStep](#setstep)) 和重绘滚动条来反映新的位置。|  
  
## <a name="remarks"></a>备注  
 进度栏控件是操作的一个窗口，其中应用程序可用于指示较长的进度。 它包含一个矩形，它逐渐填充，从左到右，用系统突出颜色显示操作进度。  
  
 进度栏控件具有范围和当前的位置。 范围表示该操作的总持续时间，当前的位置表示应用程序已完成该操作的进度。 窗口过程使用范围和当前的位置来确定的进度栏填充的突出显示颜色的百分比。 范围和当前的位置值表示为有符号整数，因为当前的位置值的可能范围是从-2147483648 到 2147483647 之间 （含）。  
  
 有关详细信息使用`CProgressCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CProgressCtrl](../../mfc/using-cprogressctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CProgressCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="cprogressctrl"></a>CProgressCtrl::CProgressCtrl  
 构造 `CProgressCtrl` 对象。  
  
```  
CProgressCtrl();
```  
  
### <a name="remarks"></a>备注  
 后构造`CProgressCtrl`对象，请调用`CProgressCtrl::Create`创建进度栏控件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CProgressCtrl # 1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]  
  
##  <a name="create"></a>Cprogressctrl:: Create  
 创建进度栏控件并将其附加到`CProgressCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定进度栏控件的样式。 应用窗口 stylesdescribed 中的任意组合[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]，除了以下进度栏控件样式，到控件︰  
  
- `PBS_VERTICAL`显示垂直进度信息、 上到下。 如果没有此标志，进度栏控件到右显示水平、 左侧。  
  
- `PBS_SMOOTH`显示逐步区平滑填写进度栏控件。 如果没有此标志，该控件将填充块。  
  
 `rect`  
 指定进度栏控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。 因为控件必须是子窗口，指定的坐标是相对于工作区`pParentWnd`。  
  
 `pParentWnd`  
 通常指定进度栏控件的父窗口`CDialog`。 它不能**NULL。**  
  
 `nID`  
 指定进度栏控件的 id。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果`CProgressCtrl`对象是已成功创建; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 构造`CProgressCtrl`两个步骤中的对象。 首先，调用的构造函数，这将创建`CProgressCtrl`对象，，然后调用**创建**，这将创建进度栏控件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CProgressCtrl # 2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]  
  
##  <a name="createex"></a>CProgressCtrl::CreateEx  
 创建控件 （子窗口），并将其与关联`CProgressCtrl`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定进度栏控件的样式。 应用中所述的窗口样式的任意组合[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构描述的大小和窗口在客户端坐标中创建的位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)将扩展的窗口样式，指定的 Windows 扩展的样式加**WS_EX_**。  
  
##  <a name="getbarcolor"></a>CProgressCtrl::GetBarColor  
 获取当前进度栏控件的进度指示器栏的颜色。  
  
```  
COLORREF GetBarColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前进度栏的颜色表示为[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，或`CLR_DEFAULT`如果进度指示器栏颜色为默认颜色。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PBM_GETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760826)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getbkcolor"></a>CProgressCtrl::GetBkColor  
 获取当前进度栏的背景色。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前进度栏的背景色表示为[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PBM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760828)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getpos"></a>CProgressCtrl::GetPos  
 检索进度栏的当前位置。  
  
```  
int GetPos();
```  
  
### <a name="return-value"></a>返回值  
 进度栏控件的位置。  
  
### <a name="remarks"></a>备注  
 进度栏控件的位置不在屏幕上，在的物理位置但而是会之间上限和下限范围表明在[SetRange](#setrange)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CProgressCtrl # 3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]  
  
##  <a name="getrange"></a>CProgressCtrl::GetRange  
 获取当前的下限和上限限制或范围，进度栏控件。  
  
```  
void GetRange(
    int& nLower,  
    int& nUpper);
```  
  
### <a name="parameters"></a>参数  
 `nLower`  
 对接收进度栏控件的下限的整数的引用。  
  
 `nUpper`  
 对接收进度栏控件的上限的整数的引用。  
  
### <a name="remarks"></a>备注  
 此函数将下限和上限限制的值复制到引用的整数`nLower`和`nUpper`分别。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CProgressCtrl # 4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]  
  
##  <a name="getstate"></a>Cprogressctrl:: Getstate  
 获取当前进度栏控件的状态。  
  
```  
int GetState() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的进度栏控件，可以为以下值之一的状态︰  
  
|值|状态|  
|-----------|-----------|  
|`PBST_NORMAL`|正在进行|  
|`PBST_ERROR`|错误|  
|`PBST_PAUSED`|Paused|  
  
### <a name="remarks"></a>备注  
 此方法可发送[PBM_GETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760834)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s&#1; 9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例检索当前进度栏控件的状态。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s&#1; 5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]  
  
##  <a name="getstep"></a>CProgressCtrl::GetStep  
 检索当前进度栏控件的进度栏的步骤增量。  
  
```  
int GetStep() const;  
```  
  
### <a name="return-value"></a>返回值  
 进度栏步骤增量。  
  
### <a name="remarks"></a>备注  
 步骤增量是依据量对的调用[CProgressCtrl::StepIt](#stepit)增加进度栏的当前位置。  
  
 此方法可发送[PBM_GETSTEP](http://msdn.microsoft.com/library/windows/desktop/bb760836)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s&#1; 9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例检索当前进度栏控件的步骤增量。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s&#1; 3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]  
  
##  <a name="offsetpos"></a>CProgressCtrl::OffsetPos  
 进度栏控件的当前位置前移由指定的增量`nPos`和重绘滚动条来反映新的位置。  
  
```  
int OffsetPos(int nPos);
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 要前移的位置的量。  
  
### <a name="return-value"></a>返回值  
 进度栏控件的前一个位置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CProgressCtrl # 5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]  
  
##  <a name="setbarcolor"></a>CProgressCtrl::SetBarColor  
 设置当前进度栏控件中的进度指示器栏的颜色。  
  
```  
COLORREF SetBarColor(COLORREF clrBar);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `clrBar`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值指定进度指示器栏的新颜色。 指定`CLR_DEFAULT`导致进度栏，以使用其默认颜色。|  
  
### <a name="return-value"></a>返回值  
 进度指示器栏，以前的颜色表示为[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，或`CLR_DEFAULT`如果进度指示器栏的颜色为默认颜色。  
  
### <a name="remarks"></a>备注  
 `SetBarColor`方法会设置进度栏颜色才[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)][主题](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx)不起作用。  
  
 此方法可发送[PBM_SETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760838)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s&#1; 9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例更改进度栏的颜色为红色、 绿色、 蓝色或默认值。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s&#1; 1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]  
  
##  <a name="setbkcolor"></a>CProgressCtrl::SetBkColor  
 设置进度栏的背景色。  
  
```  
COLORREF SetBkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>参数  
 `clrNew`  
 A **COLORREF**值，该值指定新的背景色。 指定`CLR_DEFAULT`值要用于进度栏的默认背景色。  
  
### <a name="return-value"></a>返回值  
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值指示以前的背景颜色，或**CLR_DEFAULT**如果的背景色为默认颜色。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CProgressCtrl # 6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]  
  
##  <a name="setmarquee"></a>CProgressCtrl::SetMarquee  
 关闭当前进度栏控件的字幕模式打开或关闭。  
  
```  
BOOL SetMarquee(
    BOOL fMarqueeMode,   
    int nInterval);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `fMarqueeMode`|`true`若要打开选框模式，或`false`关闭字幕模式。|  
|[in] `nInterval`|以毫秒为单位的字幕动画的更新之间的时间。|  
  
### <a name="return-value"></a>返回值  
 此方法始终返回 `true`。  
  
### <a name="remarks"></a>备注  
 当打开选框模式、 进度条动态显示和滚动喜欢登录影院选框。  
  
 此方法可发送[PBM_SETMARQUEE](http://msdn.microsoft.com/library/windows/desktop/bb760842)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s&#1; 9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例启动和停止滚动动画。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s&#1; 2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]  
  
##  <a name="setpos"></a>CProgressCtrl::SetPos  
 设置进度栏控件的当前位置由指定`nPos`和重绘滚动条来反映新的位置。  
  
```  
int SetPos(int nPos);
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 进度栏控件的新位置。  
  
### <a name="return-value"></a>返回值  
 进度栏控件的前一个位置。  
  
### <a name="remarks"></a>备注  
 进度栏控件的位置不在屏幕上，在的物理位置但而是会之间上限和下限范围表明在[SetRange](#setrange)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CProgressCtrl # 7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]  
  
##  <a name="setrange"></a>CProgressCtrl::SetRange  
 设置进度栏控件的范围的上限和下限限制和重绘滚动条来反映新的范围。  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>参数  
 `nLower`  
 指定范围的下限 （默认值为零）。  
  
 `nUpper`  
 指定范围的上限 （默认值为 100）。  
  
### <a name="remarks"></a>备注  
 成员函数`SetRange32`设置进度控件的 32 位范围。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CProgressCtrl # 8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]  
  
##  <a name="setstate"></a>CProgressCtrl::SetState  
 设置当前进度栏控件的状态。  
  
```  
int SetState(int iState);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `iState`|要将进度栏设置到的状态。 使用下列值之一：<br /><br /> - `PBST_NORMAL`-正在进行中<br />- `PBST_ERROR`-错误<br />- `PBST_PAUSED`-暂停|  
  
### <a name="return-value"></a>返回值  
 当前进度栏控件的前一个状态。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PBM_SETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760850)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s&#1; 9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例将当前进度栏控件的状态设置为“已暂停”或“正在进行中”。  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s&#1; 4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]  
  
##  <a name="setstep"></a>CProgressCtrl::SetStep  
 指定进度栏控件的步骤增量。  
  
```  
int SetStep(int nStep);
```  
  
### <a name="parameters"></a>参数  
 *nStep*  
 新步骤增量。  
  
### <a name="return-value"></a>返回值  
 以前的步骤增量。  
  
### <a name="remarks"></a>备注  
 步骤增量是依据量对的调用`CProgressCtrl::StepIt`增加进度栏的当前位置。  
  
 默认步骤增量为 10。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CProgressCtrl # 9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]  
  
##  <a name="stepit"></a>CProgressCtrl::StepIt  
 进度栏控件的当前位置前移步骤增量和重绘滚动条来反映新的位置。  
  
```  
int StepIt();
```  
  
### <a name="return-value"></a>返回值  
 进度栏控件的前一个位置。  
  
### <a name="remarks"></a>备注  
 通过设置步骤增量`CProgressCtrl::SetStep`成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CProgressCtrl # 10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



