---
title: COleDocument 类
ms.date: 11/04/2016
f1_keywords:
- COleDocument
- AFXOLE/COleDocument
- AFXOLE/COleDocument::COleDocument
- AFXOLE/COleDocument::AddItem
- AFXOLE/COleDocument::ApplyPrintDevice
- AFXOLE/COleDocument::EnableCompoundFile
- AFXOLE/COleDocument::GetInPlaceActiveItem
- AFXOLE/COleDocument::GetNextClientItem
- AFXOLE/COleDocument::GetNextItem
- AFXOLE/COleDocument::GetNextServerItem
- AFXOLE/COleDocument::GetPrimarySelectedItem
- AFXOLE/COleDocument::GetStartPosition
- AFXOLE/COleDocument::HasBlankItems
- AFXOLE/COleDocument::OnShowViews
- AFXOLE/COleDocument::RemoveItem
- AFXOLE/COleDocument::UpdateModifiedFlag
- AFXOLE/COleDocument::OnEditChangeIcon
- AFXOLE/COleDocument::OnEditConvert
- AFXOLE/COleDocument::OnEditLinks
- AFXOLE/COleDocument::OnFileSendMail
- AFXOLE/COleDocument::OnUpdateEditChangeIcon
- AFXOLE/COleDocument::OnUpdateEditLinksMenu
- AFXOLE/COleDocument::OnUpdateObjectVerbMenu
- AFXOLE/COleDocument::OnUpdatePasteLinkMenu
- AFXOLE/COleDocument::OnUpdatePasteMenu
helpviewer_keywords:
- COleDocument [MFC], COleDocument
- COleDocument [MFC], AddItem
- COleDocument [MFC], ApplyPrintDevice
- COleDocument [MFC], EnableCompoundFile
- COleDocument [MFC], GetInPlaceActiveItem
- COleDocument [MFC], GetNextClientItem
- COleDocument [MFC], GetNextItem
- COleDocument [MFC], GetNextServerItem
- COleDocument [MFC], GetPrimarySelectedItem
- COleDocument [MFC], GetStartPosition
- COleDocument [MFC], HasBlankItems
- COleDocument [MFC], OnShowViews
- COleDocument [MFC], RemoveItem
- COleDocument [MFC], UpdateModifiedFlag
- COleDocument [MFC], OnEditChangeIcon
- COleDocument [MFC], OnEditConvert
- COleDocument [MFC], OnEditLinks
- COleDocument [MFC], OnFileSendMail
- COleDocument [MFC], OnUpdateEditChangeIcon
- COleDocument [MFC], OnUpdateEditLinksMenu
- COleDocument [MFC], OnUpdateObjectVerbMenu
- COleDocument [MFC], OnUpdatePasteLinkMenu
- COleDocument [MFC], OnUpdatePasteMenu
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
ms.openlocfilehash: b92c796fdaa972966dcbfa85b1e34f267b6c629c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741599"
---
# <a name="coledocument-class"></a>COleDocument 类

支持可视编辑的 OLE 文档的基类。

## <a name="syntax"></a>语法

```
class COleDocument : public CDocument
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleDocument::COleDocument](#coledocument)|构造 `COleDocument` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleDocument::AddItem](#additem)|将一个项添加到文档所维护的项的列表中。|
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|为文档中的所有客户端项设置打印目标设备。|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|导致使用 OLE 结构化存储文件格式存储文档。|
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|返回当前就地活动的 OLE 项。|
|[COleDocument::GetNextClientItem](#getnextclientitem)|获取用于循环访问的下一个客户端项。|
|[COleDocument::GetNextItem](#getnextitem)|获取用于循环访问的下一个文档项。|
|[COleDocument::GetNextServerItem](#getnextserveritem)|获取用于循环访问的下一个服务器项。|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|返回文档中主选定的 OLE 项。|
|[COleDocument::GetStartPosition](#getstartposition)|获取开始迭代的初始位置。|
|[COleDocument::HasBlankItems](#hasblankitems)|检查文档中是否有空白项。|
|[COleDocument::OnShowViews](#onshowviews)|当文档变为可见或不可见时调用。|
|[COleDocument::RemoveItem](#removeitem)|从文档维护的项列表中移除一个项。|
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|如果已修改任何包含的 OLE 项，则将文档标记为已修改。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|处理更改图标菜单命令中的事件。|
|[COleDocument::OnEditConvert](#oneditconvert)|处理嵌入对象或链接对象从一种类型到另一种类型的转换。|
|[COleDocument::OnEditLinks](#oneditlinks)|在 "编辑" 菜单上的 "链接" 命令中处理事件。|
|[COleDocument::OnFileSendMail](#onfilesendmail)|发送附加了文档的邮件。|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|由框架调用，以更新 "编辑/更改" 图标菜单选项的命令 UI。|
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|由框架调用，以更新 "编辑/链接" 菜单选项的命令 UI。|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|由框架调用，以更新编辑/ *objectname*菜单选项的命令 UI，以及从 Edit/ *Objectname*访问的谓词子菜单。|
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|由框架调用，以更新 "选择性粘贴" 菜单选项的命令 UI。|
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|由框架调用，以更新 "粘贴" 菜单选项的命令 UI。|

## <a name="remarks"></a>备注

`COleDocument`派生自`CDocument`，这允许 OLE 应用程序使用由 Microsoft 基础类库提供的文档/视图体系结构。

`COleDocument`将文档视为用于处理 OLE 项的[CDocItem](../../mfc/reference/cdocitem-class.md)对象的集合。 容器和服务器应用程序都需要此类体系结构，因为其文档必须能够包含 OLE 项。 派生自`CDocItem`的 [COleServerItem](../../mfc/reference/coleserveritem-class.md) 和[COleClientItem](../../mfc/reference/coleclientitem-class.md)类管理应用程序和 OLE 项之间的交互。

如果要编写简单的容器应用程序，请从`COleDocument`派生文档类。 如果要编写支持链接到文档包含的嵌入项的容器应用程序，请从[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)派生文档类。 如果要编写服务器应用程序或组合容器/服务器，请从[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)派生文档类。 `COleLinkingDoc`和`COleServerDoc`派生自`COleDocument`，因此这些类继承和`CDocument`中`COleDocument`可用的所有服务。

若要`COleDocument`使用，请从其派生一个类，并添加用于管理应用程序的非 OLE 数据以及嵌入项或链接项的功能。 如果定义`CDocItem`派生类来存储应用程序的本机数据，则可以使用`COleDocument`定义的默认实现来存储 OLE 和非 OLE 数据。 你还可以设计自己的数据结构，以便将非 OLE 数据与 OLE 项分开存储。 有关详细信息，请参阅文章[容器：复合文件](../../mfc/containers-compound-files.md)。

`CDocument`如果邮件支持（MAPI）存在，则支持通过邮件发送文档。 `COleDocument`已更新[OnFileSendMail](#onfilesendmail) ，可正确处理复合文档。 有关详细信息，请参阅文章 MFC 中的[mapi](../../mfc/mapi.md)和[mapi 支持](../../mfc/mapi-support-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>要求

**标头：** afxole

##  <a name="additem"></a>COleDocument：： AddItem

调用此函数可向文档中添加项。

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向所添加文档项的指针。

### <a name="remarks"></a>备注

当接受指向文档的指针的`COleClientItem`或`COleServerItem`构造函数调用此函数时，无需显式调用此函数。

##  <a name="applyprintdevice"></a>COleDocument：： ApplyPrintDevice

调用此函数可在应用程序的容器文档中更改所有嵌入[COleClientItem](../../mfc/reference/coleclientitem-class.md)项的打印目标设备。

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>参数

*ptd*<br/>
指向`DVTARGETDEVICE`数据结构的指针，该结构包含有关新的打印目标设备的信息。 可以为 NULL。

*ppd*<br/>
指向`PRINTDLG`数据结构的指针，该结构包含有关新的打印目标设备的信息。 可以为 NULL。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

此函数更新所有项的打印目标设备，但不刷新这些项的表示缓存。 若要更新项目的表示缓存，请调用[COleClientItem：： UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)。

此函数的参数包含 OLE 用于标识目标设备的信息。 [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)结构包含 Windows 用于初始化常见 "打印" 对话框的信息。 用户关闭对话框后，Windows 将返回有关此结构中的用户选择的信息。 [CPrintDialog 对象](../../mfc/reference/cprintdialog-class.md)的`PRINTDLG`成员是结构。 `m_pd`

有关详细信息，请参阅 Windows SDK 中的[PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)结构。

有关详细信息，请参阅 Windows SDK 中的[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)结构。

##  <a name="coledocument"></a>COleDocument：： COleDocument

构造 `COleDocument` 对象。

```
COleDocument();
```

##  <a name="enablecompoundfile"></a>COleDocument：： EnableCompoundFile

如果要使用复合文件格式存储文档，请调用此函数。

```
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
指定是启用还是禁用复合文件支持。

### <a name="remarks"></a>备注

这也称为结构化存储。 通常从派生类的构造函数`COleDocument`调用此函数。 有关复合文档的详细信息，请参阅文章[容器：复合文件](../../mfc/containers-compound-files.md)。

如果未调用此成员函数，则文档将存储为 nonstructured （"平面"）文件格式。

为文档启用或禁用复合文件支持后，在文档的生存期内不应更改该设置。

##  <a name="getinplaceactiveitem"></a>  COleDocument::GetInPlaceActiveItem

调用此函数可获取当前在包含由*pWnd*标识的视图的框架窗口中就地激活的 OLE 项。

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向显示容器文档的窗口的指针。

### <a name="return-value"></a>返回值

指向单一就地活动 OLE 项的指针;如果当前没有 OLE 项处于 "就地活动" 状态，则为 NULL。

##  <a name="getnextclientitem"></a>COleDocument：： GetNextClientItem

重复调用此函数以访问文档中的每个客户端项。

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>参数

*位置*<br/>
对通过上一次调用`GetNextClientItem`设置的位置值的引用; 此初始值`GetStartPosition`由成员函数返回。

### <a name="return-value"></a>返回值

指向文档中的下一个客户端项的指针; 如果没有更多的客户端项，则为 NULL。

### <a name="remarks"></a>备注

每次调用后， *pos*的值都设置为文档中的下一项，这可能是也可能不是客户端项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

##  <a name="getnextitem"></a>COleDocument：： GetNextItem

重复调用此函数以访问文档中的每个项。

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>参数

*位置*<br/>
对通过上一次调用`GetNextItem`设置的位置值的引用; 此初始值`GetStartPosition`由成员函数返回。

### <a name="return-value"></a>返回值

指向位于指定位置处的文档项的指针。

### <a name="remarks"></a>备注

每次调用后， *pos*的值都设置为文档中下一项的位置值。 如果检索到的元素是文档中的最后一个元素，则*pos*的新值为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

##  <a name="getnextserveritem"></a>COleDocument：： GetNextServerItem

重复调用此函数以访问文档中的每个服务器项。

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>参数

*位置*<br/>
对通过上一次调用`GetNextServerItem`设置的位置值的引用; 此初始值`GetStartPosition`由成员函数返回。

### <a name="return-value"></a>返回值

指向文档中下一服务器项的指针; 如果没有更多的服务器项，则为 NULL。

### <a name="remarks"></a>备注

每次调用后， *pos*的值都设置为文档中的下一项，这可能是也可能不是服务器项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

##  <a name="getprimaryselecteditem"></a>COleDocument：： GetPrimarySelectedItem

由框架调用以检索指定视图中当前选定的 OLE 项。

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>参数

*pView*<br/>
指向显示文档的活动视图对象的指针。

### <a name="return-value"></a>返回值

指向单个选定的 OLE 项的指针;如果未选择 OLE 项或选择了多个 OLE 项，则为 NULL。

### <a name="remarks"></a>备注

默认实现会搜索单个选定项的包含 OLE 项列表，并返回指向它的指针。 如果未选择任何项，或者如果选择多个项，则该函数返回 NULL。 必须重写`CView::IsSelected`视图类中的成员函数，此函数才能工作。 如果你有自己的存储包含的 OLE 项的方法，请重写此函数。

##  <a name="getstartposition"></a>COleDocument：： GetStartPosition

调用此函数可获取文档中第一项的位置。

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>返回值

可用于开始遍历文档项的位置值;如果文档没有项，则为 NULL。

### <a name="remarks"></a>备注

传递返回到`GetNextItem`、 `GetNextClientItem`或`GetNextServerItem`的值。

##  <a name="hasblankitems"></a>COleDocument：： HasBlankItems

调用此函数可确定文档是否包含任何空白项。

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>返回值

如果文档包含任何空白项，则为非零值;否则为0。

### <a name="remarks"></a>备注

空白项是矩形为空的项。

##  <a name="oneditchangeicon"></a>COleDocument：： OnEditChangeIcon

显示 OLE "更改图标" 对话框，并将表示当前所选 OLE 项的图标更改为用户在对话框中选择的图标。

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>备注

`OnEditChangeIcon`创建并启动`COleChangeIconDialog` "更改图标" 对话框。

##  <a name="oneditconvert"></a>COleDocument：： OnEditConvert

显示 "OLE 转换" 对话框，并根据对话框中的用户选择，转换或激活当前选定的 OLE 项。

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>备注

`OnEditConvert`创建并启动`COleConvertDialog` "转换" 对话框。

转换的一个示例是将 Microsoft Word 文档转换为写字板文档。

##  <a name="oneditlinks"></a>COleDocument：： OnEditLinks

显示 "OLE 编辑/链接" 对话框。

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>备注

`OnEditLinks`创建并启动`COleLinksDialog` "链接" 对话框，该对话框允许用户更改链接的对象。

##  <a name="onfilesendmail"></a>  COleDocument::OnFileSendMail

通过居民邮件主机（如果有）将邮件作为附件发送。

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>备注

`OnFileSendMail`调用`OnSaveDocument`将无标题和修改的文档序列化（保存）到临时文件，然后通过电子邮件发送该文件。 如果未修改文档，则不需要临时文件;发送原始。 `OnFileSendMail`加载 MAPI32.DLL。如果尚未加载 DLL，则为。

与的实现`OnFileSendMail` `CDocument`不同，此函数将正确处理复合文件。

有关详细信息，请参阅 MFC 文章中的[Mapi 主题](../../mfc/mapi.md)和[mapi 支持](../../mfc/mapi-support-in-mfc.md)。

##  <a name="onshowviews"></a>COleDocument：： OnShowViews

框架在文档的可见性状态更改后调用此函数。

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>参数

*bVisible*<br/>
指示文档是否已变得可见或不可见。

### <a name="remarks"></a>备注

此函数的默认版本不执行任何操作。 如果你的应用程序在文档的可见性更改时必须执行任何特殊处理，则重写它。

##  <a name="onupdateeditchangeicon"></a>COleDocument：： OnUpdateEditChangeIcon

由框架调用，以更新 "编辑" 菜单上的 "更改图标" 命令。

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向`CCmdUI`结构的指针，该结构表示生成更新命令的菜单。 更新处理程序通过`Enable` *pCmdUI*调用`CCmdUI`结构的成员函数以更新用户界面。

### <a name="remarks"></a>备注

`OnUpdateEditChangeIcon`根据文档中是否存在有效的图标，更新命令的用户界面。 重写此函数以更改行为。

##  <a name="onupdateeditlinksmenu"></a>COleDocument：： OnUpdateEditLinksMenu

由框架调用，以更新 "编辑" 菜单上的 "链接" 命令。

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向`CCmdUI`结构的指针，该结构表示生成更新命令的菜单。 更新处理程序通过`Enable` *pCmdUI*调用`CCmdUI`结构的成员函数以更新用户界面。

### <a name="remarks"></a>备注

从文档中的第一个 OLE 项开始， `OnUpdateEditLinksMenu`访问每个项，测试该项是否为链接，如果是链接，则启用 "链接" 命令。 重写此函数以更改行为。

##  <a name="onupdateobjectverbmenu"></a>COleDocument：： OnUpdateObjectVerbMenu

由框架调用，以更新 "编辑" 菜单中的 " *objectname* " 命令和从*ObjectName*命令访问的谓词子菜单，其中*ObjectName*是嵌入在文档中的 OLE 对象的名称。

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向`CCmdUI`结构的指针，该结构表示生成更新命令的菜单。 更新处理程序通过`Enable` *pCmdUI*调用`CCmdUI`结构的成员函数以更新用户界面。

### <a name="remarks"></a>备注

`OnUpdateObjectVerbMenu`根据文档中是否存在有效的对象，更新*ObjectName*命令的用户界面。 如果对象存在，则会启用 "编辑" 菜单上的 " *ObjectName* " 命令。 选择此菜单命令后，将显示谓词子菜单。 谓词子菜单包含可用于对象的所有谓词命令，如编辑、属性等。 重写此函数以更改行为。

##  <a name="onupdatepastelinkmenu"></a>COleDocument：： OnUpdatePasteLinkMenu

由框架调用，用于确定是否可以从剪贴板中粘贴链接的 OLE 项。

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向`CCmdUI`结构的指针，该结构表示生成更新命令的菜单。 更新处理程序通过`Enable` *pCmdUI*调用`CCmdUI`结构的成员函数以更新用户界面。

### <a name="remarks"></a>备注

"选择性粘贴" 菜单命令是启用还是禁用的，具体取决于是否可以将项粘贴到文档中。

##  <a name="onupdatepastemenu"></a>COleDocument：： OnUpdatePasteMenu

由框架调用，用于确定是否可以从剪贴板中粘贴嵌入的 OLE 项。

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向`CCmdUI`结构的指针，该结构表示生成更新命令的菜单。 更新处理程序通过`Enable` *pCmdUI*调用`CCmdUI`结构的成员函数以更新用户界面。

### <a name="remarks"></a>备注

启用或禁用 "粘贴" 菜单命令和按钮，具体取决于是否可以将项粘贴到文档中。

##  <a name="removeitem"></a>COleDocument：： RemoveItem

调用此函数可从文档中移除项。

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要删除的文档项的指针。

### <a name="remarks"></a>备注

通常无需显式调用此函数;它由`COleClientItem`和`COleServerItem`的析构函数调用。

##  <a name="updatemodifiedflag"></a>COleDocument：： UpdateModifiedFlag

如果已修改任何包含的 OLE 项，则调用此函数可将文档标记为已修改。

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>备注

这允许框架在关闭前提示用户保存文档，即使未修改文档中的本机数据也是如此。

## <a name="see-also"></a>请参阅

[MFC 示例容器](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
