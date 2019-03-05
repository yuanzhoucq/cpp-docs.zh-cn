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
ms.openlocfilehash: 38f529f46623bc7095879b29fba09427626073ec
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260395"
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
|[CLinkCtrl::Create](#create)|创建链接控件，并将其附加到`CLinkCtrl`对象。|
|[CLinkCtrl::CreateEx](#createex)|创建一个链接控件具有扩展样式并将其附加到`CLinkCtrl`对象。|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|检索链接控件的理想高度。|
|[CLinkCtrl::GetIdealSize](#getidealsize)|计算当前的链接控件，具体取决于指定宽度的链接的链接文本的首选的高度。|
|[CLinkCtrl::GetItem](#getitem)|检索状态和属性的链接控件项。|
|[CLinkCtrl::GetItemID](#getitemid)|检索的链接控件项的 ID。|
|[CLinkCtrl::GetItemState](#getitemstate)|检索链接控件项的状态。|
|[CLinkCtrl::GetItemUrl](#getitemurl)|检索由链接控件项的 URL。|
|[CLinkCtrl::HitTest](#hittest)|确定用户是否单击指定的链接。|
|[CLinkCtrl::SetItem](#setitem)|设置的状态和属性的链接控件项。|
|[CLinkCtrl::SetItemID](#setitemid)|设置链接控件项的 ID。|
|[CLinkCtrl::SetItemState](#setitemstate)|设置链接控件项的状态。|
|[CLinkCtrl::SetItemUrl](#setitemurl)|设置由链接控件项的 URL。|

## <a name="remarks"></a>备注

"链接控制"提供了方便地在窗口中嵌入超文本链接。 实际控件是呈现标记向上文本，并在用户单击嵌入的链接时启动合适的应用程序的窗口。 多个链接一个控件内支持，并且可以通过从零开始的索引访问。

此控件 (并因此`CLinkCtrl`类) 仅供运行在 Windows XP 及更高版本的程序。

有关详细信息，请参阅[SysLink 控件](/windows/desktop/Controls/syslink-overview)Windows SDK 中。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="clinkctrl"></a>  CLinkCtrl::CLinkCtrl

构造 `CLinkCtrl` 对象。

```
CLinkCtrl();
```

##  <a name="create"></a>  CLinkCtrl::Create

创建链接控件，并将其附加到`CLinkCtrl`对象。

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
以零结尾的字符串，包含要显示的文本标记的指针。 有关详细信息，请参阅主题中的"标记和链接访问"一节[SysLink 控件概述](/windows/desktop/Controls/syslink-overview)。

*dwStyle*<br/>
指定链接控件的样式。 将应用控件样式的任意组合。 请参阅[常见控件样式](/windows/desktop/Controls/common-control-styles)中`Windows SDK`有关详细信息。

*rect*<br/>
指定链接控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/desktop/api/windef/ns-windef-tagrect)结构。

*pParentWnd*<br/>
指定链接控件的父窗口。 它不能为 NULL。

*nID*<br/>
指定链接控件的 id。

### <a name="return-value"></a>返回值

如果初始化成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

构造`CLinkCtrl`两个步骤中的对象。 首先，调用构造函数，然后调用`Create`，它创建的链接控件并将其附加到`CLinkCtrl`对象。 如果你想要在控件中使用扩展的 windows 样式，则调用[CLinkCtrl::CreateEx](#createex)而不是`Create`。

第二种形式的`Create`方法已弃用。 使用指定的第一个窗体*lpszLinkMarkup*参数。

### <a name="example"></a>示例

下面的代码示例定义两个变量，名为`m_Link1`和`m_Link2`，用于访问两个链接控件。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>示例

下面的代码示例创建一个基于另一个链接控件的位置的链接控件。 启动应用程序时，资源加载程序将创建第一个链接控件。 当你的应用程序进入 OnInitDialog 方法时，您将创建第二个链接控件相对于第一个链接控件的位置。 然后您调整大小以适合文本，它将显示第二个链接控件。

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

##  <a name="createex"></a>  CLinkCtrl::CreateEx

创建一个链接控件具有扩展样式并将其附加到`CLinkCtrl`对象。

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
以零结尾的字符串，包含要显示的文本标记的指针。 有关详细信息，请参阅主题中的"标记和链接访问"一节[SysLink 控件概述](/windows/desktop/Controls/syslink-overview)。

*dwExStyle*<br/>
指定链接控件的扩展的样式。 扩展 Windows 样式的列表，请参阅*dwExStyle*参数[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*dwStyle*<br/>
指定链接控件的样式。 将应用控件样式的任意组合。 有关详细信息，请参阅[常见控件样式](/windows/desktop/Controls/common-control-styles)Windows SDK 中。

*rect*<br/>
指定链接控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/desktop/api/windef/ns-windef-tagrect)结构。

*pParentWnd*<br/>
指定链接控件的父窗口。 它不能为 NULL。

*nID*<br/>
指定链接控件的 id。

### <a name="return-value"></a>返回值

如果初始化成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

使用`CreateEx`而不是[创建](#create)应用扩展的 Windows 样式常量。

第二种形式的`CreateEx`方法已弃用。 使用指定的第一个窗体*lpszLinkMarkup*参数。

##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight

检索链接控件的理想高度。

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>返回值

控件，以像素为单位的理想高度。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[LM_GETIDEALHEIGHT](/windows/desktop/Controls/lm-getidealheight)，如 Windows SDK 中所述。

##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize

计算当前的链接控件，具体取决于指定宽度的链接的链接文本的首选的高度。

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*cxMaxWidth*|[in]该链接，以像素为单位的最大宽度。|
|[out] \* *pSize*|指向 Windows[大小](/windows/desktop/api/windef/ns-windef-tagsize)结构。 此方法返回时， *cy*的成员`SIZE`结构包含由指定的链接文本宽度的理想之选链接文本高度*cxMaxWidth*。 *Cx*结构中的成员包含实际需要的链接文本宽度。|

### <a name="return-value"></a>返回值

链接文本，以像素为单位的首选的高度。 返回值是相同的值*cy*的成员`SIZE`结构。

### <a name="remarks"></a>备注

有关的示例`GetIdealSize`方法，请参阅中的示例[CLinkCtrl::Create](#create)。

此方法将发送[LM_GETIDEALSIZE](/windows/desktop/Controls/lm-getidealsize)消息，Windows SDK 中所述。

##  <a name="getitem"></a>  CLinkCtrl::GetItem

检索状态和属性的链接控件项。

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>参数

*pItem*<br/>
一个指向[LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem)结构，以接收项的信息。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[LM_GETITEM](/windows/desktop/Controls/lm-getitem)，如 Windows SDK 中所述。

##  <a name="getitemid"></a>  CLinkCtrl::GetItemID

检索的链接控件项的 ID。

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
一个[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含指定项的 ID。

*szID*<br/>
以 null 结尾的字符串，包含指定项的 ID。

*cchID*<br/>
以字符为单位的大小*szID*缓冲区。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

> [!NOTE]
>  此函数也返回 FALSE，如果的缓冲区*szID 或 strID*小于 MAX_LINKID_TEXT。

### <a name="remarks"></a>备注

检索特定链接控件项的 ID。 有关详细信息，请参阅 Win32 消息[LM_GETITEM](/windows/desktop/Controls/lm-getitem) Windows SDK 中。

##  <a name="getitemstate"></a>  CLinkCtrl::GetItemState

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
指定的状态项的值。

*stateMask*<br/>
描述要获取的状态项的标志的组合。 值的列表，请参阅的说明`state`中的成员[LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem)结构。 允许的项目是与允许在相同`state`。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

检索指定的状态项中的特定链接控件项的值。 有关详细信息，请参阅 Win32 消息[LM_GETITEM](/windows/desktop/Controls/lm-getitem) Windows SDK 中。

##  <a name="getitemurl"></a>  CLinkCtrl::GetItemUrl

检索由链接控件项的 URL。

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
一个[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含由指定的项的 URL

*szUrl*<br/>
包含由指定的项的 URL 的以 null 结尾的字符串

*cchUrl*<br/>
以字符为单位的大小*szURL*缓冲区。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

> [!NOTE]
>  此函数也返回 FALSE，如果的缓冲区*szUrl 或 strUrl*小于 MAX_LINKID_TEXT。

### <a name="remarks"></a>备注

检索由指定的链接控件项的 URL。 有关详细信息，请参阅 Win32 消息[LM_GETITEM](/windows/desktop/Controls/lm-getitem) Windows SDK 中。

##  <a name="hittest"></a>  CLinkCtrl::HitTest

确定用户是否单击指定的链接。

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>参数

*phti*<br/>
指向`LHITTESTINFO`结构，它包含有关链接用户所单击的任何信息。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[LM_HITTEST](/windows/desktop/Controls/lm-hittest)，如 Windows SDK 中所述。

##  <a name="setitem"></a>  CLinkCtrl::SetItem

设置的状态和属性的链接控件项。

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
一个指向[LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem)结构，它包含要设置的信息。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[LM_SETITEM](/windows/desktop/Controls/lm-setitem)，如 Windows SDK 中所述。

##  <a name="setitemid"></a>  CLinkCtrl::SetItemID

检索的链接控件项的 ID。

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>参数

*iLink*<br/>
链接控件项的索引。

*szID*<br/>
以 null 结尾的字符串，包含指定项的 ID。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

设置特定链接控件项的 ID。 有关详细信息，请参阅 Win32 消息[LM_SETITEM](/windows/desktop/Controls/lm-setitem) Windows SDK 中。

##  <a name="setitemstate"></a>  CLinkCtrl::SetItemState

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
设置指定的状态项的值。

*stateMask*<br/>
描述要设置状态项的标志的组合。 值的列表，请参阅的说明`state`中的成员[LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem)结构。 允许的项目是与允许在相同`state`。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

设置指定的状态的项的特定链接控件项的值。 有关详细信息，请参阅 Win32 消息[LM_SETITEM](/windows/desktop/Controls/lm-setitem) Windows SDK 中。

##  <a name="setitemurl"></a>  CLinkCtrl::SetItemUrl

设置由链接控件项的 URL。

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>参数

*iLink*<br/>
链接控件项的索引。

*szUrl*<br/>
包含由指定的项的 URL 的以 null 结尾的字符串

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

设置由指定的链接控件项的 URL。 有关详细信息，请参阅 Win32 消息[LM_SETITEM](/windows/desktop/Controls/lm-setitem) Windows SDK 中。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)
