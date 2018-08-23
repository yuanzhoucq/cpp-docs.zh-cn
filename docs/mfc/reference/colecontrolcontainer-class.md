---
title: COleControlContainer 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f33335e193997c0988cab0580c3eab612d0cc84
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852297"
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
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|创建控件站点，由该容器承载。|  
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|通知环境属性已更改的所有托管的控件。|  
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|修改指定的按钮控件。|  
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|选择一组指定的单选按钮。|  
|[COleControlContainer::CreateControl](#createcontrol)|创建托管的 ActiveX 控件。|  
|[COleControlContainer::CreateOleFont](#createolefont)|创建 OLE 字体。|  
|[COleControlContainer::FindItem](#finditem)|返回指定控件的自定义网站。|  
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|确定控件站点接受事件。|  
|[COleControlContainer::GetAmbientProp](#getambientprop)|检索指定的环境属性。|  
|[COleControlContainer::GetDlgItem](#getdlgitem)|检索指定的对话框控件。|  
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|检索指定的对话框控件的值。|  
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|检索指定的对话框控件的标题。|  
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|确定是否容器处理 WM_SETFOCUS 消息。|  
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|处理发送到无窗口控件的消息。|  
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|确定指定的按钮的状态。|  
|[COleControlContainer::OnPaint](#onpaint)|调用以重新绘制的容器的一部分。|  
|[COleControlContainer::OnUIActivate](#onuiactivate)|调用控件时，将为就地激活。|  
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|将要停用某个控件时调用。|  
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
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|托管的无窗口控件数。|  
|[COleControlContainer::m_pOleFont](#m_polefont)|一个指向自定义控件站点的 OLE 字体。|  
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|指向捕获控件站点。|  
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|指向当前具有输入焦点的控件。|  
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|指向当前就地激活的控件。|  
|[COleControlContainer::m_pWnd](#m_pwnd)|指向实现控件容器的窗口。|  
|[COleControlContainer::m_siteMap](#m_sitemap)|站点图中。|  
  
## <a name="remarks"></a>备注  
 这是通过提供的一个或多个 ActiveX 控件站点的支持 (由实现`COleControlSite`)。 `COleControlContainer` 完全实现[IOleInPlaceFrame](http://msdn.microsoft.com/library/windows/desktop/ms692770)并[IOleContainer](http://msdn.microsoft.com/library/windows/desktop/ms690103)接口，使包含的 ActiveX 控件，以满足他们作为就地项的资格。  
  
 通常，此类使用结合`COccManager`和`COleControlSite`实现自定义 ActiveX 控件容器，具有一个或多个 ActiveX 控件的自定义站点。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlContainer`  
  
## <a name="requirements"></a>要求  
 **标头：** afxocc.h  
  
##  <a name="attachcontrolsite"></a>  COleControlContainer::AttachControlSite  
 由框架调用以创建并附加控件站点。  
  
```  
virtual void AttachControlSite(
    CWnd* pWnd,  
    UINT nIDC = 0);

 
void AttachControlSite(
    CWnd* pWnd,  
    UINT nIDC = 0);
```  
  
### <a name="parameters"></a>参数  
 *pWnd*  
 一个指向`CWnd`对象。  
  
 *nIDC*  
 要附加的控件 ID。  
  
### <a name="remarks"></a>备注  
 如果你想要自定义此过程，重写此函数。  
  
> [!NOTE]
>  如果您以静态方式链接到 MFC 库，请使用此函数的第一种形式。 如果您动态链接到 MFC 库，请使用第二种形式。  
  
##  <a name="broadcastambientpropertychange"></a>  COleControlContainer::BroadcastAmbientPropertyChange  
 通知环境属性已更改的所有托管的控件。  
  
```  
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="parameters"></a>参数  
 *dispid*  
 要更改的环境属性的调度 ID。  
  
### <a name="remarks"></a>备注  
 当环境属性已更改值时，由框架调用此函数。 重写此函数可自定义此行为。  
  
##  <a name="checkdlgbutton"></a>  COleControlContainer::CheckDlgButton  
 修改按钮的当前状态。  
  
```  
virtual void CheckDlgButton(
    int nIDButton,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>参数  
 *nIDButton*  
 若要修改的按钮的 ID。  
  
 *n 请查看*  
 指定按钮的状态。 可以是以下各项之一：  
  
- BST_CHECKED 集的按钮状态检查。  
  
- BST_INDETERMINATE 设置按钮的状态为灰显，指示不确定状态。 仅当该按钮具有 BS_3STATE 或 BS_AUTO3STATE 样式，请使用此值。  
  
- BST_UNCHECKED 集将按钮为清除状态。  
  
##  <a name="checkradiobutton"></a>  COleControlContainer::CheckRadioButton  
 在组中选择某个指定的单选按钮，并清除组中的其余按钮。  
  
```  
virtual void CheckRadioButton(
    int nIDFirstButton,  
    int nIDLastButton,  
    int nIDCheckButton);
```  
  
### <a name="parameters"></a>参数  
 *nIDFirstButton*  
 指定组中的第一个单选按钮的标识符。  
  
 *nIDLastButton*  
 指定组中的最后一个单选按钮的标识符。  
  
 *nIDCheckButton*  
 指定要检查的单选按钮的标识符。  
  
##  <a name="colecontrolcontainer"></a>  COleControlContainer::COleControlContainer  
 构造 `COleControlContainer` 对象。  
  
```  
explicit COleControlContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 *pWnd*  
 指向控件容器的父窗口的指针。  
  
### <a name="remarks"></a>备注  
 一旦成功创建对象后，将通过调用自定义控件站点添加`AttachControlSite`。  
  
##  <a name="createcontrol"></a>  COleControlContainer::CreateControl  
 创建由指定承载的 ActiveX 控件`COleControlSite`对象。  
  
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
 *pWndCtrl*  
 指向表示控件的窗口对象的指针。  
  
 *clsid*  
 控件的唯一类 ID。  
  
 *lpszWindowName*  
 指向要在控件中显示的文本的指针。 设置控件的标题或文本属性的值 （如果有）。 如果为 NULL，不会更改控件的标题或文本属性。  
  
 *dwStyle*  
 窗口样式。 下列出的可用样式**备注**部分。  
  
 *rect*  
 指定控件的大小和位置。 它可以是`CRect`对象或`RECT`结构。  
  
 *nID*  
 指定控件的子窗口 id。  
  
 *pPersist*  
 一个指向`CFile`包含控件的持久状态。 默认值为 NULL，指示该控件而不从任何持久性存储区中还原其状态初始化自身。 如果不为 NULL，它应该是一个指向`CFile`-派生对象，它包含控件的持久性数据的流或存储形式。 此数据可能已保存在客户端的上一个激活。 `CFile`可以包含其他数据，但必须在调用时将设置为持久性数据的第一个字节其读写指针`CreateControl`。  
  
 *bStorage*  
 指示是否在数据*pPersist*应解释为`IStorage`或`IStream`数据。 如果中的数据*pPersist*是存储*bStorage*应为 TRUE。 如果中的数据*pPersist*是一个流*bStorage*应为 FALSE。 默认值为 FALSE。  
  
 *bstrLicKey*  
 可选的许可证密钥数据。 仅用于创建控件需要运行时许可证密钥的情况下，需要此数据。 如果控件支持授权，则必须提供要成功完成的控件创建的许可证密钥。 默认值为 NULL。  
  
 *ppNewSite*  
 指向将承载控件正在创建的现有控件站点的指针。 默认值为 NULL，指示该新控件站点将自动创建并附加到新的控件。  
  
 *ppt*  
 一个指向`POINT`结构，其中包含控件的左上角。 值确定控件的大小*psize*。 *Ppt*并*psize*的值为指定的大小和位置的控件的可选方法。  
  
 *psize*  
 一个指向`SIZE`结构，其中包含控件的大小。 值确定左上角*ppt*。 *Ppt*并*psize*的值为指定的大小和位置的控件的可选方法。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 Windows 的一个子集*dwStyle*支持标志`CreateControl`:  
  
- WS_VISIBLE 创建初始可见的窗口。 如果您希望控件立即，像普通窗口可见，则必须填写。  
  
- WS_DISABLED 创建最初处于禁用状态的窗口。 被禁用的窗口不能接收来自用户的输入。 如果控件具有已启用属性可以设置。  
  
- WS_BORDER 创建与细线边框的窗口。 如果控件具有 BorderStyle 属性可以设置。  
  
- WS_GROUP 指定一组控件的第一个控件。 用户可以通过使用箭头键键盘焦点从一个控件组中更改为下一步。 定义与 WS_GROUP 样式后的第一个控件属于相同组的所有控件。 WS_GROUP 样式的下一个控件结束组，并启动下一个组。  
  
- WS_TABSTOP 指定一个在用户按 TAB 键时可以接收键盘焦点的控件。 按 TAB 键将键盘焦点更改到 WS_TABSTOP 样式的下一个控件。  
  
 使用第二个重载来创建默认大小的控件。  
  
##  <a name="createolefont"></a>  COleControlContainer::CreateOleFont  
 创建 OLE 字体。  
  
```  
void CreateOleFont(CFont* pFont);
```  
  
### <a name="parameters"></a>参数  
 *pFont*  
 指向要使用的控件容器的字体的指针。  
  
##  <a name="finditem"></a>  COleControlContainer::FindItem  
 查找托管指定的项的自定义网站。  
  
```  
virtual COleControlSite* FindItem(UINT nID) const;  
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 要查找的项的标识符。  
  
### <a name="return-value"></a>返回值  
 一个指向指定项的自定义站点。  
  
##  <a name="freezeallevents"></a>  COleControlContainer::FreezeAllEvents  
 确定是否容器将忽略附加的控件站点中的事件，也不接受这些条款。  
  
```  
void FreezeAllEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>参数  
 *bFreeze*  
 如果将处理事件，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  该控件不需要停止触发事件，如果该控件容器请求。 它可以继续激发，但控件容器将忽略所有后续事件。  
  
##  <a name="getambientprop"></a>  COleControlContainer::GetAmbientProp  
 检索指定的环境属性的值。  
  
```  
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,  
    DISPID dispid,  
    VARIANT* pvarResult);
```  
  
### <a name="parameters"></a>参数  
 *pSite*  
 一个指向从中检索环境属性的控件站点。  
  
 *dispid*  
 所需的环境属性的调度 ID。  
  
 *pVarResult*  
 指向环境属性的值的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="getdlgitem"></a>  COleControlContainer::GetDlgItem  
 检索指向在对话框中指定的控件或子窗口或其他窗口的指针。  
  
```  
virtual CWnd* GetDlgItem(int nID) const;  
  
virtual void GetDlgItem(
    int nID,  
    HWND* phWnd) const;  
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 要检索的对话框项的标识符。  
  
 *phWnd*  
 指向对话框中指定的项的窗口对象的句柄的指针。  
  
### <a name="return-value"></a>返回值  
 指向对话框项的窗口的指针。  
  
##  <a name="getdlgitemint"></a>  COleControlContainer::GetDlgItemInt  
 检索给定控件的已翻译文本的值。  
  
```  
virtual UINT GetDlgItemInt(
    int nID,  
    BOOL* lpTrans,  
    BOOL bSigned) const;  
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 控件的标识符。  
  
 *lpTrans*  
 指向布尔变量来接收函数成功/失败值 （TRUE 表示成功，FALSE 表示失败）。  
  
 *bSigned*  
 指定函数是否应检查负号开头的文本并返回一个有符号的整数值，如果它找到一个。 如果*bSigned*参数为 TRUE 时，指定要检索的值一个有符号的整数值，将返回值强制转换**int**类型。 若要获得扩展错误信息，请调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="return-value"></a>返回值  
 如果成功，该变量指向*lpTrans*设置为 TRUE，返回值是控件文本的已翻译的值。  
  
 如果函数失败，该变量指向*lpTrans*设置为 FALSE，返回值为零。 请注意，由于零是可能的已翻译的值，返回值为 0 不单独指示失败。  
  
 如果*lpTrans*为 NULL，该函数返回不是成功还是失败有关的信息。  
  
### <a name="remarks"></a>备注  
 该函数将检索到的文本转换的最小化开头的文本的任何多余的空格，然后进行转换的十进制数字。 该函数会停止转换它达到文本的结尾或在遇到非数字字符时。  
  
 如果已转换的值大于 INT_MAX （适用于有符号的数字） 或 UINT_MAX （适用于无符号数字），此函数将返回零。  
  
##  <a name="getdlgitemtext"></a>  COleControlContainer::GetDlgItemText  
 检索给定控件的文本。  
  
```  
virtual int GetDlgItemText(
    int nID,  
    LPTSTR lpStr,  
    int nMaxCount) const;  
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 控件的标识符。  
  
 *lpStr*  
 指向控件的文本指针。  
  
 *nMaxCount*  
 指定的最大长度，以字符为单位的字符串复制到由指向的缓冲区*lpStr*。 如果字符串的长度超过限制，将截断字符串。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，返回的值指定字符复制到缓冲区，不包括终止 null 字符的数。  
  
 如果函数失败，则返回值为零。 若要获得扩展错误信息，请调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
##  <a name="handlesetfocus"></a>  COleControlContainer::HandleSetFocus  
 确定是否容器处理 WM_SETFOCUS 消息。  
  
```  
virtual BOOL HandleSetFocus();
```  
  
### <a name="return-value"></a>返回值  
 如果容器处理 WM_SETFOCUS 消息; 非零值否则为零。  
  
##  <a name="handlewindowlessmessage"></a>  COleControlContainer::HandleWindowlessMessage  
 处理无窗口控件的窗口消息。  
  
```  
virtual BOOL HandleWindowlessMessage(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam,  
    LRESULT* plResult);
```  
  
### <a name="parameters"></a>参数  
 *message*  
 窗口消息，由 Windows 提供的标识符。  
  
 *wParam*  
 消息; 参数由 Windows 提供。 指定其他特定于消息的信息。 此参数的内容取决于的值*消息*参数。  
  
 *lParam*  
 消息; 参数由 Windows 提供。 指定其他特定于消息的信息。 此参数的内容取决于的值*消息*参数。  
  
 *plResult*  
 Windows 结果代码。 指定的消息处理结果，并取决于发送的消息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义无窗口控件消息的处理。  
  
##  <a name="isdlgbuttonchecked"></a>  COleControlContainer::IsDlgButtonChecked  
 确定指定的按钮的状态。  
  
```  
virtual UINT IsDlgButtonChecked(int nIDButton) const;  
```  
  
### <a name="parameters"></a>参数  
 *nIDButton*  
 按钮控件的标识符。  
  
### <a name="return-value"></a>返回值  
 返回的值，从使用 BS_AUTOCHECKBOX、 BS_AUTORADIOBUTTON、 BS_AUTO3STATE、 BS_CHECKBOX、 BS_RADIOBUTTON 或 BS_3STATE 样式创建的按钮。 可以是以下各项之一：  
  
- BST_CHECKED 按钮被选中。  
  
- BST_INDETERMINATE 按钮为灰色，指示不确定状态 （仅适用于该按钮具有 BS_3STATE 或 BS_AUTO3STATE 样式的情况）。  
  
- BST_UNCHECKED 按钮已被清除。  
  
### <a name="remarks"></a>备注  
 如果该按钮具有三个状态的控件，此成员函数将确定是否它灰显，选中，或都不。  
  
##  <a name="m_crback"></a>  COleControlContainer::m_crBack  
 容器的背景色。  
  
```  
COLORREF m_crBack;  
```  
  
##  <a name="m_crfore"></a>  COleControlContainer::m_crFore  
 容器的前景色。  
  
```  
COLORREF m_crFore;  
```  
  
##  <a name="m_listsitesorwnds"></a>  COleControlContainer::m_listSitesOrWnds  
 由该容器承载控件站点的列表。  
  
```  
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;  
```  
  
##  <a name="m_nwindowlesscontrols"></a>  COleControlContainer::m_nWindowlessControls  
 无窗口控件承载的控件容器数。  
  
```  
int m_nWindowlessControls;  
```  
  
##  <a name="m_polefont"></a>  COleControlContainer::m_pOleFont  
 一个指向自定义控件站点的 OLE 字体。  
  
```  
LPFONTDISP m_pOleFont;  
```  
  
##  <a name="m_psitecapture"></a>  COleControlContainer::m_pSiteCapture  
 指向捕获控件站点。  
  
```  
COleControlSite* m_pSiteCapture;  
```  
  
##  <a name="m_psitefocus"></a>  COleControlContainer::m_pSiteFocus  
 指向当前具有输入焦点的控件站点的指针。  
  
```  
COleControlSite* m_pSiteFocus;  
```  
  
##  <a name="m_psiteuiactive"></a>  COleControlContainer::m_pSiteUIActive  
 指向就地激活的控件站点的指针。  
  
```  
COleControlSite* m_pSiteUIActive;  
```  
  
##  <a name="m_pwnd"></a>  COleControlContainer::m_pWnd  
 指向与此容器关联的窗口对象的指针。  
  
```  
CWnd* m_pWnd;  
```  
  
##  <a name="m_sitemap"></a>  COleControlContainer::m_siteMap  
 站点图中。  
  
```  
CMapPtrToPtr m_siteMap;  
```  
  
##  <a name="onpaint"></a>  COleControlContainer::OnPaint  
 由框架调用以处理 WM_PAINT 请求。  
  
```  
virtual BOOL OnPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 *pDC*  
 指向由容器使用的设备上下文的指针。  
  
### <a name="return-value"></a>返回值  
 如果该消息已处理; 非零值否则为零。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义绘制过程。  
  
##  <a name="onuiactivate"></a>  COleControlContainer::OnUIActivate  
 由框架调用时控制站点中，指向*pSite*，之后，将为在就地激活。  
  
```  
virtual void OnUIActivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>参数  
 *pSite*  
 指向控件站点，将为就地激活的指针。  
  
### <a name="remarks"></a>备注  
 就地激活意味着容器的主菜单中将被替换为适当地复合菜单。  
  
##  <a name="onuideactivate"></a>  COleControlContainer::OnUIDeactivate  
 由框架调用时控制站点中，指向*pSite*，即将停用。  
  
```  
virtual void OnUIDeactivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>参数  
 *pSite*  
 指向控件站点将要停用的指针。  
  
### <a name="remarks"></a>备注  
 收到此通知后，容器应重新安装其用户界面，并获得焦点。  
  
##  <a name="scrollchildren"></a>  COleControlContainer::ScrollChildren  
 从子窗口接收滚动消息时由框架调用。  
  
```  
virtual void ScrollChildren(
    int dx,  
    int dy);
```  
  
### <a name="parameters"></a>参数  
 *dx*  
 沿 x 轴滚动量，以像素为单位。  
  
 *dy*  
 沿 y 轴滚动量，以像素为单位。  
  
##  <a name="senddlgitemmessage"></a>  COleControlContainer::SendDlgItemMessage  
 将消息发送到指定控件。  
  
```  
virtual LRESULT SendDlgItemMessage(
    int nID,  
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 指定接收消息的控件的标识符。  
  
 *message*  
 指定要发送的消息。  
  
 *wParam*  
 指定其他特定于消息的信息。  
  
 *lParam*  
 指定其他特定于消息的信息。  
  
##  <a name="setdlgitemint"></a>  COleControlContainer::SetDlgItemInt  
 在对话框中指定的整数值的字符串表示形式中设置控件的文本。  
  
```  
virtual void SetDlgItemInt(
    int nID,  
    UINT nValue,  
    BOOL bSigned);
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 控件的标识符。  
  
 *n 值*  
 要显示的整数值。  
  
 *bSigned*  
 指定是否*n 值*签名或未签名的参数。 如果此参数为 TRUE， *n 值*进行签名。 如果此参数为 TRUE 并*n 值*小于零，放置在登录之前在字符串中的第一个数字相减。 如果此参数为 FALSE 时， *n 值*是无符号。  
  
##  <a name="setdlgitemtext"></a>  COleControlContainer::SetDlgItemText  
 设置指定的控件，使用中包含的文本的文本*lpszString*。  
  
```  
virtual void SetDlgItemText(
    int nID,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 控件的标识符。  
  
 *lpszString*  
 指向控件的文本指针。  
  
## <a name="see-also"></a>请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [COleControlSite 类](../../mfc/reference/colecontrolsite-class.md)   
 [COccManager 类](../../mfc/reference/coccmanager-class.md)
