---
title: COlePropertyPage 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7db08ae9b9c2899709f4c6511478714869475ae7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386426"
---
# <a name="colepropertypage-class"></a>COlePropertyPage 类

用于在图形界面（类似于对话框）中显示自定义控件的属性。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
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
|[COlePropertyPage::OnHelp](#onhelp)|当用户调用帮助时由框架调用。|
|[COlePropertyPage::OnInitDialog](#oninitdialog)|初始化的属性页时，由框架调用。|
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|选择具有新属性的另一个 OLE 控件时由框架调用。|
|[COlePropertyPage::OnSetPageSite](#onsetpagesite)|当属性框架提供页面的站点时由框架调用。|
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|设置一个标志，指示用户是否已修改控件中的值。|
|[COlePropertyPage::SetDialogResource](#setdialogresource)|设置属性页对话框资源。|
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|设置属性页的简短帮助文本、 其帮助文件和其帮助上下文的名称。|
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|设置一个标志，指示用户是否已修改的属性页。|
|[COlePropertyPage::SetPageName](#setpagename)|设置属性页的名称 （标题）。|

## <a name="remarks"></a>备注

例如，属性页可能包括允许用户查看和修改控件的标题属性的编辑控件。

每个自定义或库存控制属性可以具有控件的用户可以查看当前属性值并根据需要修改该值的对话框控件。

有关使用的详细信息`COlePropertyPage`，请参阅文章[ActiveX 控件： 属性页](../../mfc/mfc-activex-controls-property-pages.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>要求

**标头：** afxctl.h

##  <a name="colepropertypage"></a>  COlePropertyPage::COlePropertyPage

构造 `COlePropertyPage` 对象。

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>参数

*idDlg*<br/>
在对话框模板资源 ID。

*idCaption*<br/>
属性页的标题的资源 ID。

### <a name="remarks"></a>备注

当您实现的子类`COlePropertyPage`，子类的构造函数应使用`COlePropertyPage`构造函数，以标识的对话框模板资源上它的属性页为基础，并包含其标题的字符串资源。

##  <a name="getcontrolstatus"></a>  COlePropertyPage::GetControlStatus

确定用户是否已修改的值的属性页控件指定的资源 id。

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
资源 ID 的属性页控件。

### <a name="return-value"></a>返回值

如果控件值已修改，则为 TRUE否则为 FALSE。

##  <a name="getobjectarray"></a>  COlePropertyPage::GetObjectArray

返回正在编辑的属性页的对象的数组。

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>参数

*pnObjects*<br/>
指向将接收所编辑的页的对象数的无符号长整数的指针。

### <a name="return-value"></a>返回值

指向数组的指针`IDispatch`指针，用于访问属性页上的每个控件的属性。 调用方必须释放这些接口指针。

### <a name="remarks"></a>备注

每个属性页对象维护指向的指针的数组`IDispatch`正在编辑的页的对象的接口。 此函数将其*pnObjects*该数组中的元素数目的参数和返回指向数组的第一个元素的指针。

##  <a name="getpagesite"></a>  COlePropertyPage::GetPageSite

获取一个指针指向的属性页`IPropertyPageSite`接口。

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>返回值

指向属性页的`IPropertyPageSite`接口。

### <a name="remarks"></a>备注

控件与容器的协作，以便用户可以浏览和编辑控件属性。 此控件提供属性页，其中每个是允许用户编辑一组相关的属性的 OLE 对象。 容器提供了显示的属性页的属性帧。 对于每个页中，属性框架提供支持的页站点`IPropertyPageSite`接口。

##  <a name="ignoreapply"></a>  COlePropertyPage::IgnoreApply

确定哪些控件不能将应用按钮。

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
若要忽略的控件 ID。

### <a name="remarks"></a>备注

仅当属性页控件的值已更改时，才启用属性页的应用按钮。 使用此函数指定不会导致其值更改时启用应用按钮的控件。

##  <a name="ismodified"></a>  COlePropertyPage::IsModified

确定用户是否已更改的属性页上的任何值。

```
BOOL IsModified();
```

### <a name="return-value"></a>返回值

如果已修改的属性页，则为 TRUE。

##  <a name="oneditproperty"></a>  COlePropertyPage::OnEditProperty

若要对其进行编辑的特定属性时，框架将调用此函数。

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>参数

*dispid*<br/>
正在编辑的属性的调度 ID。

### <a name="return-value"></a>返回值

默认实现将返回 FALSE。 重写此函数应返回 TRUE。

### <a name="remarks"></a>备注

可以重写它以将焦点设置到的页上的相应控件。 默认实现不执行任何操作，并返回 FALSE。

##  <a name="onhelp"></a>  COlePropertyPage::OnHelp

当用户请求的联机帮助时，框架将调用此函数。

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>参数

*lpszHelpDir*<br/>
包含属性页的帮助文件的目录。

### <a name="return-value"></a>返回值

默认实现将返回 FALSE。

### <a name="remarks"></a>备注

如果属性页必须执行的任何特殊操作，在用户访问帮助时，重写它。 默认实现不执行任何操作，并将返回 FALSE，这会指示框架调用 WinHelp。

##  <a name="oninitdialog"></a>  COlePropertyPage::OnInitDialog

初始化属性页的对话框时，框架将调用此函数。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

默认实现将返回 FALSE。

### <a name="remarks"></a>备注

如果初始化对话框时，不需要执行任何特殊操作，请将其覆盖。 默认实现将调用`CDialog::OnInitDialog`，返回 FALSE。

##  <a name="onobjectschanged"></a>  COlePropertyPage::OnObjectsChanged

选择具有新属性的另一个 OLE 控件时由框架调用。

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>备注

当开发人员环境中查看 OLE 控件的属性，无模式对话框用于显示其属性页。 如果选择另一个控件，则一组不同的属性页必须显示为一组新的属性。 框架调用此函数，以通知此更改的属性页。

重写此函数可接收此操作的通知和执行任何特殊操作。

##  <a name="onsetpagesite"></a>  COlePropertyPage::OnSetPageSite

当属性框架提供的属性页的页站点时，框架将调用此函数。

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>备注

默认实现将加载页面的标题，并会尝试确定从对话框资源的页面的大小。 如果属性页面所需任何进一步的操作; 重写此函数重写应调用基类实现。

##  <a name="setcontrolstatus"></a>  COlePropertyPage::SetControlStatus

属性页控件状态更改。

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>参数

*nID*<br/>
包含的属性页控件的 ID。

*bDirty*<br/>
指定是否已修改的属性页字段。 如果该字段已被修改，FALSE 如果它未被修改，则设置为 TRUE。

### <a name="return-value"></a>返回值

设置指定的控件; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

如果关闭属性页或选择应用按钮时，属性页控件的状态已更新，将使用适当的值更新控件的属性。

##  <a name="setdialogresource"></a>  COlePropertyPage::SetDialogResource

设置属性页对话框资源。

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>参数

*hDialog*<br/>
属性页对话框资源的句柄。

##  <a name="sethelpinfo"></a>  COlePropertyPage::SetHelpInfo

指定工具提示信息、 帮助文件名和属性页的帮助上下文。

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>参数

*lpszDocString*<br/>
包含用于显示一个状态栏或其他位置中的简短帮助信息的字符串。

*lpszHelpFile*<br/>
属性页的帮助文件的名称。

*dwHelpContext*<br/>
属性页的帮助上下文。

##  <a name="setmodifiedflag"></a>  COlePropertyPage::SetModifiedFlag

指示用户是否已修改的属性页。

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>参数

*bModified*<br/>
指定的属性页修改标志的新值。

##  <a name="setpagename"></a>  COlePropertyPage::SetPageName

设置属性页的名称，通常会在页面的选项卡上显示属性框架。

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>参数

*lpszPageName*<br/>
包含属性页的名称的字符串指针。

## <a name="see-also"></a>请参阅

[MFC 示例 CIRC3](../../visual-cpp-samples.md)<br/>
[MFC 示例 TESTHELP](../../visual-cpp-samples.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
