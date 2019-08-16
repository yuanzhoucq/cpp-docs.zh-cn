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
ms.openlocfilehash: fe8e3109b110c27ab32dc1a4f9a132f1e1c18638
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505820"
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl 类

提供 Windows 公共 IP 地址控件的功能。

## <a name="syntax"></a>语法

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|构造 `CIPAddressCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|清除 IP 地址控件的内容。|
|[CIPAddressCtrl::Create](#create)|创建 IP 地址控件, 并将其附加到`CIPAddressCtrl`对象。|
|[CIPAddressCtrl::CreateEx](#createex)|创建具有指定 Windows 扩展样式的 IP 地址控件, 并将其附加到`CIPAddressCtrl`对象。|
|[CIPAddressCtrl::GetAddress](#getaddress)|检索 IP 地址控件中所有四个字段的地址值。|
|[CIPAddressCtrl::IsBlank](#isblank)|确定 IP 地址控件中的所有字段是否为空。|
|[CIPAddressCtrl::SetAddress](#setaddress)|设置 IP 地址控件中所有四个字段的地址值。|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|将键盘焦点设置到 IP 地址控件中的指定字段。|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|设置 IP 地址控件中指定字段的范围。|

## <a name="remarks"></a>备注

IP 地址控件是一个类似于编辑控件的控件, 它允许您输入和操作 Internet 协议 (IP) 格式的数字地址。

此控件 (因而`CIPAddressCtrl`类) 仅适用于在 Microsoft Internet Explorer 4.0 和更高版本下运行的程序。 它们还将在未来版本的 Windows 和 Windows NT 下可用。

有关 IP 地址控制的更多常规信息, 请参阅 Windows SDK 中的[Ip 地址控制](/windows/win32/Controls/ip-address-controls)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="cipaddressctrl"></a>  CIPAddressCtrl::CIPAddressCtrl

创建一个 `CIPAddressCtrl` 对象。

```
CIPAddressCtrl();
```

##  <a name="clearaddress"></a>  CIPAddressCtrl::ClearAddress

清除 IP 地址控件的内容。

```
void ClearAddress();
```

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress)的行为, 如 Windows SDK 中所述。

##  <a name="create"></a>  CIPAddressCtrl::Create

创建 IP 地址控件, 并将其附加到`CIPAddressCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
IP 地址控件的样式。 应用窗口样式的组合。 必须包含 WS_CHILD 样式, 因为控件必须是子窗口。 有关 Windows 样式的列表, 请参阅 Windows SDK 中的[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 。

*rect*<br/>
对 IP 地址控件的大小和位置的引用。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构。

*pParentWnd*<br/>
指向 IP 地址控件的父窗口的指针。 它不能为 NULL。

*nID*<br/>
IP 地址控件的 ID。

### <a name="return-value"></a>返回值

如果初始化成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

可以通过`CIPAddressCtrl`两个步骤构造对象。

1. 调用构造函数, 该构造函数`CIPAddressCtrl`创建对象。

1. 调用`Create`, 它创建 IP 地址控件。

如果要在控件中使用扩展的 windows 样式, 请调用[CreateEx](#createex)而不`Create`是。

##  <a name="createex"></a>  CIPAddressCtrl::CreateEx

调用此函数可创建控件 (子窗口) 并将其与`CIPAddressCtrl`对象关联。

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
IP 地址控件的样式。 应用窗口样式的组合。 必须包含 WS_CHILD 样式, 因为控件必须是子窗口。 有关 Windows 样式的列表, 请参阅 Windows SDK 中的[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 。

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

##  <a name="getaddress"></a>  CIPAddressCtrl::GetAddress

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
从打包的 IP 地址对字段0值的引用。

*nField1*<br/>
从打包的 IP 地址对字段1值的引用。

*nField2*<br/>
对打包的 IP 地址中的字段2值的引用。

*nField3*<br/>
对来自打包 IP 地址的字段3值的引用。

*dwAddress*<br/>
对接收 IP 地址的 DWORD 值地址的引用。 有关显示*dwAddress*填充方式的表, 请参阅 "**备注**"。

### <a name="return-value"></a>返回值

IP 地址控件中的非空字段数。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)的行为, 如 Windows SDK 中所述。 在上面的第一个原型中, 控件的第0到3个字段中的数字分别从左向右读取, 并填充了这四个参数。 在上述第二个原型中, *dwAddress*按如下方式填充。

|字段|包含字段值的位|
|-----------|-------------------------------------|
|0|24到31|
|1|16到23|
|2|8到15|
|3|0到7|

##  <a name="isblank"></a>CIPAddressCtrl:: IsBlank

确定 IP 地址控件中的所有字段是否为空。

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>返回值

如果所有 IP 地址控件字段为空, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[IPM_ISBLANK](/windows/win32/Controls/ipm-isblank)的行为, 如 Windows SDK 中所述。

##  <a name="setaddress"></a>  CIPAddressCtrl::SetAddress

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
打包的 IP 地址的字段0值。

*nField1*<br/>
来自已打包 IP 地址的字段1值。

*nField2*<br/>
来自已打包 IP 地址的字段2值。

*nField3*<br/>
来自已打包 IP 地址的字段3值。

*dwAddress*<br/>
一个包含新 IP 地址的 DWORD 值。 有关显示 DWORD 值的方式的表, 请参阅 "**备注**"。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)的行为, 如 Windows SDK 中所述。 在上面的第一个原型中, 控件的第0到3个字段中的数字分别从左向右读取, 并填充了这四个参数。 在上述第二个原型中, *dwAddress*按如下方式填充。

|字段|包含字段值的位|
|-----------|-------------------------------------|
|0|24到31|
|1|16到23|
|2|8到15|
|3|0到7|

##  <a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus

将键盘焦点设置到 IP 地址控件中的指定字段。

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>参数

*nField*<br/>
应将焦点设置到的从零开始的字段索引。 如果此值大于字段数, 则将焦点设置为第一个空白字段。 如果所有字段均不为空, 则将焦点设置为第一个字段。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus)的行为, 如 Windows SDK 中所述。

##  <a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange

设置 IP 地址控件中指定字段的范围。

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>参数

*nField*<br/>
范围将应用到的从零开始的字段索引。

*nLower*<br/>
对接收此 IP 地址控件中指定字段下限的整数的引用。

*nUpper*<br/>
对接收此 IP 地址控件中指定字段上限的整数的引用。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[IPM_SETRANGE](/windows/win32/Controls/ipm-setrange)的行为, 如 Windows SDK 中所述。 使用*nLower*和*nUpper*这两个参数来指示字段的下限和上限, 而不是与 Win32 消息一起使用的*wRange*参数。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
