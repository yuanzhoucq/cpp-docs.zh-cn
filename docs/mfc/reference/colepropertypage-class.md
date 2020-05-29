---
title: COle属性页类
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
ms.openlocfilehash: 872ade08438e54098da730012f98cdd906483887
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753793"
---
# <a name="colepropertypage-class"></a>COle属性页类

用于在图形界面（类似于对话框）中显示自定义控件的属性。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle属性页：COle属性页](#colepropertypage)|构造 `COlePropertyPage` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle 属性页：获取控制状态](#getcontrolstatus)|指示用户是否已修改控件中的值。|
|[COle属性页：获取对象数组](#getobjectarray)|返回属性页正在编辑的对象数组。|
|[COle属性页面：获取页面网站](#getpagesite)|返回指向属性页界面的`IPropertyPageSite`指针。|
|[COle属性页：忽略应用](#ignoreapply)|确定哪些控件不启用"应用"按钮。|
|[COle 属性页：已修改](#ismodified)|指示用户是否已修改属性页。|
|[COle属性页：编辑属性](#oneditproperty)|当用户编辑属性时由框架调用。|
|[COle属性页面：上帮助](#onhelp)|当用户调用帮助时由框架调用。|
|[COle属性页：onInitDialog](#oninitdialog)|在初始化属性页时由框架调用。|
|[COle 属性页：打开对象已更改](#onobjectschanged)|当选择另一个 OLE 控件（具有新属性）时，由框架调用。|
|[COle属性页面：在设置页面网站](#onsetpagesite)|当属性框架提供页面的站点时，由框架调用。|
|[COle 属性页：设置控制状态](#setcontrolstatus)|设置一个标志，指示用户是否已修改控件中的值。|
|[COle属性页：设置对话资源](#setdialogresource)|设置属性页的对话框资源。|
|[COle属性页面：设置帮助信息](#sethelpinfo)|设置属性页的简短帮助文本、其帮助文件的名称及其帮助上下文。|
|[COle 属性页：：设置修改后的 Flag](#setmodifiedflag)|设置指示用户是否修改了属性页的标志。|
|[COle属性页：：设置页面名称](#setpagename)|设置属性页的名称（标题）。|

## <a name="remarks"></a>备注

例如，属性页可能包含一个编辑控件，允许用户查看和修改控件的标题属性。

每个自定义控件属性都可以具有一个对话框控件，该控件允许用户查看当前属性值并根据需要修改该值。

有关 使用`COlePropertyPage`的详细信息，请参阅["ActiveX 控件：属性页](../../mfc/mfc-activex-controls-property-pages.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>要求

**标题：** afxctl.h

## <a name="colepropertypagecolepropertypage"></a><a name="colepropertypage"></a>COle属性页：COle属性页

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

实现 子`COlePropertyPage`类的子类时，子类的构造函数应使用`COlePropertyPage`构造函数来标识属性页所基于的对话框模板资源和包含其标题的字符串资源。

## <a name="colepropertypagegetcontrolstatus"></a><a name="getcontrolstatus"></a>COle 属性页：获取控制状态

确定用户是否已使用指定的资源 ID 修改属性页控件的值。

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
属性页控件的资源 ID。

### <a name="return-value"></a>返回值

如果控件值已被修改，则为 TRUE;否则 FALSE。

## <a name="colepropertypagegetobjectarray"></a><a name="getobjectarray"></a>COle属性页：获取对象数组

返回属性页正在编辑的对象数组。

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>参数

*pn对象*<br/>
指向未签名的长整数的指针，该整数将接收页面正在编辑的对象数。

### <a name="return-value"></a>返回值

指向指针数组的`IDispatch`指针，用于访问属性页上每个控件的属性。 调用方不得释放这些接口指针。

### <a name="remarks"></a>备注

每个属性页对象都维护指向页面正在编辑的对象`IDispatch`的接口的指针数组。 此函数将其*pnObjects*参数设置为该数组中的元素数，并返回指向数组第一个元素的指针。

## <a name="colepropertypagegetpagesite"></a><a name="getpagesite"></a>COle属性页面：获取页面网站

获取指向属性页界面的`IPropertyPageSite`指针。

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>返回值

指向属性页界面的`IPropertyPageSite`指针。

### <a name="remarks"></a>备注

控件和容器相互配合，以便用户可以浏览和编辑控件属性。 该控件提供属性页，每个属性页都是一个 OLE 对象，允许用户编辑一组相关的属性。 容器提供显示属性页的属性框架。 对于每个页面，属性框架提供一个页面站点，该页站点`IPropertyPageSite`支持该接口。

## <a name="colepropertypageignoreapply"></a><a name="ignoreapply"></a>COle属性页：忽略应用

确定哪些控件不启用"应用"按钮。

```cpp
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
要忽略的控件的 ID。

### <a name="remarks"></a>备注

仅当更改属性页控件的值时，才启用属性页的"应用"按钮。 使用此函数可以指定在值更改时不会启用"应用"按钮的控件。

## <a name="colepropertypageismodified"></a><a name="ismodified"></a>COle 属性页：已修改

确定用户是否已更改属性页上的任何值。

```
BOOL IsModified();
```

### <a name="return-value"></a>返回值

如果属性页已被修改，则为 TRUE。

## <a name="colepropertypageoneditproperty"></a><a name="oneditproperty"></a>COle属性页：编辑属性

当要编辑特定属性时，框架将调用此函数。

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>参数

*不一部分*<br/>
要编辑的属性的调度 ID。

### <a name="return-value"></a>返回值

默认实现返回 FALSE。 此函数的重写应返回 TRUE。

### <a name="remarks"></a>备注

您可以重写它，将焦点设置为页面上的相应控件。 默认实现不执行任何操作，并返回 FALSE。

## <a name="colepropertypageonhelp"></a><a name="onhelp"></a>COle属性页面：上帮助

当用户请求联机帮助时，框架将调用此功能。

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>参数

*lpszHelpDir*<br/>
包含属性页帮助文件的目录。

### <a name="return-value"></a>返回值

默认实现返回 FALSE。

### <a name="remarks"></a>备注

如果属性页必须在用户访问帮助时执行任何特殊操作，请覆盖它。 默认实现不执行任何操作，并返回 FALSE，它指示框架调用 WinHelp。

## <a name="colepropertypageoninitdialog"></a><a name="oninitdialog"></a>COle属性页：onInitDialog

在初始化属性页的对话框时，框架将调用此函数。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

默认实现返回 FALSE。

### <a name="remarks"></a>备注

如果对话框初始化时需要任何特殊操作，则覆盖它。 默认实现调用`CDialog::OnInitDialog`并返回 FALSE。

## <a name="colepropertypageonobjectschanged"></a><a name="onobjectschanged"></a>COle 属性页：打开对象已更改

当选择另一个 OLE 控件（具有新属性）时，由框架调用。

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>备注

在开发人员环境中查看 OLE 控件的属性时，将使用无模式对话框来显示其属性页。 如果选择了另一个控件，则必须为新属性集显示一组不同的属性页。 框架调用此函数以通知更改的属性页。

重写此函数以接收此操作的通知并执行任何特殊操作。

## <a name="colepropertypageonsetpagesite"></a><a name="onsetpagesite"></a>COle属性页面：在设置页面网站

当属性框架提供属性页的页面站点时，框架将调用此函数。

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>备注

默认实现加载页面的标题，并尝试从对话框资源确定页面的大小。 如果属性页需要任何进一步操作，请覆盖此函数;重写应调用基类实现。

## <a name="colepropertypagesetcontrolstatus"></a><a name="setcontrolstatus"></a>COle 属性页：设置控制状态

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
指定属性页的字段是否已被修改。 如果字段已被修改，则设置为 TRUE;如果未修改该字段，则为 FALSE。

### <a name="return-value"></a>返回值

如果设置了指定的控件，则为 TRUE;如果设置了指定的控件。否则 FALSE。

### <a name="remarks"></a>备注

如果在关闭属性页或选择"应用"按钮时属性页控件的状态为脏，则控件的属性将使用相应的值进行更新。

## <a name="colepropertypagesetdialogresource"></a><a name="setdialogresource"></a>COle属性页：设置对话资源

设置属性页的对话框资源。

```cpp
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>参数

*h对话*<br/>
处理属性页的对话框资源。

## <a name="colepropertypagesethelpinfo"></a><a name="sethelpinfo"></a>COle属性页面：设置帮助信息

指定工具提示信息、帮助文件名和属性页的帮助上下文。

```cpp
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>参数

*lpszDocString*<br/>
包含用于在状态栏或其他位置显示的简短帮助信息的字符串。

*lpszHelp文件*<br/>
属性页帮助文件的名称。

*dwHelpContext*<br/>
属性页的帮助上下文。

## <a name="colepropertypagesetmodifiedflag"></a><a name="setmodifiedflag"></a>COle 属性页：：设置修改后的 Flag

指示用户是否已修改属性页。

```cpp
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>参数

*b 修改*<br/>
指定属性页已修改标志的新值。

## <a name="colepropertypagesetpagename"></a><a name="setpagename"></a>COle属性页：：设置页面名称

设置属性页的名称，属性框架通常会显示在页面的选项卡上。

```cpp
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>参数

*lpszPage名称*<br/>
指向包含属性页名称的字符串的指针。

## <a name="see-also"></a>请参阅

[MFC 样品 CIRC3](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品测试](../../overview/visual-cpp-samples.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
