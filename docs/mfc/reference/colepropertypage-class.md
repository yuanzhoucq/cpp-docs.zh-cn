---
title: "COlePropertyPage 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePropertyPage
- AFXCTL/COlePropertyPage
- AFXCTL/COlePropertyPage::COlePropertyPage
- AFXCTL/COlePropertyPage::GetControlStatus
- AFXCTL/COlePropertyPage::GetObjectArray
- AFXCTL/COlePropertyPage::GetPageSite
- AFXCTL/COlePropertyPage::IgnoreApply
- AFXCTL/COlePropertyPage::IsModified
- AFXCTL/COlePropertyPage::OnEditProperty
- AFXCTL/COlePropertyPage::OnHelp
- AFXCTL/COlePropertyPage::OnInitDialog
- AFXCTL/COlePropertyPage::OnObjectsChanged
- AFXCTL/COlePropertyPage::OnSetPageSite
- AFXCTL/COlePropertyPage::SetControlStatus
- AFXCTL/COlePropertyPage::SetDialogResource
- AFXCTL/COlePropertyPage::SetHelpInfo
- AFXCTL/COlePropertyPage::SetModifiedFlag
- AFXCTL/COlePropertyPage::SetPageName
dev_langs:
- C++
helpviewer_keywords:
- OLE property pages
- custom controls [MFC], properties
- COlePropertyPage class
- properties [C++], displaying
- displaying properties
- property pages, OLE
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 20d70cc25305fc5d17860314d9cfbe927df65c70
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="colepropertypage-class"></a>COlePropertyPage 类
用于在图形界面（类似于对话框）中显示自定义控件的属性。  
  
## <a name="syntax"></a>语法  
  
```  
class AFX_NOVTABLE COlePropertyPage : public CDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|构造 `COlePropertyPage` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|指示用户是否已修改控件中的值。|  
|[COlePropertyPage::GetObjectArray](#getobjectarray)|返回正在编辑的属性页的对象的数组。|  
|[COlePropertyPage::GetPageSite](#getpagesite)|返回一个指向属性页的`IPropertyPageSite`接口。|  
|[COlePropertyPage::IgnoreApply](#ignoreapply)|确定哪些控件不能将应用按钮。|  
|[COlePropertyPage::IsModified](#ismodified)|指示用户是否已修改的属性页。|  
|[COlePropertyPage::OnEditProperty](#oneditproperty)|当用户编辑属性时，由框架调用。|  
|[COlePropertyPage::OnHelp](#onhelp)|由框架调用，当用户调用帮助。|  
|[COlePropertyPage::OnInitDialog](#oninitdialog)|在属性页上初始化时由框架调用。|  
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|选择另一个 OLE 控件，并使用新属性时，由框架调用。|  
|[COlePropertyPage::OnSetPageSite](#onsetpagesite)|当属性框架提供页面的站点时，由框架调用。|  
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|设置一个标志，指示用户是否已修改控件中的值。|  
|[COlePropertyPage::SetDialogResource](#setdialogresource)|设置属性页对话框资源。|  
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|设置属性页的简短的帮助文本、 其帮助文件和其帮助上下文的名称。|  
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|设置一个标志，指示用户是否已修改的属性页。|  
|[COlePropertyPage::SetPageName](#setpagename)|设置属性页的名称 （标题）。|  
  
## <a name="remarks"></a>备注  
 例如，属性页可能包含编辑控件，它允许用户查看和修改控件的 caption 属性。  
  
 每个自定义或常用控件属性可以具有对话框控件，该控件的用户可以查看当前属性值并根据需要修改该值。  
  
 有关详细信息使用`COlePropertyPage`，请参阅文章[ActiveX 控件︰ 属性页](../../mfc/mfc-activex-controls-property-pages.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `COlePropertyPage`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxctl.h  
  
##  <a name="colepropertypage"></a>COlePropertyPage::COlePropertyPage  
 构造 `COlePropertyPage` 对象。  
  
```  
COlePropertyPage(
    UINT idDlg,  
    UINT idCaption);
```  
  
### <a name="parameters"></a>参数  
 *idDlg*  
 对话框模板资源 ID。  
  
 *idCaption*  
 属性页的标题的资源 ID。  
  
### <a name="remarks"></a>备注  
 当您实现的一个子类`COlePropertyPage`，子类的构造函数应使用`COlePropertyPage`构造函数来标识的对话框模板资源上它基于属性页上，并包含其标题的字符串资源。  
  
##  <a name="getcontrolstatus"></a>COlePropertyPage::GetControlStatus  
 确定用户是否已修改的值的属性页控件替换为指定的资源 id。  
  
```  
BOOL GetControlStatus(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 属性页控件的资源 ID。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果控件值已被修改; 否则为**FALSE**。  
  
##  <a name="getobjectarray"></a>COlePropertyPage::GetObjectArray  
 返回正在编辑的属性页的对象的数组。  
  
```  
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```  
  
### <a name="parameters"></a>参数  
 `pnObjects`  
 为将收到页上所编辑的对象的数目无符号长整数的指针。  
  
### <a name="return-value"></a>返回值  
 指向数组的指针`IDispatch`指针，用于访问每个控件的属性页上的属性。 调用方必须释放这些接口指针。  
  
### <a name="remarks"></a>备注  
 每个属性页对象维护的指针数组`IDispatch`页上所编辑的对象的接口。 此函数将其`pnObjects`为该数组中的元素数目的参数和返回指向数组的第一个元素的指针。  
  
##  <a name="getpagesite"></a>COlePropertyPage::GetPageSite  
 获取一个指针指向属性页的`IPropertyPageSite`接口。  
  
```  
LPPROPERTYPAGESITE GetPageSite();
```  
  
### <a name="return-value"></a>返回值  
 到属性页的指针`IPropertyPageSite`接口。  
  
### <a name="remarks"></a>备注  
 控件和容器合作，以便用户可以浏览和编辑控件属性。 该控件提供了属性页中，每种是允许用户同时编辑一组相关的属性的 OLE 对象。 容器将提供的属性框架中显示的属性页。 对于每一页，属性框架提供了一个网页组成，它支持`IPropertyPageSite`接口。  
  
##  <a name="ignoreapply"></a>COlePropertyPage::IgnoreApply  
 确定哪些控件不能将应用按钮。  
  
```  
void IgnoreApply(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 若要忽略控件的 ID。  
  
### <a name="remarks"></a>备注  
 只有已更改属性页控件的值时，才启用属性页的应用按钮。 使用此函数指定不会导致应用按钮，其值更改时要启用的控件。  
  
##  <a name="ismodified"></a>COlePropertyPage::IsModified  
 确定用户是否已更改的属性页上的任何值。  
  
```  
BOOL IsModified();
```  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果属性页上进行了修改。  
  
##  <a name="oneditproperty"></a>COlePropertyPage::OnEditProperty  
 要编辑的特定属性时，框架将调用此函数。  
  
```  
virtual BOOL OnEditProperty(DISPID dispid);
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 正在编辑的属性的调度 ID。  
  
### <a name="return-value"></a>返回值  
 默认实现返回**FALSE**。 重写此函数应返回**TRUE**。  
  
### <a name="remarks"></a>备注  
 您可以重写它以将焦点设置到相应的页上的控件。 默认实现不执行任何操作并返回**FALSE**。  
  
##  <a name="onhelp"></a>COlePropertyPage::OnHelp  
 当用户请求联机帮助时，框架将调用此函数。  
  
```  
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```  
  
### <a name="parameters"></a>参数  
 *lpszHelpDir*  
 包含属性页的帮助文件的目录。  
  
### <a name="return-value"></a>返回值  
 默认实现返回**FALSE**。  
  
### <a name="remarks"></a>备注  
 如果属性页必须执行任何特殊操作，当用户访问帮助，请将其覆盖。 默认实现不执行任何操作并返回**FALSE**，它指示框架调用 WinHelp。  
  
##  <a name="oninitdialog"></a>COlePropertyPage::OnInitDialog  
 初始化属性页对话框时，框架将调用此函数。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>返回值  
 默认实现返回**FALSE**。  
  
### <a name="remarks"></a>备注  
 如果对话框中初始化时，不需要执行任何特殊操作，请将其覆盖。 默认实现调用`CDialog::OnInitDialog`，并返回**FALSE**。  
  
##  <a name="onobjectschanged"></a>COlePropertyPage::OnObjectsChanged  
 选择另一个 OLE 控件，并使用新属性时，由框架调用。  
  
```  
virtual void OnObjectsChanged();
```  
  
### <a name="remarks"></a>备注  
 在开发环境中查看 OLE 控件的属性时, 无模式对话框用于显示其属性页。 如果选择另一个控件，则必须为新的属性集显示一组不同的属性页。 框架调用此函数可通知这一变化的属性页。  
  
 重写此函数以接收此操作的通知并执行任何特殊操作。  
  
##  <a name="onsetpagesite"></a>COlePropertyPage::OnSetPageSite  
 当属性框架提供属性页的页网站时，框架将调用此函数。  
  
```  
virtual void OnSetPageSite();
```  
  
### <a name="remarks"></a>备注  
 默认实现将加载该页面的标题，并尝试确定从对话框资源的页的大小。 重写此函数，如果属性页需要任何进一步的操作;重写应调用基类实现。  
  
##  <a name="setcontrolstatus"></a>COlePropertyPage::SetControlStatus  
 更改属性页控件的状态。  
  
```  
BOOL SetControlStatus(
    UINT nID,  
    BOOL bDirty);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 包含属性页控件的 ID。  
  
 `bDirty`  
 指定属性页上的某个字段已被修改。 设置为**TRUE**如果该字段已被修改， **FALSE**如果尚未修改。  
  
### <a name="return-value"></a>返回值  
 **TRUE**，如果指定的控件已设置; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 如果属性页控件的状态已更新，关闭属性页上或选择应用按钮时，将使用适当的值更新控件的属性。  
  
##  <a name="setdialogresource"></a>COlePropertyPage::SetDialogResource  
 设置属性页对话框资源。  
  
```  
void SetDialogResource(HGLOBAL hDialog);
```  
  
### <a name="parameters"></a>参数  
 *hDialog*  
 属性页对话框资源的句柄。  
  
##  <a name="sethelpinfo"></a>COlePropertyPage::SetHelpInfo  
 指定工具提示信息、 帮助文件名和属性页的帮助上下文。  
  
```  
void SetHelpInfo(
    LPCTSTR lpszDocString,  
    LPCTSTR lpszHelpFile = NULL,  
    DWORD dwHelpContext = 0);
```  
  
### <a name="parameters"></a>参数  
 *lpszDocString*  
 包含显示在状态栏或其他位置的简要的帮助信息的字符串。  
  
 `lpszHelpFile`  
 属性页的帮助文件的名称。  
  
 *dwHelpContext*  
 属性页上的帮助上下文。  
  
##  <a name="setmodifiedflag"></a>COlePropertyPage::SetModifiedFlag  
 指示用户是否已修改的属性页。  
  
```  
void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bModified`  
 指定属性页的修改的标志的新值。  
  
##  <a name="setpagename"></a>COlePropertyPage::SetPageName  
 设置属性框架通常会显示在页面的选项卡上的属性页的名称。  
  
```  
void SetPageName(LPCTSTR lpszPageName);
```  
  
### <a name="parameters"></a>参数  
 *lpszPageName*  
 包含属性页的名称的字符串的指针。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CIRC3](../../visual-cpp-samples.md)   
 [MFC 示例 TESTHELP](../../visual-cpp-samples.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)

