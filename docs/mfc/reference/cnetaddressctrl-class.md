---
title: CNetAddressCtrl 类
ms.date: 11/19/2018
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
ms.openlocfilehash: 71e3b1a9fde84f96696d26c891ab6688f246d575
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363311"
---
# <a name="cnetaddressctrl-class"></a>CNetAddressCtrl 类

`CNetAddressCtrl` 类表示网络地址控件，可使用此控件输入和验证 IPv4、IPv6 与命名的 DNS 地址的格式。

## <a name="syntax"></a>语法

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CNet地址：：CNetAddressCtrl](#cnetaddressctrl)|构造 `CNetAddressCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CNetAddressCtrl：：创建](#create)|创建具有指定样式的网络地址控件并将其附加到当前`CNetAddressCtrl`对象。|
|[CNetAddressCtrl：：创建Ex](#createex)|创建具有指定扩展样式的网络地址控件，并将其附加到当前`CNetAddressCtrl`对象。|
|[CNetAddressCtrl：:D播放错误提示](#displayerrortip)|当用户在当前网络地址控件中输入不受支持的网络地址时，将显示错误气球提示。|
|[CNetAddressCtrl：：获取地址](#getaddress)|检索与当前网络地址控件关联的网络地址的已验证和解析表示形式。|
|[CNetAddressCtrl：：获取允许类型](#getallowtype)|检索当前网络地址控件可以支持的网络地址类型。|
|[CNetAddressCtrl：：SetAllow类型](#setallowtype)|设置当前网络地址控件可以支持的网络地址类型。|

## <a name="remarks"></a>备注

网络地址控件验证用户输入的地址格式是否正确。 控件实际上未连接到网络地址。 [CNetAddressCtrl：setAllowType](#setallowtype)方法指定[了 CNetAddressCtrl：：getAddress](#getaddress)方法可以解析和验证的一种或多种地址类型。 地址可以是 IPv4、IPv6 或服务器、网络、主机或广播消息目标的命名地址。 如果地址的格式不正确，则可以使用[CNetAddressCtrl：:DisplayErrorTip](#displayerrortip)方法显示一个信息提示消息框，该消息框以图形方式指向网络地址控件的文本框并显示预定义的错误消息。

类`CNetAddressCtrl`派生自[CEdit](../../mfc/reference/cedit-class.md)类。 因此，网络地址控件提供对所有 Windows 编辑控制消息的访问。

下图描述了包含网络地址控件的对话框。 网络地址控件的文本框 （1） 包含无效的网络地址。 如果网络地址无效，将显示信息提示消息 （2）。

![具有网络地址控件和信息提示的对话框。](../../mfc/reference/media/cnetaddctrl.png "具有网络地址控件和信息提示的对话框。")

## <a name="example"></a>示例

以下代码示例是验证网络地址的对话框的一部分。 三个单选按钮的事件处理程序指定网络地址可以是三种地址类型之一。 用户在网络控件的文本框中输入地址，然后按下一个按钮来验证地址。 如果地址有效，将显示成功消息;如果地址有效，则会显示成功消息。否则，将显示预定义的信息提示错误消息。

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>示例

对话框头文件中的以下代码示例定义[CNetAddressCtrl：：getAddress](#getaddress)方法所需的[NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address)[和NET_ADDRESS_INFO](/windows/win32/shell/hkey-type)变量。

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

此类在 Windows Vista 和更高版本中受支持。

此类的其他要求在 Windows [Vista 通用控件的生成要求中](../../mfc/build-requirements-for-windows-vista-common-controls.md)介绍。

## <a name="cnetaddressctrlcnetaddressctrl"></a><a name="cnetaddressctrl"></a>CNet地址：：CNetAddressCtrl

构造 `CNetAddressCtrl` 对象。

```
CNetAddressCtrl();
```

### <a name="remarks"></a>备注

使用[CNetAddressCtrl：：创建](#create)或[CNetAddressCtrl：createEx](#createex)方法创建网络控件并将其附加到`CNetAddressCtrl`对象。

## <a name="cnetaddressctrlcreate"></a><a name="create"></a>CNetAddressCtrl：：创建

创建具有指定样式的网络地址控件并将其附加到当前`CNetAddressCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*dwStyle*|[在]要应用于控件的样式的位组合。 有关详细信息，请参阅[编辑样式](../../mfc/reference/styles-used-by-mfc.md#edit-styles)。|
|*矩形*|[在]对包含控件位置和大小的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用。|
|*pparentwnd*|[在]指向作为控件的父窗口的[CWnd](../../mfc/reference/cwnd-class.md)对象的非空指针。|
|*nID*|[在]控件的 ID。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

## <a name="cnetaddressctrlcreateex"></a><a name="createex"></a>CNetAddressCtrl：：创建Ex

创建具有指定扩展样式的网络地址控件，并将其附加到当前`CNetAddressCtrl`对象。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*dwExStyle*|[在]要应用于控件的扩展样式的位组合 （OR）。 有关详细信息，请参阅[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函数的*dwExStyle*参数。|
|*dwStyle*|[在]要应用于控件的样式的位组合 （OR）。 有关详细信息，请参阅[编辑样式](../../mfc/reference/styles-used-by-mfc.md#edit-styles)。|
|*矩形*|[在]对包含控件位置和大小的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用。|
|*pparentwnd*|[在]指向作为控件的父窗口的[CWnd](../../mfc/reference/cwnd-class.md)对象的非空指针。|
|*nID*|[在]控件的 ID。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

## <a name="cnetaddressctrldisplayerrortip"></a><a name="displayerrortip"></a>CNetAddressCtrl：:D播放错误提示

在与当前网络地址控件关联的气球提示中显示一条错误消息。

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>返回值

此方法成功`S_OK`时的值;否则，错误代码。

### <a name="remarks"></a>备注

使用[CNetAddressCtrl：：SetAllowType](#setallowtype)方法指定当前网络地址控件可以支持的地址类型。 使用[CNetAddressCtrl：：GetAddress](#getaddress)方法验证和分析用户输入的网络地址。 如果[CNetAddressCtrl：：getAddress](#getaddress)方法不成功，请使用[CNetAddressCtrl：:DisplayErrorTip](#displayerrortip)方法显示错误消息信息提示。

此消息调用[NetAddr_DisplayErrorTip](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip)宏，这在 Windows SDK 中介绍。 该宏发送消息`NCM_DISPLAYERRORTIP`。

## <a name="cnetaddressctrlgetaddress"></a><a name="getaddress"></a>CNetAddressCtrl：：获取地址

检索与当前网络地址控件关联的网络地址的已验证和已分析表示形式。

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>参数

*p地址*<br/>
[进出]指向[NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address)结构的指针。  在调用 GetAddress 方法之前，将此结构的*pAddrInfo*成员设置为[NET_ADDRESS_INFO](/windows/win32/shell/hkey-type)结构的地址。

### <a name="return-value"></a>返回值

如果此方法成功，则该值S_OK;否则，COM 错误代码。 有关可能的错误代码的详细信息，请参阅[NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress)宏的返回值部分。

### <a name="remarks"></a>备注

如果此方法成功[，NET_ADDRESS_INFO](/windows/win32/shell/hkey-type)结构包含有关网络地址的其他信息。

使用[CNetAddressCtrl：：SetAllowType](#setallowtype)方法指定当前网络地址控件可以支持的地址类型。 使用[CNetAddressCtrl：：GetAddress](#getaddress)方法验证和分析用户输入的网络地址。 如果[CNetAddressCtrl：：getAddress](#getaddress)方法不成功，请使用[CNetAddressCtrl：:DisplayErrorTip](#displayerrortip)方法显示错误消息信息提示。

此方法调用[NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress)宏，这在 Windows SDK 中介绍。 该宏发送NCM_GETADDRESS消息。

## <a name="cnetaddressctrlgetallowtype"></a><a name="getallowtype"></a>CNetAddressCtrl：：获取允许类型

检索当前网络地址控件可以支持的网络地址类型。

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>返回值

指定网络地址控件可以支持的地址类型的标志的位组合 （OR）。 有关详细信息，请参阅[NET_STRING](/windows/win32/shell/net-string)。

### <a name="remarks"></a>备注

此消息调用[NetAddr_GetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype)宏，这在 Windows SDK 中介绍。 该宏发送NCM_GETALLOWTYPE消息。

## <a name="cnetaddressctrlsetallowtype"></a><a name="setallowtype"></a>CNetAddressCtrl：：SetAllow类型

设置当前网络地址控件可以支持的网络地址类型。

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*德瓦德尔·马斯克*|[在]指定网络地址控件可以支持的地址类型的标志的位组合 （OR）。 有关详细信息，请参阅[NET_STRING](/windows/win32/shell/net-string)。|

### <a name="return-value"></a>返回值

S_OK此方法是否成功;如果此方法成功，则否则，COM 错误代码。

### <a name="remarks"></a>备注

使用[CNetAddressCtrl：：SetAllowType](#setallowtype)方法指定当前网络地址控件可以支持的地址类型。 使用[CNetAddressCtrl：：GetAddress](#getaddress)方法验证和分析用户输入的网络地址。 如果[CNetAddressCtrl：：getAddress](#getaddress)方法不成功，请使用[CNetAddressCtrl：:DisplayErrorTip](#displayerrortip)方法显示错误消息信息提示。

此消息调用[NetAddr_SetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype)宏，这在 Windows SDK 中介绍。 该宏发送NCM_SETALLOWTYPE消息。

## <a name="see-also"></a>另请参阅

[CNetAddressCtrl 类](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)
