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
ms.openlocfilehash: 51169de521997890190aab52e4afd02ed383af3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375034"
---
# <a name="coledocument-class"></a>COleDocument 类

支持可视编辑的 OLE 文档的基类。

## <a name="syntax"></a>语法

```
class COleDocument : public CDocument
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle 文档：COleDocument](#coledocument)|构造 `COleDocument` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleDocument：：添加项目](#additem)|将项添加到文档维护的项列表中。|
|[COle 文档：：应用打印设备](#applyprintdevice)|设置文档中所有客户端项的打印目标设备。|
|[COle 文档：：启用复合文件](#enablecompoundfile)|使用 OLE 结构化存储文件格式存储文档。|
|[COle 文档：获取位置活动项目](#getinplaceactiveitem)|返回当前就地处于活动状态的 OLE 项。|
|[COle 文档：获取下一个客户端项目](#getnextclientitem)|获取用于迭代的下一个客户端项。|
|[COle 文档：获取下一个项目](#getnextitem)|获取下一个文档项以进行迭代。|
|[COle 文档：获取下一个服务器项目](#getnextserveritem)|获取用于迭代的下一个服务器项。|
|[COleDocument：获取主要选定项目](#getprimaryselecteditem)|返回文档中主要选定的 OLE 项。|
|[COle 文档：获取起始位置](#getstartposition)|获取开始迭代的初始位置。|
|[COle 文档：：有空白项目](#hasblankitems)|检查文档中的空白项。|
|[COle 文档：：在显示视图](#onshowviews)|当文档变得可见或不可见时调用。|
|[COle 文档：删除项目](#removeitem)|从文档维护的项列表中删除项。|
|[COle 文档：：更新已修改的标记](#updatemodifiedflag)|如果包含的任何 OLE 项已被修改，则将文档标记为已修改。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[COle 文档：：在编辑更改图标上](#oneditchangeicon)|在"更改图标"菜单命令中处理事件。|
|[COle 文档：：打开转换](#oneditconvert)|处理嵌入或链接对象从一种类型转换为另一种类型。|
|[COleDocument：：在编辑链接上](#oneditlinks)|在"编辑"菜单上处理"链接"命令中的事件。|
|[COle 文档：：在文件发送邮件](#onfilesendmail)|发送附有文档的邮件。|
|[COle 文档：：更新编辑更改图标](#onupdateeditchangeicon)|由框架调用以更新"编辑/更改图标"菜单选项的命令 UI。|
|[COle 文档：：更新链接菜单](#onupdateeditlinksmenu)|由框架调用以更新"编辑/链接"菜单选项的命令 UI。|
|[COleDocument：：更新对象Verbmenu](#onupdateobjectverbmenu)|由框架调用以更新"编辑/*对象名称"* 菜单选项的命令 UI，以及从"编辑/*对象名称*"访问的 Verb 子菜单。|
|[COle 文档：：更新粘贴链接菜单](#onupdatepastelinkmenu)|由框架调用以更新"粘贴特殊"菜单选项的命令 UI。|
|[COle 文档：：更新粘贴菜单](#onupdatepastemenu)|由框架调用以更新"粘贴"菜单选项的命令 UI。|

## <a name="remarks"></a>备注

`COleDocument`派生自`CDocument`，它允许 OLE 应用程序使用 Microsoft 基础类库提供的文档/视图体系结构。

`COleDocument`将文档视为处理 OLE 项的[CDocItem](../../mfc/reference/cdocitem-class.md)对象的集合。 容器和服务器应用程序都需要这样的体系结构，因为它们的文档必须能够包含 OLE 项。 [COleServerItem](../../mfc/reference/coleserveritem-class.md)和[COleClientItem](../../mfc/reference/coleclientitem-class.md)类都派生`CDocItem`自 ，管理应用程序和 OLE 项之间的交互。

如果要编写一个简单的容器应用程序，请从`COleDocument`派生文档类。 如果要编写一个容器应用程序，该应用程序支持链接到其文档中包含的嵌入项，请从[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)派生您的文档类。 如果要编写服务器应用程序或组合容器/服务器，请从[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)派生文档类。 `COleLinkingDoc``COleServerDoc`派生`COleDocument`自 ，因此这些类继承 和`COleDocument``CDocument`中提供的所有服务。

要使用`COleDocument`派生类，并添加用于管理应用程序的非 OLE 数据以及嵌入或链接项的功能。 如果定义`CDocItem`派生类以存储应用程序的本机数据，则可以使用 定义的`COleDocument`默认实现来存储 OLE 和非 OLE 数据。 您还可以设计自己的数据结构，以便将非 OLE 数据与 OLE 项分开存储。 有关详细信息，请参阅文章[容器：复合文件](../../mfc/containers-compound-files.md).

`CDocument`支持通过邮件支持 （MAPI） 发送文档。 `COleDocument`已更新[OnFileSendMail](#onfilesendmail)以正确处理复合文档。 有关详细信息，请参阅 MFC 中的[MAPI](../../mfc/mapi.md)和[MAPI 支持](../../mfc/mapi-support-in-mfc.md)文章 。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="coledocumentadditem"></a><a name="additem"></a>COleDocument：：添加项目

调用此函数以向文档添加项。

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要添加的文档项的指针。

### <a name="remarks"></a>备注

当 接受指向文档的指针的`COleClientItem`或`COleServerItem`构造函数调用此函数时，不需要显式调用它。

## <a name="coledocumentapplyprintdevice"></a><a name="applyprintdevice"></a>COle 文档：：应用打印设备

调用此函数可更改应用程序容器文档中所有嵌入式[COleClientItem 项目的](../../mfc/reference/coleclientitem-class.md)打印目标设备。

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>参数

*ptd*<br/>
指向数据结构`DVTARGETDEVICE`的指针，其中包含有关新打印目标设备的信息。 可以为 NULL。

*Ppd*<br/>
指向数据结构`PRINTDLG`的指针，其中包含有关新打印目标设备的信息。 可以为 NULL。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0。

### <a name="remarks"></a>备注

此函数更新所有项目的打印目标设备，但不会刷新这些项目的演示文稿缓存。 要更新项目的演示文稿缓存，请致电[COleClientItem：：更新链接](../../mfc/reference/coleclientitem-class.md#updatelink)。

此函数的参数包含 OLE 用于标识目标设备的信息。 [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)结构包含 Windows 用于初始化公共打印对话框的信息。 用户关闭对话框后，Windows 将返回有关用户在此结构中选择的信息。 `m_pd` [CPrintDialog](../../mfc/reference/cprintdialog-class.md)对象的成员是一个`PRINTDLG`结构。

有关详细信息，请参阅 Windows SDK 中的[PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)结构。

有关详细信息，请参阅 Windows SDK 中的[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)结构。

## <a name="coledocumentcoledocument"></a><a name="coledocument"></a>COle 文档：COleDocument

构造 `COleDocument` 对象。

```
COleDocument();
```

## <a name="coledocumentenablecompoundfile"></a><a name="enablecompoundfile"></a>COle 文档：：启用复合文件

如果要使用复合文件格式存储文档，请调用此函数。

```
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
指定是启用还是禁用复合文件支持。

### <a name="remarks"></a>备注

这也称为结构化存储。 通常从`COleDocument`派生类的构造函数调用此函数。 有关复合文档的详细信息，请参阅文章["容器：复合文件](../../mfc/containers-compound-files.md)"。

如果不调用此成员函数，文档将以非结构化（"平面"）文件格式存储。

为文档启用或禁用复合文件支持后，不应在文档的生存期内更改设置。

## <a name="coledocumentgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>COle 文档：获取位置活动项目

调用此函数，获取当前在包含*pWnd*标识的视图的帧窗口中当前激活的 OLE 项。

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向显示容器文档的窗口的指针。

### <a name="return-value"></a>返回值

指向单个、就地活动 OLE 项的指针;如果当前没有 OLE 项处于"就地活动"状态，则为 NULL。

## <a name="coledocumentgetnextclientitem"></a><a name="getnextclientitem"></a>COle 文档：获取下一个客户端项目

重复调用此函数以访问文档中的每个客户端项。

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>参数

*Pos*<br/>
对由上一个调用 为 设置的定位`GetNextClientItem`值的引用。成员函数返回`GetStartPosition`初始值。

### <a name="return-value"></a>返回值

指向文档中下一个客户端项的指针，如果没有更多的客户端项，则指向 NULL。

### <a name="remarks"></a>备注

每次调用后，为文档中的下一个项设置*pos*值，该项可能是客户端项，也可能不是客户端项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

## <a name="coledocumentgetnextitem"></a><a name="getnextitem"></a>COle 文档：获取下一个项目

重复调用此函数以访问文档中的每个项目。

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>参数

*Pos*<br/>
对由上一个调用 为 设置的定位`GetNextItem`值的引用。成员函数返回`GetStartPosition`初始值。

### <a name="return-value"></a>返回值

指向指定位置的文档项的指针。

### <a name="remarks"></a>备注

每次调用后 *，pos*值将设置为文档中下一项的"位置"值。 如果检索到的元素是文档中的最后一个元素，则*pos*的新值为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

## <a name="coledocumentgetnextserveritem"></a><a name="getnextserveritem"></a>COle 文档：获取下一个服务器项目

重复调用此函数以访问文档中的每个服务器项。

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>参数

*Pos*<br/>
对由上一个调用 为 设置的定位`GetNextServerItem`值的引用。成员函数返回`GetStartPosition`初始值。

### <a name="return-value"></a>返回值

指向文档中下一个服务器项的指针，如果没有更多的服务器项，则指向 NULL。

### <a name="remarks"></a>备注

每次调用后，为文档中的下一个项设置*pos*值，该项可能是服务器项，也可能不是服务器项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

## <a name="coledocumentgetprimaryselecteditem"></a><a name="getprimaryselecteditem"></a>COleDocument：获取主要选定项目

由框架调用以检索指定视图中当前选定的 OLE 项。

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>参数

*pView*<br/>
指向显示文档的活动视图对象的指针。

### <a name="return-value"></a>返回值

指向单个所选 OLE 项的指针;如果未选择 OLE 项或选择多个 OLE 项，则为 NULL。

### <a name="remarks"></a>备注

默认实现搜索单个选定项包含的 OLE 项的列表，并返回指向它的指针。 如果没有选择任何项，或者有多个项目被选中，则函数将返回 NULL。 您必须重写视图类`CView::IsSelected`中的成员函数，才能工作。 如果您有自己的方法来存储包含的 OLE 项，请重写此函数。

## <a name="coledocumentgetstartposition"></a><a name="getstartposition"></a>COle 文档：获取起始位置

调用此函数以获取文档中第一个项目的位置。

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>返回值

可用于开始遍历文档项的"位置"值;如果文档没有项目，则为 NULL。

### <a name="remarks"></a>备注

将返回的值传递给`GetNextItem`或`GetNextClientItem`。 `GetNextServerItem`

## <a name="coledocumenthasblankitems"></a><a name="hasblankitems"></a>COle 文档：：有空白项目

调用此函数以确定文档是否包含任何空白项。

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>返回值

如果文档包含任何空白项，则非零;否则 0。

### <a name="remarks"></a>备注

空白项是其矩形为空的项目。

## <a name="coledocumentoneditchangeicon"></a><a name="oneditchangeicon"></a>COle 文档：：在编辑更改图标上

显示 OLE 更改图标对话框，并将表示当前选择的 OLE 项的图标更改为用户在对话框中选择的图标。

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>备注

`OnEditChangeIcon`创建并启动`COleChangeIconDialog`"更改图标"对话框。

## <a name="coledocumentoneditconvert"></a><a name="oneditconvert"></a>COle 文档：：打开转换

显示 OLE 转换对话框，并根据对话框中的用户选择转换或激活当前选定的 OLE 项目。

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>备注

`OnEditConvert`创建并启动`COleConvertDialog`"转换"对话框。

转换的一个示例是将 Microsoft Word 文档转换为 WordPad 文档。

## <a name="coledocumentoneditlinks"></a><a name="oneditlinks"></a>COleDocument：：在编辑链接上

显示"OLE 编辑/链接"对话框。

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>备注

`OnEditLinks`创建并启动"`COleLinksDialog`链接"对话框，该对话框允许用户更改链接的对象。

## <a name="coledocumentonfilesendmail"></a><a name="onfilesendmail"></a>COle 文档：：在文件发送邮件

通过驻留邮件主机（如果有）发送邮件，并将文档作为附件。

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>备注

`OnFileSendMail`调用`OnSaveDocument`序列化（保存）无标题和修改的文档到临时文件，然后通过电子邮件发送。 如果文档尚未修改，则不需要临时文件;因此，不需要临时文件。原始文件已发送。 `OnFileSendMail`加载 MAPI32。尚未加载 DLL。

与`OnFileSendMail`的`CDocument`实现不同，此函数正确处理复合文件。

有关详细信息，请参阅 MFC 文章中的[MAPI 主题](../../mfc/mapi.md)和[MAPI 支持](../../mfc/mapi-support-in-mfc.md)。

## <a name="coledocumentonshowviews"></a><a name="onshowviews"></a>COle 文档：：在显示视图

在文档的可见性状态更改后，框架调用此函数。

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>参数

*b可见*<br/>
指示文档是可见的还是不可见的。

### <a name="remarks"></a>备注

此函数的默认版本不执行任何操作。 如果应用程序必须在文档的可见性更改时执行任何特殊处理，请覆盖它。

## <a name="coledocumentonupdateeditchangeicon"></a><a name="onupdateeditchangeicon"></a>COle 文档：：更新编辑更改图标

由框架调用以更新"编辑"菜单上的"更改图标"命令。

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向表示生成更新`CCmdUI`命令的菜单的结构的指针。 更新处理程序通过`Enable`*pCmdUI* `CCmdUI`调用结构的成员函数以更新用户界面。

### <a name="remarks"></a>备注

`OnUpdateEditChangeIcon`更新命令的用户界面，具体取决于文档中是否存在有效的图标。 重写此函数以更改行为。

## <a name="coledocumentonupdateeditlinksmenu"></a><a name="onupdateeditlinksmenu"></a>COle 文档：：更新链接菜单

由框架调用以更新"编辑"菜单上的"链接"命令。

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向表示生成更新`CCmdUI`命令的菜单的结构的指针。 更新处理程序通过`Enable`*pCmdUI* `CCmdUI`调用结构的成员函数以更新用户界面。

### <a name="remarks"></a>备注

从文档中的第一个 OLE 项开始`OnUpdateEditLinksMenu`，访问每个项，测试该项是否为链接，如果是链接，则启用 Links 命令。 重写此函数以更改行为。

## <a name="coledocumentonupdateobjectverbmenu"></a><a name="onupdateobjectverbmenu"></a>COleDocument：：更新对象Verbmenu

由框架调用以更新"编辑"菜单上*的 ObjectName*命令，以及从*ObjectName*命令访问的 Verb 子菜单，其中*ObjectName*是嵌入在文档中的 OLE 对象的名称。

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向表示生成更新`CCmdUI`命令的菜单的结构的指针。 更新处理程序通过`Enable`*pCmdUI* `CCmdUI`调用结构的成员函数以更新用户界面。

### <a name="remarks"></a>备注

`OnUpdateObjectVerbMenu`更新*ObjectName*命令的用户界面，具体取决于文档中是否存在有效对象。 如果存在对象，则启用"编辑"菜单上*的对象名称*命令。 选择此菜单命令时，将显示"动词子菜单"。 "动词"子菜单包含可用于对象的所有谓词命令，如"编辑"、"属性"等。 重写此函数以更改行为。

## <a name="coledocumentonupdatepastelinkmenu"></a><a name="onupdatepastelinkmenu"></a>COle 文档：：更新粘贴链接菜单

由框架调用以确定是否可以从剪贴板粘贴链接的 OLE 项。

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向表示生成更新`CCmdUI`命令的菜单的结构的指针。 更新处理程序通过`Enable`*pCmdUI* `CCmdUI`调用结构的成员函数以更新用户界面。

### <a name="remarks"></a>备注

根据项目是否可以粘贴到文档中，启用或禁用"粘贴特殊"菜单命令。

## <a name="coledocumentonupdatepastemenu"></a><a name="onupdatepastemenu"></a>COle 文档：：更新粘贴菜单

由框架调用以确定是否可以从剪贴板粘贴嵌入的 OLE 项。

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向表示生成更新`CCmdUI`命令的菜单的结构的指针。 更新处理程序通过`Enable`*pCmdUI* `CCmdUI`调用结构的成员函数以更新用户界面。

### <a name="remarks"></a>备注

"粘贴"菜单命令和按钮已启用或禁用，具体取决于项目是否可以粘贴到文档中。

## <a name="coledocumentremoveitem"></a><a name="removeitem"></a>COle 文档：删除项目

调用此函数从文档中删除项目。

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要删除的文档项的指针。

### <a name="remarks"></a>备注

您通常不需要显式调用此函数;因此，您不需要显式调用此函数。它由`COleClientItem`和`COleServerItem`的析构函数调用。

## <a name="coledocumentupdatemodifiedflag"></a><a name="updatemodifiedflag"></a>COle 文档：：更新已修改的标记

如果包含的任何 OLE 项已被修改，请调用此函数将文档标记为已修改。

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>备注

这允许框架提示用户在关闭之前保存文档，即使文档中的本机数据尚未修改也是如此。

## <a name="see-also"></a>另请参阅

[MFC 样品容器](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
