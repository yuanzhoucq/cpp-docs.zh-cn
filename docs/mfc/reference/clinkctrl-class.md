---
title: 链接课程
ms.date: 11/04/2016
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
ms.openlocfilehash: aa1f630b448c60a0eeb6a905ed6eef6f84a2ff8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372255"
---
# <a name="clinkctrl-class"></a>链接课程

提供 Windows 公共 SysLink 控件的功能。

## <a name="syntax"></a>语法

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[链接：：CLinkCtrl](#clinkctrl)|构造 `CLinkCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[链接：：创建](#create)|创建链接控件并将其附加到`CLinkCtrl`对象。|
|[链接：：创建Ex](#createex)|创建具有扩展样式的链接控件并将其附加到`CLinkCtrl`对象。|
|[链接：：获取理想高度](#getidealheight)|检索链路控件的理想高度。|
|[链接：：获取理想尺寸](#getidealsize)|根据链接的指定宽度计算当前链接控件的链接文本的首选高度。|
|[链接：获取项目](#getitem)|检索链接控件项的状态和属性。|
|[链接：：获取项目ID](#getitemid)|检索链接控件项的 ID。|
|[链接：：获取项目状态](#getitemstate)|检索链接控制项的状态。|
|[链接：：获取项目Url](#getitemurl)|检索链接控制项表示的 URL。|
|[链接：：HitTest](#hittest)|确定用户是否单击指定的链接。|
|[链接：设置项目](#setitem)|设置链接控件项的状态和属性。|
|[链接：：设置项目ID](#setitemid)|设置链接控件项的 ID。|
|[链接：：设置项目状态](#setitemstate)|设置链接控件项的状态。|
|[链接：：设置项目Url](#setitemurl)|设置由链接控件项表示的 URL。|

## <a name="remarks"></a>备注

"链接控件"提供了一种在窗口中嵌入超文本链接的便捷方法。 实际控件是一个窗口，用于呈现标记的文本，并在用户单击嵌入链接时启动相应的应用程序。 一个控件中支持多个链接，并且可以通过基于零的索引访问。

此控件（因此是`CLinkCtrl`类）仅适用于在 Windows XP 下运行的程序以及更高版本的程序。

有关详细信息，请参阅 Windows SDK 中的[SysLink 控件](/windows/win32/Controls/syslink-overview)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="clinkctrlclinkctrl"></a><a name="clinkctrl"></a>链接：：CLinkCtrl

构造 `CLinkCtrl` 对象。

```
CLinkCtrl();
```

## <a name="clinkctrlcreate"></a><a name="create"></a>链接：：创建

创建链接控件并将其附加到`CLinkCtrl`对象。

```
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*lpszLinkMarkup*<br/>
指向包含要显示的标记的向上文本的零端接字符串的指针。 有关详细信息，请参阅["SysLink 控件概述](/windows/win32/Controls/syslink-overview)"主题中的"标记和链接访问"部分。

*dwStyle*<br/>
指定链接控件的样式。 应用控件样式的任意组合。 有关详细信息，请参阅 中的`Windows SDK`[通用控件样式](/windows/win32/Controls/common-control-styles)。

*矩形*<br/>
指定链接控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构。

*pparentwnd*<br/>
指定链接控件的父窗口。 值不得为 NULL。

*nID*<br/>
指定链接控件的 ID。

### <a name="return-value"></a>返回值

如果初始化成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

分两步`CLinkCtrl`构造对象。 首先调用构造函数，然后调用`Create`，这将创建链接控件并将其附加到`CLinkCtrl`对象。 如果要将扩展窗口样式与控件一起使用，请致电[CLinkCtrl：：createEx](#createex)而不是`Create`。

方法的第`Create`二种形式被弃用。 使用指定*lpszLinkMarkup*参数的第一个窗体。

### <a name="example"></a>示例

以下代码示例定义用于访问两个链接控件的`m_Link1`两`m_Link2`个变量，名为 和 ，用于访问两个链接控件。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>示例

以下代码示例基于另一个链接控件的位置创建一个链接控件。 应用程序启动时，资源加载程序将创建第一个链接控件。 当应用程序进入 OnInitDialog 方法时，您将创建相对于第一个链接控件的位置的第二个链接控件。 然后调整第二个链接控件的大小，以适合它显示的文本。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

## <a name="clinkctrlcreateex"></a><a name="createex"></a>链接：：创建Ex

创建具有扩展样式的链接控件并将其附加到`CLinkCtrl`对象。

```
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```

### <a name="parameters"></a>参数

*lpszLinkMarkup*<br/>
指向包含要显示的标记的向上文本的零端接字符串的指针。 有关详细信息，请参阅["SysLink 控件概述](/windows/win32/Controls/syslink-overview)"主题中的"标记和链接访问"部分。

*dwExStyle*<br/>
指定链接控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[创建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定链接控件的样式。 应用控件样式的任意组合。 有关详细信息，请参阅 Windows SDK 中的[通用控件样式](/windows/win32/Controls/common-control-styles)。

*矩形*<br/>
指定链接控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构。

*pparentwnd*<br/>
指定链接控件的父窗口。 值不得为 NULL。

*nID*<br/>
指定链接控件的 ID。

### <a name="return-value"></a>返回值

如果初始化成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

使用`CreateEx`而不是["创建](#create)"来应用扩展的 Windows 样式常量。

方法的第`CreateEx`二种形式被弃用。 使用指定*lpszLinkMarkup*参数的第一个窗体。

## <a name="clinkctrlgetidealheight"></a><a name="getidealheight"></a>链接：：获取理想高度

检索链路控件的理想高度。

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>返回值

控件的理想高度（以像素为单位）。

### <a name="remarks"></a>备注

此成员函数实现 win32 消息[的行为LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight)，如 Windows SDK 中所述。

## <a name="clinkctrlgetidealsize"></a><a name="getidealsize"></a>链接：：获取理想尺寸

根据链接的指定宽度计算当前链接控件的链接文本的首选高度。

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*cxMaxWidth*|[在]链接的最大宽度（以像素为单位）。|
|[出]\* *pSize*|指向 Windows [SIZE](/windows/win32/api/windef/ns-windef-size)结构的指针。 当此方法返回时，`SIZE`结构的*cy*成员包含*cxMaxWidth*指定的链接文本宽度的理想链接文本高度。 结构的*cx*成员包含实际需要的链接文本宽度。|

### <a name="return-value"></a>返回值

链接文本的首选高度（以像素为单位）。 返回值与`SIZE`结构的*cy*成员的值相同。

### <a name="remarks"></a>备注

有关方法的示例，`GetIdealSize`请参阅[CLinkCtrl：：：：创建](#create)中的示例。

此方法发送[LM_GETIDEALSIZE](/windows/win32/Controls/lm-getidealsize)消息，这在 Windows SDK 中介绍。

## <a name="clinkctrlgetitem"></a><a name="getitem"></a>链接：获取项目

检索链接控件项的状态和属性。

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)结构的指针，用于接收项信息。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[LM_GETITEM](/windows/win32/Controls/lm-getitem)的行为，如 Windows SDK 中所述。

## <a name="clinkctrlgetitemid"></a><a name="getitemid"></a>链接：：获取项目ID

检索链接控件项的 ID。

```
BOOL GetItemID(
    int iLink,
    CString& strID) const;

BOOL GetItemID(
    int iLink,
    LPWSTR szID,
    UINT cchID) const;
```

### <a name="parameters"></a>参数

*i链接*<br/>
链接控件项的索引。

*斯特里德*<br/>
包含指定项 ID 的[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)对象。

*szID*<br/>
包含指定项 ID 的 null 终止字符串。

*cchID*<br/>
*szID*缓冲区的大小（以字符表示）。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

> [!NOTE]
> 如果*szID 或 strID*的缓冲区小于 MAX_LINKID_TEXT，则此功能也会返回 FALSE。

### <a name="remarks"></a>备注

检索特定链接控件项的 ID。 有关详细信息，请参阅 Windows SDK 中[LM_GETITEM](/windows/win32/Controls/lm-getitem)的 Win32 消息。

## <a name="clinkctrlgetitemstate"></a><a name="getitemstate"></a>链接：：获取项目状态

检索链接控制项的状态。

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>参数

*i链接*<br/>
链接控件项的索引。

*pnState*<br/>
指定状态项的值。

*状态掩码*<br/>
描述要获取的状态项的标志的组合。 有关值列表，请参阅[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)结构中`state`成员的说明。 允许的项目与 中允许的项目`state`相同。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

检索特定链接控件项的指定状态项的值。 有关详细信息，请参阅 Windows SDK 中[LM_GETITEM](/windows/win32/Controls/lm-getitem)的 Win32 消息。

## <a name="clinkctrlgetitemurl"></a><a name="getitemurl"></a>链接：：获取项目Url

检索链接控制项表示的 URL。

```
BOOL GetItemUrl(
    int iLink,
    CString& strUrl) const;

BOOL GetItemUrl(
    int iLink,
    LPWSTR szUrl,
    UINT cchUrl) const;
```

### <a name="parameters"></a>参数

*i链接*<br/>
链接控件项的索引。

*斯特鲁*<br/>
包含指定项表示的 URL 的[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)对象

*szUrl*<br/>
包含指定项表示的 URL 的 null 端接字符串

*cchUrl*<br/>
*szURL*缓冲区的大小（以字符表示）。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

> [!NOTE]
> 如果*szUrl 或 strUrl*的缓冲区小于 MAX_LINKID_TEXT，则此功能也会返回 FALSE。

### <a name="remarks"></a>备注

检索由指定的链接控制项表示的 URL。 有关详细信息，请参阅 Windows SDK 中[LM_GETITEM](/windows/win32/Controls/lm-getitem)的 Win32 消息。

## <a name="clinkctrlhittest"></a><a name="hittest"></a>链接：：HitTest

确定用户是否单击指定的链接。

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>参数

*菲蒂*<br/>
指向包含用户`LHITTESTINFO`单击的链接的任何信息的结构的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[LM_HITTEST](/windows/win32/Controls/lm-hittest)的行为，如 Windows SDK 中所述。

## <a name="clinkctrlsetitem"></a><a name="setitem"></a>链接：设置项目

设置链接控件项的状态和属性。

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)结构的指针，其中包含要设置的信息。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为LM_SETITEM](/windows/win32/Controls/lm-setitem)，如 Windows SDK 中所述。

## <a name="clinkctrlsetitemid"></a><a name="setitemid"></a>链接：：设置项目ID

检索链接控件项的 ID。

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>参数

*i链接*<br/>
链接控件项的索引。

*szID*<br/>
包含指定项 ID 的 null 终止字符串。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

设置特定链接控件项的 ID。 有关详细信息，请参阅 Windows SDK 中的 Win32 消息[LM_SETITEM。](/windows/win32/Controls/lm-setitem)

## <a name="clinkctrlsetitemstate"></a><a name="setitemstate"></a>链接：：设置项目状态

检索链接控制项的状态。

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>参数

*i链接*<br/>
链接控件项的索引。

*pnState*<br/>
正在设置的指定状态项的值。

*状态掩码*<br/>
描述要设置的状态项的标志的组合。 有关值列表，请参阅[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)结构中`state`成员的说明。 允许的项目与 中允许的项目`state`相同。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

设置特定链接控件项的指定状态项的值。 有关详细信息，请参阅 Windows SDK 中的 Win32 消息[LM_SETITEM。](/windows/win32/Controls/lm-setitem)

## <a name="clinkctrlsetitemurl"></a><a name="setitemurl"></a>链接：：设置项目Url

设置由链接控件项表示的 URL。

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>参数

*i链接*<br/>
链接控件项的索引。

*szUrl*<br/>
包含指定项表示的 URL 的 null 端接字符串

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

设置由指定的链接控制项表示的 URL。 有关详细信息，请参阅 Windows SDK 中的 Win32 消息[LM_SETITEM。](/windows/win32/Controls/lm-setitem)

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)
