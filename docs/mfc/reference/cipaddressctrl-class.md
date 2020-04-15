---
title: CIPAddressCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
helpviewer_keywords:
- CIPAddressCtrl [MFC], CIPAddressCtrl
- CIPAddressCtrl [MFC], ClearAddress
- CIPAddressCtrl [MFC], Create
- CIPAddressCtrl [MFC], CreateEx
- CIPAddressCtrl [MFC], GetAddress
- CIPAddressCtrl [MFC], IsBlank
- CIPAddressCtrl [MFC], SetAddress
- CIPAddressCtrl [MFC], SetFieldFocus
- CIPAddressCtrl [MFC], SetFieldRange
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
ms.openlocfilehash: 28aa0e7137647bc49406dab1e82b9c2b05ca3538
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372344"
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl 类

提供 Windows 公共 IP 地址控件的功能。

## <a name="syntax"></a>语法

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CIPAddressCtrl：CIPAddressCtrl](#cipaddressctrl)|构造 `CIPAddressCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CIP地址：：清除地址](#clearaddress)|清除 IP 地址控件的内容。|
|[CIP地址Ctrl：创建](#create)|创建 IP 地址控件并将其附加到`CIPAddressCtrl`对象。|
|[CIP地址Ctrl：创建Ex](#createex)|使用指定的 Windows 扩展样式创建 IP 地址控件，并将其附加到`CIPAddressCtrl`对象。|
|[CIP地址：：获取地址](#getaddress)|检索 IP 地址控件中所有四个字段的地址值。|
|[CIP地址：：是空白](#isblank)|确定 IP 地址控件中的所有字段是否为空。|
|[CIP地址：：设置地址](#setaddress)|设置 IP 地址控件中所有四个字段的地址值。|
|[CIPAddressCtrl：：集场焦点](#setfieldfocus)|将键盘焦点设置到 IP 地址控件中的指定字段。|
|[CIPAddressCtrl：：塞特菲尔德](#setfieldrange)|设置 IP 地址控件中指定字段中的范围。|

## <a name="remarks"></a>备注

IP 地址控件（类似于编辑控件）允许您输入和操作 Internet 协议 （IP） 格式的数字地址。

此控件（因此是`CIPAddressCtrl`类）仅适用于在 Microsoft Internet Explorer 4.0 和更高版本下运行的程序。 它们也将在未来版本的 Windows 和 Windows NT 下提供。

有关 IP 地址控件的更多一般信息，请参阅 Windows SDK 中的[IP 地址控件](/windows/win32/Controls/ip-address-controls)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="cipaddressctrlcipaddressctrl"></a><a name="cipaddressctrl"></a>CIPAddressCtrl：CIPAddressCtrl

创建一个 `CIPAddressCtrl` 对象。

```
CIPAddressCtrl();
```

## <a name="cipaddressctrlclearaddress"></a><a name="clearaddress"></a>CIP地址：：清除地址

清除 IP 地址控件的内容。

```
void ClearAddress();
```

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress)，如 Windows SDK 中所述。

## <a name="cipaddressctrlcreate"></a><a name="create"></a>CIP地址Ctrl：创建

创建 IP 地址控件并将其附加到`CIPAddressCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
IP 地址控件的样式。 应用窗口样式的组合。 您必须包括WS_CHILD样式，因为控件必须是子窗口。 有关窗口样式的列表，请参阅 Windows SDK 中[创建窗口](/windows/win32/api/winuser/nf-winuser-createwindoww)。

*矩形*<br/>
对 IP 地址控件的大小和位置的引用。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构。

*pparentwnd*<br/>
指向 IP 地址控件的父窗口的指针。 值不得为 NULL。

*nID*<br/>
IP 地址控件的 ID。

### <a name="return-value"></a>返回值

初始化成功时非零;否则 0。

### <a name="remarks"></a>备注

分两步`CIPAddressCtrl`构造对象。

1. 调用构造函数，该构造函数创建`CIPAddressCtrl`对象。

1. 调用`Create`，它创建 IP 地址控件。

如果要将扩展窗口样式与控件一起使用，请调用[CreateEx](#createex) `Create`而不是 。

## <a name="cipaddressctrlcreateex"></a><a name="createex"></a>CIP地址Ctrl：创建Ex

调用此函数以创建控件（子窗口），并将其与`CIPAddressCtrl`对象关联。

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
IP 地址控件的样式。 应用窗口样式的组合。 您必须包括WS_CHILD样式，因为控件必须是子窗口。 有关窗口样式的列表，请参阅 Windows SDK 中[创建窗口](/windows/win32/api/winuser/nf-winuser-createwindoww)。

*矩形*<br/>
对[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用，描述要创建的窗口的大小和位置，在*pParentWnd*的客户端坐标中。

*pparentwnd*<br/>
指向控件的父窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是["创建](#create)"来应用扩展的 Windows 样式，该样式由 Windows 扩展样式前言**WS_EX_** 指定。

## <a name="cipaddressctrlgetaddress"></a><a name="getaddress"></a>CIP地址：：获取地址

检索 IP 地址控件中所有四个字段的地址值。

```
int GetAddress(
    BYTE& nField0,
    BYTE& nField1,
    BYTE& nField2,
    BYTE& nField3);

int GetAddress(DWORD& dwAddress);
```

### <a name="parameters"></a>参数

*nField0*<br/>
从打包的 IP 地址对字段 0 值的引用。

*nField1*<br/>
从打包的 IP 地址对字段 1 值的引用。

*nField2*<br/>
从打包的 IP 地址对字段 2 值的引用。

*nField3*<br/>
从打包的 IP 地址对字段 3 值的引用。

*dwAddress*<br/>
对接收 IP 地址的 DWORD 值地址的引用。 请参阅显示*dwAddress*填充方式的表**的备注**。

### <a name="return-value"></a>返回值

IP 地址控件中的非空白字段数。

### <a name="remarks"></a>备注

此成员函数实现 win32 消息[IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)的行为，如 Windows SDK 中所述。 在上面的第一个原型中，控件的字段 0 到 3 中的数字分别从左到右读取，填充四个参数。 在上面的第二个原型中 *，dwAddress*填充如下。

|字段|包含字段值的位|
|-----------|-------------------------------------|
|0|24 到 31|
|1|16 到 23|
|2|8 到 15|
|3|0 到 7|

## <a name="cipaddressctrlisblank"></a><a name="isblank"></a>CIP地址：：是空白

确定 IP 地址控件中的所有字段是否为空。

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>返回值

如果所有 IP 地址控制字段都为空，则非零;否则 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[IPM_ISBLANK](/windows/win32/Controls/ipm-isblank)的行为，如 Windows SDK 中所述。

## <a name="cipaddressctrlsetaddress"></a><a name="setaddress"></a>CIP地址：：设置地址

设置 IP 地址控件中所有四个字段的地址值。

```
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>参数

*nField0*<br/>
来自打包 IP 地址的字段 0 值。

*nField1*<br/>
来自打包 IP 地址的字段 1 值。

*nField2*<br/>
包装 IP 地址中的字段 2 值。

*nField3*<br/>
来自打包 IP 地址的字段 3 值。

*dwAddress*<br/>
包含新 IP 地址的 DWORD 值。 请参阅显示如何填充 DWORD 值的表**的备注**。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)的行为，如 Windows SDK 中所述。 在上面的第一个原型中，控件的字段 0 到 3 中的数字分别从左到右读取，填充四个参数。 在上面的第二个原型中 *，dwAddress*填充如下。

|字段|包含字段值的位|
|-----------|-------------------------------------|
|0|24 到 31|
|1|16 到 23|
|2|8 到 15|
|3|0 到 7|

## <a name="cipaddressctrlsetfieldfocus"></a><a name="setfieldfocus"></a>CIPAddressCtrl：：集场焦点

将键盘焦点设置到 IP 地址控件中的指定字段。

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>参数

*n菲尔德*<br/>
应设置焦点的零基字段索引。 如果此值大于字段数，则焦点将设置为第一个空白字段。 如果所有字段均为非空白，则焦点将设置为第一个字段。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus)的行为，如 Windows SDK 中所述。

## <a name="cipaddressctrlsetfieldrange"></a><a name="setfieldrange"></a>CIPAddressCtrl：：塞特菲尔德

设置 IP 地址控件中指定字段中的范围。

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>参数

*n菲尔德*<br/>
将应用范围的零字段索引。

*n 更低*<br/>
对在此 IP 地址控件中接收指定字段的下限的整数的引用。

*n 上*<br/>
对在此 IP 地址控件中接收指定字段上限的整数的引用。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[IPM_SETRANGE](/windows/win32/Controls/ipm-setrange)的行为，如 Windows SDK 中所述。 使用两个参数*nLower*和*nUpper*来指示字段的下限和上限，而不是与 Win32 消息一起使用的*wRange*参数。

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
