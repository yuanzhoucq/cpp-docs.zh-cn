---
title: COlePropertyPage 类
ms.date: 11/04/2016
f1_keywords:
- COlePropertyPage
- AFXCTL/COlePropertyPage
- AFXCTL/COlePropertyPage::COlePropertyPage
- AFXCTL/COlePropertyPage::GetControlStatus
- AFXCTL/COlePropertyPage::GetObjectArray
- AFXCTL/COlePropertyPage::GetPageSite
- AFXCTL/COlePropertyPage::OVERWRITEApply
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
helpviewer_keywords:
- COlePropertyPage [MFC], COlePropertyPage
- COlePropertyPage [MFC], GetControlStatus
- COlePropertyPage [MFC], GetObjectArray
- COlePropertyPage [MFC], GetPageSite
- COlePropertyPage [MFC], IgnoreApply
- COlePropertyPage [MFC], IsModified
- COlePropertyPage [MFC], OnEditProperty
- COlePropertyPage [MFC], OnHelp
- COlePropertyPage [MFC], OnInitDialog
- COlePropertyPage [MFC], OnObjectsChanged
- COlePropertyPage [MFC], OnSetPageSite
- COlePropertyPage [MFC], SetControlStatus
- COlePropertyPage [MFC], SetDialogResource
- COlePropertyPage [MFC], SetHelpInfo
- COlePropertyPage [MFC], SetModifiedFlag
- COlePropertyPage [MFC], SetPageName
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
ms.openlocfilehash: 8253b2c2fa6b93ec51c7ede983ef710eed039970
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865881"
---
# <a name="colepropertypage-class"></a>COlePropertyPage 类

用于在图形界面（类似于对话框）中显示自定义控件的属性。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COlePropertyPage：： COlePropertyPage](#colepropertypage)|构造 `COlePropertyPage` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COlePropertyPage：： GetControlStatus](#getcontrolstatus)|指示用户是否已修改控件中的值。|
|[COlePropertyPage：： GetObjectArray](#getobjectarray)|返回由属性页编辑的对象的数组。|
|[COlePropertyPage：： GetPageSite](#getpagesite)|返回指向属性页的 `IPropertyPageSite` 接口的指针。|
|[COlePropertyPage：： IgnoreApply](#ignoreapply)|确定哪些控件不启用 "应用" 按钮。|
|[COlePropertyPage：： IsModified](#ismodified)|指示用户是否已修改了属性页。|
|[COlePropertyPage：： OnEditProperty](#oneditproperty)|当用户编辑属性时由框架调用。|
|[COlePropertyPage：： OnHelp](#onhelp)|当用户调用帮助时由框架调用。|
|[COlePropertyPage：： OnInitDialog](#oninitdialog)|当初始化属性页时由框架调用。|
|[COlePropertyPage：： OnObjectsChanged](#onobjectschanged)|当选择另一个具有新属性的 OLE 控件时由框架调用。|
|[COlePropertyPage：： OnSetPageSite](#onsetpagesite)|当属性框架提供页面的站点时由框架调用。|
|[COlePropertyPage：： SetControlStatus](#setcontrolstatus)|设置一个标志，该标志指示用户是否已修改控件中的值。|
|[COlePropertyPage：： SetDialogResource](#setdialogresource)|设置属性页的对话框资源。|
|[COlePropertyPage：： SetHelpInfo](#sethelpinfo)|设置属性页的简短帮助文本、其帮助文件的名称及其帮助上下文。|
|[COlePropertyPage：： SetModifiedFlag](#setmodifiedflag)|设置一个标志，该标志指示用户是否已修改了属性页。|
|[COlePropertyPage：： SetPageName](#setpagename)|设置属性页的名称（标题）。|

## <a name="remarks"></a>备注

例如，属性页可能包含一个编辑控件，该控件允许用户查看和修改控件的 caption 属性。

每个自定义或常用控件属性都可以有一个对话框控件，该控件允许控件的用户查看当前属性值并根据需要修改该值。

有关使用 `COlePropertyPage`的详细信息，请参阅文章[ActiveX 控件：属性页](../../mfc/mfc-activex-controls-property-pages.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>要求

**标头：** afxctl。h

##  <a name="colepropertypage"></a>COlePropertyPage：： COlePropertyPage

构造 `COlePropertyPage` 对象。

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>参数

*idDlg*<br/>
对话框模板的资源 ID。

*idCaption*<br/>
属性页标题的资源 ID。

### <a name="remarks"></a>备注

在实现 `COlePropertyPage`的子类时，子类的构造函数应使用 `COlePropertyPage` 构造函数来标识属性页所基于的对话框模板资源以及包含其标题的字符串资源。

##  <a name="getcontrolstatus"></a>COlePropertyPage：： GetControlStatus

确定用户是否已修改具有指定资源 ID 的属性页控件的值。

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
属性页控件的资源 ID。

### <a name="return-value"></a>返回值

如果控件值已修改，则为 TRUE;否则为 FALSE。

##  <a name="getobjectarray"></a>COlePropertyPage：： GetObjectArray

返回由属性页编辑的对象的数组。

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>参数

*pnObjects*<br/>
指向一个无符号长整数的指针，该整数将接收该页正在编辑的对象数。

### <a name="return-value"></a>返回值

指向 `IDispatch` 指针的数组的指针，这些指针用于访问属性页上每个控件的属性。 调用方不能释放这些接口指针。

### <a name="remarks"></a>备注

每个属性页对象维护一个指针数组，这些指针指向该页正在编辑的对象的 `IDispatch` 接口。 此函数将其*pnObjects*参数设置为该数组中的元素数，并返回一个指向数组中第一个元素的指针。

##  <a name="getpagesite"></a>COlePropertyPage：： GetPageSite

获取指向属性页的 `IPropertyPageSite` 接口的指针。

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>返回值

指向属性页的 `IPropertyPageSite` 接口的指针。

### <a name="remarks"></a>备注

协作控件和容器，使用户可以浏览和编辑控件属性。 控件提供了属性页，其中每个都是允许用户编辑一组相关属性的 OLE 对象。 容器提供显示属性页的属性框架。 对于每个页面，属性框架都提供一个支持 `IPropertyPageSite` 接口的页面站点。

##  <a name="ignoreapply"></a>COlePropertyPage：： IgnoreApply

确定哪些控件不启用 "应用" 按钮。

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
要忽略的控件的 ID。

### <a name="remarks"></a>备注

仅当属性页控件的值已更改时，才会启用属性页的 "应用" 按钮。 使用此函数指定在其值更改时不会启用 "应用" 按钮的控件。

##  <a name="ismodified"></a>COlePropertyPage：： IsModified

确定用户是否已更改属性页上的任何值。

```
BOOL IsModified();
```

### <a name="return-value"></a>返回值

如果已修改属性页，则为 TRUE。

##  <a name="oneditproperty"></a>COlePropertyPage：： OnEditProperty

当要编辑特定属性时，框架会调用此函数。

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>参数

*dispid*<br/>
正在编辑的属性的调度 ID。

### <a name="return-value"></a>返回值

默认实现返回 FALSE。 此函数的重写应返回 TRUE。

### <a name="remarks"></a>备注

您可以重写它以将焦点设置到页面上的相应控件。 默认实现不执行任何操作并返回 FALSE。

##  <a name="onhelp"></a>COlePropertyPage：： OnHelp

当用户请求联机帮助时，框架会调用此函数。

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>参数

*lpszHelpDir*<br/>
包含属性页的帮助文件的目录。

### <a name="return-value"></a>返回值

默认实现返回 FALSE。

### <a name="remarks"></a>备注

如果在用户访问帮助时属性页必须执行任何特殊操作，请重写此方法。 默认实现不执行任何操作并返回 FALSE，这会指示框架调用 WinHelp。

##  <a name="oninitdialog"></a>COlePropertyPage：： OnInitDialog

当初始化属性页的对话框时，框架会调用此函数。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

默认实现返回 FALSE。

### <a name="remarks"></a>备注

如果在初始化对话框时需要进行任何特殊操作，请重写此方法。 默认实现将调用 `CDialog::OnInitDialog` 并返回 FALSE。

##  <a name="onobjectschanged"></a>COlePropertyPage：： OnObjectsChanged

当选择另一个具有新属性的 OLE 控件时由框架调用。

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>备注

在开发人员环境中查看 OLE 控件的属性时，无模式对话框用于显示其属性页。 如果选择了其他控件，则必须为新属性集显示一组不同的属性页。 框架调用此函数以通知属性页的更改。

重写此函数以接收此操作的通知并执行任何特殊操作。

##  <a name="onsetpagesite"></a>COlePropertyPage：： OnSetPageSite

当属性框架提供属性页的页面站点时，框架会调用此函数。

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>备注

默认实现将加载页面的标题，并尝试从对话框资源确定页面的大小。 如果属性页需要进一步的操作，请重写此函数;重写应调用基类实现。

##  <a name="setcontrolstatus"></a>COlePropertyPage：： SetControlStatus

更改属性页控件的状态。

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>参数

*nID*<br/>
包含属性页控件的 ID。

*bDirty*<br/>
指定是否修改了属性页的字段。 如果已修改字段，则设置为 TRUE，如果未修改，则设置为 FALSE。

### <a name="return-value"></a>返回值

如果设置了指定的控件，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果在关闭属性页或选择 "应用" 按钮时，属性页控件的状态为 "已更新"，则将使用适当的值更新控件的属性。

##  <a name="setdialogresource"></a>COlePropertyPage：： SetDialogResource

设置属性页的对话框资源。

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>参数

*hDialog*<br/>
属性页的对话框资源的句柄。

##  <a name="sethelpinfo"></a>COlePropertyPage：： SetHelpInfo

指定属性页的工具提示信息、帮助文件名和帮助上下文。

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>参数

*lpszDocString*<br/>
一个字符串，其中包含要在状态栏或其他位置显示的简短帮助信息。

*lpszHelpFile*<br/>
属性页的帮助文件的名称。

*dwHelpContext*<br/>
属性页的帮助上下文。

##  <a name="setmodifiedflag"></a>COlePropertyPage：： SetModifiedFlag

指示用户是否已修改了属性页。

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>参数

*bModified*<br/>
指定属性页的已修改标志的新值。

##  <a name="setpagename"></a>COlePropertyPage：： SetPageName

设置属性页的名称，属性框架通常会在页的选项卡上显示该名称。

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>参数

*lpszPageName*<br/>
指向包含属性页名称的字符串的指针。

## <a name="see-also"></a>另请参阅

[MFC 示例 CIRC3](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
