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
ms.openlocfilehash: b1737b2ac114181a4245fff027b756ca30b64129
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366185"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer 类

充当 ActiveX 控件的控件容器。

## <a name="syntax"></a>语法

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle 控制容器：COle 控制容器](#colecontrolcontainer)|构造 `COleControlContainer` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle 控制容器：：附加控制站点](#attachcontrolsite)|创建由容器托管的控制站点。|
|[COle 控制容器：：广播环境属性更改](#broadcastambientpropertychange)|通知所有托管控件环境属性已更改。|
|[COle 控制容器：：检查DlgButton](#checkdlgbutton)|修改指定的按钮控件。|
|[COle 控制容器：：检查无线按钮](#checkradiobutton)|选择组的指定单选按钮。|
|[COle 控制容器：创建控制](#createcontrol)|创建托管的 ActiveX 控件。|
|[COle 控制容器：：创建 OleFont](#createolefont)|创建 OLE 字体。|
|[COle 控制容器：查找项目](#finditem)|返回指定控件的自定义站点。|
|[COle 控制容器：：冻结所有事件](#freezeallevents)|确定控制站点是否接受事件。|
|[COle 控制容器：获取环境](#getambientprop)|检索指定的环境属性。|
|[COle 控制容器：：GetDlgItem](#getdlgitem)|检索指定的对话框控件。|
|[COle 控制容器：：getDlgItemint](#getdlgitemint)|检索指定的对话框控件的值。|
|[COle 控制容器：：获取DlgItemtext](#getdlgitemtext)|检索指定对话框控件的标题。|
|[COle 控制容器：：手柄集焦点](#handlesetfocus)|确定容器是否处理WM_SETFOCUS消息。|
|[COle 控制容器：：无窗口处理消息](#handlewindowlessmessage)|处理发送到无窗口控件的消息。|
|[COle 控制容器：IsDlgButton 检查](#isdlgbuttonchecked)|确定指定按钮的状态。|
|[COle 控制容器：：上漆](#onpaint)|调用以重新绘制容器的一部分。|
|[COle 控制容器：：启用 UI](#onuiactivate)|当控件即将就地激活时调用。|
|[COle 控制容器：：启用](#onuideactivate)|当控件即将停用时调用。|
|[COle 控制容器：：滚动子级](#scrollchildren)|当从子窗口接收滚动消息时，由框架调用。|
|[COle 控制容器：：发送DlgItem消息](#senddlgitemmessage)|将消息发送到指定控件。|
|[COle 控制容器：：SetDlgItemint](#setdlgitemint)|设置指定控件的值。|
|[COle 控制容器：：设置DlgItemtext](#setdlgitemtext)|设置指定控件的文本。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COle 控制容器：：m_crBack](#m_crback)|容器的背景颜色。|
|[COle 控制容器：：m_crFore](#m_crfore)|容器的前景颜色。|
|[COle 控制容器：：m_listSitesOrWnds](#m_listsitesorwnds)|支持的控制站点的列表。|
|[COle 控制容器：：m_nWindowlessControls](#m_nwindowlesscontrols)|托管无窗口控件的数量。|
|[COle 控制容器：：m_pOleFont](#m_polefont)|指向自定义控件站点的 OLE 字体的指针。|
|[COle 控制容器：：m_pSiteCapture](#m_psitecapture)|指向捕获控制站点的指针。|
|[COle 控制容器：：m_pSiteFocus](#m_psitefocus)|指向当前具有输入焦点的控件的指针。|
|[COle 控制容器：：m_pSiteUIActive](#m_psiteuiactive)|指向当前就地激活的控件的指针。|
|[COle 控制容器：：m_pWnd](#m_pwnd)|指向实现控件容器的窗口的指针。|
|[COle 控制容器：：m_siteMap](#m_sitemap)|站点地图。|

## <a name="remarks"></a>备注

这是通过向一个或多个 ActiveX 控制站点提供支持（由 实现）`COleControlSite`来实现的。 `COleControlContainer`完全实现[IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe)和[IOleContainer 接口](/windows/win32/api/oleidl/nn-oleidl-iolecontainer)，允许包含的 ActiveX 控件满足其作为就地项目的资格。

通常，此类与`COccManager`和`COleControlSite`实现自定义 ActiveX 控件容器结合使用，并结合一个或多个 ActiveX 控件的自定义站点。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>要求

**标题：** afxocc.h

## <a name="colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a>COle 控制容器：：附加控制站点

由框架调用以创建和附加控件站点。

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
一个指向 `CWnd` 对象的指针。

*nIDC*<br/>
要附加的控件的 ID。

### <a name="remarks"></a>备注

如果要自定义此过程，请重写此函数。

> [!NOTE]
> 如果要以静态方式链接到 MFC 库，请使用此函数的第一种形式。 如果要动态链接到 MFC 库，请使用第二个窗体。

## <a name="colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a>COle 控制容器：：广播环境属性更改

通知所有托管控件环境属性已更改。

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>参数

*不一部分*<br/>
要更改的环境属性的调度 ID。

### <a name="remarks"></a>备注

当环境属性更改值时，框架将调用此功能。 重写此函数以自定义此行为。

## <a name="colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a>COle 控制容器：：检查DlgButton

修改按钮的当前状态。

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>参数

*nIDButton*<br/>
要修改的按钮的 ID。

*n检查*<br/>
指定按钮的状态。 可以是以下值之一：

- BST_CHECKED 将按钮状态设置为已选中状态。

- BST_INDETERMINATE 将按钮状态设为灰色，指示不确定状态。 仅当按钮具有BS_3STATE或BS_AUTO3STATE样式时，才使用此值。

- BST_UNCHECKED 将按钮状态设置清除。

## <a name="colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a>COle 控制容器：：检查无线按钮

在组中选择指定的单选按钮，并清除组中的剩余按钮。

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>参数

*nID第一按钮*<br/>
指定组中第一个单选按钮的标识符。

*nIDLastButton*<br/>
指定组中最后一个单选按钮的标识符。

*nID检查按钮*<br/>
指定要检查的单选按钮的标识符。

## <a name="colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a>COle 控制容器：COle 控制容器

构造 `COleControlContainer` 对象。

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向控件容器的父窗口的指针。

### <a name="remarks"></a>备注

成功创建对象后，添加一个自定义控件站点，该站点将调用`AttachControlSite`。

## <a name="colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a>COle 控制容器：创建控制

创建由指定`COleControlSite`对象托管的 ActiveX 控件。

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

*Clsid*<br/>
控件的唯一类 ID。

*lpsz窗口名称*<br/>
指向要在控件中显示的文本的指针。 设置控件的标题或文本属性的值（如果有）。 如果为 NULL，则控件的标题或文本属性不会更改。

*dwStyle*<br/>
窗口样式。 可用样式列在 **"备注"** 部分下。

*矩形*<br/>
指定控件的大小和位置。 它可以是`CRect`对象或`RECT`结构。

*nID*<br/>
指定控件的子窗口 ID。

*p 坚持*<br/>
指向`CFile`包含控件的持久状态的 指针。 默认值为 NULL，指示控件在不从任何持久存储还原其状态的情况下初始化自身。 如果不是 NULL，它应该是指向包含控件持久数据的`CFile`派生对象的指针，其形式是流或存储。 此数据可能已保存在客户端的上次激活中。 `CFile`可以包含其他数据，但必须将其读写指针设置为调用`CreateControl`时持久性数据的第一个字节。

*b 存储*<br/>
指示是否应将*pPersist*中的数据解释为`IStorage`或`IStream`数据。 如果*pPersist*中的数据是存储，*则 b 存储*应为 TRUE。 如果*pPersist*中的数据是流，*则 b 存储*应为 FALSE。 默认值是 FALSE。

*bstrLicKey*<br/>
可选的许可证密钥数据。 仅创建需要运行时许可证密钥的控件才需要此数据。 如果控件支持许可，则必须提供许可证密钥才能成功创建控件。 默认值为 NULL。

*ppNewSite*<br/>
指向将承载正在创建的控件的现有控件站点的指针。 默认值为 NULL，表示将自动创建新的控件站点并附加到新控件。

*Ppt*<br/>
指向包含控件左`POINT`上角的结构的指针。 控件的大小由*size*的值决定。 *ppt*和*size 值*是指定控件大小和位置的可选方法。

*psize*<br/>
指向包含控件大小的`SIZE`结构的指针。 左上角由*ppt*的值决定。 *ppt*和*size 值*是指定控件大小和位置的可选方法。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

只有 Windows *dwStyle*标志的子集受`CreateControl`支持：

- WS_VISIBLE 创建最初可见的窗口。 如果希望控件立即可见（如普通窗口），则需要。

- WS_DISABLED 创建最初禁用的窗口。 禁用的窗口无法接收用户输入。 如果控件具有"已启用"属性，则可以进行设置。

- WS_BORDER 创建具有细线边框的窗口。 如果控件具有 BorderStyle 属性，则可以进行设置。

- WS_GROUP 指定一组控件的第一个控件。 用户可以使用方向键将键盘焦点从组中的一个控件更改为下一个控件。 在第一个控件之后使用WS_GROUP样式定义的所有控件都属于同一组。 具有WS_GROUP样式的下一个控件将结束组并启动下一个组。

- WS_TABSTOP 指定可在用户按下 TAB 键时接收键盘焦点的控件。 按下 TAB 键会将键盘焦点更改为WS_TABSTOP样式的下一个控件。

使用第二个重载创建默认大小的控件。

## <a name="colecontrolcontainercreateolefont"></a><a name="createolefont"></a>COle 控制容器：：创建 OleFont

创建 OLE 字体。

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
指向控件容器使用的字体的指针。

## <a name="colecontrolcontainerfinditem"></a><a name="finditem"></a>COle 控制容器：查找项目

查找承载指定项的自定义站点。

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>参数

*nID*<br/>
要找到的项的标识符。

### <a name="return-value"></a>返回值

指向指定项的自定义站点的指针。

## <a name="colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a>COle 控制容器：：冻结所有事件

确定容器是忽略来自附加控制站点的事件还是接受这些事件。

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>参数

*bFreeze*<br/>
如果将处理事件，则非零;否则 0。

### <a name="remarks"></a>备注

> [!NOTE]
> 如果控制容器请求，则不需要该控件停止触发事件。 它可以继续触发，但控制容器将忽略所有后续事件。

## <a name="colecontrolcontainergetambientprop"></a><a name="getambientprop"></a>COle 控制容器：获取环境

检索指定环境属性的值。

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>参数

*pSite*<br/>
指向将从中检索环境属性的控制站点的指针。

*不一部分*<br/>
所需环境属性的调度 ID。

*pVarResult*<br/>
指向环境属性值的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

## <a name="colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a>COle 控制容器：：GetDlgItem

在对话框或其他窗口中检索指向指定控件或子窗口的指针。

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>参数

*nID*<br/>
要检索的对话框项的标识符。

*phwnd*<br/>
指向指定对话框项窗口对象的句柄的指针。

### <a name="return-value"></a>返回值

指向对话框项窗口的指针。

## <a name="colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a>COle 控制容器：：getDlgItemint

检索给定控件的翻译文本的值。

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
指向接收函数成功/失败值的布尔变量的指针（TRUE 表示成功，FALSE 表示失败）。

*b签名*<br/>
指定函数是否应在开头检查文本中的减号，并在找到已签名的整数值时返回该值。 如果*bSigned 参数*为 TRUE，则指定要检索的值是已签名的整数值，则将返回值转换为**int**类型。 要获取扩展的错误信息，请致电[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="return-value"></a>返回值

如果成功 *，lpTrans*指向的变量将设置为 TRUE，返回值是控件文本的已转换值。

如果函数失败 *，lpTrans*指向的变量将设置为 FALSE，返回值为零。 请注意，由于零是可能翻译的值，因此返回值为零本身并不表示失败。

如果*lpTrans*为 NULL，则函数不会返回任何有关成功或失败的信息。

### <a name="remarks"></a>备注

该函数通过剥离文本开头的任何额外空格，然后转换十进制数字来转换检索的文本。 当函数到达文本末尾或遇到非数字字符时，该函数将停止翻译。

如果转换的值大于INT_MAX（对于签名数字）或UINT_MAX（对于未签名的数字），则此功能返回零。

## <a name="colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a>COle 控制容器：：获取DlgItemtext

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
指定要复制到*lpStr*指向的缓冲区的字符串的最大长度（以字符表示） 如果字符串的长度超过限制，则该字符串将被截断。

### <a name="return-value"></a>返回值

如果函数成功，返回值将指定复制到缓冲区的字符数，不包括终止空字符。

如果函数失败，则返回值为零。 要获取扩展的错误信息，请致电[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a>COle 控制容器：：手柄集焦点

确定容器是否处理WM_SETFOCUS消息。

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>返回值

如果容器处理WM_SETFOCUS消息，则非零;否则为零。

## <a name="colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a>COle 控制容器：：无窗口处理消息

处理无窗口控件的窗口消息。

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>参数

*消息*<br/>
窗口消息的标识符，由 Windows 提供。

*wParam*<br/>
消息的参数;由 Windows 提供。 指定其他特定于消息的信息。 此参数的内容取决于*消息*参数的值。

*lParam*<br/>
消息的参数;由 Windows 提供。 指定其他特定于消息的信息。 此参数的内容取决于*消息*参数的值。

*plResult*<br/>
窗口结果代码。 指定消息处理的结果，并取决于发送的消息。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

重写此函数以自定义无窗口控制消息的处理。

## <a name="colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a>COle 控制容器：IsDlgButton 检查

确定指定按钮的状态。

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>参数

*nIDButton*<br/>
按钮控件的标识符。

### <a name="return-value"></a>返回值

返回值，来自使用BS_AUTOCHECKBOX、BS_AUTORADIOBUTTON、BS_AUTO3STATE、BS_CHECKBOX、BS_RADIOBUTTON 或BS_3STATE样式创建的按钮。 可以是以下值之一：

- BST_CHECKED按钮选中。

- BST_INDETERMINATE按钮为灰色，指示不确定状态（仅适用于按钮具有BS_3STATE或BS_AUTO3STATE样式时）。

- BST_UNCHECKED按钮清除。

### <a name="remarks"></a>备注

如果按钮是三状态控件，则成员函数将确定该按钮是变暗、选中还是两者均未调暗。

## <a name="colecontrolcontainerm_crback"></a><a name="m_crback"></a>COle 控制容器：：m_crBack

容器的背景颜色。

```
COLORREF m_crBack;
```

## <a name="colecontrolcontainerm_crfore"></a><a name="m_crfore"></a>COle 控制容器：：m_crFore

容器的前景颜色。

```
COLORREF m_crFore;
```

## <a name="colecontrolcontainerm_listsitesorwnds"></a><a name="m_listsitesorwnds"></a>COle 控制容器：：m_listSitesOrWnds

容器托管的控制站点的列表。

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

## <a name="colecontrolcontainerm_nwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a>COle 控制容器：：m_nWindowlessControls

控件容器托管的无窗口控件数。

```
int m_nWindowlessControls;
```

## <a name="colecontrolcontainerm_polefont"></a><a name="m_polefont"></a>COle 控制容器：：m_pOleFont

指向自定义控件站点的 OLE 字体的指针。

```
LPFONTDISP m_pOleFont;
```

## <a name="colecontrolcontainerm_psitecapture"></a><a name="m_psitecapture"></a>COle 控制容器：：m_pSiteCapture

指向捕获控制站点的指针。

```
COleControlSite* m_pSiteCapture;
```

## <a name="colecontrolcontainerm_psitefocus"></a><a name="m_psitefocus"></a>COle 控制容器：：m_pSiteFocus

指向当前具有输入焦点的控制站点的指针。

```
COleControlSite* m_pSiteFocus;
```

## <a name="colecontrolcontainerm_psiteuiactive"></a><a name="m_psiteuiactive"></a>COle 控制容器：：m_pSiteUIActive

指向就地激活的控制站点的指针。

```
COleControlSite* m_pSiteUIActive;
```

## <a name="colecontrolcontainerm_pwnd"></a><a name="m_pwnd"></a>COle 控制容器：：m_pWnd

指向与容器关联的窗口对象的指针。

```
CWnd* m_pWnd;
```

## <a name="colecontrolcontainerm_sitemap"></a><a name="m_sitemap"></a>COle 控制容器：：m_siteMap

站点地图。

```
CMapPtrToPtr m_siteMap;
```

## <a name="colecontrolcontaineronpaint"></a><a name="onpaint"></a>COle 控制容器：：上漆

由框架调用以处理WM_PAINT请求。

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向容器使用的设备上下文的指针。

### <a name="return-value"></a>返回值

处理消息时非零;否则为零。

### <a name="remarks"></a>备注

重写此函数以自定义绘制过程。

## <a name="colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a>COle 控制容器：：启用 UI

当控制站点（由*pSite*指向）即将就地激活时，由框架调用。

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>参数

*pSite*<br/>
指向即将就地激活的控制站点的指针。

### <a name="remarks"></a>备注

就地激活意味着容器的主菜单替换为就地复合菜单。

## <a name="colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a>COle 控制容器：：启用

当控制站点（*由 pSite*指向）即将停用时，由框架调用。

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>参数

*pSite*<br/>
指向即将停用的控制站点的指针。

### <a name="remarks"></a>备注

收到此通知时，容器应重新安装其用户界面并集中注意力。

## <a name="colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a>COle 控制容器：：滚动子级

当从子窗口接收滚动消息时，由框架调用。

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>参数

*Dx*<br/>
沿 x 轴滚动的数量（以像素为单位）。

*Dy*<br/>
沿 y 轴滚动的数量（以像素为单位）。

## <a name="colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a>COle 控制容器：：发送DlgItem消息

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

*消息*<br/>
指定要发送的消息。

*wParam*<br/>
指定其他特定于消息的信息。

*lParam*<br/>
指定其他特定于消息的信息。

## <a name="colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a>COle 控制容器：：SetDlgItemint

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

*n值*<br/>
要显示的整数值。

*b签名*<br/>
指定*nValue*参数是签名还是未签名。 如果此参数为 TRUE，则*对 nValue*进行签名。 如果此参数为*TRUE，nValue*小于零，则在字符串中的第一个数字之前放置一个减号。 如果此参数为 FALSE，*则 nValue*是无符号的。

## <a name="colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a>COle 控制容器：：设置DlgItemtext

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
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite 类](../../mfc/reference/colecontrolsite-class.md)<br/>
[COcc经理类](../../mfc/reference/coccmanager-class.md)
