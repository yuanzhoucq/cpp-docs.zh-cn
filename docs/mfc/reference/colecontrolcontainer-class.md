---
title: "COleControlContainer 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6d04faa904eba416b290515e5e6773ac6ef9837
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
|名称|描述|  
|----------|-----------------|  
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|创建控件站点时，由该容器承载。|  
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|通知环境属性已更改的所有托管的控件。|  
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|修改指定的按钮控件。|  
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|选择一组指定的单选按钮。|  
|[COleControlContainer::CreateControl](#createcontrol)|创建托管的 ActiveX 控件。|  
|[COleControlContainer::CreateOleFont](#createolefont)|创建 OLE 字体。|  
|[COleControlContainer::FindItem](#finditem)|返回指定控件的自定义站点。|  
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|确定控件站点正在接受事件。|  
|[COleControlContainer::GetAmbientProp](#getambientprop)|检索指定的环境属性。|  
|[COleControlContainer::GetDlgItem](#getdlgitem)|检索指定的对话框控件。|  
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|检索指定的对话框控件的值。|  
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|检索指定的对话框控件的标题。|  
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|确定是否容器处理`WM_SETFOCUS`消息。|  
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|处理发送到无窗口控件的消息。|  
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|确定指定的按钮的状态。|  
|[COleControlContainer::OnPaint](#onpaint)|调用以重新绘制容器的一部分。|  
|[COleControlContainer::OnUIActivate](#onuiactivate)|当控件将被就地激活时调用。|  
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|当控件以将其停用时调用。|  
|[COleControlContainer::ScrollChildren](#scrollchildren)|从子窗口接收滚动消息时由框架调用。|  
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|将消息发送到指定控件。|  
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|设置指定控件的值。|  
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|设置指定控件的文本。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleControlContainer::m_crBack](#m_crback)|容器的背景色。|  
|[COleControlContainer::m_crFore](#m_crfore)|容器的前景色。|  
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|支持的控件站点的列表。|  
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|托管的无窗口控件的数目。|  
|[COleControlContainer::m_pOleFont](#m_polefont)|指向自定义控件站点的 OLE 字体的指针。|  
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|指向捕获控件所在位置的指针。|  
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|指向当前具有输入焦点的控件。|  
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|到目前就地激活的控件的指针。|  
|[COleControlContainer::m_pWnd](#m_pwnd)|指向实现控件容器窗口的指针。|  
|[COleControlContainer::m_siteMap](#m_sitemap)|站点图中。|  
  
## <a name="remarks"></a>备注  
 这可以通过一个或多个 ActiveX 控件站点提供支持 (由实现`COleControlSite`)。 `COleControlContainer`完全实现[IOleInPlaceFrame](http://msdn.microsoft.com/library/windows/desktop/ms692770)和[IOleContainer](http://msdn.microsoft.com/library/windows/desktop/ms690103)接口，允许所含的 ActiveX 控件，以满足其作为就地项的限定资格。  
  
 通常情况下，此类使用结合`COccManager`和`COleControlSite`实现自定义的 ActiveX 控件容器，包含一个或多个 ActiveX 控件的自定义站点。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlContainer`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxocc.h  
  
##  <a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite  
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
 `pWnd`  
 指向的指针`CWnd`对象。  
  
 `nIDC`  
 要附加的控件 ID。  
  
### <a name="remarks"></a>备注  
 如果你想要自定义此过程，重写此函数。  
  
> [!NOTE]
>  如果你以静态方式链接到 MFC 库，请使用此函数的第一种形式。 如果你动态链接到 MFC 库，请使用第二种形式。  
  
##  <a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange  
 通知环境属性已更改的所有托管的控件。  
  
```  
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要更改的环境属性调度 ID。  
  
### <a name="remarks"></a>备注  
 当环境属性已更改值时，将由框架调用此函数。 重写此函数可自定义此行为。  
  
##  <a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton  
 修改按钮的当前的状态。  
  
```  
virtual void CheckDlgButton(
    int nIDButton,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>参数  
 `nIDButton`  
 要修改的按钮的 ID。  
  
 `nCheck`  
 指定按钮的状态。 可以是以下各项之一：  
  
- **BST_CHECKED**按钮状态设置为已选中。  
  
- **BST_INDETERMINATE**按钮状态设置为显示为灰色，指示不确定状态。 使用此值，仅当该按钮具有**BS_3STATE**或**BS_AUTO3STATE**样式。  
  
- **BST_UNCHECKED**按钮状态设置为已清除。  
  
##  <a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton  
 选择指定的单选按钮组中，并清除组中的剩余按钮。  
  
```  
virtual void CheckRadioButton(
    int nIDFirstButton,  
    int nIDLastButton,  
    int nIDCheckButton);
```  
  
### <a name="parameters"></a>参数  
 `nIDFirstButton`  
 指定组中的第一个单选按钮的标识符。  
  
 `nIDLastButton`  
 指定组中的最后一个单选按钮的标识符。  
  
 `nIDCheckButton`  
 指定要检查的单选按钮的标识符。  
  
##  <a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer  
 构造 `COleControlContainer` 对象。  
  
```  
explicit COleControlContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向控件容器的父窗口的指针。  
  
### <a name="remarks"></a>备注  
 一旦成功创建对象后，添加具有调用的自定义控件站点`AttachControlSite`。  
  
##  <a name="createcontrol"></a>COleControlContainer::CreateControl  
 创建 ActiveX 控件，通过指定托管`COleControlSite`对象。  
  
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
 `pWndCtrl`  
 指向表示控件的窗口对象的指针。  
  
 `clsid`  
 控件的唯一类 ID。  
  
 `lpszWindowName`  
 指向要在控件中显示的文本的指针。 设置控件的标题或文本属性的值 （如果有）。 如果**NULL**，不会更改控件的标题或文本属性。  
  
 `dwStyle`  
 窗口样式。 可用的样式下列出**备注**部分。  
  
 `rect`  
 指定控件的大小和位置。 它可以是`CRect`对象或`RECT`结构。  
  
 `nID`  
 指定控件的子窗口 id。  
  
 `pPersist`  
 指向的指针`CFile`包含控件的持久状态。 默认值是**NULL**，，该值指示该控件而不是从任何持久性存储区还原其状态初始化自身。 如果不是**NULL**，它应为一个指向`CFile`-派生的对象，包含控件的持久性数据，流或存储的形式。 无法在客户端以前激活保存此数据。 `CFile`可以包含其他数据，但必须在调用的时间设置为永久数据的第一个字节其读写指针`CreateControl`。  
  
 `bStorage`  
 指示是否在数据`pPersist`应被视为`IStorage`或`IStream`数据。 如果中的数据`pPersist`是一种存储，`bStorage`应**TRUE**。 如果中的数据`pPersist`是流、`bStorage`应**FALSE**。 默认值是**FALSE**。  
  
 `bstrLicKey`  
 可选的许可证密钥数据。 仅用于创建控件需要运行时许可证密钥所需要的此数据。 如果该控件支持授权，则必须提供要成功的控件创建的许可密钥。 默认值是**NULL**。  
  
 *ppNewSite*  
 指向要承载正在创建该控件的现有控件站点的指针。 默认值是**NULL**，指示，新的控件站点将自动创建并连接到新的控件。  
  
 `ppt`  
 指向的指针**点**结构，它包含控件的左上角。 控件的大小由值*psize*。 `ppt`和*psize*的值为指定的大小和位置的控件的可选方法。  
  
 *psize*  
 指向的指针**大小**结构，它包含控件的大小。 由的值确定的左上角`ppt`。 `ppt`和*psize*的值为指定的大小和位置的控件的可选方法。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 Windows 的一个子集`dwStyle`标志受`CreateControl`:  
  
- **WS_VISIBLE**创建初始可见的窗口。 如果您希望控件，使其立即，像普通的窗口可见，则必须填写。  
  
- **WS_DISABLED**创建最初处于禁用状态的窗口。 已禁用的窗口无法接收来自用户输入。 如果控件具有 Enabled 属性可以设置。  
  
- `WS_BORDER`创建一个窗口，有精简行的边框。 如果控件具有 BorderStyle 属性可以设置。  
  
- **WS_GROUP**指定一组控件的第一个控件。 用户可以通过使用箭头键键盘焦点从一个控件组中更改为下一步。 使用定义的所有控件**WS_GROUP**样式后的第一个控件属于同一个组。 使用下一个控件**WS_GROUP**样式组结束和开始下一个组。  
  
- **WS_TABSTOP**指定在用户按 TAB 键时，可以接收键盘焦点的控件。 按 TAB 键将键盘焦点更改到下一个控件的**WS_TABSTOP**样式。  
  
 使用第二个重载来创建默认大小的控件。  
  
##  <a name="createolefont"></a>COleControlContainer::CreateOleFont  
 创建 OLE 字体。  
  
```  
void CreateOleFont(CFont* pFont);
```  
  
### <a name="parameters"></a>参数  
 `pFont`  
 指向通过控件容器使用的字体的指针。  
  
##  <a name="finditem"></a>COleControlContainer::FindItem  
 查找托管指定的项的自定义站点。  
  
```  
virtual COleControlSite* FindItem(UINT nID) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 要找的项标识符。  
  
### <a name="return-value"></a>返回值  
 指定的项的自定义站点指向的指针。  
  
##  <a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents  
 确定是否该容器将忽略附加的控件站点中的事件，或者接受这些条款。  
  
```  
void FreezeAllEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>参数  
 `bFreeze`  
 如果无法处理的事件; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  控件不需要停止激发事件，如果请求的控件容器。 它可以继续激发，但所有后续的事件将被忽略，控件容器。  
  
##  <a name="getambientprop"></a>COleControlContainer::GetAmbientProp  
 检索指定的环境属性的值。  
  
```  
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,  
    DISPID dispid,  
    VARIANT* pvarResult);
```  
  
### <a name="parameters"></a>参数  
 `pSite`  
 控制站点将从其检索环境属性指向的指针。  
  
 `dispid`  
 所需的环境属性的调度 ID。  
  
 *pVarResult*  
 指向环境属性的值的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="getdlgitem"></a>COleControlContainer::GetDlgItem  
 检索对话框中指定的控件或子窗口或其他窗口的指针。  
  
```  
virtual CWnd* GetDlgItem(int nID) const;  
  
virtual void GetDlgItem(
    int nID,  
    HWND* phWnd) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 要检索的对话框项的标识符。  
  
 `phWnd`  
 指向指定的对话框项的窗口对象的句柄的指针。  
  
### <a name="return-value"></a>返回值  
 指向对话框项的窗口的指针。  
  
##  <a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt  
 检索给定控件的已翻译文本的值。  
  
```  
virtual UINT GetDlgItemInt(
    int nID,  
    BOOL* lpTrans,  
    BOOL bSigned) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 控件的标识符。  
  
 `lpTrans`  
 指向接收函数成功/失败值的布尔变量 ( **TRUE**表示成功， **FALSE**指示失败)。  
  
 `bSigned`  
 指定函数是否应检查负号开头的文本，如果它找到一个返回带符号的整数值。 如果`bSigned`参数是**TRUE**，指定要检索的值一个有符号的整数值，将返回值强制转换`int`类型。 若要获得扩展的错误信息，调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="return-value"></a>返回值  
 如果成功，变量的指向`lpTrans`设置为**TRUE**，并且返回值是控件文本的已翻译的值。  
  
 如果函数失败，指向的变量由`lpTrans`设置为**FALSE**，和返回值为零。 请注意，由于零是一个可能的已翻译的值，返回值为 0 不自行指示失败。  
  
 如果`lpTrans`是**NULL**，该函数返回有关成功或失败的任何信息。  
  
### <a name="remarks"></a>备注  
 该函数将检索到的文本转换通过去除开头的文本的任何额外空格，然后进行转换的十进制数字。 函数转换它达到文本的末尾或遇到的非数字字符时，将停止。  
  
 此函数将返回零，如果已转换的值大于**INT_MAX** （为有符号数字） 或**UINT_MAX** （对于无符号数字）。  
  
##  <a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText  
 检索给定控件的文本。  
  
```  
virtual int GetDlgItemText(
    int nID,  
    LPTSTR lpStr,  
    int nMaxCount) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 控件的标识符。  
  
 `lpStr`  
 指向控件的文本指针。  
  
 `nMaxCount`  
 指定的最大长度，以字符为单位，要复制到通过指向的缓冲区的字符串的`lpStr`。 如果字符串的长度超过了限制，该字符串将被截断。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，返回值将指定字符将复制到缓冲区，不包括终止 null 字符的数。  
  
 如果函数失败，则返回值为零。 若要获得扩展的错误信息，调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
##  <a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus  
 确定是否容器处理`WM_SETFOCUS`消息。  
  
```  
virtual BOOL HandleSetFocus();
```  
  
### <a name="return-value"></a>返回值  
 如果容器处理非零`WM_SETFOCUS`消息; 否则为零。  
  
##  <a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage  
 处理无窗口控件的窗口消息。  
  
```  
virtual BOOL HandleWindowlessMessage(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam,  
    LRESULT* plResult);
```  
  
### <a name="parameters"></a>参数  
 `message`  
 窗口消息，由 Windows 提供的标识符。  
  
 `wParam`  
 消息; 参数由 Windows 提供。 指定消息特定的附加信息。 此参数的内容依赖于的值`message`参数。  
  
 `lParam`  
 消息; 参数由 Windows 提供。 指定消息特定的附加信息。 此参数的内容依赖于的值`message`参数。  
  
 *plResult*  
 Windows 结果代码。 指定的消息处理的结果，并且依赖于发送的消息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义的无窗口控件消息的处理。  
  
##  <a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonChecked  
 确定指定的按钮的状态。  
  
```  
virtual UINT IsDlgButtonChecked(int nIDButton) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIDButton`  
 按钮控件的标识符。  
  
### <a name="return-value"></a>返回值  
 返回值，通过使用创建按钮**BS_AUTOCHECKBOX**， **BS_AUTORADIOBUTTON**， **BS_AUTO3STATE**， **BS_CHECKBOX**，**BS_RADIOBUTTON**，或**BS_3STATE**样式。 可以是以下各项之一：  
  
- **BST_CHECKED**按钮被选中。  
  
- **BST_INDETERMINATE**按钮为灰显，指示不确定状态 (仅适用于该按钮具有**BS_3STATE**或**BS_AUTO3STATE**样式)。  
  
- **BST_UNCHECKED**按钮处于未选中状态。  
  
### <a name="remarks"></a>备注  
 如果按钮是具有三个状态的控件，该成员函数将确定是否它显示为灰色，选中，或都不。  
  
##  <a name="m_crback"></a>COleControlContainer::m_crBack  
 容器的背景色。  
  
```  
COLORREF m_crBack;  
```  
  
##  <a name="m_crfore"></a>COleControlContainer::m_crFore  
 容器的前景色。  
  
```  
COLORREF m_crFore;  
```  
  
##  <a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds  
 由该容器承载的控件站点的列表。  
  
```  
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;  
```  
  
##  <a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls  
 无窗口控件承载的控件容器数。  
  
```  
int m_nWindowlessControls;  
```  
  
##  <a name="m_polefont"></a>COleControlContainer::m_pOleFont  
 指向自定义控件站点的 OLE 字体的指针。  
  
```  
LPFONTDISP m_pOleFont;  
```  
  
##  <a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture  
 指向捕获控件所在位置的指针。  
  
```  
COleControlSite* m_pSiteCapture;  
```  
  
##  <a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus  
 指向当前具有输入焦点的控件站点的指针。  
  
```  
COleControlSite* m_pSiteFocus;  
```  
  
##  <a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive  
 指向就地激活的控件站点的指针。  
  
```  
COleControlSite* m_pSiteUIActive;  
```  
  
##  <a name="m_pwnd"></a>COleControlContainer::m_pWnd  
 指向与此容器关联的窗口对象的指针。  
  
```  
CWnd* m_pWnd;  
```  
  
##  <a name="m_sitemap"></a>COleControlContainer::m_siteMap  
 站点图中。  
  
```  
CMapPtrToPtr m_siteMap;  
```  
  
##  <a name="onpaint"></a>COleControlContainer::OnPaint  
 由框架来处理调用`WM_PAINT`请求。  
  
```  
virtual BOOL OnPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向由容器使用的设备上下文的指针。  
  
### <a name="return-value"></a>返回值  
 如果该消息已处理; 则为非 0否则为零。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义绘制过程。  
  
##  <a name="onuiactivate"></a>COleControlContainer::OnUIActivate  
 由框架调用时控件所在位置，指向由`pSite`，即将在就地激活。  
  
```  
virtual void OnUIActivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>参数  
 `pSite`  
 指向控件所在位置将要就地激活的指针。  
  
### <a name="remarks"></a>备注  
 就地激活意味着容器的主菜单将被替换为就地复合菜单。  
  
##  <a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate  
 由框架调用时控件所在位置，指向由`pSite`，即将停用。  
  
```  
virtual void OnUIDeactivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>参数  
 `pSite`  
 指向控件站点以将其停用的指针。  
  
### <a name="remarks"></a>备注  
 收到此通知时，容器应重新安装其用户界面，并获得焦点。  
  
##  <a name="scrollchildren"></a>COleControlContainer::ScrollChildren  
 从子窗口接收滚动消息时由框架调用。  
  
```  
virtual void ScrollChildren(
    int dx,  
    int dy);
```  
  
### <a name="parameters"></a>参数  
 `dx`  
 沿 x 轴滚动的量，以像素为单位。  
  
 *dy*  
 量，以像素为单位，在 y 轴上滚动。  
  
##  <a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage  
 将消息发送到指定控件。  
  
```  
virtual LRESULT SendDlgItemMessage(
    int nID,  
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 指定接收消息的控件的标识符。  
  
 `message`  
 指定要发送的消息。  
  
 `wParam`  
 指定消息特定的附加信息。  
  
 `lParam`  
 指定消息特定的附加信息。  
  
##  <a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt  
 在对话框中的字符串表示形式指定的整数值到设置控件的文本。  
  
```  
virtual void SetDlgItemInt(
    int nID,  
    UINT nValue,  
    BOOL bSigned);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 控件的标识符。  
  
 `nValue`  
 要显示的整数值。  
  
 `bSigned`  
 指定是否`nValue`参数进行签名或未签名。 如果此参数为**TRUE**，`nValue`进行签名。 如果此参数为**TRUE**和`nValue`小于零的负号置于之前在字符串中的第一个数字。 如果此参数为**FALSE**，`nValue`是无符号。  
  
##  <a name="setdlgitemtext"></a>COleControlContainer::SetDlgItemText  
 设置指定的控件，使用中包含的文本的文本`lpszString`。  
  
```  
virtual void SetDlgItemText(
    int nID,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 控件的标识符。  
  
 `lpszString`  
 指向控件的文本指针。  
  
## <a name="see-also"></a>请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleControlSite 类](../../mfc/reference/colecontrolsite-class.md)   
 [COccManager 类](../../mfc/reference/coccmanager-class.md)
