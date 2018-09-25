---
title: CSpinButtonCtrl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e37f277c4d1676a15aa5f1c0cd593bf0a181040
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395734"
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
|[CSpinButtonCtrl::Create](#create)|创建数值调节按钮控件，并将其附加到`CSpinButtonCtrl`对象。|
|[CSpinButtonCtrl::CreateEx](#createex)|使用指定的 Windows 扩展样式创建数值调节按钮控件，并将其附加到`CSpinButtonCtrl`对象。|
|[CSpinButtonCtrl::GetAccel](#getaccel)|检索调节钮控件的加速信息。|
|[CSpinButtonCtrl::GetBase](#getbase)|检索调节钮控件的当前基。|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|检索指向当前合作者窗口的指针。|
|[CSpinButtonCtrl::GetPos](#getpos)|检索调节钮控件的当前位置。|
|[CSpinButtonCtrl::GetRange](#getrange)|检索的上限和下限限制 （范围） 数值调节按钮控件。|
|[CSpinButtonCtrl::SetAccel](#setaccel)|设置数值调节按钮控件的加速。|
|[CSpinButtonCtrl::SetBase](#setbase)|设置数值调节按钮控件的基础。|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|设置数值调节按钮控件的合作者窗口。|
|[CSpinButtonCtrl::SetPos](#setpos)|设置控件的当前位置。|
|[Cspinbuttonctrl:: Setrange](#setrange)|设置的上限和下限限制 （范围） 数值调节按钮控件。|

## <a name="remarks"></a>备注

"调节按钮控件"（也称为 up-down 控件） 是一对箭头按钮，用户可以单击要递增或递减值，如滚动位置或在附带控件中显示一个行号。 调节钮控件与关联的值被调用其当前位置。 调节钮控件最常用于与配套控件，称为"合作者窗口"。

此控件 (并因此`CSpinButtonCtrl`类) 仅适用于 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。

对用户来说，调节钮控件以及其合作者窗口通常如下所示单个控件。 您可以指定，调节钮控件自动将自身定位旁边其合作者窗口，并且它自动设置为其当前位置合作者窗口的标题。 可以使用一个编辑控件的调节钮控件来提示用户输入数字输入。

单击向上箭头则沿当前最大值，并单击向下箭头则沿当前最小值。 默认情况下，最小值为 100，最大值为 0。 最小值设置为大于最大值设置 （例如，当使用默认设置），请单击向上箭头减少任何时间位置值并单击向下箭头将增高。

作为一种简化的滚动条的函数没有合作者窗口的数值调节钮按钮控件。 例如，一个选项卡控件有时显示调节按钮控件，使用户能够滚动到视图的其他选项卡。

有关使用的详细信息`CSpinButtonCtrl`，请参阅[控件](../../mfc/controls-mfc.md)并[使用 CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="create"></a>  CSpinButtonCtrl::Create

创建数值调节按钮控件，并将其附加到`CSpinButtonCtrl`对象...

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定数值调节钮 button 控件的样式。 应用于控件的数值调节钮按钮控件样式的任意组合。 这些样式中所述[Up-down 控件样式](/windows/desktop/Controls/up-down-control-styles)Windows SDK 中。

*rect*<br/>
指定数值调节钮 button 控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构

*pParentWnd*<br/>
数值调节钮按钮控件的父窗口，通常一个指向`CDialog`。 它不能为 NULL。

*nID*<br/>
指定数值调节钮 button 控件的 id。

### <a name="return-value"></a>返回值

如果初始化成功，则非零值否则为 0。

### <a name="remarks"></a>备注

在构造`CSpinButtonCtrl`首先对象在两个步骤中，调用构造函数中，，然后调用`Create`，它创建数值调节按钮控件并将其附加到`CSpinButtonCtrl`对象。

若要使用扩展的窗口样式创建数值调节按钮控件，调用[CSpinButtonCtrl::CreateEx](#createex)而不是`Create`。

##  <a name="createex"></a>  CSpinButtonCtrl::CreateEx

创建控件 （子窗口），并将其与`CSpinButtonCtrl`对象。

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
指定要创建的控件的扩展的样式。 扩展的 windows 样式的列表，请参阅*dwExStyle*参数[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*dwStyle*<br/>
指定数值调节钮 button 控件的样式。 应用于控件的数值调节钮按钮控件样式的任意组合。 这些样式中所述[Up-down 控件样式](/windows/desktop/Controls/up-down-control-styles)Windows SDK 中。

*rect*<br/>
对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口的工作区中创建的位置*pParentWnd*。

*pParentWnd*<br/>
指向控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是[创建](#create)应用指定的 Windows 扩展的样式前言 WS_EX_ 扩展的 Windows 样式。

##  <a name="cspinbuttonctrl"></a>  CSpinButtonCtrl::CSpinButtonCtrl

构造 `CSpinButtonCtrl` 对象。

```
CSpinButtonCtrl();
```

##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel

检索调节钮控件的加速信息。

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>参数

*nAccel*<br/>
指定的数组中的元素数目*pAccel*。

*pAccel*<br/>
指向数组的指针[UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel)接收加速信息的结构。

### <a name="return-value"></a>返回值

检索的加速器结构数。

##  <a name="getbase"></a>  CSpinButtonCtrl::GetBase

检索调节钮控件的当前基。

```
UINT GetBase() const;
```

### <a name="return-value"></a>返回值

当前的基础值。

##  <a name="getbuddy"></a>  CSpinButtonCtrl::GetBuddy

检索指向当前合作者窗口的指针。

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>返回值

指向当前合作者窗口的指针。

##  <a name="getpos"></a>  CSpinButtonCtrl::GetPos

检索调节钮控件的当前位置。

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>参数

*lpbError*<br/>
已成功检索到或非零出错时，指向一个布尔值，该值设置为零的指针。 如果此参数设置为 NULL，将不会报告错误。

### <a name="return-value"></a>返回值

第一个版本返回 16 位中的当前位置低序位字。 高序位字为非零，如果出现错误。

第二个版本返回的 32 位位置。

### <a name="remarks"></a>备注

当它处理返回的值时，该控件更新其当前位置基于合作者窗口的标题。 如果没有合作者窗口或标题指定的无效或越界的值，该控件将返回错误。

##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange

检索的上限和下限限制 （范围） 数值调节按钮控件。

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

*较低*<br/>
一个整数，它接收控件的下限值对的引用。

*上限*<br/>
对一个整数，它接收控件的上限值的引用。

### <a name="return-value"></a>返回值

第一个版本将返回包含上限和下限限制为 32 位值。 低序位字是该控件的上限和高序位字是较低的限制。

### <a name="remarks"></a>备注

成员函数`GetRange32`检索作为 32 位整数的数值调节钮 button 控件的范围。

##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel

设置数值调节按钮控件的加速。

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>参数

*nAccel*<br/>
数[UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel)由指定的结构*pAccel*。

*pAccel*<br/>
指向 UDACCEL 结构，包含加速信息的数组的指针。 元素应按升序排序基于`nSec`成员。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase

设置数值调节按钮控件的基础。

```
int SetBase(int nBase);
```

### <a name="parameters"></a>参数

*nBase*<br/>
控件的新基本值。 它可以为 10 个十进制或十六进制的 16。

### <a name="return-value"></a>返回值

如果成功，以前的基础值或零，如果给定了无效的基数。

### <a name="remarks"></a>备注

基础值确定合作者窗口是否以十进制或十六进制数字显示数字。 十六进制数字始终是无符号;十进制数字进行签名。

##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy

设置数值调节按钮控件的合作者窗口。

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>参数

*pWndBuddy*<br/>
指向新的合作者窗口的指针。

### <a name="return-value"></a>返回值

指向上一个合作者窗口的指针。

### <a name="remarks"></a>备注

数值调节钮控件几乎始终是与另一个窗口，如一个编辑控件，显示一些内容相关联。 此其他窗口称为数值调节钮控件的"好友"。

##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos

设置数值调节按钮控件的当前位置。

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
控件的新位置。 此值必须为指定控件的上限和下限限制的范围。

### <a name="return-value"></a>返回值

以前的位置 (16 位精度`SetPos`32 位的精度`SetPos32`)。

### <a name="remarks"></a>备注

`SetPos32` 设置 32 位位置。

##  <a name="setrange"></a>  Cspinbuttonctrl:: Setrange

设置的上限和下限限制 （范围） 数值调节按钮控件。

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
控件的上限和下限限制。 有关`SetRange`、 既不限制可能会超出 UD_MAXVAL 或小于 UD_MINVAL; 此外，两个限制之间的差异不能超过 UD_MAXVAL。 `SetRange32` 限制; 提出任何限制使用任何整数。

### <a name="remarks"></a>备注

成员函数`SetRange32`设置调节钮控件的 32 位范围。

> [!NOTE]
>  调节按钮的默认范围具有设置为零 (0) 的最大值和最小值设置为 100。 因为最大值小于最小值，单击向上箭头将降低位置，并单击向下箭头会增加。 使用`CSpinButtonCtrl::SetRange`调整这些值。

## <a name="see-also"></a>请参阅

[MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl 类](../../mfc/reference/csliderctrl-class.md)
