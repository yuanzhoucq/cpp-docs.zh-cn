---
title: "CSpinButtonCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSpinButtonCtrl
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [C++], CSpinButtonCtrl
- CSpinButtonCtrl class
- CSpinButtonCtrl class, common controls
- up-down controls, spin button control
- spin button control
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
caps.latest.revision: 23
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
ms.openlocfilehash: 486a0842ed04f0e760bbb332986a97a35ce9851f
ms.lasthandoff: 02/24/2017

---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl 类
提供 Windows 公共数值调节钮控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CSpinButtonCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|构造 `CSpinButtonCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSpinButtonCtrl::Create](#create)|创建数值调节钮控件，并将其附加到`CSpinButtonCtrl`对象。|  
|[CSpinButtonCtrl::CreateEx](#createex)|与指定的 Windows 扩展样式创建数值调节钮控件，并将其附加到`CSpinButtonCtrl`对象。|  
|[CSpinButtonCtrl::GetAccel](#getaccel)|检索数值调节钮控件的加速信息。|  
|[CSpinButtonCtrl::GetBase](#getbase)|检索数值调节钮控件的当前基。|  
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|检索与当前的合作者窗口的指针。|  
|[CSpinButtonCtrl::GetPos](#getpos)|检索数值调节钮控件的当前位置。|  
|[CSpinButtonCtrl::GetRange](#getrange)|检索的上限和下限限制 （范围） 数值调节钮控件。|  
|[CSpinButtonCtrl::SetAccel](#setaccel)|设置数值调节钮控件的加速。|  
|[CSpinButtonCtrl::SetBase](#setbase)|设置数值调节钮控件的基础。|  
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|设置数值调节钮控件在合作者窗口。|  
|[CSpinButtonCtrl::SetPos](#setpos)|设置控件的当前位置。|  
|[Cspinbuttonctrl:: Setrange](#setrange)|设置的上限和下限限制 （范围） 数值调节钮控件。|  
  
## <a name="remarks"></a>备注  
 "数值调节钮控件"（也称为 up-down 控件） 是一对箭头按钮，用户可以单击递增或递减值，如滚动位置或在附带控件中显示一个行号。 数值调节钮控件与关联的值称为当前位置。 数值调节钮控件是最常用于附带控件，称为"合作者窗口"。  
  
 此控件 (并因此`CSpinButtonCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 对用户来说，数值调节钮控件和其合作者窗口通常看起来像一个控件。 您可以指定，数值调节钮控件自动将自身定位旁边其合作者窗口，并且它自动设置合作者窗口的标题为当前位置。 使用一个编辑控件的数值调节钮控件，以提示用户输入数字输入。  
  
 单击向上箭头将朝着最大值，当前位置移动，并单击向下箭头将朝着最小值的当前位置。 默认情况下，最小值为 100 且最大值为 0。 最小值设置为大于最大值设置 （例如，当将使用默认设置），请单击向上箭头减少任何时候位置值并单击向下箭头将增高。  
  
 而无需合作者窗口数值调节钮控件可用作一种简化的滚动条。 例如，一个选项卡控件有时显示数值调节钮控件，以使用户能够滚动到视图中的其他选项卡。  
  
 有关详细信息使用`CSpinButtonCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="a-namecreatea--cspinbuttonctrlcreate"></a><a name="create"></a>CSpinButtonCtrl::Create  
 创建数值调节钮控件，并将其附加到`CSpinButtonCtrl`对象...  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定数值调节钮控件的样式。 适用于控件的任意组合数值调节按钮控件样式。 中介绍了这些样式[Up-down 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb759885)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 指定数值调节钮控件的大小和位置。 它可为[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构  
  
 `pParentWnd`  
 数值调节钮控件的父窗口，通常一个指向`CDialog`。 它不能**NULL。**  
  
 `nID`  
 指定数值调节钮控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CSpinButtonCtrl`两个步骤中的第一次对象、 调用构造函数中，，然后调用**创建**，它创建数值调节钮控件，并将其附加到`CSpinButtonCtrl`对象。  
  
 若要使用扩展的窗口样式创建数值调节钮控件，调用[CSpinButtonCtrl::CreateEx](#createex)而不是**创建**。  
  
##  <a name="a-namecreateexa--cspinbuttonctrlcreateex"></a><a name="createex"></a>CSpinButtonCtrl::CreateEx  
 创建控件 （子窗口），并将其与相关联`CSpinButtonCtrl`对象。  
  
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
 指定要创建的控件的扩展的样式。 扩展的窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定数值调节钮控件的样式。 适用于控件的任意组合数值调节按钮控件样式。 中介绍了这些样式[Up-down 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb759885)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口，在中创建的工作区坐标位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)应用扩展的窗口样式、 指定的 Windows 扩展的样式前言**WS_EX_**。  
  
##  <a name="a-namecspinbuttonctrla--cspinbuttonctrlcspinbuttonctrl"></a><a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl  
 构造 `CSpinButtonCtrl` 对象。  
  
```  
CSpinButtonCtrl();
```  
  
##  <a name="a-namegetaccela--cspinbuttonctrlgetaccel"></a><a name="getaccel"></a>CSpinButtonCtrl::GetAccel  
 检索数值调节钮控件的加速信息。  
  
```  
UINT GetAccel(
    int nAccel,  
    UDACCEL* pAccel) const;  
```  
  
### <a name="parameters"></a>参数  
 `nAccel`  
 指定的数组中的元素数`pAccel`。  
  
 `pAccel`  
 指向数组的指针[UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897)接收加速信息的结构。  
  
### <a name="return-value"></a>返回值  
 检索加速器结构的数量。  
  
##  <a name="a-namegetbasea--cspinbuttonctrlgetbase"></a><a name="getbase"></a>CSpinButtonCtrl::GetBase  
 检索数值调节钮控件的当前基。  
  
```  
UINT GetBase() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的基础值。  
  
##  <a name="a-namegetbuddya--cspinbuttonctrlgetbuddy"></a><a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy  
 检索与当前的合作者窗口的指针。  
  
```  
CWnd* GetBuddy() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向当前合作者窗口的指针。  
  
##  <a name="a-namegetposa--cspinbuttonctrlgetpos"></a><a name="getpos"></a>CSpinButtonCtrl::GetPos  
 检索数值调节钮控件的当前位置。  
  
```  
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;  ```  
  
### Parameters  
 *lpbError*  
 A pointer to a boolean value that is set to zero if the value is successfully retrieved or non-zero if an error occurs. If this parameter is set to **NULL**, errors are not reported.  
  
### Return Value  
 The first version returns the 16-bit current position in the low-order word. The high-order word is nonzero if an error occurred.  
  
 The second version returns the 32-bit position.  
  
### Remarks  
 When it processes the value returned, the control updates its current position based on the caption of the buddy window. The control returns an error if there is no buddy window or if the caption specifies an invalid or out-of-range value.  
  
##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange  
 Retrieves the upper and lower limits (range) for a spin button control.  
  
```  
DWORD GetRange() const;  
  
void GetRange （int & 较低，  
    int & 上限) const;  
  
void GetRange32 (int & 低一些，  
    int & 上限) const;  
```  
  
### Parameters  
 *lower*  
 Reference to an integer that receives the lower limit for the control.  
  
 *upper*  
 Reference to an integer that receives the upper limit for the control.  
  
### Return Value  
 The first version returns a 32-bit value containing the upper and lower limits. The low-order word is the upper limit for the control, and the high-order word is the lower limit.  
  
### Remarks  
 The member function `GetRange32` retrieves the spin button control's range as a 32-bit integer.  
  
##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel  
 Sets the acceleration for a spin button control.  
  
```  
BOOL SetAccel (int nAccel，  
    UDACCEL* pAccel);
```  
  
### Parameters  
 `nAccel`  
 Number of [UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897) structures specified by `pAccel`.  
  
 `pAccel`  
 Pointer to an array of `UDACCEL` structures, which contain acceleration information. Elements should be sorted in ascending order based on the **nSec** member.  
  
### Return Value  
 Nonzero if successful; otherwise 0.  
  
##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase  
 Sets the base for a spin button control.  
  
```  
int SetBase (int nBase);
```  
  
### Parameters  
 `nBase`  
 New base value for the control. It can be 10 for decimal or 16 for hexadecimal.  
  
### Return Value  
 The previous base value if successful, or zero if an invalid base is given.  
  
### Remarks  
 The base value determines whether the buddy window displays numbers in decimal or hexadecimal digits. Hexadecimal numbers are always unsigned; decimal numbers are signed.  
  
##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy  
 Sets the buddy window for a spin button control.  
  
```  
CWnd* SetBuddy (CWnd* pWndBuddy);
```  
  
### Parameters  
 `pWndBuddy`  
 Pointer to the new buddy window.  
  
### Return Value  
 A pointer to the previous buddy window.  
  
### Remarks  
 A spin control is almost always associated with another window, such as an edit control, that displays some content. This other window is called the "buddy" of the spin control.  
  
##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos  
 Sets the current position for a spin button control.  
  
```  
int SetPos (int nPos);  
int SetPos32(int nPos);
```  
  
### Parameters  
 `nPos`  
 New position for the control. This value must be in the range specified by the upper and lower limits for the control.  
  
### Return Value  
 The previous position (16-bit precision for `SetPos`, 32-bit precision for `SetPos32`).  
  
### Remarks  
 `SetPos32` sets the 32-bit position.  
  
##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange  
 Sets the upper and lower limits (range) for a spin button control.  
  
```  
void SetRange (短 nLower，  
    短 nUpper);

 
void SetRange32 (int nLower，  
    int nUpper);
```  
  
### Parameters  
 `nLower`and `nUpper`  
 Upper and lower limits for the control. For `SetRange`, neither limit can be greater than **UD_MAXVAL** or less than **UD_MINVAL**; in addition, the difference between the two limits cannot exceed **UD_MAXVAL**. `SetRange32` places no restrictions on the limits; use any integers.  
  
### Remarks  
 The member function `SetRange32` sets the 32-bit range for the spin button control.  
  
> [!NOTE]
>  The default range for the spin button has the maximum set to zero (0) and the minimum set to 100. Because the maximum value is less than the minimum value, clicking the up arrow will decrease the position and clicking the down arrow will increase it. Use `CSpinButtonCtrl::SetRange` to adjust these values.  
  
## See Also  
 [MFC Sample CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd Class](../../mfc/reference/cwnd-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [CSliderCtrl Class](../../mfc/reference/csliderctrl-class.md)

