---
title: COleServerItem 类
ms.date: 11/04/2016
f1_keywords:
- COleServerItem
- AFXOLE/COleServerItem
- AFXOLE/COleServerItem::COleServerItem
- AFXOLE/COleServerItem::AddOtherClipboardData
- AFXOLE/COleServerItem::CopyToClipboard
- AFXOLE/COleServerItem::DoDragDrop
- AFXOLE/COleServerItem::GetClipboardData
- AFXOLE/COleServerItem::GetDocument
- AFXOLE/COleServerItem::GetEmbedSourceData
- AFXOLE/COleServerItem::GetItemName
- AFXOLE/COleServerItem::GetLinkSourceData
- AFXOLE/COleServerItem::GetObjectDescriptorData
- AFXOLE/COleServerItem::IsConnected
- AFXOLE/COleServerItem::IsLinkedItem
- AFXOLE/COleServerItem::NotifyChanged
- AFXOLE/COleServerItem::OnDoVerb
- AFXOLE/COleServerItem::OnDraw
- AFXOLE/COleServerItem::OnDrawEx
- AFXOLE/COleServerItem::OnGetClipboardData
- AFXOLE/COleServerItem::OnGetExtent
- AFXOLE/COleServerItem::OnInitFromData
- AFXOLE/COleServerItem::OnQueryUpdateItems
- AFXOLE/COleServerItem::OnRenderData
- AFXOLE/COleServerItem::OnRenderFileData
- AFXOLE/COleServerItem::OnRenderGlobalData
- AFXOLE/COleServerItem::OnSetColorScheme
- AFXOLE/COleServerItem::OnSetData
- AFXOLE/COleServerItem::OnSetExtent
- AFXOLE/COleServerItem::OnUpdate
- AFXOLE/COleServerItem::OnUpdateItems
- AFXOLE/COleServerItem::SetItemName
- AFXOLE/COleServerItem::GetDataSource
- AFXOLE/COleServerItem::OnHide
- AFXOLE/COleServerItem::OnOpen
- AFXOLE/COleServerItem::OnShow
- AFXOLE/COleServerItem::m_sizeExtent
helpviewer_keywords:
- COleServerItem [MFC], COleServerItem
- COleServerItem [MFC], AddOtherClipboardData
- COleServerItem [MFC], CopyToClipboard
- COleServerItem [MFC], DoDragDrop
- COleServerItem [MFC], GetClipboardData
- COleServerItem [MFC], GetDocument
- COleServerItem [MFC], GetEmbedSourceData
- COleServerItem [MFC], GetItemName
- COleServerItem [MFC], GetLinkSourceData
- COleServerItem [MFC], GetObjectDescriptorData
- COleServerItem [MFC], IsConnected
- COleServerItem [MFC], IsLinkedItem
- COleServerItem [MFC], NotifyChanged
- COleServerItem [MFC], OnDoVerb
- COleServerItem [MFC], OnDraw
- COleServerItem [MFC], OnDrawEx
- COleServerItem [MFC], OnGetClipboardData
- COleServerItem [MFC], OnGetExtent
- COleServerItem [MFC], OnInitFromData
- COleServerItem [MFC], OnQueryUpdateItems
- COleServerItem [MFC], OnRenderData
- COleServerItem [MFC], OnRenderFileData
- COleServerItem [MFC], OnRenderGlobalData
- COleServerItem [MFC], OnSetColorScheme
- COleServerItem [MFC], OnSetData
- COleServerItem [MFC], OnSetExtent
- COleServerItem [MFC], OnUpdate
- COleServerItem [MFC], OnUpdateItems
- COleServerItem [MFC], SetItemName
- COleServerItem [MFC], GetDataSource
- COleServerItem [MFC], OnHide
- COleServerItem [MFC], OnOpen
- COleServerItem [MFC], OnShow
- COleServerItem [MFC], m_sizeExtent
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
ms.openlocfilehash: dcae304e8571ecb5743002638ea23f13c3e21517
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884100"
---
# <a name="coleserveritem-class"></a>COleServerItem 类

提供 OLE 项的服务器接口。

## <a name="syntax"></a>语法

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|构造 `COleServerItem` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|在 `COleDataSource` 对象中放置表示形式和转换格式。|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|将项复制到剪贴板。|
|[COleServerItem::DoDragDrop](#dodragdrop)|执行拖放操作。|
|[COleServerItem::GetClipboardData](#getclipboarddata)|获取用于数据传输（拖放或剪贴板）的数据源。|
|[COleServerItem::GetDocument](#getdocument)|返回包含该项的服务器文档。|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|获取 OLE 项的 CF_EMBEDSOURCE 数据。|
|[COleServerItem::GetItemName](#getitemname)|返回项的名称。 仅用于链接的项。|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|获取 OLE 项的 CF_LINKSOURCE 数据。|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|获取 OLE 项的 CF_OBJECTDESCRIPTOR 数据。|
|[COleServerItem::IsConnected](#isconnected)|指示该项当前是否已附加到活动容器。|
|[COleServerItem::IsLinkedItem](#islinkeditem)|指示项是否表示链接的 OLE 项。|
|[COleServerItem::NotifyChanged](#notifychanged)|更新具有自动链接更新的所有容器。|
|[COleServerItem::OnDoVerb](#ondoverb)|调用以执行谓词。|
|[COleServerItem::OnDraw](#ondraw)|当容器请求绘制项时调用;需要实现。|
|[COleServerItem::OnDrawEx](#ondrawex)|为专用项绘图调用。|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|由框架调用以获取要复制到剪贴板的数据。|
|[COleServerItem::OnGetExtent](#ongetextent)|由框架调用以检索 OLE 项的大小。|
|[COleServerItem::OnInitFromData](#oninitfromdata)|由框架调用，以使用指定的数据传输对象的内容初始化 OLE 项。|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|调用以确定是否有任何链接项需要更新。|
|[COleServerItem::OnRenderData](#onrenderdata)|在延迟呈现过程中检索数据。|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|将数据作为延迟呈示的一部分检索到 `CFile` 对象。|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|将数据作为延迟呈示的一部分检索到 HGLOBAL。|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|调用以设置项的配色方案。|
|[COleServerItem::OnSetData](#onsetdata)|调用以设置项的数据。|
|[COleServerItem::OnSetExtent](#onsetextent)|由框架调用以设置 OLE 项的大小。|
|[COleServerItem::OnUpdate](#onupdate)|当项所属的文档的某些部分发生更改时调用。|
|[COleServerItem::OnUpdateItems](#onupdateitems)|调用以更新服务器文档中所有项的表示缓存。|
|[COleServerItem::SetItemName](#setitemname)|设置项的名称。 仅用于链接的项。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|获取用于存储转换格式的对象。|
|[COleServerItem::OnHide](#onhide)|由框架调用以隐藏 OLE 项。|
|[COleServerItem::OnOpen](#onopen)|由框架调用，以在其自己的顶级窗口中显示 OLE 项。|
|[COleServerItem::OnShow](#onshow)|当容器请求显示项时调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|通知服务器有多少 OLE 项可见。|

## <a name="remarks"></a>备注

链接项可以表示服务器文档的一部分或全部。 嵌入项始终表示整个服务器文档。

`COleServerItem` 类定义多个可重写的成员函数，这些函数由 OLE 系统动态链接库（Dll）调用，通常用于响应来自容器应用程序的请求。 这些成员函数允许容器应用程序以各种方式间接操作项，例如显示、执行其谓词或以各种格式检索其数据。

若要使用 `COleServerItem`，请从中派生一个类，并实现[OnDraw](#ondraw)并[序列化](../../mfc/reference/cobject-class.md#serialize)成员函数。 `OnDraw` 函数提供项的图元文件表示形式，以便在容器应用程序打开复合文档时显示它。 `CObject` 的 `Serialize` 函数提供项的本机表示形式，允许在服务器和容器应用程序之间传输嵌入项。 [OnGetExtent](#ongetextent)提供项到容器的自然大小，使容器能够调整项的大小。

有关服务器和相关主题的详细信息，请参阅文章 [服务器：在 [容器中实现服务器](../../mfc/servers-implementing-a-server.md) 和 "创建容器/服务器应用程序"：](../../mfc/containers-advanced-features.md)的高级功能。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>要求

**标头：** afxole

##  <a name="addotherclipboarddata"></a>COleServerItem：： AddOtherClipboardData

调用此函数可将 OLE 项的呈现格式和转换格式放入指定的 `COleDataSource` 对象。

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>参数

*pDataSource*<br/>
指向应在其中放置数据的 `COleDataSource` 对象的指针。

### <a name="remarks"></a>备注

必须已实现[OnDraw](#ondraw)成员函数才能为该项提供显示格式（图元文件图片）。 若要支持其他转换格式，请使用[GetDataSource](#getdatasource)返回的[COleDataSource](../../mfc/reference/coledatasource-class.md)对象进行注册，并覆盖[OnRenderData](#onrenderdata)成员函数以提供要支持的格式的数据。

##  <a name="coleserveritem"></a>COleServerItem：： COleServerItem

构造 `COleServerItem` 对象并将其添加到服务器文档的文档项集合。

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>参数

*pServerDoc*<br/>
指向将包含新项的文档的指针。

*bAutoDelete*<br/>
一个标志，用于指示在释放对象的链接时是否可将其删除。 如果 `COleServerItem` 对象是您必须删除的文档数据的组成部分，则将此值设置为 FALSE。 如果对象是一个辅助结构，则将此项设置为 TRUE，该结构用于标识可通过框架删除的文档数据中的范围。

##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard

调用此函数可将 OLE 项复制到剪贴板。

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>参数

*bIncludeLink*<br/>
如果应将链接数据复制到剪贴板，请将此值设置为 TRUE。 如果服务器应用程序不支持链接，则将此值设置为 "FALSE"。

### <a name="remarks"></a>备注

函数使用[OnGetClipboardData](#ongetclipboarddata)成员函数以支持的格式创建包含 OLE 项的数据的[COleDataSource](../../mfc/reference/coledatasource-class.md)对象。 然后，该函数使用[COleDataSource：： SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函数将 `COleDataSource` 对象置于剪贴板上。 `COleDataSource` 对象包括该项的本机数据及其在 CF_METAFILEPICT 格式中的表示形式，以及你选择支持的任何转换格式的数据。 必须已实现了[序列化](../../mfc/reference/cobject-class.md#serialize)和[OnDraw](#ondraw) ，此成员函数才能工作。

##  <a name="dodragdrop"></a>  COleServerItem::DoDragDrop

调用 `DoDragDrop` 成员函数以执行拖放操作。

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>参数

*lpRectItem*<br/>
相对于工作区的屏幕上的项的矩形（以像素为单位）。

*ptOffset*<br/>
拖动时鼠标位置*lpItemRect*的偏移量。

*bIncludeLink*<br/>
如果应将链接数据复制到剪贴板，请将此值设置为 TRUE。 如果你的应用程序不支持链接，则将其设置为 FALSE。

*dwEffects*<br/>
确定拖动操作（复制、移动和链接的组合）中的拖动操作允许的效果。

*lpRectStartDrag*<br/>
一个指针，指向用于定义拖动实际起始位置的矩形。 有关更多信息，请参见下面的“备注”部分。

### <a name="return-value"></a>返回值

DROPEFFECT 枚举中的一个值。 如果 DROPEFFECT_MOVE，则应删除原始数据。

### <a name="remarks"></a>备注

拖放操作不会立即启动。 它会一直等待，直到鼠标光标离开*lpRectStartDrag*指定的矩形，或直到经过指定的毫秒数。 如果*lpRectStartDrag*为 NULL，则使用默认矩形，以便在鼠标光标移动一个像素时开始拖动。

延迟时间由注册表项设置指定。 可以通过调用[CWinApp：： WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[CWinApp：： WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint)来更改延迟时间。 如果未指定延迟时间，则使用默认值200毫秒。 拖动延迟时间按如下方式存储：

- Windows NT 拖动延迟时间存储在 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay. 中。

- Windows 3. x 拖动延迟时间存储在 WIN 中。INI 文件中。

- Windows 95/98 拖动延迟时间存储在 WIN 的缓存版本中.INI.

有关如何将拖动延迟信息存储在注册表或中的详细信息。INI 文件，请参阅 Windows SDK 中的[WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) 。

##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData

调用此函数可将指定的[COleDataSource](../../mfc/reference/coledatasource-class.md)对象填充到指定的对象，该对象包含将被复制到剪贴板的所有数据（如果调用了[CopyToClipboard](#copytoclipboard) ，也会传输相同的[数据）。](#dodragdrop)

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>参数

*pDataSource*<br/>
指向 `COleDataSource` 对象的指针，该对象将接收所有受支持格式的 OLE 项数据。

*bIncludeLink*<br/>
如果应将链接数据复制到剪贴板，则为 TRUE。 如果你的服务器应用程序不支持链接，则为 FALSE。

*lpOffset*<br/>
鼠标光标相对于对象原点的偏移量（以像素为单位）。

*lpSize*<br/>
对象的大小（以像素为单位）。

### <a name="remarks"></a>备注

此函数调用[GetEmbedSourceData](#getembedsourcedata)成员函数以获取 OLE 项的本机数据，并调用[AddOtherClipboardData](#addotherclipboarddata)成员函数以获取呈现格式和任何受支持的转换格式。 如果*bIncludeLink*为 TRUE，函数还会调用[GetLinkSourceData](#getlinksourcedata)来获取该项的链接数据。

如果要在 `CopyToClipboard`提供的格式前后放置 `COleDataSource` 对象中的格式，请重写此函数。

##  <a name="getdatasource"></a>COleServerItem：： GetDataSource

调用此函数可获取用于存储服务器应用程序所支持的转换格式的[COleDataSource](../../mfc/reference/coledatasource-class.md)对象。

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>返回值

指向用于存储转换格式的 `COleDataSource` 对象的指针。

### <a name="remarks"></a>备注

如果希望服务器应用程序在数据传输操作期间提供各种格式的数据，请使用此函数返回的 `COleDataSource` 对象来注册这些格式。 例如，如果您想要为剪贴板或拖放操作提供 OLE 项的 CF_TEXT 表示形式，则可以使用此函数返回的 `COleDataSource` 对象注册该格式，然后重写 `OnRenderXxxData` 成员函数以提供数据。

##  <a name="getdocument"></a>COleServerItem：： GetDocument

调用此函数可获取指向包含该项的文档的指针。

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向包含该项的文档的指针;如果项不是文档的一部分，则为 NULL。

### <a name="remarks"></a>备注

这允许访问作为参数传递给 `COleServerItem` 构造函数的服务器文档。

##  <a name="getembedsourcedata"></a>COleServerItem：： GetEmbedSourceData

调用此函数可获取 OLE 项的 CF_EMBEDSOURCE 数据。

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>参数

*lpStgMedium*<br/>
指向将接收 OLE 项 CF_EMBEDSOURCE 数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构的指针。

### <a name="remarks"></a>备注

此格式包括项的本机数据。 为了使此函数正常工作，您必须已实现 `Serialize` 成员函数。

然后，可以使用[COleDataSource：： CacheData](../../mfc/reference/coledatasource-class.md#cachedata)将结果添加到数据源。 [COleServerItem：： OnGetClipboardData](#ongetclipboarddata)自动调用此函数。

有关详细信息，请参阅 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) 。

##  <a name="getitemname"></a>COleServerItem：： GetItemName

调用此函数可获取项的名称。

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>返回值

项的名称。

### <a name="remarks"></a>备注

通常仅对链接项调用此函数。

##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData

调用此函数可获取 OLE 项的 CF_LINKSOURCE 数据。

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>参数

*lpStgMedium*<br/>
指向将接收 OLE 项 CF_LINKSOURCE 数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此格式包括描述 OLE 项类型的 CLSID 以及查找包含 OLE 项的文档所需的信息。

然后，可以使用[COleDataSource：： CacheData](../../mfc/reference/coledatasource-class.md#cachedata)将结果添加到数据源。 此函数由[OnGetClipboardData](#ongetclipboarddata)自动调用。

有关详细信息，请参阅 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) 。

##  <a name="getobjectdescriptordata"></a>COleServerItem：： GetObjectDescriptorData

调用此函数可获取 OLE 项的 CF_OBJECTDESCRIPTOR 数据。

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>参数

*lpOffset*<br/>
从 OLE 项的左上角按鼠标单击的偏移量。 可以为 NULL。

*lpSize*<br/>
OLE 项的大小。 可以为 NULL。

*lpStgMedium*<br/>
指向将接收 OLE 项 CF_OBJECTDESCRIPTOR 数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构的指针。

### <a name="remarks"></a>备注

该信息将被复制到*lpStgMedium*所指向的 `STGMEDIUM` 结构。 此格式包括 "选择性粘贴" 对话框所需的信息。

有关详细信息，请参阅 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) 。

##  <a name="isconnected"></a>COleServerItem：： Connectionmultiplexer.isconnected

调用此函数可查看 OLE 项是否已连接。

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>返回值

如果该项已连接，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果一个或多个容器引用了项，则将 OLE 项视为已连接。 如果项的引用计数大于0，或者它是嵌入项，则该项已连接。

##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem

调用此函数可查看 OLE 项是否为链接项。

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>返回值

如果项是链接项，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果项有效并且在文档的嵌入项列表中未返回，则链接该项。 链接项可能会也可能不会连接到容器。

对于链接项和嵌入项，通常使用相同的类。 `IsLinkedItem` 允许您使链接项的行为与嵌入项不同，尽管代码很多情况都很常见。

##  <a name="m_sizeextent"></a>COleServerItem：： m_sizeExtent

此成员告诉服务器容器文档中显示的对象的数量。

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>备注

[OnSetExtent](#onsetextent)的默认实现设置此成员。

##  <a name="notifychanged"></a>COleServerItem：： NotifyChanged

更改链接项后调用此函数。

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>参数

*nDrawAspect*<br/>
DVASPECT 枚举中的一个值，该值指示 OLE 项的哪个方面发生了更改。 此参数可以具有下列任意值：

- DVASPECT_CONTENT 项以这样一种方式表示，它可以在其容器中显示为嵌入的对象。

- DVASPECT_THUMBNAIL 项以 "缩略图" 表示形式呈现，以便可以在浏览工具中显示它。

- DVASPECT_ICON 项由图标表示。

- DVASPECT_DOCPRINT 项表示为使用 "文件" 菜单中的 "打印" 命令打印项。

### <a name="remarks"></a>备注

如果容器项已链接到带有自动链接的文档，则项会更新以反映所做的更改。 在使用 Microsoft 基础类库编写的容器应用程序中，将在响应中调用[COleClientItem：： OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 。

##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb

由框架调用以执行指定的谓词。

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
指定要执行的谓词。 它可以是以下任一项：

|值|含义|符号|
|-----------|-------------|------------|
|0|主谓词|OLEIVERB_PRIMARY|
|1|辅助谓词|（无）|
|- 1|显示要编辑的项|OLEIVERB_SHOW|
|- 2|在单独的窗口中编辑项|OLEIVERB_OPEN|
|- 3|隐藏项|OLEIVERB_HIDE|

-1 值通常是另一个谓词的别名。 如果不支持打开编辑，则-2 的效果与-1 相同。 有关其他值，请参阅 IOleObject： Windows SDK 中的[：:D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 。

### <a name="remarks"></a>备注

如果容器应用程序是用 Microsoft 基础类库编写的，则调用相应 `COleClientItem` 对象的[COleClientItem：： Activate](../../mfc/reference/coleclientitem-class.md#activate)成员函数时，将调用此函数。 如果指定了主谓词或 OLEIVERB_SHOW，则默认实现将调用[OnShow](#onshow)成员函数，如果指定了辅助谓词或 OLEIVERB_OPEN，则为 OnOpen [; 如果指定 OLEIVERB_HIDE，则为](#onhide) [OnOpen](#onopen) 。 如果*iVerb*不是上面列出的其中一个谓词，则默认实现将调用 `OnShow`。

如果主谓词不显示该项，则重写此函数。 例如，如果项是声音录制，其主要谓词是播放，则无需显示服务器应用程序来播放该项。

有关详细信息，请参阅 IOleObject： Windows SDK 中的[：:D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 。

##  <a name="ondraw"></a>  COleServerItem::OnDraw

由框架调用，以将 OLE 项呈现到图元文件中。

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向要在其上绘制该项的[CDC](../../mfc/reference/cdc-class.md)对象的指针。 显示上下文会自动连接到属性显示上下文，因此，您可以调用特性函数，但这样做会使图元文件特定于设备。

*rSize*<br/>
要在其中绘制图元文件的 HIMETRIC 单元中的大小。

### <a name="return-value"></a>返回值

如果已成功绘制该项，则为非零值;否则为0。

### <a name="remarks"></a>备注

OLE 项的图元文件表示形式用于在容器应用程序中显示项。 如果容器应用程序是使用 Microsoft 基础类库编写的，则相应[COleClientItem](../../mfc/reference/coleclientitem-class.md)对象的[Draw](../../mfc/reference/coleclientitem-class.md#draw)成员函数使用图元文件。 没有默认实现。 必须重写此函数以将项绘制到指定的设备上下文中。

##  <a name="ondrawex"></a>COleServerItem：： OnDrawEx

由框架为所有绘图调用。

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向要在其上绘制该项的[CDC](../../mfc/reference/cdc-class.md)对象的指针。 DC 会自动连接到属性 DC，因此，您可以调用特性函数，但这样做会使图元文件设备特定。

*nDrawAspect*<br/>
DVASPECT 枚举中的一个值。 此参数可以具有下列任意值：

- DVASPECT_CONTENT 项以这样一种方式表示，它可以在其容器中显示为嵌入的对象。

- DVASPECT_THUMBNAIL 项以 "缩略图" 表示形式呈现，以便可以在浏览工具中显示它。

- DVASPECT_ICON 项由图标表示。

- DVASPECT_DOCPRINT 项表示为使用 "文件" 菜单中的 "打印" 命令打印项。

*rSize*<br/>
项的大小（以 HIMETRIC 单位表示）。

### <a name="return-value"></a>返回值

如果已成功绘制该项，则为非零值;否则为0。

### <a name="remarks"></a>备注

当 DVASPECT 等于 DVASPECT_CONTENT 时，默认实现将调用 `OnDraw`;否则，它会失败。

重写此函数以提供除 DVASPECT_CONTENT 以外的其他方面（如 DVASPECT_ICON 或 DVASPECT_THUMBNAIL）的呈现数据。

##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData

由框架调用，以获取一个 `COleDataSource` 对象，该对象包含通过调用[CopyToClipboard](#copytoclipboard)成员函数而放置在剪贴板上的所有数据。

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>参数

*bIncludeLink*<br/>
如果应将链接数据复制到剪贴板，请将此值设置为 TRUE。 如果服务器应用程序不支持链接，则将此值设置为 "FALSE"。

*lpOffset*<br/>
鼠标光标相对于对象原点的偏移量（以像素为单位）。

*lpSize*<br/>
对象的大小（以像素为单位）。

### <a name="return-value"></a>返回值

指向包含剪贴板数据的[COleDataSource](../../mfc/reference/coledatasource-class.md)对象的指针。

### <a name="remarks"></a>备注

此函数的默认实现将调用[GetClipboardData](#getclipboarddata)。

##  <a name="ongetextent"></a>COleServerItem：： OnGetExtent

由框架调用以检索 OLE 项的大小（以 HIMETRIC 单位表示）。

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>参数

*nDrawAspect*<br/>
指定要检索其边界的 OLE 项的特性。 此参数可以具有下列任意值：

- DVASPECT_CONTENT 项以这样一种方式表示，它可以在其容器中显示为嵌入的对象。

- DVASPECT_THUMBNAIL 项以 "缩略图" 表示形式呈现，以便可以在浏览工具中显示它。

- DVASPECT_ICON 项由图标表示。

- DVASPECT_DOCPRINT 项表示为使用 "文件" 菜单中的 "打印" 命令打印项。

*rSize*<br/>
对将接收 OLE 项大小的 `CSize` 对象的引用。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果容器应用程序是用 Microsoft 基础类库编写的，则调用相应 `COleClientItem` 对象的[GetExtent](../../mfc/reference/coleclientitem-class.md#getextent)成员函数时，将调用此函数。 默认实现不执行任何操作。 您必须自行实现。 如果要在处理 OLE 项的大小请求时执行特殊处理，请重写此函数。

##  <a name="onhide"></a>COleServerItem：： OnHide

由框架调用以隐藏 OLE 项。

```
virtual void OnHide();
```

### <a name="remarks"></a>备注

默认调用 `COleServerDoc::OnShowDocument( FALSE )`。 函数还通知容器 OLE 项已隐藏。 如果要在隐藏 OLE 项时执行特殊处理，请重写此函数。

##  <a name="oninitfromdata"></a>COleServerItem：： OnInitFromData

由框架调用以初始化使用*pDataObject*的内容的 OLE 项。

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>参数

*pDataObject*<br/>
指向 OLE 数据对象的指针，该对象包含用于初始化 OLE 项的各种格式的数据。

*bCreation*<br/>
如果调用该函数以初始化由容器应用程序新建的 OLE 项，则为 TRUE。 如果调用函数以替换现有 OLE 项的内容，则为 FALSE。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果*bCreation*为 TRUE，则当容器实现基于当前所选内容插入新对象时，将调用此函数。 创建新的 OLE 项时，将使用所选数据。 例如，在电子表格程序中选择单元范围，然后使用 "插入新对象" 基于选定范围内的值创建图表时。 默认实现不执行任何操作。 重写此函数以从*pDataObject*提供的格式中选择可接受的格式，并根据提供的数据初始化 OLE 项。 这是一种高级的可重写。

有关详细信息，请参阅 Windows SDK 中的[IOleObject：： InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) 。

##  <a name="onopen"></a>COleServerItem：： OnOpen

由框架调用，以在服务器应用程序的单独实例中显示 OLE 项，而不是就地显示。

```
virtual void OnOpen();
```

### <a name="remarks"></a>备注

默认实现激活显示包含 OLE 项的文档的第一个框架窗口;如果应用程序是小型服务器，则默认实现将显示主窗口。 函数还通知容器 OLE 项已打开。

如果希望在打开 OLE 项时执行特殊处理，请重写此函数。 这对于链接项尤其常见，在此情况下，你想要在链接打开时设置对该链接的选择。

有关详细信息，请参阅 Windows SDK 中的[IOleClientSite：： OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) 。

##  <a name="onqueryupdateitems"></a>COleServerItem：： OnQueryUpdateItems

由框架调用，以确定当前服务器文档中的任何链接项是否已过时。

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>返回值

如果文档包含需要更新的项，则为非零值;如果所有项都是最新的，则为0。

### <a name="remarks"></a>备注

如果项的源文档已更改，但链接项尚未更新以反映文档中的更改，则该项过期。

##  <a name="onrenderdata"></a>COleServerItem：： OnRenderData

由框架调用以检索指定格式的数据。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，指定请求信息时所用的格式。

*lpStgMedium*<br/>
指向要返回数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)或[DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)成员函数在 `COleDataSource` 对象中放置的格式，用于延迟渲染。 此函数的默认实现分别调用[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)（如果提供的存储介质是文件或内存）。 如果这两种格式都未提供，则默认实现将返回0并不执行任何操作。

如果 TYMED_NULL *lpStgMedium*-> *TYMED* ，则 STGMEDIUM 应按照*lpFormatEtc-> tymed*指定的方式进行分配和填充。 如果未 TYMED_NULL，则应将 STGMEDIUM 与数据一起填充。

这是一种高级的可重写。 重写此函数以按请求的格式和媒体提供数据。 根据您的数据，您可能需要替代此函数的其他版本之一。 如果数据大小较小且固定，请覆盖 `OnRenderGlobalData`。 如果数据位于文件中或大小可变，请覆盖 `OnRenderFileData`。

有关详细信息，请参阅 Windows SDK 中的[IDataObject：：](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) [STGMEDIUM、](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)和[TYMED](/windows/win32/api/objidl/ne-objidl-tymed) 。

##  <a name="onrenderfiledata"></a>COleServerItem：： OnRenderFileData

当存储介质为文件时，由框架调用以检索指定格式的数据。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，指定请求信息时所用的格式。

*pFile*<br/>
指向要在其中呈现数据的 `CFile` 对象。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)成员函数在 `COleDataSource` 对象中放置的格式，用于延迟渲染。 此函数的默认实现只返回 FALSE。

这是一种高级的可重写。 重写此函数以按请求的格式和媒体提供数据。 根据您的数据，您可能希望改为重写此函数的其他版本之一。 如果要处理多个存储媒体，请重写[OnRenderData](#onrenderdata)。 如果数据位于文件中或大小可变，请重写[OnRenderFileData](#onrenderfiledata)。

有关详细信息，请参阅 Windows SDK 中的[IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 和 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)。

##  <a name="onrenderglobaldata"></a>COleServerItem：： OnRenderGlobalData

当指定的存储介质为全局内存时，由框架调用以检索指定格式的数据。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，指定请求信息时所用的格式。

*phGlobal*<br/>
指向全局内存的句柄，其中的数据将被返回。 如果未分配内存，则此参数可以为 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)成员函数在 `COleDataSource` 对象中放置的格式，用于延迟渲染。 此函数的默认实现只返回 FALSE。

如果*phGlobal*为 NULL，则应在*phGlobal*中分配并返回新的 HGLOBAL。 否则，由*phGlobal*指定的 HGLOBAL 应使用数据进行填充。 放置在 HGLOBAL 中的数据量不能超过内存块的当前大小。 此外，不能将块重新分配到更大的大小。

这是一种高级的可重写。 重写此函数以按请求的格式和媒体提供数据。 根据您的数据，您可能需要替代此函数的其他版本之一。 如果要处理多个存储媒体，请重写[OnRenderData](#onrenderdata)。 如果数据位于文件中或大小可变，请重写[OnRenderFileData](#onrenderfiledata)。

有关详细信息，请参阅 Windows SDK 中的[IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 和 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)。

##  <a name="onsetcolorscheme"></a>COleServerItem：： OnSetColorScheme

由框架调用以指定编辑 OLE 项时要使用的调色板。

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>参数

*lpLogPalette*<br/>
指向 Windows [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)结构的指针。

### <a name="return-value"></a>返回值

如果使用调色板，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果使用 Microsoft 基础类库编写容器应用程序，则调用相应 `COleClientItem` 对象的[IOleObject：： SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme)函数时，将调用此函数。 默认实现返回 FALSE。 如果要使用推荐的调色板，请重写此函数。 服务器应用程序不需要使用建议的调色板。

有关详细信息，请参阅 Windows SDK 中的[IOleObject：： SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) 。

##  <a name="onsetdata"></a>COleServerItem：： OnSetData

由框架调用，以将 OLE 项的数据替换为指定的数据。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构的指针，该结构指定数据的格式。

*lpStgMedium*<br/>
指向数据所在的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构的指针。

*bRelease*<br/>
指示在完成函数调用之后谁拥有存储介质的所有权。 调用方决定由谁来代表存储介质释放分配的资源。 调用方通过设置*bRelease*来实现此功能。 如果*bRelease*为非零值，则服务器项将获得所有权，并在使用完介质后将其释放。 当*bRelease*为0时，调用方将保留所有权，并且服务器项只能在调用期间使用存储介质。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

在成功获取数据之前，服务器项不会获得数据的所有权。 也就是说，如果返回0，则不获取所有权。 如果数据源获得所有权，它将通过调用[ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium)函数来释放存储介质。

默认实现不执行任何操作。 重写此函数可将 OLE 项的数据替换为指定的数据。 这是一种高级的可重写。

有关详细信息，请参阅 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)、 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)和[ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 。

##  <a name="onsetextent"></a>COleServerItem：： OnSetExtent

由框架调用，以通知 OLE 项容器文档中的可用空间量。

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>参数

*nDrawAspect*<br/>
指定指定其边界的 OLE 项的特性。 此参数可以具有下列任意值：

- DVASPECT_CONTENT 项以这样一种方式表示，它可以在其容器中显示为嵌入的对象。

- DVASPECT_THUMBNAIL 项以 "缩略图" 表示形式呈现，以便可以在浏览工具中显示它。

- DVASPECT_ICON 项由图标表示。

- DVASPECT_DOCPRINT 项表示为使用 "文件" 菜单中的 "打印" 命令打印项。

*size*<br/>
一个[CSize](../../atl-mfc-shared/reference/csize-class.md)结构，它指定 OLE 项的新大小。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果容器应用程序是用 Microsoft 基础类库编写的，则调用相应 `COleClientItem` 对象的[SetExtent](../../mfc/reference/coleclientitem-class.md#setextent)成员函数时，将调用此函数。 如果*nDrawAspect*为 DVASPECT_CONTENT，则默认实现将[m_sizeExtent](#m_sizeextent)成员设置为指定的大小;否则，返回0。 重写此函数以在更改项大小时执行特殊处理。

##  <a name="onshow"></a>COleServerItem：： OnShow

由框架调用，指示服务器应用程序就地显示 OLE 项。

```
virtual void OnShow();
```

### <a name="remarks"></a>备注

此函数通常在容器应用程序的用户创建项或执行需要显示项的谓词（如编辑）时调用。 默认实现尝试就地激活。 如果此操作失败，则函数将调用 `OnOpen` 成员函数以在单独的窗口中显示 OLE 项。

如果要在显示 OLE 项时执行特殊处理，请重写此函数。

##  <a name="onupdate"></a>COleServerItem：： OnUpdate

当项已修改时由框架调用。

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>参数

*pSender*<br/>
指向修改文档的项的指针。 可以为 NULL。

*lHint*<br/>
包含有关修改的信息。

*pHint*<br/>
指向存储有关修改信息的对象的指针。

*nDrawAspect*<br/>
DVASPECT 枚举中的一个值。 此参数可以具有下列值之一：

- DVASPECT_CONTENT 项以这样一种方式表示，它可以在其容器中显示为嵌入的对象。

- DVASPECT_THUMBNAIL 项以 "缩略图" 表示形式呈现，以便可以在浏览工具中显示它。

- DVASPECT_ICON 项由图标表示。

- DVASPECT_DOCPRINT 项表示为使用 "文件" 菜单中的 "打印" 命令打印项。

### <a name="remarks"></a>备注

默认实现将调用[NotifyChanged](#notifychanged)，而不考虑提示或发送方。

##  <a name="onupdateitems"></a>COleServerItem：： OnUpdateItems

由框架调用以更新服务器文档中的所有项。

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>备注

默认实现对文档中的所有`COleClientItem`对象调用 [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)。

##  <a name="setitemname"></a>COleServerItem：： SetItemName

创建链接项来设置其名称时，请调用此函数。

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>参数

*lpszItemName*<br/>
指向项的新名称的指针。

### <a name="remarks"></a>备注

该名称在文档中必须是唯一的。 在调用服务器应用程序以编辑链接项时，应用程序将使用此名称来查找项。 不需要为嵌入项调用此函数。

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem 类](../../mfc/reference/cdocitem-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)
