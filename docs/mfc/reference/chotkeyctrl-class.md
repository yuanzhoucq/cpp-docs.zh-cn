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
ms.openlocfilehash: 0b673c873f773844c13894d3f0448536f297dc53
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894505"
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
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|构造 `CHotKeyCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CHotKeyCtrl::Create](#create)|创建热键控件，并将其附加到`CHotKeyCtrl`对象。|
|[CHotKeyCtrl::CreateEx](#createex)|创建具有指定的 Windows 扩展样式的热键控件并将其附加到`CHotKeyCtrl`对象。|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|从热键控件检索热键的虚拟键代码和修饰符标志。|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|检索分配给热键的本地字符集中的项名称。|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|检索分配给指定的虚拟键代码的本地字符集中的项名称。|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|设置热键控件的热键组合。|
|[CHotKeyCtrl::SetRules](#setrules)|定义的无效组合和热键控件的默认修饰符组合。|

## <a name="remarks"></a>备注

"热键控件"是一个窗口，使用户能够创建热键。 "热键"是用户可以按下，以便快速执行操作的键组合。 （例如，用户可以创建热键，会激活给定的窗口并将其置于 Z 顺序的顶部。）热键控件显示用户的选择，并确保用户选择有效的键组合。

此控件 (并因此`CHotKeyCtrl`类) 仅适用于 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。

当用户已选择的组合键时，应用程序可以从控件检索指定的键组合，并使用 WM_SETHOTKEY 消息系统中设置热键。 每当用户按热键此后，在系统中，任何部分 WM_SETHOTKEY 消息中指定的窗口接收指定 SC_HOTKEY WM_SYSCOMMAND 消息。 此消息激活接收它的窗口。 热键之前调用 WM_SETHOTKEY 退出该应用程序将保持有效。

此机制是依赖于 WM_HOTKEY 消息和 Windows 的热密钥支持不同[RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey)并[UnregisterHotKey](/windows/desktop/api/winuser/nf-winuser-unregisterhotkey)函数。

有关使用的详细信息`CHotKeyCtrl`，请参阅[控件](../../mfc/controls-mfc.md)并[使用 CHotKeyCtrl](../../mfc/using-chotkeyctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="chotkeyctrl"></a>  CHotKeyCtrl::CHotKeyCtrl

构造 `CHotKeyCtrl` 对象。

```
CHotKeyCtrl();
```

##  <a name="create"></a>  CHotKeyCtrl::Create

创建热键控件，并将其附加到`CHotKeyCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定热键控件的样式。 将应用控件样式的任意组合。 请参阅[常见控件样式](/windows/desktop/Controls/common-control-styles)Windows SDK for 的详细信息中。

*rect*<br/>
指定热键控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT 结构](/windows/desktop/api/windef/ns-windef-tagrect)。

*pParentWnd*<br/>
指定热键控件的父窗口中，通常[CDialog](../../mfc/reference/cdialog-class.md)。 它不能为 NULL。

*nID*<br/>
指定热键控件的 id。

### <a name="return-value"></a>返回值

非零值，如果初始化成功，则否则为 0。

### <a name="remarks"></a>备注

构造`CHotKeyCtrl`两个步骤中的对象。 首先，调用构造函数，然后调用`Create`，它创建热键控件并将其附加到`CHotKeyCtrl`对象。

如果你想要在控件中使用扩展的 windows 样式，则调用[CreateEx](#createex)而不是`Create`。

##  <a name="createex"></a>  CHotKeyCtrl::CreateEx

调用此函数可创建的控件 （子窗口），并将其与`CHotKeyCtrl`对象。

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
指定要创建的控件的扩展的样式。 扩展 Windows 样式的列表，请参阅*dwExStyle*参数[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*dwStyle*<br/>
指定热键控件的样式。 将应用控件样式的任意组合。 有关详细信息，请参阅[常见控件样式](/windows/desktop/Controls/common-control-styles)Windows SDK 中。

*rect*<br/>
对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口的工作区中创建的位置*pParentWnd*。

*pParentWnd*<br/>
指向控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是[创建](#create)若要将应用扩展的 Windows 样式，指定的 Windows 扩展的样式加**WS_EX_**。

##  <a name="gethotkey"></a>  CHotKeyCtrl::GetHotKey

从热键控件中检索的键盘快捷方式的虚拟键代码和修饰符标志。

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>参数

*wVirtualKeyCode*<br/>
[out]键盘快捷方式的虚拟键代码。 标准虚拟键代码的列表，请参见 Winuser.h。

*wModifiers*<br/>
[out]按位组合 (OR) 这些标志指示键盘快捷方式中的修改键。

修饰符标志如下所示：

|Flag|对应的键|
|----------|-----------------------|
|HOTKEYF_ALT|Alt 键|
|HOTKEYF_CONTROL|CTRL 键|
|HOTKEYF_EXT|扩展的密钥|
|HOTKEYF_SHIFT|Shift 键|

### <a name="return-value"></a>返回值

在第一个重载方法，一个 dword 值，其中包含虚拟键代码和修饰符标志。 低序位字的低序位字节包含虚拟键代码，低序位字的高序位字节包含修饰符标志，并且高序位字为零。

### <a name="remarks"></a>备注

虚拟键代码和组合在一起的修改键定义的键盘快捷方式。

##  <a name="gethotkeyname"></a>  CHotKeyCtrl::GetHotKeyName

调用此成员函数可获取热键的本地化的名称。

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>返回值

当前所选热键的本地化的名称。 如果没有所选的热键`GetHotKeyName`返回空字符串。

### <a name="remarks"></a>备注

此成员函数返回的名称来自键盘驱动程序。 可以安装的非本地化键盘驱动程序中的 Windows，本地化版本，反之亦然。

##  <a name="getkeyname"></a>  CHotKeyCtrl::GetKeyName

调用此成员函数以获取分配给指定的虚拟键代码的键的本地化的名称。

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>参数

*vk*<br/>
虚拟键代码。

*fExtended*<br/>
如果虚拟键代码是否为扩展的键，则为 TRUE;否则为 FALSE。

### <a name="return-value"></a>返回值

指定的键的本地化的名称*vk*参数。 如果该密钥没有映射的名称，`GetKeyName`返回空字符串。

### <a name="remarks"></a>备注

此函数返回的项名称来自键盘驱动程序，以便可以安装的非本地化键盘驱动程序中的 Windows，本地化版本，反之亦然。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

##  <a name="sethotkey"></a>  CHotKeyCtrl::SetHotKey

设置热键控件的键盘快捷方式。

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>参数

*wVirtualKeyCode*<br/>
[in]键盘快捷方式的虚拟键代码。 标准虚拟键代码的列表，请参见 Winuser.h。

*wModifiers*<br/>
[in]按位组合 (OR) 这些标志指示键盘快捷方式中的修改键。

修饰符标志如下所示：

|Flag|对应的键|
|----------|-----------------------|
|HOTKEYF_ALT|Alt 键|
|HOTKEYF_CONTROL|CTRL 键|
|HOTKEYF_EXT|扩展的密钥|
|HOTKEYF_SHIFT|Shift 键|

### <a name="remarks"></a>备注

虚拟键代码和组合在一起的修改键定义的键盘快捷方式。

##  <a name="setrules"></a>  CHotKeyCtrl::SetRules

调用此函数可定义的无效组合和热键控件的默认修饰符组合。

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>参数

*wInvalidComb*<br/>
指定无效的键组合标志的数组。 它可以是以下值的组合：

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- HKCOMB_NONE 未修改键

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT+ALT

- HKCOMB_SC SHIFT+CTRL

- HKCOMB_SCA SHIFT+CTRL+ALT

*wModifiers*<br/>
标志数组，指定用户输入组合无效时要使用的键组合。 修饰符标志的详细信息，请参阅[GetHotKey](#gethotkey)。

### <a name="remarks"></a>备注

当用户输入无效的键组合，定义中指定的标志的*wInvalidComb*，系统使用 OR 运算符组合中指定的标志与用户输入的密钥*wModifiers*. 生成的键组合是转换为字符串，然后显示在热键控件。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)

