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
ms.openlocfilehash: e569829c100a581e24b5ce05df2f90ac7088024b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266286"
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
|[CIPAddressCtrl::Create](#create)|创建 IP 地址控件，并将其附加到`CIPAddressCtrl`对象。|
|[CIPAddressCtrl::CreateEx](#createex)|使用指定的 Windows 扩展样式创建 IP 地址控件，并将其附加到`CIPAddressCtrl`对象。|
|[CIPAddressCtrl::GetAddress](#getaddress)|检索 IP 地址控件中的所有四个字段的地址值。|
|[CIPAddressCtrl::IsBlank](#isblank)|确定是否 IP 地址控件中的所有字段都为空。|
|[CIPAddressCtrl::SetAddress](#setaddress)|设置 IP 地址控件中的所有四个字段的地址值。|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|将键盘焦点设置为 IP 地址控件中的指定字段。|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|在 IP 地址控件中的指定字段中设置的范围。|

## <a name="remarks"></a>备注

一个 IP 地址控件，类似于一个编辑控件，控件，可输入和操作中 Internet 协议 (IP) 格式的数字地址。

此控件 (并因此`CIPAddressCtrl`类) 仅供运行在 Microsoft Internet Explorer 4.0 及更高版本的程序。 它们也将在未来版本的 Windows 和 Windows NT 下可用。

IP 地址控件有关的更多常规信息，请参阅[IP 地址控件](/windows/desktop/Controls/ip-address-controls)Windows SDK 中。

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

此成员函数可实现 Win32 消息的行为[IPM_CLEARADDRESS](/windows/desktop/Controls/ipm-clearaddress)，如 Windows SDK 中所述。

##  <a name="create"></a>  CIPAddressCtrl::Create

创建 IP 地址控件，并将其附加到`CIPAddressCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
IP 地址控件的样式。 应用窗口样式的组合。 必须包括 WS_CHILD 样式，因为该控件必须是子窗口。 请参阅[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) Windows SDK for windows 样式的列表中。

*rect*<br/>
对 IP 地址控件的大小和位置的引用。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构。

*pParentWnd*<br/>
指向 IP 地址控件的父窗口的指针。 它不能为 NULL。

*nID*<br/>
IP 地址控件的 id。

### <a name="return-value"></a>返回值

如果初始化成功，则非零值否则为 0。

### <a name="remarks"></a>备注

构造`CIPAddressCtrl`两个步骤中的对象。

1. 调用构造函数，创建`CIPAddressCtrl`对象。

1. 调用`Create`，这将创建 IP 地址控件。

如果你想要在控件中使用扩展的 windows 样式，则调用[CreateEx](#createex)而不是`Create`。

##  <a name="createex"></a>  CIPAddressCtrl::CreateEx

调用此函数可创建的控件 （子窗口），并将其与`CIPAddressCtrl`对象。

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
IP 地址控件的样式。 应用窗口样式的组合。 必须包括 WS_CHILD 样式，因为该控件必须是子窗口。 请参阅[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) Windows SDK for windows 样式的列表中。

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

##  <a name="getaddress"></a>  CIPAddressCtrl::GetAddress

检索 IP 地址控件中的所有四个字段的地址值。

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
字段 0 值对发件人已打包的 IP 地址的引用。

*nField1*<br/>
对字段 1 值发件人已打包的 IP 地址的引用。

*nField2*<br/>
对字段 2 值发件人已打包的 IP 地址的引用。

*nField3*<br/>
对字段 3 值发件人已打包的 IP 地址的引用。

*dwAddress*<br/>
对接收的 IP 地址的 DWORD 值的地址的引用。 请参阅**备注**的表显示了如何*dwAddress*进行填充。

### <a name="return-value"></a>返回值

在 IP 地址控件中的非空字段数。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[IPM_GETADDRESS](/windows/desktop/Controls/ipm-getaddress)，如 Windows SDK 中所述。 在上面的第一个原型中, 读取的字段 0 到 3 的控件中的数字从左到右分别，填充的四个参数。 在上面的第二个原型*dwAddress*填充，如下所示。

|字段|包含字段值的位|
|-----------|-------------------------------------|
|0|24 到 31|
|1|16 到 23|
|2|8 到 15|
|3|0 到 7|

##  <a name="isblank"></a>  CIPAddressCtrl::IsBlank

确定是否 IP 地址控件中的所有字段都为空。

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>返回值

如果所有的 IP 地址控件字段都是空，则为非零值否则为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[IPM_ISBLANK](/windows/desktop/Controls/ipm-isblank)，如 Windows SDK 中所述。

##  <a name="setaddress"></a>  CIPAddressCtrl::SetAddress

设置 IP 地址控件中的所有四个字段的地址值。

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
中的已打包的 IP 地址的字段 0 值。

*nField1*<br/>
中的已打包的 IP 地址的字段 1 值。

*nField2*<br/>
中的已打包的 IP 地址的字段 2 值。

*nField3*<br/>
中的已打包的 IP 地址的字段 3 值。

*dwAddress*<br/>
一个 DWORD 值，该值包含新的 IP 地址。 请参阅**备注**的表显示了如何填充 DWORD 值。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[IPM_SETADDRESS](/windows/desktop/Controls/ipm-setaddress)，如 Windows SDK 中所述。 在上面的第一个原型中, 读取的字段 0 到 3 的控件中的数字从左到右分别，填充的四个参数。 在上面的第二个原型*dwAddress*填充，如下所示。

|字段|包含字段值的位|
|-----------|-------------------------------------|
|0|24 到 31|
|1|16 到 23|
|2|8 到 15|
|3|0 到 7|

##  <a name="setfieldfocus"></a>  CIPAddressCtrl::SetFieldFocus

将键盘焦点设置为 IP 地址控件中的指定字段。

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>参数

*nField*<br/>
应将焦点设置到的从零开始的字段索引。 如果此值大于的字段数，则会将焦点设置到第一个空白字段。 如果所有字段都均为非空，则会将焦点设置到的第一个字段。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[IPM_SETFOCUS](/windows/desktop/Controls/ipm-setfocus)，如 Windows SDK 中所述。

##  <a name="setfieldrange"></a>  CIPAddressCtrl::SetFieldRange

在 IP 地址控件中的指定字段中设置的范围。

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>参数

*nField*<br/>
将应用范围的从零开始的字段索引。

*nLower*<br/>
对此 IP 地址控件在接收指定的字段的下限的整数的引用。

*nUpper*<br/>
对此 IP 地址控件在接收指定的字段的上限的整数的引用。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[IPM_SETRANGE](/windows/desktop/Controls/ipm-setrange)，如 Windows SDK 中所述。 使用两个参数， *nLower*并*nUpper*，以指示该字段的下限和上限限制而不是*wRange* Win32 消息所使用的参数。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
