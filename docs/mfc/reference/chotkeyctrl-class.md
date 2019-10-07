---
title: CHotKeyCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
ms.openlocfilehash: 9818c32a7779d646ca5a9485a1331dfa393408ba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506150"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl 类

提供 Windows 公共热键控件的功能。

## <a name="syntax"></a>语法

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CHotKeyCtrl:: CHotKeyCtrl](#chotkeyctrl)|构造 `CHotKeyCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CHotKeyCtrl::Create](#create)|创建热键控件并将其附加到`CHotKeyCtrl`对象。|
|[CHotKeyCtrl::CreateEx](#createex)|使用指定的 Windows 扩展样式创建热键控件, 并将其附加到`CHotKeyCtrl`对象。|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|从热键控件中检索热键的虚拟键代码和修饰符标志。|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|检索本地字符集中分配给热键的密钥名称。|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|检索本地字符集中分配给指定虚拟键代码的键名称。|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|设置热键控件的热键组合。|
|[CHotKeyCtrl::SetRules](#setrules)|为热键控件定义无效的组合和默认修饰符组合。|

## <a name="remarks"></a>备注

"热键控件" 是使用户能够创建热键的窗口。 "热键" 是用户可以按其快速执行操作的组合键。 (例如, 用户可以创建激活给定窗口的热键, 并将其放到 Z 顺序的顶部。)热键控件显示用户的选择, 并确保用户选择有效的键组合。

此控件 (因而`CHotKeyCtrl`类) 仅适用于在 windows 95/98 和 windows NT 版本3.51 及更高版本下运行的程序。

当用户选择了组合键后, 应用程序可以从控件中检索指定的组合键, 并使用 WM_SETHOTKEY 消息在系统中设置热键。 每当用户按下热键后, 在系统的任何部分中, 在 WM_SETHOTKEY 消息中指定的窗口将接收指定 SC_HOTKEY 的 WM_SYSCOMMAND 消息。 此消息将激活接收它的窗口。 热键始终有效, 直到调用 WM_SETHOTKEY 的应用程序退出。

此机制不同于依赖于 WM_HOTKEY 消息和 Windows [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey)和[UnregisterHotKey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey)函数的热键支持。

有关使用`CHotKeyCtrl`的详细信息, 请参阅[控件](../../mfc/controls-mfc.md)和[使用 CHotKeyCtrl](../../mfc/using-chotkeyctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="chotkeyctrl"></a>CHotKeyCtrl:: CHotKeyCtrl

构造 `CHotKeyCtrl` 对象。

```
CHotKeyCtrl();
```

##  <a name="create"></a>CHotKeyCtrl:: Create

创建热键控件并将其附加到`CHotKeyCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定热键控件的样式。 应用任何控件样式组合。 有关详细信息, 请参阅 Windows SDK 中的[常见控件样式](/windows/win32/Controls/common-control-styles)。

*rect*<br/>
指定热键控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT 结构](/windows/win32/api/windef/ns-windef-rect)。

*pParentWnd*<br/>
指定热键控件的父窗口, 通常为[CDialog](../../mfc/reference/cdialog-class.md)。 它不能为 NULL。

*nID*<br/>
指定热键控件的 ID。

### <a name="return-value"></a>返回值

如果初始化成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

可以通过`CHotKeyCtrl`两个步骤构造对象。 首先, 调用构造函数, 然后调用`Create`, 它将创建热键控件并将其附加`CHotKeyCtrl`到对象。

如果要在控件中使用扩展的 windows 样式, 请调用[CreateEx](#createex)而不`Create`是。

##  <a name="createex"></a>CHotKeyCtrl:: CreateEx

调用此函数可创建控件 (子窗口) 并将其与`CHotKeyCtrl`对象关联。

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
指定正在创建的控件的扩展样式。 有关扩展 Windows 样式的列表, 请参阅 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定热键控件的样式。 应用任何控件样式组合。 有关详细信息, 请参阅 Windows SDK 中的[常见控件样式](/windows/win32/Controls/common-control-styles)。

*rect*<br/>
对[矩形](/previous-versions/dd162897\(v=vs.85\))结构的引用, 该结构描述要创建的窗口的大小和位置 (以*pParentWnd*的工作区坐标表示)。

*pParentWnd*<br/>
指向作为控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是[Create](#create)来应用扩展的 windows 样式, 由 windows 扩展样式指定的**WS_EX_** 。

##  <a name="gethotkey"></a>CHotKeyCtrl:: GetHotKey

从热键控件中检索键盘快捷方式的虚拟键代码和修饰符标志。

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>参数

*wVirtualKeyCode*<br/>
弄键盘快捷方式的虚拟键代码。 有关标准虚拟键代码的列表, 请参阅 Winuser.h。

*wModifiers*<br/>
弄标志的按位组合 (OR), 用来指示键盘快捷方式中的修改键。

修饰符标志如下所示:

|Flag|对应的键|
|----------|-----------------------|
|HOTKEYF_ALT|Alt 键|
|HOTKEYF_CONTROL|CTRL 键|
|HOTKEYF_EXT|扩展密钥|
|HOTKEYF_SHIFT|SHIFT 键|

### <a name="return-value"></a>返回值

在第一个重载的方法中, 包含虚拟键代码和修饰符标志的 DWORD。 低序位字的低序位字节包含虚拟键代码, 低序位字的高序位字节包含修饰符标志, 而高序位字为零。

### <a name="remarks"></a>备注

虚拟键代码和修改键共同定义键盘快捷方式。

##  <a name="gethotkeyname"></a>CHotKeyCtrl:: GetHotKeyName

调用此成员函数以获取热键的本地化名称。

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>返回值

当前选定的热键的本地化名称。 如果没有选定的热键, `GetHotKeyName`则返回空字符串。

### <a name="remarks"></a>备注

此成员函数返回的名称来自键盘驱动程序。 您可以在 Windows 的本地化版本中安装非本地化键盘驱动程序, 反之亦然。

##  <a name="getkeyname"></a>CHotKeyCtrl:: GetKeyName

调用此成员函数以获取分配给指定虚拟键代码的密钥的本地化名称。

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>参数

*vk*<br/>
虚拟键代码。

*fExtended*<br/>
如果虚拟键代码是扩展密钥, 则为 TRUE;否则为 FALSE。

### <a name="return-value"></a>返回值

*Vk*参数指定的密钥的本地化名称。 如果该键没有映射名称, `GetKeyName`则返回空字符串。

### <a name="remarks"></a>备注

此函数返回的键名称来自键盘驱动程序, 因此您可以在本地化版本的 Windows 中安装非本地化键盘驱动程序, 反之亦然。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

##  <a name="sethotkey"></a>CHotKeyCtrl:: SetHotKey

设置热键控件的键盘快捷键。

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>参数

*wVirtualKeyCode*<br/>
中键盘快捷方式的虚拟键代码。 有关标准虚拟键代码的列表, 请参阅 Winuser.h。

*wModifiers*<br/>
中标志的按位组合 (OR), 用来指示键盘快捷方式中的修改键。

修饰符标志如下所示:

|Flag|对应的键|
|----------|-----------------------|
|HOTKEYF_ALT|Alt 键|
|HOTKEYF_CONTROL|CTRL 键|
|HOTKEYF_EXT|扩展密钥|
|HOTKEYF_SHIFT|SHIFT 键|

### <a name="remarks"></a>备注

虚拟键代码和修改键共同定义键盘快捷方式。

##  <a name="setrules"></a>CHotKeyCtrl:: 指向

调用此函数可为热键控件定义无效的组合和默认修饰符组合。

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>参数

*wInvalidComb*<br/>
指定无效键组合的标志数组。 它可以是下列值的组合:

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- HKCOMB_NONE 未修改的密钥

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT + ALT

- HKCOMB_SC SHIFT + CTRL

- HKCOMB_SCA SHIFT + CTRL + ALT

*wModifiers*<br/>
标志的数组, 指定在用户输入无效组合时要使用的键组合。 有关修饰符标志的详细信息, 请参阅[GetHotKey](#gethotkey)。

### <a name="remarks"></a>备注

如果用户输入无效的键组合 (如*wInvalidComb*中指定的标志所定义), 系统将使用 OR 运算符将用户输入的密钥与*wModifiers*中指定的标志组合在一起。 生成的键组合将转换为字符串, 然后显示在热键控件中。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
