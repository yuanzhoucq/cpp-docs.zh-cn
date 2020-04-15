---
title: CSpinButtonCtrl 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 4230d43bad8bcc15bcb26aaf0357e70216909ba1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318130"
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
|[CSpinButtonCtrl：：CspinButtonCtrl](#cspinbuttonctrl)|构造 `CSpinButtonCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSpinButtonCtrl：：创建](#create)|创建旋转按钮控件并将其附加到`CSpinButtonCtrl`对象。|
|[CSpinButtonCtrl：：创建Ex](#createex)|使用指定的 Windows 扩展样式创建旋转按钮控件，并将其附加到`CSpinButtonCtrl`对象。|
|[CSpinButtonctrl：：GetAccel](#getaccel)|检索旋转按钮控件的加速信息。|
|[CSpinButtonCtrl：获取基础](#getbase)|检索旋转按钮控件的当前底座。|
|[CSpinButtonctrl：GetBuddy](#getbuddy)|检索指向当前好友窗口的指针。|
|[CSpinButtonctrl：getPos](#getpos)|检索旋转按钮控件的当前位置。|
|[CSpinButtonCtrl：获取范围](#getrange)|检索旋转按钮控件的上限和下限（范围）。|
|[CSpinButtonctrl：：SetAccel](#setaccel)|设置旋转按钮控件的加速度。|
|[CSpinButtonctrl：：设置基](#setbase)|设置旋转按钮控件的基础。|
|[CSpinButtonctrl：：SetBuddy](#setbuddy)|设置旋转按钮控件的好友窗口。|
|[CSpinButtonctrl：：SetPos](#setpos)|设置控件的当前位置。|
|[CSpinButtonctrl：：设置范围](#setrange)|设置旋转按钮控件的上限和下限（范围）。|

## <a name="remarks"></a>备注

"旋转按钮控件"（也称为向上向下控件）是一对箭头按钮，用户可以单击该按钮以递增或递减值，例如滚动位置或配套控件中显示的数字。 与旋转按钮控件关联的值称为其当前位置。 旋转按钮控件最常与称为"好友窗口"的配套控件一起使用。

此控件（因此该`CSpinButtonCtrl`类）仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

对用户，旋转按钮控件及其好友窗口通常看起来像单个控件。 您可以指定旋转按钮控件会自动将其定位在其好友窗口旁边，并且它会自动将好友窗口的标题设置为其当前位置。 您可以将旋转按钮控件与编辑控件一起提示用户输入数字。

单击向上箭头将当前位置向最大值移动，单击向下箭头将当前位置向最小值移动。 默认情况下，最小值为 100，最大值为 0。 每当最小设置大于最大设置（例如，使用默认设置时），单击向上箭头会减小位置值，单击向下箭头会增加位置值。

没有好友窗口的旋转按钮控件可充当一种简化的滚动条。 例如，选项卡控件有时会显示旋转按钮控件，使用户能够将其他选项卡滚动到视图中。

有关 使用`CSpinButtonCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)[和使用 CspinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="cspinbuttonctrlcreate"></a><a name="create"></a>CSpinButtonCtrl：：创建

创建旋转按钮控件并将其附加到`CSpinButtonCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定旋转按钮控件的样式。 将旋转按钮控制样式的任意组合应用于控件。 这些样式在 Windows SDK 中的["向上向下控制样式"](/windows/win32/Controls/up-down-control-styles)中描述。

*矩形*<br/>
指定旋转按钮控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构

*pparentwnd*<br/>
指向旋转按钮控件的父窗口（通常为 的指针`CDialog`） 的指针。 值不得为 NULL。

*nID*<br/>
指定旋转按钮控件的 ID。

### <a name="return-value"></a>返回值

初始化成功时非零;否则 0。

### <a name="remarks"></a>备注

先分两`CSpinButtonCtrl`个步骤构造对象，调用构造函数，然后调用`Create`，这将创建旋转按钮控件并将其附加到`CSpinButtonCtrl`对象。

要创建具有扩展窗口样式的旋转按钮控件，请调用[CSpinButtonCtrl：：createEx](#createex)而不是`Create`。

## <a name="cspinbuttonctrlcreateex"></a><a name="createex"></a>CSpinButtonCtrl：：创建Ex

创建控件（子窗口），并将其与`CSpinButtonCtrl`对象关联。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwExStyle*<br/>
指定要创建的控件的扩展样式。 有关扩展窗口样式的列表，请参阅 Windows SDK 中创建[WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定旋转按钮控件的样式。 将旋转按钮控制样式的任意组合应用于控件。 这些样式在 Windows SDK 中的["向上向下控制样式"](/windows/win32/Controls/up-down-control-styles)中描述。

*矩形*<br/>
对[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用，描述要创建的窗口的大小和位置，在*pParentWnd*的客户端坐标中。

*pparentwnd*<br/>
指向控件的父窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是["创建](#create)"来应用 Windows 扩展样式WS_EX_指定扩展的 Windows 样式。

## <a name="cspinbuttonctrlcspinbuttonctrl"></a><a name="cspinbuttonctrl"></a>CSpinButtonCtrl：：CspinButtonCtrl

构造 `CSpinButtonCtrl` 对象。

```
CSpinButtonCtrl();
```

## <a name="cspinbuttonctrlgetaccel"></a><a name="getaccel"></a>CSpinButtonctrl：：GetAccel

检索旋转按钮控件的加速信息。

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>参数

*nAccel*<br/>
*pAccel*指定的数组中的元素数。

*pAccel*<br/>
指向接收加速信息的[UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel)结构数组的指针。

### <a name="return-value"></a>返回值

检索的加速器结构数。

## <a name="cspinbuttonctrlgetbase"></a><a name="getbase"></a>CSpinButtonCtrl：获取基础

检索旋转按钮控件的当前底座。

```
UINT GetBase() const;
```

### <a name="return-value"></a>返回值

当前基值。

## <a name="cspinbuttonctrlgetbuddy"></a><a name="getbuddy"></a>CSpinButtonctrl：GetBuddy

检索指向当前好友窗口的指针。

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>返回值

指向当前好友窗口的指针。

## <a name="cspinbuttonctrlgetpos"></a><a name="getpos"></a>CSpinButtonctrl：getPos

检索旋转按钮控件的当前位置。

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>参数

*lpbError*<br/>
指向布尔值的指针，如果成功检索该值，则设置为零;如果发生错误，则设置为非零。 如果此参数设置为 NULL，则不报告错误。

### <a name="return-value"></a>返回值

第一个版本返回低阶单词中的 16 位当前位置。 如果发生错误，高阶单词为非零。

第二个版本返回 32 位位置。

### <a name="remarks"></a>备注

处理返回的值时，控件会根据好友窗口的标题更新其当前位置。 如果没有好友窗口或标题指定无效或范围外值，则控件将返回错误。

## <a name="cspinbuttonctrlgetrange"></a><a name="getrange"></a>CSpinButtonCtrl：获取范围

检索旋转按钮控件的上限和下限（范围）。

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

*降低*<br/>
引用接收控件下限的整数。

*上*<br/>
引用接收控件上限的整数。

### <a name="return-value"></a>返回值

第一个版本返回包含上限和下限的 32 位值。 低阶词是控件的上限，高阶词是下限。

### <a name="remarks"></a>备注

成员函数`GetRange32`检索旋转按钮控件的范围作为 32 位整数。

## <a name="cspinbuttonctrlsetaccel"></a><a name="setaccel"></a>CSpinButtonctrl：：SetAccel

设置旋转按钮控件的加速度。

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>参数

*nAccel*<br/>
*pAccel*指定的[UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel)结构数。

*pAccel*<br/>
指向包含加速度信息的 UDACCEL 结构数组的指针。 元素应按升序按成员排序`nSec`。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

## <a name="cspinbuttonctrlsetbase"></a><a name="setbase"></a>CSpinButtonctrl：：设置基

设置旋转按钮控件的基础。

```
int SetBase(int nBase);
```

### <a name="parameters"></a>参数

*nBase*<br/>
控件的新基值。 十进制可以是 10，十进制也可以是 16，十六进制为十六进制。

### <a name="return-value"></a>返回值

如果成功，则上一个基值;如果给定无效基，则为零。

### <a name="remarks"></a>备注

基值确定好友窗口是以十进制数字还是十六进制数字显示数字。 十六进制数字始终未签名;十进制数字已签名。

## <a name="cspinbuttonctrlsetbuddy"></a><a name="setbuddy"></a>CSpinButtonctrl：：SetBuddy

设置旋转按钮控件的好友窗口。

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>参数

*普恩德布迪*<br/>
指向新好友窗口的指针。

### <a name="return-value"></a>返回值

指向上一个好友窗口的指针。

### <a name="remarks"></a>备注

旋转控件几乎总是与另一个窗口（如编辑控件）相关联，该窗口显示某些内容。 此另一个窗口称为自旋控件的"伙伴"。

## <a name="cspinbuttonctrlsetpos"></a><a name="setpos"></a>CSpinButtonctrl：：SetPos

设置旋转按钮控件的当前位置。

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
控件的新位置。 此值必须位于控件的上限和下限指定的范围内。

### <a name="return-value"></a>返回值

上一个位置（16 位精度，`SetPos`为`SetPos32`32 位精度）。

### <a name="remarks"></a>备注

`SetPos32`设置 32 位位置。

## <a name="cspinbuttonctrlsetrange"></a><a name="setrange"></a>CSpinButtonctrl：：设置范围

设置旋转按钮控件的上限和下限（范围）。

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>参数

*n 下部*和*nUpper*<br/>
控件的上限和下限。 对于`SetRange`，两个限制都不能大于UD_MAXVAL或小于UD_MINVAL;此外，两个限制之间的差异不能超过UD_MAXVAL。 `SetRange32`对限制没有限制;使用任何整数。

### <a name="remarks"></a>备注

成员函数`SetRange32`为旋转按钮控件设置 32 位范围。

> [!NOTE]
> 旋转按钮的默认范围的最大设置为零 （0），最小设置为 100。 由于最大值小于最小值，单击向上箭头将减小位置，单击向下箭头将增加该位置。 用于`CSpinButtonCtrl::SetRange`调整这些值。

## <a name="see-also"></a>另请参阅

[MFC 样品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl 类](../../mfc/reference/csliderctrl-class.md)
