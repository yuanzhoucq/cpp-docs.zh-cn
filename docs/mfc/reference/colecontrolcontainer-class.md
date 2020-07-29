---
title: COleControlContainer 类
ms.date: 11/04/2016
f1_keywords:
- COleControlContainer
- AFXOCC/COleControlContainer
- AFXOCC/COleControlContainer::COleControlContainer
- AFXOCC/COleControlContainer::AttachControlSite
- AFXOCC/COleControlContainer::BroadcastAmbientPropertyChange
- AFXOCC/COleControlContainer::CheckDlgButton
- AFXOCC/COleControlContainer::CheckRadioButton
- AFXOCC/COleControlContainer::CreateControl
- AFXOCC/COleControlContainer::CreateOleFont
- AFXOCC/COleControlContainer::FindItem
- AFXOCC/COleControlContainer::FreezeAllEvents
- AFXOCC/COleControlContainer::GetAmbientProp
- AFXOCC/COleControlContainer::GetDlgItem
- AFXOCC/COleControlContainer::GetDlgItemInt
- AFXOCC/COleControlContainer::GetDlgItemText
- AFXOCC/COleControlContainer::HandleSetFocus
- AFXOCC/COleControlContainer::HandleWindowlessMessage
- AFXOCC/COleControlContainer::IsDlgButtonChecked
- AFXOCC/COleControlContainer::OnPaint
- AFXOCC/COleControlContainer::OnUIActivate
- AFXOCC/COleControlContainer::OnUIDeactivate
- AFXOCC/COleControlContainer::ScrollChildren
- AFXOCC/COleControlContainer::SendDlgItemMessage
- AFXOCC/COleControlContainer::SetDlgItemInt
- AFXOCC/COleControlContainer::SetDlgItemText
- AFXOCC/COleControlContainer::m_crBack
- AFXOCC/COleControlContainer::m_crFore
- AFXOCC/COleControlContainer::m_listSitesOrWnds
- AFXOCC/COleControlContainer::m_nWindowlessControls
- AFXOCC/COleControlContainer::m_pOleFont
- AFXOCC/COleControlContainer::m_pSiteCapture
- AFXOCC/COleControlContainer::m_pSiteFocus
- AFXOCC/COleControlContainer::m_pSiteUIActive
- AFXOCC/COleControlContainer::m_pWnd
- AFXOCC/COleControlContainer::m_siteMap
helpviewer_keywords:
- COleControlContainer [MFC], COleControlContainer
- COleControlContainer [MFC], AttachControlSite
- COleControlContainer [MFC], BroadcastAmbientPropertyChange
- COleControlContainer [MFC], CheckDlgButton
- COleControlContainer [MFC], CheckRadioButton
- COleControlContainer [MFC], CreateControl
- COleControlContainer [MFC], CreateOleFont
- COleControlContainer [MFC], FindItem
- COleControlContainer [MFC], FreezeAllEvents
- COleControlContainer [MFC], GetAmbientProp
- COleControlContainer [MFC], GetDlgItem
- COleControlContainer [MFC], GetDlgItemInt
- COleControlContainer [MFC], GetDlgItemText
- COleControlContainer [MFC], HandleSetFocus
- COleControlContainer [MFC], HandleWindowlessMessage
- COleControlContainer [MFC], IsDlgButtonChecked
- COleControlContainer [MFC], OnPaint
- COleControlContainer [MFC], OnUIActivate
- COleControlContainer [MFC], OnUIDeactivate
- COleControlContainer [MFC], ScrollChildren
- COleControlContainer [MFC], SendDlgItemMessage
- COleControlContainer [MFC], SetDlgItemInt
- COleControlContainer [MFC], SetDlgItemText
- COleControlContainer [MFC], m_crBack
- COleControlContainer [MFC], m_crFore
- COleControlContainer [MFC], m_listSitesOrWnds
- COleControlContainer [MFC], m_nWindowlessControls
- COleControlContainer [MFC], m_pOleFont
- COleControlContainer [MFC], m_pSiteCapture
- COleControlContainer [MFC], m_pSiteFocus
- COleControlContainer [MFC], m_pSiteUIActive
- COleControlContainer [MFC], m_pWnd
- COleControlContainer [MFC], m_siteMap
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
ms.openlocfilehash: 2c2c97090fc8255c06e1678a377fe2dcc968ffd2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214108"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer 类

充当 ActiveX 控件的控件容器。

## <a name="syntax"></a>语法

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|构造 `COleControlContainer` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|创建由容器承载的控制站点。|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|通知所有宿主控件环境属性已更改。|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|修改指定的按钮控件。|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|选择组的指定单选按钮。|
|[COleControlContainer：： CreateControl](#createcontrol)|创建承载的 ActiveX 控件。|
|[COleControlContainer::CreateOleFont](#createolefont)|创建 OLE 字体。|
|[COleControlContainer::FindItem](#finditem)|返回指定控件的自定义网站。|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|确定控制站点是否正在接受事件。|
|[COleControlContainer::GetAmbientProp](#getambientprop)|检索指定的环境属性。|
|[COleControlContainer::GetDlgItem](#getdlgitem)|检索指定的对话框控件。|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|检索指定对话框控件的值。|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|检索指定对话框控件的标题。|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|确定容器是否处理 WM_SETFOCUS 消息。|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|处理发送到无窗口控件的消息。|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|确定指定按钮的状态。|
|[COleControlContainer：： OnPaint](#onpaint)|调用以重绘部分容器。|
|[COleControlContainer::OnUIActivate](#onuiactivate)|当控件即将就地激活时调用。|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|当控件即将停用时调用。|
|[COleControlContainer::ScrollChildren](#scrollchildren)|当从子窗口接收到滚动消息时由框架调用。|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|将消息发送到指定控件。|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|设置指定控件的值。|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|设置指定控件的文本。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleControlContainer：： m_crBack](#m_crback)|容器的背景色。|
|[COleControlContainer：： m_crFore](#m_crfore)|容器的前景色。|
|[COleControlContainer：： m_listSitesOrWnds](#m_listsitesorwnds)|支持的控制站点的列表。|
|[COleControlContainer：： m_nWindowlessControls](#m_nwindowlesscontrols)|承载的无窗口控件数。|
|[COleControlContainer：： m_pOleFont](#m_polefont)|指向自定义控件网站的 OLE 字体的指针。|
|[COleControlContainer：： m_pSiteCapture](#m_psitecapture)|指向捕获控制站点的指针。|
|[COleControlContainer：： m_pSiteFocus](#m_psitefocus)|指向当前具有输入焦点的控件的指针。|
|[COleControlContainer：： m_pSiteUIActive](#m_psiteuiactive)|一个指针，指向当前就地激活的控件。|
|[COleControlContainer：： m_pWnd](#m_pwnd)|指向实现控件容器的窗口的指针。|
|[COleControlContainer：： m_siteMap](#m_sitemap)|站点地图。|

## <a name="remarks"></a>备注

这是通过提供对一个或多个 ActiveX 控件站点（由实现）的支持来完成的 `COleControlSite` 。 `COleControlContainer`完全实现[IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe)和[IOleContainer](/windows/win32/api/oleidl/nn-oleidl-iolecontainer)接口，允许包含的 ActiveX 控件将其限定为就地项。

通常，此类与和结合使用 `COccManager` `COleControlSite` 来实现自定义 ActiveX 控件容器，其中包含一个或多个 ActiveX 控件的自定义网站。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>要求

**标头：** afxocc

## <a name="colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite

由框架调用，用于创建和附加控件站点。

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
一个指向 `CWnd` 对象的指针。

*nIDC*<br/>
要附加的控件的 ID。

### <a name="remarks"></a>备注

如果要自定义此过程，请重写此函数。

> [!NOTE]
> 如果静态链接到 MFC 库，请使用此函数的第一种形式。 如果您动态链接到 MFC 库，请使用第二种形式。

## <a name="colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange

通知所有宿主控件环境属性已更改。

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>参数

*dispid*<br/>
要更改的环境属性的调度 ID。

### <a name="remarks"></a>备注

当环境属性的值发生更改时，框架会调用此函数。 重写此函数以自定义此行为。

## <a name="colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton

修改按钮的当前状态。

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>参数

*nIDButton*<br/>
要修改的按钮的 ID。

*n*<br/>
指定按钮的状态。 可以是以下值之一：

- BST_CHECKED 将按钮状态设置为 "已选中"。

- BST_INDETERMINATE 将按钮状态设置为灰显，表示状态不确定。 仅当按钮具有 BS_3STATE 或 BS_AUTO3STATE 样式时才使用此值。

- BST_UNCHECKED 将按钮状态设置为 "已清除"。

## <a name="colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton

选择组中的指定单选按钮，并清除组中剩余的按钮。

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>参数

*nIDFirstButton*<br/>
指定组中第一个单选按钮的标识符。

*nIDLastButton*<br/>
指定组中最后一个单选按钮的标识符。

*nIDCheckButton*<br/>
指定要检查的单选按钮的标识符。

## <a name="colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer

构造 `COleControlContainer` 对象。

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向控件容器的父窗口的指针。

### <a name="remarks"></a>备注

成功创建对象后，添加一个自定义控件站点，同时调用 `AttachControlSite` 。

## <a name="colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a>COleControlContainer：： CreateControl

创建由指定的对象承载的 ActiveX 控件 `COleControlSite` 。

```
BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);

BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);
```

### <a name="parameters"></a>参数

*pWndCtrl*<br/>
指向表示控件的窗口对象的指针。

*clsid*<br/>
控件的唯一类 ID。

*lpszWindowName*<br/>
指向要在控件中显示的文本的指针。 设置控件的标题或文本属性的值（如果有）。 如果为 NULL，则不更改控件的 "标题" 或 "文本" 属性。

*dwStyle*<br/>
窗口样式。 可用样式在 "**备注**" 部分下列出。

*rect*<br/>
指定控件的大小和位置。 它可以是 `CRect` 对象或 `RECT` 结构。

*nID*<br/>
指定控件的子窗口 ID。

*pPersist*<br/>
指向的指针，该指针 `CFile` 包含控件的持久状态。 默认值为 NULL，指示控件将初始化自身，而不从任何持久性存储还原其状态。 如果不为 NULL，则它应为指向 `CFile` 派生对象的指针，该对象包含控件的持久性数据（以流或存储的形式）。 此数据可能已在以前的客户端激活中保存。 `CFile`可以包含其他数据，但必须在调用时将其读写指针设置为持久性数据的第一个字节 `CreateControl` 。

*bStorage*<br/>
指示*pPersist*中的数据是否应解释为 `IStorage` 或 `IStream` 数据。 如果*pPersist*中的数据是存储，则*bStorage*应为 TRUE。 如果*pPersist*中的数据是流，则*BSTORAGE*应为 FALSE。 默认值是 FALSE。

*bstrLicKey*<br/>
可选许可证密钥数据。 此数据仅用于创建需要运行时许可证密钥的控件。 如果控件支持授权，则必须提供许可证密钥才能成功创建控件。 默认值为 NULL。

*ppNewSite*<br/>
一个指针，指向将承载要创建的控件的现有控件站点。 默认值为 NULL，表示将自动创建新的控制站点并将其附加到新控件。

*ppt*<br/>
指向 `POINT` 结构的指针，该结构包含控件的左上角。 控件的大小由*psize*的值确定。 *Ppt*和*psize*值是指定控件的大小和位置的可选方法。

*psize*<br/>
指向 `SIZE` 结构的指针，该结构包含控件的大小。 左上角由*ppt*的值确定。 *Ppt*和*psize*值是指定控件的大小和位置的可选方法。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

仅支持部分 Windows *dwStyle*标志 `CreateControl` ：

- WS_VISIBLE 创建一个最初可见的窗口。 如果希望立即显示控件（如普通窗口），则为必需。

- WS_DISABLED 创建一个最初处于禁用状态的窗口。 禁用的窗口无法接收来自用户的输入。 如果控件具有 Enabled 属性，则可以设置。

- WS_BORDER 创建一个具有细线边框的窗口。 如果控件具有 BorderStyle 属性，则可以设置。

- WS_GROUP 指定一组控件的第一个控件。 用户可以使用方向键将键盘焦点从组中的一个控件更改为下一个控件。 在第一个控件属于同一组之后，用 WS_GROUP 样式定义的所有控件。 具有 WS_GROUP 样式的下一个控件将结束组并启动下一组。

- WS_TABSTOP 指定在用户按 TAB 键时可接收键盘焦点的控件。 按 TAB 键会将键盘焦点更改为 WS_TABSTOP 样式的下一个控件。

使用第二个重载创建默认大小的控件。

## <a name="colecontrolcontainercreateolefont"></a><a name="createolefont"></a>COleControlContainer::CreateOleFont

创建 OLE 字体。

```cpp
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
一个指针，指向控件容器使用的字体。

## <a name="colecontrolcontainerfinditem"></a><a name="finditem"></a>COleControlContainer::FindItem

查找承载指定项的自定义网站。

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>参数

*nID*<br/>
要查找的项的标识符。

### <a name="return-value"></a>返回值

指向指定项的自定义站点的指针。

## <a name="colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents

确定容器是否将忽略附加的控制站点的事件或接受这些事件。

```cpp
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>参数

*bFreeze*<br/>
如果要处理事件，则为非零值;否则为0。

### <a name="remarks"></a>备注

> [!NOTE]
> 如果控件容器请求，则不需要控件来停止激发事件。 它可以继续触发，但所有后续事件都将被控件容器忽略。

## <a name="colecontrolcontainergetambientprop"></a><a name="getambientprop"></a>COleControlContainer::GetAmbientProp

检索指定环境属性的值。

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>参数

*pSite*<br/>
指向要从中检索环境属性的控制站点的指针。

*dispid*<br/>
所需环境属性的调度 ID。

*pVarResult*<br/>
一个指针，指向环境属性的值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

## <a name="colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a>COleControlContainer::GetDlgItem

检索指向对话框或其他窗口中的指定控件或子窗口的指针。

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>参数

*nID*<br/>
要检索的对话项的标识符。

*phWnd*<br/>
一个指针，指向指定的对话框项的窗口对象的句柄。

### <a name="return-value"></a>返回值

指向对话框项窗口的指针。

## <a name="colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt

检索给定控件的翻译后的文本值。

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>参数

*nID*<br/>
控件的标识符。

*lpTrans*<br/>
一个指针，指向接收函数成功/失败值的布尔变量（TRUE 表示成功，FALSE 表示失败）。

*bSigned*<br/>
指定函数是否应检查开头的减号的文本，并在找到有符号整数值时返回该整数值。 如果*bSigned*参数为 TRUE，则指定要检索的值为有符号整数值，并将返回值强制转换为 **`int`** 类型。 若要获取扩展的错误信息，请调用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="return-value"></a>返回值

如果成功，则*lpTrans*指向的变量将设置为 TRUE，并且返回值为控件文本的已转换值。

如果函数失败，则*lpTrans*指向的变量将设置为 FALSE，并且返回值为零。 请注意，由于零是可能转换后的值，因此返回值0本身并不表示失败。

如果*lpTrans*为 NULL，则该函数不返回任何有关成功或失败的信息。

### <a name="remarks"></a>备注

函数通过去除文本开头的任何多余空格，然后转换十进制数字来转换检索到的文本。 函数在到达文本末尾或遇到非数字字符时停止转换。

如果翻译后的值大于 INT_MAX （对于有符号数字）或 UINT_MAX （对于无符号数字），则此函数将返回零。

## <a name="colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText

检索给定控件的文本。

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>参数

*nID*<br/>
控件的标识符。

*lpStr*<br/>
指向控件文本的指针。

*nMaxCount*<br/>
指定要复制到*lpStr*所指向的缓冲区中的字符串的最大长度（以字符为字符）。 如果字符串的长度超出了限制，则字符串将被截断。

### <a name="return-value"></a>返回值

如果函数成功，则返回值指定复制到缓冲区的字符数，不包括终止 null 字符。

如果函数失败，则返回值为零。 若要获取扩展的错误信息，请调用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus

确定容器是否处理 WM_SETFOCUS 消息。

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>返回值

如果容器处理 WM_SETFOCUS 消息，则为非零值;否则为零。

## <a name="colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage

处理无窗口控件的窗口消息。

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>参数

*message*<br/>
Windows 提供的窗口消息的标识符。

*wParam*<br/>
消息的参数;由 Windows 提供。 指定其他特定于消息的信息。 此参数的内容取决于*message*参数的值。

*lParam*<br/>
消息的参数;由 Windows 提供。 指定其他特定于消息的信息。 此参数的内容取决于*message*参数的值。

*plResult*<br/>
Windows 结果代码。 指定消息处理的结果，并取决于所发送的消息。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

重写此函数以自定义无窗口控制消息的处理。

## <a name="colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonChecked

确定指定按钮的状态。

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>参数

*nIDButton*<br/>
按钮控件的标识符。

### <a name="return-value"></a>返回值

从使用 BS_AUTOCHECKBOX、BS_AUTORADIOBUTTON、BS_AUTO3STATE、BS_CHECKBOX、BS_RADIOBUTTON 或 BS_3STATE 样式创建的按钮的返回值。 可以是以下值之一：

- 已选中 BST_CHECKED 按钮。

- BST_INDETERMINATE 按钮显示为灰色，表示状态不确定（仅当按钮具有 BS_3STATE 或 BS_AUTO3STATE 样式时才适用）。

- 已清除 BST_UNCHECKED 按钮。

### <a name="remarks"></a>备注

如果该按钮是三状态控件，则成员函数将确定它是灰显还是选中，或者两者都不是。

## <a name="colecontrolcontainerm_crback"></a><a name="m_crback"></a>COleControlContainer：： m_crBack

容器的背景色。

```
COLORREF m_crBack;
```

## <a name="colecontrolcontainerm_crfore"></a><a name="m_crfore"></a>COleControlContainer：： m_crFore

容器的前景色。

```
COLORREF m_crFore;
```

## <a name="colecontrolcontainerm_listsitesorwnds"></a><a name="m_listsitesorwnds"></a>COleControlContainer：： m_listSitesOrWnds

容器承载的控制站点的列表。

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

## <a name="colecontrolcontainerm_nwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a>COleControlContainer：： m_nWindowlessControls

控件容器承载的无窗口控件的数目。

```
int m_nWindowlessControls;
```

## <a name="colecontrolcontainerm_polefont"></a><a name="m_polefont"></a>COleControlContainer：： m_pOleFont

指向自定义控件网站的 OLE 字体的指针。

```
LPFONTDISP m_pOleFont;
```

## <a name="colecontrolcontainerm_psitecapture"></a><a name="m_psitecapture"></a>COleControlContainer：： m_pSiteCapture

指向捕获控制站点的指针。

```
COleControlSite* m_pSiteCapture;
```

## <a name="colecontrolcontainerm_psitefocus"></a><a name="m_psitefocus"></a>COleControlContainer：： m_pSiteFocus

指向当前具有输入焦点的控件站点的指针。

```
COleControlSite* m_pSiteFocus;
```

## <a name="colecontrolcontainerm_psiteuiactive"></a><a name="m_psiteuiactive"></a>COleControlContainer：： m_pSiteUIActive

指向就地激活的控件站点的指针。

```
COleControlSite* m_pSiteUIActive;
```

## <a name="colecontrolcontainerm_pwnd"></a><a name="m_pwnd"></a>COleControlContainer：： m_pWnd

指向与容器关联的窗口对象的指针。

```
CWnd* m_pWnd;
```

## <a name="colecontrolcontainerm_sitemap"></a><a name="m_sitemap"></a>COleControlContainer：： m_siteMap

站点地图。

```
CMapPtrToPtr m_siteMap;
```

## <a name="colecontrolcontaineronpaint"></a><a name="onpaint"></a>COleControlContainer：： OnPaint

由框架调用，用于处理 WM_PAINT 的请求。

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向容器使用的设备上下文的指针。

### <a name="return-value"></a>返回值

如果消息已处理，则为非零值;否则为零。

### <a name="remarks"></a>备注

重写此函数以自定义绘制过程。

## <a name="colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a>COleControlContainer::OnUIActivate

当由*pSite*指向的控制站点即将就地激活时，由框架调用。

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>参数

*pSite*<br/>
指向要就地激活的控件站点的指针。

### <a name="remarks"></a>备注

就地激活意味着容器的主菜单被替换为就地复合菜单。

## <a name="colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate

当由*pSite*指向的控制站点即将停用时，由框架调用。

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>参数

*pSite*<br/>
指向要停用的控件站点的指针。

### <a name="remarks"></a>备注

收到此通知后，容器应重新安装其用户界面并获得焦点。

## <a name="colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a>COleControlContainer::ScrollChildren

当从子窗口接收到滚动消息时由框架调用。

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>参数

*dx*<br/>
沿 x 轴滚动的量（以像素为单位）。

*dy*<br/>
沿 y 轴滚动的量（以像素为单位）。

## <a name="colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage

将消息发送到指定控件。

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*nID*<br/>
指定接收消息的控件的标识符。

*message*<br/>
指定要发送的消息。

*wParam*<br/>
指定其他特定于消息的信息。

*lParam*<br/>
指定其他特定于消息的信息。

## <a name="colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt

将对话框中控件的文本设置为指定整数值的字符串表示形式。

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>参数

*nID*<br/>
控件的标识符。

*N 值*<br/>
要显示的整数值。

*bSigned*<br/>
指定*n 值*参数是否为已签名或未签名。 如果此参数为 TRUE，则对*n 值*进行签名。 如果此参数为 TRUE 且*n 值*小于零，则在字符串中的第一个数字前面放置一个减号。 如果此参数为 FALSE，则*n 值*为无符号。

## <a name="colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a>COleControlContainer::SetDlgItemText

使用*lpszString*中包含的文本设置指定控件的文本。

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*nID*<br/>
控件的标识符。

*lpszString*<br/>
指向控件文本的指针。

## <a name="see-also"></a>另请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite 类](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager 类](../../mfc/reference/coccmanager-class.md)
