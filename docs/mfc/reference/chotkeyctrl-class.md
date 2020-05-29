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
ms.openlocfilehash: a79cc0ab2c01633f96430477aa536a60385461e9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750800"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl 类

提供 Windows 公共热键控件的功能。

## <a name="syntax"></a>语法

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CHotKeyctrl：：CHotkeyCtrl](#chotkeyctrl)|构造 `CHotKeyCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CHotKeyCtrl：：创建](#create)|创建热键控件并将其附加到`CHotKeyCtrl`对象。|
|[CHotKeyctrl：：创建Ex](#createex)|使用指定的 Windows 扩展样式创建热键控件，并将其附加到`CHotKeyCtrl`对象。|
|[CHotKeyctrl：获取HotKey](#gethotkey)|从热键控件检索热键的虚拟密钥代码和修改器标志。|
|[CHotKeyctrl：获取Hotkey名称](#gethotkeyname)|检索分配给热键的本地字符集中的键名称。|
|[CHotKeyctrl：获取键名称](#getkeyname)|检索分配给指定虚拟密钥代码的本地字符集中的密钥名称。|
|[CHotKeyctrl：：设置HotKey](#sethotkey)|设置热键控制的热键组合。|
|[CHotKeyctrl：：设置规则](#setrules)|定义热键控件的无效组合和默认修改器组合。|

## <a name="remarks"></a>备注

"热键控件"是允许用户创建热键的窗口。 "热键"是用户可以按快速执行操作的键组合。 （例如，用户可以创建一个热键，该热键可激活给定的窗口并将其带到 Z 顺序的顶部。热键控件显示用户的选择，并确保用户选择有效的密钥组合。

此控件（因此该`CHotKeyCtrl`类）仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

当用户选择密钥组合后，应用程序可以从控件中检索指定的密钥组合，并使用WM_SETHOTKEY消息在系统中设置热键。 此后，每当用户从系统的任何部分按下热键时，WM_SETHOTKEY消息中指定的窗口都会收到指定SC_HOTKEYWM_SYSCOMMAND消息。 此消息将激活接收它的窗口。 热键在调用WM_SETHOTKEY的应用程序退出之前保持有效。

此机制不同于依赖于WM_HOTKEY消息和 Windows[注册HotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey)和[取消注册 HotKey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey)功能的热键支持。

有关 使用`CHotKeyCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)[和使用 CHotKeyCtrl](../../mfc/using-chotkeyctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="chotkeyctrlchotkeyctrl"></a><a name="chotkeyctrl"></a>CHotKeyctrl：：CHotkeyCtrl

构造 `CHotKeyCtrl` 对象。

```
CHotKeyCtrl();
```

## <a name="chotkeyctrlcreate"></a><a name="create"></a>CHotKeyCtrl：：创建

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
指定热键控件的样式。 应用控件样式的任意组合。 有关详细信息，请参阅 Windows SDK 中的[通用控件样式](/windows/win32/Controls/common-control-styles)。

*矩形*<br/>
指定热键控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT 结构](/windows/win32/api/windef/ns-windef-rect)。

*pparentwnd*<br/>
指定热键控件的父窗口，通常为[CDialog](../../mfc/reference/cdialog-class.md)。 值不得为 NULL。

*nID*<br/>
指定热键控件的 ID。

### <a name="return-value"></a>返回值

非零，如果初始化成功;否则 0。

### <a name="remarks"></a>备注

分两步`CHotKeyCtrl`构造对象。 首先调用构造函数，然后调用`Create`，这将创建热键控件并将其附加到`CHotKeyCtrl`对象。

如果要将扩展窗口样式与控件一起使用，请调用[CreateEx](#createex) `Create`而不是 。

## <a name="chotkeyctrlcreateex"></a><a name="createex"></a>CHotKeyctrl：：创建Ex

调用此函数以创建控件（子窗口），并将其与`CHotKeyCtrl`对象关联。

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
指定要创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[创建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定热键控件的样式。 应用控件样式的任意组合。 有关详细信息，请参阅 Windows SDK 中的[通用控件样式](/windows/win32/Controls/common-control-styles)。

*矩形*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，描述要创建的窗口的大小和位置，在*pParentWnd*的客户端坐标中。

*pparentwnd*<br/>
指向控件的父窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是["创建](#create)"来应用扩展的 Windows 样式，该样式由 Windows 扩展样式前言**WS_EX_** 指定。

## <a name="chotkeyctrlgethotkey"></a><a name="gethotkey"></a>CHotKeyctrl：获取HotKey

从热键控件检索键盘快捷方式的虚拟键代码和修改器标志。

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>参数

*w虚拟密钥代码*<br/>
[出]键盘快捷键的虚拟键码。 有关标准虚拟密钥代码的列表，请参阅 Winuser.h。

*w 修饰器*<br/>
[出]指示键盘快捷键中修改器键的字面组合 （OR）。

修改器标志如下所示：

|标志|对应键|
|----------|-----------------------|
|HOTKEYF_ALT|Alt 键|
|HOTKEYF_CONTROL|CTRL 密钥|
|HOTKEYF_EXT|扩展密钥|
|HOTKEYF_SHIFT|换档键|

### <a name="return-value"></a>返回值

在第一个重载方法中，包含虚拟密钥代码和修改器标志的 DWORD。 低阶字的低阶字节包含虚拟键码，低阶单词的高阶字节包含修饰符标志，高阶字为零。

### <a name="remarks"></a>备注

虚拟键代码和修改器键一起定义键盘快捷键。

## <a name="chotkeyctrlgethotkeyname"></a><a name="gethotkeyname"></a>CHotKeyctrl：获取Hotkey名称

调用此成员函数获取热键的本地化名称。

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>返回值

当前选定的热键的本地化名称。 如果没有选定的热键，则`GetHotKeyName`返回一个空字符串。

### <a name="remarks"></a>备注

此成员函数返回的名称来自键盘驱动程序。 您可以在本地化版本的 Windows 中安装非本地化的键盘驱动程序，反之亦然。

## <a name="chotkeyctrlgetkeyname"></a><a name="getkeyname"></a>CHotKeyctrl：获取键名称

调用此成员函数获取分配给指定虚拟密钥代码的密钥的本地化名称。

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>参数

*vk*<br/>
虚拟密钥代码。

*f 扩展*<br/>
如果虚拟密钥代码是扩展密钥，则 TRUE;否则 FALSE。

### <a name="return-value"></a>返回值

*vk*参数指定的键的本地化名称。 如果键没有映射的名称，则`GetKeyName`返回一个空字符串。

### <a name="remarks"></a>备注

此功能返回的键名称来自键盘驱动程序，因此您可以在本地化版本的 Windows 中安装非本地化键盘驱动程序，反之亦然。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

## <a name="chotkeyctrlsethotkey"></a><a name="sethotkey"></a>CHotKeyctrl：：设置HotKey

设置热键控件的键盘快捷方式。

```cpp
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>参数

*w虚拟密钥代码*<br/>
[在]键盘快捷键的虚拟键码。 有关标准虚拟密钥代码的列表，请参阅 Winuser.h。

*w 修饰器*<br/>
[在]指示键盘快捷键中修改器键的字面组合 （OR）。

修改器标志如下所示：

|标志|对应键|
|----------|-----------------------|
|HOTKEYF_ALT|Alt 键|
|HOTKEYF_CONTROL|CTRL 密钥|
|HOTKEYF_EXT|扩展密钥|
|HOTKEYF_SHIFT|换档键|

### <a name="remarks"></a>备注

虚拟键代码和修改器键一起定义键盘快捷键。

## <a name="chotkeyctrlsetrules"></a><a name="setrules"></a>CHotKeyctrl：：设置规则

调用此函数以定义热键控件的无效组合和默认修改器组合。

```cpp
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>参数

*w 无效康布*<br/>
指定无效键组合的标志数组。 它可以是以下值的组合：

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL_ALT

- HKCOMB_NONE未修改的键

- HKCOMB_S班次

- HKCOMB_SA SHIFT_ALT

- HKCOMB_SC班位_CTRL

- HKCOMB_SCA班位_CTRL_ALT

*w 修饰器*<br/>
标记数组，指定用户输入无效组合时要使用的键组合。 有关修改标记的详细信息，请参阅[GetHotKey](#gethotkey)。

### <a name="remarks"></a>备注

当用户输入无效的键组合（由*wInvalidComb*中指定的标志定义）时，系统使用 OR 运算符将用户输入的键与*w 修改器*中指定的标志合并。 生成的键组合将转换为字符串，然后显示在热键控件中。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
