---
title: "CSpinButtonCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
dev_langs:
- C++
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b00fc554c6ca677756cf6a9a9c7fa83cd9d255f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl 类
提供 Windows 公共数值调节钮控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CSpinButtonCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|构造 `CSpinButtonCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSpinButtonCtrl::Create](#create)|创建数值调节钮控件，并将其附加到`CSpinButtonCtrl`对象。|  
|[CSpinButtonCtrl::CreateEx](#createex)|指定的 Windows 扩展样式创建数值调节钮控件，并将其附加到`CSpinButtonCtrl`对象。|  
|[CSpinButtonCtrl::GetAccel](#getaccel)|检索加速数值调节钮控件的信息。|  
|[CSpinButtonCtrl::GetBase](#getbase)|检索数值调节钮控件的当前基。|  
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|检索指向当前合作者窗口的指针。|  
|[CSpinButtonCtrl::GetPos](#getpos)|检索数值调节钮控件的当前位置。|  
|[CSpinButtonCtrl::GetRange](#getrange)|检索的上限和下限限制 （范围） 数值调节钮控件。|  
|[CSpinButtonCtrl::SetAccel](#setaccel)|设置数值调节钮控件的加速。|  
|[CSpinButtonCtrl::SetBase](#setbase)|设置数值调节钮控件的基。|  
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|设置数值调节钮控件合作者窗口。|  
|[CSpinButtonCtrl::SetPos](#setpos)|设置控件的当前位置。|  
|[Cspinbuttonctrl:: Setrange](#setrange)|设置的上限和下限限制 （范围） 数值调节钮控件。|  
  
## <a name="remarks"></a>备注  
 "数值调节钮控件"（也称为 up-down 控件） 是一个对的用户可以单击递增或递减值，如滚动位置或在附带控件中显示一个行号的箭头按钮。 数值调节钮控件与关联的值调用其当前位置。 数值调节钮控件通常用于附带控件，调用"合作者窗口"。  
  
 此控件 (因此`CSpinButtonCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 对用户来说，数值调节钮控件和其合作者窗口通常看起来的单个控件。 你可以指定，数值调节钮控件自动将自身置于其合作者窗口，并确保它自动设置合作者窗口的标题为当前位置。 可以使用数值调节钮控件与编辑控件，以提示用户输入数字输入。  
  
 单击向上箭头将朝着最大值，当前位置移动，并单击向下箭头将当前位置朝着最小值。 默认情况下，最小值为 100 和最大值为 0。 任何时间的最小设置大于最大值设置 （例如，当使用默认设置），单击向上箭头降低位置值并单击向下箭头会增加它。  
  
 数值调节按钮控件，而无需合作者窗口函数用作一种简化的滚动条。 例如，选项卡控件有时显示数值调节按钮控件，使用户能够滚动到视图的其他选项卡。  
  
 有关详细信息使用`CSpinButtonCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxcmn.h  
  
##  <a name="create"></a>CSpinButtonCtrl::Create  
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
 指定数值调节钮控件的样式。 应用于控件的数值调节按钮控件样式的任意组合。 这些样式中所述[Up-down 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb759885)Windows SDK 中。  
  
 `rect`  
 指定数值调节钮控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构  
  
 `pParentWnd`  
 数值调节钮控件的父窗口，通常一个指向`CDialog`。 它不能**NULL。**  
  
 `nID`  
 指定数值调节钮控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CSpinButtonCtrl`首先对象在两个步骤中，调用的构造函数，然后调用**创建**，它创建数值调节钮控件并将其附加到`CSpinButtonCtrl`对象。  
  
 若要使用扩展的窗口样式创建数值调节钮控件，调用[CSpinButtonCtrl::CreateEx](#createex)而不是**创建**。  
  
##  <a name="createex"></a>CSpinButtonCtrl::CreateEx  
 创建控件 （子窗口），并将其与关联`CSpinButtonCtrl`对象。  
  
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
 指定要创建的控件的扩展的样式。 扩展的窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 `dwStyle`  
 指定数值调节钮控件的样式。 应用于控件的数值调节按钮控件样式的任意组合。 这些样式中所述[Up-down 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb759885)Windows SDK 中。  
  
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
  
##  <a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl  
 构造 `CSpinButtonCtrl` 对象。  
  
```  
CSpinButtonCtrl();
```  
  
##  <a name="getaccel"></a>CSpinButtonCtrl::GetAccel  
 检索加速数值调节钮控件的信息。  
  
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
 检索的快捷键结构。  
  
##  <a name="getbase"></a>CSpinButtonCtrl::GetBase  
 检索数值调节钮控件的当前基。  
  
```  
UINT GetBase() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的基础值。  
  
##  <a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy  
 检索指向当前合作者窗口的指针。  
  
```  
CWnd* GetBuddy() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向当前合作者窗口的指针。  
  
##  <a name="getpos"></a>CSpinButtonCtrl::GetPos  
 检索数值调节钮控件的当前位置。  
  
```  
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpbError*  
 指向一个布尔值，值设置为零的指针是已成功检索到或非零如果发生错误。 如果此参数设置为**NULL**，不会报告错误。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回低序位字中的 16 位当前位置。 高序位字不为零，如果出现错误。  
  
 第二个版本返回的 32 位位置。  
  
### <a name="remarks"></a>备注  
 当它处理返回的值时，控件将更新其基于在合作者窗口的标题的当前位置。 如果未合作者窗口或标题指定了一个无效或超出范围的值，该控件将返回错误。  
  
##  <a name="getrange"></a>CSpinButtonCtrl::GetRange  
 检索的上限和下限限制 （范围） 数值调节钮控件。  
  
```  
DWORD GetRange() const;  
  
void GetRange(
    int& lower,  
    int& upper) const;  
  
void GetRange32(
    int& lower,  
    int &upper) const;  
```  
  
### <a name="parameters"></a>参数  
 *较低*  
 对接收控件的下限的整数的引用。  
  
 *上限*  
 对一个整数，它接收的上限为该控件的引用。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回包含上限和下限的 32 位值。 低序位字是该控件的上限，高序位字的下限。  
  
### <a name="remarks"></a>备注  
 成员函数`GetRange32`检索作为 32 位整数的数值调节钮控件的范围。  
  
##  <a name="setaccel"></a>CSpinButtonCtrl::SetAccel  
 设置数值调节钮控件的加速。  
  
```  
BOOL SetAccel(
    int nAccel,  
    UDACCEL* pAccel);
```  
  
### <a name="parameters"></a>参数  
 `nAccel`  
 数[UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897)结构指定`pAccel`。  
  
 `pAccel`  
 指向数组的指针`UDACCEL`结构，其中包含加速信息。 元素应按升序排序基于**nSec**成员。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="setbase"></a>CSpinButtonCtrl::SetBase  
 设置数值调节钮控件的基。  
  
```  
int SetBase(int nBase);
```  
  
### <a name="parameters"></a>参数  
 `nBase`  
 控件的新基值。 它可以是表示小数点 10 或 16 个十六进制。  
  
### <a name="return-value"></a>返回值  
 如果成功，以前的基值或零，如果未提供的 base 无效。  
  
### <a name="remarks"></a>备注  
 基础值确定合作者窗口是否以十进制或十六进制数字显示数字。 十六进制数字始终是无符号;十进制数字进行签名。  
  
##  <a name="setbuddy"></a>CSpinButtonCtrl::SetBuddy  
 设置数值调节钮控件合作者窗口。  
  
```  
CWnd* SetBuddy(CWnd* pWndBuddy);
```  
  
### <a name="parameters"></a>参数  
 `pWndBuddy`  
 指向新的合作者窗口的指针。  
  
### <a name="return-value"></a>返回值  
 指向上一个合作者窗口的指针。  
  
### <a name="remarks"></a>备注  
 数值调节钮控件对于几乎始终与另一个窗口，如编辑控件，显示一些内容。 此其他窗口称为"好友"的数值调节钮控件。  
  
##  <a name="setpos"></a>CSpinButtonCtrl::SetPos  
 设置数值调节钮控件的当前位置。  
  
```  
int SetPos(int nPos);  
int SetPos32(int nPos);
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 控件的新位置。 此值必须为指定控件的上限和下限限制的范围。  
  
### <a name="return-value"></a>返回值  
 前一个位置 (16 位精度`SetPos`、 32 位精度的`SetPos32`)。  
  
### <a name="remarks"></a>备注  
 `SetPos32`设置的 32 位位置。  
  
##  <a name="setrange"></a>Cspinbuttonctrl:: Setrange  
 设置的上限和下限限制 （范围） 数值调节钮控件。  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>参数  
 `nLower` 和 `nUpper`  
 控件的上限和下限限制。 有关`SetRange`，既不限制可以大于**UD_MAXVAL**或小于**UD_MINVAL**; 此外，不能超过两个限制之间的差异**UD_MAXVAL**. `SetRange32`无限制将限制;使用任何整数。  
  
### <a name="remarks"></a>备注  
 成员函数`SetRange32`设置数值调节钮控件的 32 位范围。  
  
> [!NOTE]
>  数值调节钮的默认范围具有设置为零 (0) 的最大和最小设置为 100。 因为最大值小于最小值，单击向上箭头将降低位置，单击向下箭头将增加它。 使用`CSpinButtonCtrl::SetRange`来调整这些值。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSliderCtrl 类](../../mfc/reference/csliderctrl-class.md)
