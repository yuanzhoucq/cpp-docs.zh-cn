---
title: CLinkCtrl 类
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
ms.openlocfilehash: 37d9e624c40f0d6aa7f3d3fa1ed3d97ffa478ee7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505700"
---
# <a name="clinkctrl-class"></a>CLinkCtrl 类

提供 Windows 公共 SysLink 控件的功能。

## <a name="syntax"></a>语法

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|构造 `CLinkCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CLinkCtrl::Create](#create)|创建一个链接控件, 并将其附加`CLinkCtrl`到对象。|
|[CLinkCtrl::CreateEx](#createex)|创建具有扩展样式的链接控件, 并将其附加`CLinkCtrl`到对象。|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|检索链接控件的理想高度。|
|[CLinkCtrl::GetIdealSize](#getidealsize)|根据指定的链接宽度, 计算当前链接控件的链接文本的首选高度。|
|[CLinkCtrl::GetItem](#getitem)|检索链接控件项的状态和特性。|
|[CLinkCtrl::GetItemID](#getitemid)|检索链接控件项的 ID。|
|[CLinkCtrl::GetItemState](#getitemstate)|检索链接控件项的状态。|
|[CLinkCtrl::GetItemUrl](#getitemurl)|检索链接控件项表示的 URL。|
|[CLinkCtrl::HitTest](#hittest)|确定用户是否单击了指定的链接。|
|[CLinkCtrl::SetItem](#setitem)|设置链接控件项的状态和属性。|
|[CLinkCtrl::SetItemID](#setitemid)|设置链接控件项的 ID。|
|[CLinkCtrl::SetItemState](#setitemstate)|设置链接控件项的状态。|
|[CLinkCtrl::SetItemUrl](#setitemurl)|设置由链接控件项表示的 URL。|

## <a name="remarks"></a>备注

使用 "链接控件", 可以方便地在窗口中嵌入超文本链接。 实际控件是一个窗口, 它在用户单击嵌入的链接时呈现标记的文本并启动相应的应用程序。 一个控件中支持多个链接, 可通过从零开始的索引进行访问。

此控件 (因而`CLinkCtrl`类) 仅适用于在 Windows XP 和更高版本下运行的程序。

有关详细信息, 请参阅 Windows SDK 中的[SysLink 控件](/windows/win32/Controls/syslink-overview)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="clinkctrl"></a>CLinkCtrl:: CLinkCtrl

构造 `CLinkCtrl` 对象。

```
CLinkCtrl();
```

##  <a name="create"></a>CLinkCtrl:: Create

创建一个链接控件, 并将其附加`CLinkCtrl`到对象。

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
指向以零结尾的字符串的指针, 该字符串包含要显示的标记的文本。 有关详细信息, 请参阅[SysLink 控件概述](/windows/win32/Controls/syslink-overview)中的 "标记和链接访问" 一节。

*dwStyle*<br/>
指定链接控件的样式。 应用任何控件样式组合。 有关详细信息, 请参阅`Windows SDK`中的[常见控件样式](/windows/win32/Controls/common-control-styles)。

*rect*<br/>
指定链接控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构。

*pParentWnd*<br/>
指定链接控件的父窗口。 它不能为 NULL。

*nID*<br/>
指定链接控件的 ID。

### <a name="return-value"></a>返回值

如果初始化成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

可以通过`CLinkCtrl`两个步骤构造对象。 首先, 调用构造函数, 然后调用`Create`, 它将创建链接控件并将其附加`CLinkCtrl`到对象。 如果要在控件中使用扩展的 windows 样式, 请调用[CLinkCtrl:: CreateEx](#createex)而不`Create`是。

不推荐使用该`Create`方法的第二种形式。 使用指定*lpszLinkMarkup*参数的第一个窗体。

### <a name="example"></a>示例

下面的代码示例定义了两个名`m_Link1`为`m_Link2`和的变量, 用于访问两个链接控件。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>示例

下面的代码示例基于另一个链接控件的位置创建一个链接控件。 当应用程序启动时, 资源加载程序会创建第一个链接控件。 当应用程序进入 OnInitDialog 方法时, 可以创建相对于第一个链接控件位置的第二个链接控件。 然后, 将第二个链接控件调整为适合它显示的文本。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

##  <a name="createex"></a>CLinkCtrl:: CreateEx

创建具有扩展样式的链接控件, 并将其附加`CLinkCtrl`到对象。

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
指向以零结尾的字符串的指针, 该字符串包含要显示的标记的文本。 有关详细信息, 请参阅[SysLink 控件概述](/windows/win32/Controls/syslink-overview)中的 "标记和链接访问" 一节。

*dwExStyle*<br/>
指定链接控件的扩展样式。 有关扩展 Windows 样式的列表, 请参阅 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定链接控件的样式。 应用任何控件样式组合。 有关详细信息, 请参阅 Windows SDK 中的[常见控件样式](/windows/win32/Controls/common-control-styles)。

*rect*<br/>
指定链接控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构。

*pParentWnd*<br/>
指定链接控件的父窗口。 它不能为 NULL。

*nID*<br/>
指定链接控件的 ID。

### <a name="return-value"></a>返回值

如果初始化成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

使用`CreateEx`而不是[Create](#create)来应用扩展的 Windows 样式常量。

不推荐使用该`CreateEx`方法的第二种形式。 使用指定*lpszLinkMarkup*参数的第一个窗体。

##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight

检索链接控件的理想高度。

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>返回值

控件的理想高度 (以像素为单位)。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight)的行为, 如 Windows SDK 中所述。

##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize

根据指定的链接宽度, 计算当前链接控件的链接文本的首选高度。

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*cxMaxWidth*|中链接的最大宽度 (以像素为单位)。|
|弄\* *pSize*|指向 Windows[大小](/windows/win32/api/windef/ns-windef-size)结构的指针。 此方法返回时, `SIZE`结构的*cy*成员将包含*cxMaxWidth*指定的链接文本宽度的理想链接文本高度。 结构的*cx*成员包含实际所需的链接文本宽度。|

### <a name="return-value"></a>返回值

链接文本的首选高度 (以像素为单位)。 返回值与`SIZE`结构的*cy*成员的值相同。

### <a name="remarks"></a>备注

有关`GetIdealSize`方法的示例, 请参见[CLinkCtrl:: Create](#create)中的示例。

此方法发送[LM_GETIDEALSIZE](/windows/win32/Controls/lm-getidealsize)消息, 如 Windows SDK 中所述。

##  <a name="getitem"></a>CLinkCtrl:: GetItem

检索链接控件项的状态和特性。

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向用于接收项信息的[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)结构的指针。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[LM_GETITEM](/windows/win32/Controls/lm-getitem)的行为, 如 Windows SDK 中所述。

##  <a name="getitemid"></a>CLinkCtrl:: GetItemID

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

*iLink*<br/>
链接控件项的索引。

*strID*<br/>
一个包含指定项的 ID 的[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)对象。

*szID*<br/>
一个以 null 结尾的字符串, 其中包含指定项的 ID。

*cchID*<br/>
*SzID*缓冲区的大小 (以字符为限)。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

> [!NOTE]
>  如果*szID 或 strID*的缓冲区小于 MAX_LINKID_TEXT, 此函数也会返回 FALSE。

### <a name="remarks"></a>备注

检索特定链接控件项的 ID。 有关详细信息, 请参阅 Windows SDK 中的 Win32 消息[LM_GETITEM](/windows/win32/Controls/lm-getitem) 。

##  <a name="getitemstate"></a>CLinkCtrl:: GetItemState

检索链接控件项的状态。

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>参数

*iLink*<br/>
链接控件项的索引。

*pnState*<br/>
指定状态项的值。

*stateMask*<br/>
描述要获取哪个状态项的标志组合。 有关值的列表, 请参阅`state` [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)结构中成员的说明。 允许的项与中`state`允许的项相同。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

检索特定链接控件项的指定状态项的值。 有关详细信息, 请参阅 Windows SDK 中的 Win32 消息[LM_GETITEM](/windows/win32/Controls/lm-getitem) 。

##  <a name="getitemurl"></a>CLinkCtrl:: GetItemUrl

检索链接控件项表示的 URL。

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

*iLink*<br/>
链接控件项的索引。

*strUrl*<br/>
一个[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)对象, 该对象包含由指定项表示的 URL

*szUrl*<br/>
一个以 null 结尾的字符串, 其中包含由指定项表示的 URL

*cchUrl*<br/>
*SzURL*缓冲区的大小 (以字符为限)。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

> [!NOTE]
>  如果*szUrl 或 strUrl*的缓冲区小于 MAX_LINKID_TEXT, 此函数也会返回 FALSE。

### <a name="remarks"></a>备注

检索由指定的链接控件项表示的 URL。 有关详细信息, 请参阅 Windows SDK 中的 Win32 消息[LM_GETITEM](/windows/win32/Controls/lm-getitem) 。

##  <a name="hittest"></a>CLinkCtrl:: System.windows.media.visualtreehelper.hittest

确定用户是否单击了指定的链接。

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>参数

*phti*<br/>
指向一个结构`LHITTESTINFO`的指针, 该结构包含有关用户所单击的链接的任何信息。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[LM_HITTEST](/windows/win32/Controls/lm-hittest)的行为, 如 Windows SDK 中所述。

##  <a name="setitem"></a>CLinkCtrl:: SetItem

设置链接控件项的状态和属性。

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向[LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)结构的指针, 该结构包含要设置的信息。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[LM_SETITEM](/windows/win32/Controls/lm-setitem)的行为, 如 Windows SDK 中所述。

##  <a name="setitemid"></a>CLinkCtrl:: SetItemID

检索链接控件项的 ID。

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>参数

*iLink*<br/>
链接控件项的索引。

*szID*<br/>
一个以 null 结尾的字符串, 其中包含指定项的 ID。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

设置特定链接控件项的 ID。 有关详细信息, 请参阅 Windows SDK 中的 Win32 消息[LM_SETITEM](/windows/win32/Controls/lm-setitem) 。

##  <a name="setitemstate"></a>CLinkCtrl:: SetItemState

检索链接控件项的状态。

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>参数

*iLink*<br/>
链接控件项的索引。

*pnState*<br/>
要设置的指定状态项的值。

*stateMask*<br/>
描述要设置的状态项的标志的组合。 有关值的列表, 请参阅`state` [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem)结构中成员的说明。 允许的项与中`state`允许的项相同。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

设置特定链接控件项的指定状态项的值。 有关详细信息, 请参阅 Windows SDK 中的 Win32 消息[LM_SETITEM](/windows/win32/Controls/lm-setitem) 。

##  <a name="setitemurl"></a>CLinkCtrl:: SetItemUrl

设置由链接控件项表示的 URL。

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>参数

*iLink*<br/>
链接控件项的索引。

*szUrl*<br/>
一个以 null 结尾的字符串, 其中包含由指定项表示的 URL

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

### <a name="remarks"></a>备注

设置由指定的链接控件项表示的 URL。 有关详细信息, 请参阅 Windows SDK 中的 Win32 消息[LM_SETITEM](/windows/win32/Controls/lm-setitem) 。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)
