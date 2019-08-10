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
ms.openlocfilehash: da247524dae77627bbf041b83bc1534a75c3b073
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916701"
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
|[CSpinButtonCtrl::Create](#create)|创建数值调节钮控件, 并将其附加`CSpinButtonCtrl`到对象。|
|[CSpinButtonCtrl::CreateEx](#createex)|创建具有指定 Windows 扩展样式的数值调节钮控件, 并将其附加`CSpinButtonCtrl`到对象。|
|[CSpinButtonCtrl::GetAccel](#getaccel)|检索数值调节钮控件的加速信息。|
|[CSpinButtonCtrl::GetBase](#getbase)|检索数值调节钮控件的当前基。|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|检索指向当前合作者窗口的指针。|
|[CSpinButtonCtrl::GetPos](#getpos)|检索数值调节钮控件的当前位置。|
|[CSpinButtonCtrl::GetRange](#getrange)|检索数值调节钮控件的上限和下限 (范围)。|
|[CSpinButtonCtrl::SetAccel](#setaccel)|为数值调节钮控件设置加速。|
|[CSpinButtonCtrl::SetBase](#setbase)|为数值调节钮控件设置基准。|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|设置数值调节钮控件的合作者窗口。|
|[CSpinButtonCtrl::SetPos](#setpos)|设置控件的当前位置。|
|[CSpinButtonCtrl::SetRange](#setrange)|设置数值调节钮控件的上限和下限 (范围)。|

## <a name="remarks"></a>备注

"数值调节钮控件" (也称为 up-down 控件) 是一对箭头按钮, 用户可以单击这些按钮来递增或递减值, 例如滚动位置或伴随控件中显示的数字。 与数字显示按钮控件关联的值称为其当前位置。 数值调节钮控件最常用于伴向控制, 称为 "合作者窗口"。

此控件 (因而`CSpinButtonCtrl`类) 仅适用于在 windows 95/98 和 windows NT 版本3.51 及更高版本下运行的程序。

对于用户, 数值调节钮控件及其合作者窗口通常类似于单个控件。 您可以指定数值调节钮控件自动定位在其合作者窗口的旁边, 并自动将合作者窗口的标题设置为其当前位置。 您可以通过 "编辑" 控件使用数值调节钮控件来提示用户输入数字。

单击向上箭头将当前位置移动到最大值, 然后单击向下箭头将当前位置向下移动。 默认情况下, 最小值为 100, 最大值为0。 当最小设置大于最大设置时 (例如, 使用默认设置时), 单击向上箭头可减小位置值, 单击向下箭头将增加位置值。

没有合作者窗口的数值调节钮控件的功能是一种简化的滚动条。 例如, 选项卡控件有时显示数值调节钮控件, 以使用户能够将其他选项卡滚动到视图中。

有关使用`CSpinButtonCtrl`的详细信息, 请参阅[控件](../../mfc/controls-mfc.md)和[使用 CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="create"></a>CSpinButtonCtrl:: Create

创建数值调节钮控件, 并将其附加`CSpinButtonCtrl`到对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定数值调节钮控件的样式。 将数值调节钮控件样式的任意组合应用于控件。 Windows SDK 中的 up-down[控件样式](/windows/desktop/Controls/up-down-control-styles)介绍了这些样式。

*rect*<br/>
指定数值调节钮控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构

*pParentWnd*<br/>
指向数值调节钮控件的父窗口的指针, 通常`CDialog`为。 它不能为 NULL。

*nID*<br/>
指定数值调节钮控件的 ID。

### <a name="return-value"></a>返回值

如果初始化成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

首先在两`CSpinButtonCtrl`个步骤中构造对象, 调用构造函数, 然后调用`Create`, 它将创建数值调节钮控件, `CSpinButtonCtrl`并将其附加到对象。

若要创建具有扩展窗口样式的数值调节钮控件, 请调用[CSpinButtonCtrl:: CreateEx](#createex)而不是`Create`。

##  <a name="createex"></a>CSpinButtonCtrl:: CreateEx

创建一个控件 (子窗口) 并将`CSpinButtonCtrl`其与对象关联。

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
指定正在创建的控件的扩展样式。 有关扩展 windows 样式的列表, 请参阅 Windows SDK 中[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)的*dwExStyle*参数。

*dwStyle*<br/>
指定数值调节钮控件的样式。 将数值调节钮控件样式的任意组合应用于控件。 Windows SDK 中的 up-down[控件样式](/windows/desktop/Controls/up-down-control-styles)介绍了这些样式。

*rect*<br/>
对[矩形](/previous-versions/dd162897\(v=vs.85\))结构的引用, 该结构描述要创建的窗口的大小和位置 (以*pParentWnd*的工作区坐标表示)。

*pParentWnd*<br/>
指向作为控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是[Create](#create)来应用扩展的 windows 样式, 由 windows 扩展样式指定的 WS_EX_。

##  <a name="cspinbuttonctrl"></a>CSpinButtonCtrl:: CSpinButtonCtrl

构造 `CSpinButtonCtrl` 对象。

```
CSpinButtonCtrl();
```

##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel

检索数值调节钮控件的加速信息。

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>参数

*nAccel*<br/>
由*pAccel*指定的数组中的元素数。

*pAccel*<br/>
指向接收加速信息的[UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-udaccel)结构的数组的指针。

### <a name="return-value"></a>返回值

检索的快捷键结构数。

##  <a name="getbase"></a>CSpinButtonCtrl:: GetBase

检索数值调节钮控件的当前基。

```
UINT GetBase() const;
```

### <a name="return-value"></a>返回值

当前基值。

##  <a name="getbuddy"></a>CSpinButtonCtrl:: GetBuddy

检索指向当前合作者窗口的指针。

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>返回值

指向当前合作者窗口的指针。

##  <a name="getpos"></a>CSpinButtonCtrl:: GetPos

检索数值调节钮控件的当前位置。

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>参数

*lpbError*<br/>
一个指向布尔值的指针, 如果值成功检索, 则该值设置为零; 如果发生错误, 则设置为非零值。 如果将此参数设置为 NULL, 则不会报告错误。

### <a name="return-value"></a>返回值

第一个版本返回低序位字中的16位当前位置。 如果发生错误, 高位字为非零。

第二个版本返回32位位置。

### <a name="remarks"></a>备注

当它处理返回的值时, 控件将根据合作者窗口的标题更新其当前位置。 如果没有合作者窗口, 或者标题指定了无效或超出范围的值, 则控件会返回错误。

##  <a name="getrange"></a>CSpinButtonCtrl:: GetRange

检索数值调节钮控件的上限和下限 (范围)。

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

*下移*<br/>
对接收控件下限的整数的引用。

*upper*<br/>
对接收控件上限的整数的引用。

### <a name="return-value"></a>返回值

第一个版本返回包含上限和下限的32位值。 低序位字是控件的上限, 而高序位字是下限。

### <a name="remarks"></a>备注

该成员函数`GetRange32`将数值调节钮控件的范围检索为32位整数。

##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel

为数值调节钮控件设置加速。

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>参数

*nAccel*<br/>
*PAccel*指定的[UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-udaccel)结构的数量。

*pAccel*<br/>
指向 UDACCEL 结构的数组的指针, 该数组包含加速信息。 元素应根据`nSec`成员按升序排序。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="setbase"></a>CSpinButtonCtrl:: SetBase

为数值调节钮控件设置基准。

```
int SetBase(int nBase);
```

### <a name="parameters"></a>参数

*nBase*<br/>
控件的新基础值。 对于十进制, 它可以是 10, 对于十六进制则可为16。

### <a name="return-value"></a>返回值

如果成功, 则为上一个基值; 如果给定了无效的基, 则为零。

### <a name="remarks"></a>备注

基值确定合作者窗口是以十进制数字还是十六进制数字显示数字。 十六进制数字始终无符号;对十进制数字进行签名。

##  <a name="setbuddy"></a>CSpinButtonCtrl:: SetBuddy

设置数值调节钮控件的合作者窗口。

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>参数

*pWndBuddy*<br/>
指向新的合作者窗口的指针。

### <a name="return-value"></a>返回值

指向上一个合作者窗口的指针。

### <a name="remarks"></a>备注

旋转控件几乎总是与另一个窗口 (如编辑控件) 关联, 后者显示某些内容。 此窗口称为陀螺旋控件的 "合作者"。

##  <a name="setpos"></a>CSpinButtonCtrl:: SetPos

设置数值调节钮控件的当前位置。

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
控件的新位置。 此值必须在控件的上限和下限指定的范围内。

### <a name="return-value"></a>返回值

上一个位置 (16 位精度, 为`SetPos`, 32 位`SetPos32`精度)。

### <a name="remarks"></a>备注

`SetPos32`设置32位位置。

##  <a name="setrange"></a>CSpinButtonCtrl:: SetRange

设置数值调节钮控件的上限和下限 (范围)。

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>参数

*nLower*和*nUpper*<br/>
控件的上限和下限。 对于`SetRange`, 两个限制都不能大于 UD_MAXVAL 或小于 UD_MINVAL; 此外, 这两个限制之间的差异不能超过 UD_MAXVAL。 `SetRange32`对限制无限制;使用任意整数。

### <a name="remarks"></a>备注

此成员函数`SetRange32`为数值调节钮控件设置32位范围。

> [!NOTE]
>  数值调节钮的默认范围最大值设置为零 (0), 最小值设置为100。 由于最大值小于最小值, 因此单击上箭头将减小位置, 单击向下箭头将增加位置。 用于`CSpinButtonCtrl::SetRange`调整这些值。

## <a name="see-also"></a>请参阅

[MFC 示例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl 类](../../mfc/reference/csliderctrl-class.md)
