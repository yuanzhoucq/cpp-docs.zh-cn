---
title: COleServer 项目类
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
ms.openlocfilehash: 5373075cf6dfc54e6e2368e46f48f317fcec64d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376119"
---
# <a name="coleserveritem-class"></a>COleServer 项目类

提供 OLE 项的服务器接口。

## <a name="syntax"></a>语法

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[COleServer项目：COleServer项目](#coleserveritem)|构造 `COleServerItem` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleServer项目：添加其他剪贴板数据](#addotherclipboarddata)|在`COleDataSource`对象中放置表示和转换格式。|
|[COleServer项目：：复制到剪贴板](#copytoclipboard)|将项目复制到剪贴板。|
|[COleServer项目：:DoDragDrop](#dodragdrop)|执行拖放操作。|
|[COleServer项目：获取剪贴板数据](#getclipboarddata)|获取用于数据传输（拖放或剪贴板）的数据源。|
|[COleServer项目：获取文档](#getdocument)|返回包含该项目的服务器文档。|
|[COleServer项目：获取嵌入源数据](#getembedsourcedata)|获取 OLE 项的CF_EMBEDSOURCE数据。|
|[COleServer项目：获取项目名称](#getitemname)|返回项的名称。 仅用于链接项目。|
|[COleServer项目：获取链接源数据](#getlinksourcedata)|获取 OLE 项CF_LINKSOURCE数据。|
|[COleServer项目：获取对象描述数据](#getobjectdescriptordata)|获取 OLE 项CF_OBJECTDESCRIPTOR数据。|
|[COleServer项目：已连接](#isconnected)|指示项目当前是否附加到活动容器。|
|[COleServer项目：是链接项目](#islinkeditem)|指示项目是否表示链接的 OLE 项。|
|[COleServer项目：通知已更改](#notifychanged)|使用自动链接更新更新所有容器。|
|[COleServer项目：OnDoVerb](#ondoverb)|被调用以执行动词。|
|[COleServer项目：在画上](#ondraw)|当容器请求绘制项时调用;需要实现。|
|[COleServer项目：OnDrawEx](#ondrawex)|调用专用项目绘图。|
|[COleServer项目：在获取剪贴板数据](#ongetclipboarddata)|由框架调用，获取将复制到剪贴板的数据。|
|[COleServerItem::OnGetExtent](#ongetextent)|由框架调用以检索 OLE 项的大小。|
|[COleServer项目：从数据中打开](#oninitfromdata)|框架调用使用指定的数据传输对象的内容初始化 OLE 项。|
|[COleServer项目：打开查询更新项目](#onqueryupdateitems)|调用 以确定是否有任何链接的项目需要更新。|
|[COleServer项目：在渲染数据上](#onrenderdata)|检索数据作为延迟呈现的一部分。|
|[COleServer项目：在渲染文件数据上](#onrenderfiledata)|将数据检索到对象中`CFile`作为延迟呈现的一部分。|
|[COleServer项目：在渲染全局数据上](#onrenderglobaldata)|将数据检索到 HGLOBAL 中，作为延迟呈现的一部分。|
|[COleServer项目：打开颜色方案](#onsetcolorscheme)|调用以设置项目的配色方案。|
|[COleServer项目：OnSetData](#onsetdata)|调用以设置项的数据。|
|[COleServerItem::OnSetExtent](#onsetextent)|由框架调用以设置 OLE 项的大小。|
|[COleServer项目：更新](#onupdate)|当项目所属的文档的某些部分已更改时调用。|
|[COleServer项目：更新项目](#onupdateitems)|调用 以更新服务器文档中所有项的演示文稿缓存。|
|[COleServer项目：设置项目名称](#setitemname)|设置项的名称。 仅用于链接项目。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[COleServer项目：获取数据来源](#getdatasource)|获取用于存储转换格式的对象。|
|[COleServer项目：打开隐藏](#onhide)|由框架调用以隐藏 OLE 项。|
|[COleServer项目：打开](#onopen)|由框架调用以在其自己的顶级窗口中显示 OLE 项。|
|[COleServer项目：在展会上](#onshow)|当容器请求显示项时调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COleServer项目：m_sizeExtent](#m_sizeextent)|通知服务器有多少 OLE 项可见。|

## <a name="remarks"></a>备注

链接项可以表示部分或全部服务器文档。 嵌入的项目始终表示整个服务器文档。

该`COleServerItem`类定义由 OLE 系统动态链接库 （DLL） 调用的多个可重写成员函数，通常是为了响应来自容器应用程序的请求。 这些成员函数允许容器应用程序以各种方式间接操作项目，例如通过显示项目、执行其谓词或以各种格式检索其数据。

要使用`COleServerItem`，从中派生类并实现[OnDraw](#ondraw)和[序列化](../../mfc/reference/cobject-class.md#serialize)成员函数。 该`OnDraw`函数提供项的元文件表示形式，允许在容器应用程序打开复合文档时显示它。 提供`Serialize``CObject`项的本机表示形式，允许在服务器和容器应用程序之间传输嵌入项。 [OnGetExtent](#ongetextent)向容器提供项目的自然大小，使容器能够调整项目的大小。

有关服务器和相关主题的详细信息，请参阅文章"[服务器：实现服务器"](../../mfc/servers-implementing-a-server.md)和"创建容器/服务器应用程序"一文[：高级功能](../../mfc/containers-advanced-features.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="coleserveritemaddotherclipboarddata"></a><a name="addotherclipboarddata"></a>COleServer项目：添加其他剪贴板数据

调用此函数将 OLE 项的表示格式和转换格式放在指定`COleDataSource`对象中。

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>参数

*pData来源*<br/>
指向应放置`COleDataSource`数据的对象的指针。

### <a name="remarks"></a>备注

您必须已实现[OnDraw](#ondraw)成员函数，才能为项目提供表示格式（元文件图片）。 要支持其他转换格式，请使用[GetDataSource](#getdatasource)返回的[COleDataSource](../../mfc/reference/coledatasource-class.md)对象注册它们，并重写[OnRenderData](#onrenderdata)成员函数以您想要支持的格式提供数据。

## <a name="coleserveritemcoleserveritem"></a><a name="coleserveritem"></a>COleServer项目：COleServer项目

构造对象`COleServerItem`并将其添加到服务器文档的文档项集合中。

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>参数

*pServerDoc*<br/>
指向将包含新项目的文档的指针。

*b自动删除*<br/>
指示在释放指向对象的链接时是否可以删除该对象的标志。 如果对象是必须删除的文档`COleServerItem`数据的组成部分，则将其设置为 FALSE。 如果对象是用于标识文档数据中可由框架删除的范围的辅助结构，则将其设置为 TRUE。

## <a name="coleserveritemcopytoclipboard"></a><a name="copytoclipboard"></a>COleServer项目：：复制到剪贴板

调用此函数以将 OLE 项复制到剪贴板。

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>参数

*bInclude链接*<br/>
如果链接数据应复制到剪贴板，则将其设置为 TRUE。 如果服务器应用程序不支持链接，请将此设置为 FALSE。

### <a name="remarks"></a>备注

该函数使用[OnGetClipboardData](#ongetclipboarddata)成员函数创建一个包含 OLE 项数据的[COleDataSource](../../mfc/reference/coledatasource-class.md)对象，该对象采用支持的格式。 然后，该函数使用`COleDataSource` [COleDataSource：：setClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函数将对象放在剪贴板上。 该`COleDataSource`对象包括项目的本机数据及其CF_METAFILEPICT格式的表示形式，以及您选择的任何转换格式的数据。 您必须已实现[序列化和](../../mfc/reference/cobject-class.md#serialize) [OnDraw，](#ondraw)才能使此成员函数正常工作。

## <a name="coleserveritemdodragdrop"></a><a name="dodragdrop"></a>COleServer项目：:DoDragDrop

调用`DoDragDrop`成员函数以执行拖放操作。

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>参数

*lprect项目*<br/>
相对于工作区，屏幕上的项目矩形（以像素为单位）。

*pt偏移*<br/>
鼠标位置在拖动时所在的*lpItemRect*的偏移量。

*bInclude链接*<br/>
如果链接数据应复制到剪贴板，则将其设置为 TRUE。 如果应用程序不支持链接，请将其设置为 FALSE。

*dwEffects*<br/>
确定拖动源在拖动操作中允许的效果（复制、移动和链接的组合）。

*lpRect开始拖动*<br/>
指向定义拖动实际开始位置的矩形的指针。 有关更多信息，请参见下面的“备注”部分。

### <a name="return-value"></a>返回值

DROPVALUE 枚举中的值。 如果DROPEFFECT_MOVE，则应删除原始数据。

### <a name="remarks"></a>备注

拖放操作不会立即启动。 它等待鼠标光标离开*lpRectStartDrag 指定的*矩形或直到经过指定数量的毫秒。 如果*lpRectStartDrag*为 NULL，则使用默认矩形，以便在鼠标光标移动一个像素时开始拖动。

延迟时间由注册表键设置指定。 您可以通过调用[CWinApp：：WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[CWinApp：：WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint)来更改延迟时间。 如果不指定延迟时间，则使用默认值 200 毫秒。 拖动延迟时间存储如下：

- Windows NT 拖动延迟时间存储在HKEY_LOCAL_MACHINE_SOFTWARE_微软\Windows_NT_当前版本\iniFile映射\win.ini_Windows_Dragdelay。

- Windows 3.x 拖动延迟时间存储在 WIN 中。INI 文件，在 [Windows] 部分下。

- Windows 95/98 拖动延迟时间存储在 WIN 的缓存版本中。Ini。

有关拖动延迟信息如何存储在注册表或 中的详细信息。INI 文件，请参阅 Windows SDK 中的[写入配置文件字符串](/windows/win32/api/winbase/nf-winbase-writeprofilestringw)。

## <a name="coleserveritemgetclipboarddata"></a><a name="getclipboarddata"></a>COleServer项目：获取剪贴板数据

调用此函数以填充指定的[COleDataSource](../../mfc/reference/coledatasource-class.md)对象，其中包含将复制到剪贴板的所有数据（如果您调用[CopyToClipboard](#copytoclipboard)[DoDragDrop，](#dodragdrop)也会传输相同的数据）。

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>参数

*pData来源*<br/>
指向将以`COleDataSource`所有受支持格式接收 OLE 项数据的对象的指针。

*bInclude链接*<br/>
如果链接数据应复制到剪贴板，则为 TRUE。 如果服务器应用程序不支持链接，则 FALSE。

*lpOffset*<br/>
鼠标光标与对象原点的偏移量（以像素为单位）。

*lpSize*<br/>
对象的大小（以像素为单位）。

### <a name="remarks"></a>备注

此函数调用[GetEmbedSourceData](#getembedsourcedata)成员函数获取 OLE 项目的本机数据，并调用[AddOtherClipboard 数据](#addotherclipboarddata)成员函数来获取表示格式和任何支持的转换格式。 如果*bIncludeLink*为 TRUE，则函数还会调用[GetLinkSourceData](#getlinksourcedata)来获取该项目的链接数据。

如果要在`CopyToClipboard`提供的格式之前或之后将格式`COleDataSource`放在对象中，则重写此函数。

## <a name="coleserveritemgetdatasource"></a><a name="getdatasource"></a>COleServer项目：获取数据来源

调用此函数获取用于存储服务器应用程序支持的转换格式的[COleDataSource](../../mfc/reference/coledatasource-class.md)对象。

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>返回值

指向用于存储转换`COleDataSource`格式的对象的指针。

### <a name="remarks"></a>备注

如果希望服务器应用程序在数据传输操作期间以各种格式提供数据，请将这些格式注册到此函数返回`COleDataSource`的对象中。 例如，如果要为剪贴板或拖放操作提供 OLE 项的CF_TEXT表示形式，则需要将格式注册到此函数返回`COleDataSource`的对象，然后覆盖`OnRenderXxxData`成员函数以提供数据。

## <a name="coleserveritemgetdocument"></a><a name="getdocument"></a>COleServer项目：获取文档

调用此函数以获取指向包含项的文档的指针。

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向包含项的文档的指针;如果项目不是文档的一部分，则 NULL。

### <a name="remarks"></a>备注

这允许访问作为参数传递给构造函数的`COleServerItem`服务器文档。

## <a name="coleserveritemgetembedsourcedata"></a><a name="getembedsourcedata"></a>COleServer项目：获取嵌入源数据

调用此函数以获取 OLE 项CF_EMBEDSOURCE数据。

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>参数

*lpStg 中*<br/>
指向将接收 OLE 项CF_EMBEDSOURCE数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构的指针。

### <a name="remarks"></a>备注

此格式包括项目的本机数据。 您必须已实现`Serialize`成员函数，才能使此函数正常工作。

然后，可以使用[COleDataSource：：CacheData](../../mfc/reference/coledatasource-class.md#cachedata)将结果添加到数据源中。 此函数由[COleServerItem 自动调用：：在GetClipboard数据上](#ongetclipboarddata)。

有关详细信息，请参阅 Windows SDK 中的[STGMEDIUM。](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)

## <a name="coleserveritemgetitemname"></a><a name="getitemname"></a>COleServer项目：获取项目名称

调用此函数以获取项的名称。

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>返回值

项的名称。

### <a name="remarks"></a>备注

通常仅针对链接的项目调用此函数。

## <a name="coleserveritemgetlinksourcedata"></a><a name="getlinksourcedata"></a>COleServer项目：获取链接源数据

调用此函数以获取 OLE 项的CF_LINKSOURCE数据。

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>参数

*lpStg 中*<br/>
指向将接收 OLE 项CF_LINKSOURCE数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此格式包括 CLSID，描述 OLE 项的类型以及查找包含 OLE 项的文档所需的信息。

然后，可以使用[COleDataSource：：CacheData](../../mfc/reference/coledatasource-class.md#cachedata)将结果添加到数据源中。 此功能由[OnGetClipboard 数据](#ongetclipboarddata)自动调用。

有关详细信息，请参阅 Windows SDK 中的[STGMEDIUM。](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)

## <a name="coleserveritemgetobjectdescriptordata"></a><a name="getobjectdescriptordata"></a>COleServer项目：获取对象描述数据

调用此函数以获取 OLE 项CF_OBJECTDESCRIPTOR数据。

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>参数

*lpOffset*<br/>
鼠标单击从 OLE 项目的左上角偏移。 可以为 NULL。

*lpSize*<br/>
OLE 项的大小。 可以为 NULL。

*lpStg 中*<br/>
指向将接收 OLE 项CF_OBJECTDESCRIPTOR数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构的指针。

### <a name="remarks"></a>备注

信息被复制到`STGMEDIUM`*lpStgMedia*指向的结构中。 此格式包括粘贴特殊对话框所需的信息。

有关详细信息，请参阅 Windows SDK 中的[STGMEDIUM。](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)

## <a name="coleserveritemisconnected"></a><a name="isconnected"></a>COleServer项目：已连接

调用此函数以查看 OLE 项是否已连接。

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>返回值

如果项目已连接，则非零;否则 0。

### <a name="remarks"></a>备注

如果一个或多个容器对该项目具有引用，则 OLE 项被视为已连接。 如果项的引用计数大于 0 或是嵌入项，则连接该项。

## <a name="coleserveritemislinkeditem"></a><a name="islinkeditem"></a>COleServer项目：是链接项目

调用此函数以查看 OLE 项是否为链接项。

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>返回值

如果项是链接项，则非零;否则 0。

### <a name="remarks"></a>备注

如果项有效且未在文档中的嵌入项列表中返回，则项将链接。 链接的项可能已连接到容器，也可能未连接到容器。

对于链接和嵌入项使用相同的类是很常见的。 `IsLinkedItem`允许您使链接项的行为方式与嵌入项不同，尽管代码多次常见。

## <a name="coleserveritemm_sizeextent"></a><a name="m_sizeextent"></a>COleServer项目：m_sizeExtent

此成员告诉服务器容器文档中有多少对象可见。

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>备注

[OnSetA.的](#onsetextent)默认实现将设置此成员。

## <a name="coleserveritemnotifychanged"></a><a name="notifychanged"></a>COleServer项目：通知已更改

更改链接项后调用此函数。

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>参数

*nDrawAspect*<br/>
DVASPECT 枚举中的值，指示 OLE 项的哪个方面已更改。 此参数可能具有以下任何值：

- DVASPECT_CONTENT项的表示方式可以将其显示为容器内的嵌入对象。

- DVASPECT_THUMBNAIL项目以"缩略图"表示形式呈现，以便它可以显示在浏览工具中。

- DVASPECT_ICON项由图标表示。

- DVASPECT_DOCPRINT项表示，就好像它是使用"文件"菜单中的"打印"命令一样。

### <a name="remarks"></a>备注

如果容器项链接到具有自动链接的文档，则该项将更新以反映更改。 在使用 Microsoft 基础类库编写的容器应用程序中[，COleClientItem：onChange](../../mfc/reference/coleclientitem-class.md#onchange)是响应调用的。

## <a name="coleserveritemondoverb"></a><a name="ondoverb"></a>COleServer项目：OnDoVerb

由框架调用以执行指定的谓词。

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
指定要执行的谓词。 它可以是以下任一项：

|“值”|含义|符号|
|-----------|-------------|------------|
|0|主谓词|OLEIVERB_PRIMARY|
|1|次要动词|（无）|
|- 1|显示要编辑的项目|OLEIVERB_SHOW|
|- 2|在单独的窗口中编辑项目|OLEIVERB_OPEN|
|- 3|隐藏项目|OLEIVERB_HIDE|

-1 值通常是另一个谓词的别名。 如果不支持打开编辑，-2 的效果与 -1 相同。 有关其他值，请参阅 Windows SDK 中的[IOleObject：:DoVerb。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)

### <a name="remarks"></a>备注

如果容器应用程序是使用 Microsoft 基础类库编写的，则当调用相应对象的[COleClientItem：：激活](../../mfc/reference/coleclientitem-class.md#activate)相应`COleClientItem`对象的成员函数时，将调用此函数。 如果指定了主谓词或OLEIVERB_SHOW，则默认实现将调用[OnShow](#onshow)成员函数;指定辅助谓词或OLEIVERB_OPEN时[打开](#onopen);如果指定了OLEIVERB_HIDE，则[调用 OnHide。](#onhide) 如果`OnShow`*iVerb*不是上面列出的动词之一，则默认实现将调用。

如果主动词不显示该项目，请覆盖此函数。 例如，如果项是录音，并且其主要谓词是"播放"，则不必显示服务器应用程序来播放该项目。

有关详细信息，请参阅 Windows SDK 中的[IOleObject：:DoVerb。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)

## <a name="coleserveritemondraw"></a><a name="ondraw"></a>COleServer项目：在画上

由框架调用，以将 OLE 项呈现为元文件。

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向要在其中绘制项的[CDC](../../mfc/reference/cdc-class.md)对象的指针。 显示上下文会自动连接到属性显示上下文，因此您可以调用属性函数，尽管这样做会使元文件设备特定于。

*rSize*<br/>
大小，以 HIMETRIC 单位表示，用于绘制元文件。

### <a name="return-value"></a>返回值

如果项目已成功绘制，则非零;否则 0。

### <a name="remarks"></a>备注

OLE 项的元文件表示形式用于在容器应用程序中显示该项目。 如果容器应用程序是使用 Microsoft 基础类库编写的，则元文件由相应[COleClientItem](../../mfc/reference/coleclientitem-class.md)对象的[Draw](../../mfc/reference/coleclientitem-class.md#draw)成员函数使用。 没有默认实现。 必须重写此函数才能将项绘制到指定的设备上下文中。

## <a name="coleserveritemondrawex"></a><a name="ondrawex"></a>COleServer项目：OnDrawEx

由所有绘图的框架调用。

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向要在其中绘制项的[CDC](../../mfc/reference/cdc-class.md)对象的指针。 DC 会自动连接到属性 DC，因此您可以调用属性函数，尽管这样做会使元文件设备特定于。

*nDrawAspect*<br/>
DVASPECT 枚举中的值。 此参数可能具有以下任何值：

- DVASPECT_CONTENT项的表示方式可以将其显示为容器内的嵌入对象。

- DVASPECT_THUMBNAIL项目以"缩略图"表示形式呈现，以便它可以显示在浏览工具中。

- DVASPECT_ICON项由图标表示。

- DVASPECT_DOCPRINT项表示，就好像它是使用"文件"菜单中的"打印"命令一样。

*rSize*<br/>
物料的大小（以 HIMETRIC 单位为单位）。

### <a name="return-value"></a>返回值

如果项目已成功绘制，则非零;否则 0。

### <a name="remarks"></a>备注

当 DVASPECT`OnDraw`等于DVASPECT_CONTENT时，默认实现调用;否则，它失败。

重写此函数以为DVASPECT_CONTENT以外的方面（如DVASPECT_ICON或DVASPECT_THUMBNAIL）提供表示数据。

## <a name="coleserveritemongetclipboarddata"></a><a name="ongetclipboarddata"></a>COleServer项目：在获取剪贴板数据

由框架调用，获取一个`COleDataSource`对象，其中包含通过调用[CopyToClipboard](#copytoclipboard)成员函数在剪贴板上放置的所有数据。

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>参数

*bInclude链接*<br/>
如果链接数据应复制到剪贴板，则将其设置为 TRUE。 如果服务器应用程序不支持链接，请将此设置为 FALSE。

*lpOffset*<br/>
鼠标光标与对象原点的偏移量（以像素为单位）。

*lpSize*<br/>
对象的大小（以像素为单位）。

### <a name="return-value"></a>返回值

指向包含剪贴板数据的[COleDataSource](../../mfc/reference/coledatasource-class.md)对象的指针。

### <a name="remarks"></a>备注

此函数的默认实现调用[GetClipboardData](#getclipboarddata)。

## <a name="coleserveritemongetextent"></a><a name="ongetextent"></a>COleServer项目：在获取范围

由框架调用以检索 OLE 项的大小（以 HIMETRIC 单位为单位）。

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>参数

*nDrawAspect*<br/>
指定要检索其边界的 OLE 项的方面。 此参数可能具有以下任何值：

- DVASPECT_CONTENT项的表示方式可以将其显示为容器内的嵌入对象。

- DVASPECT_THUMBNAIL项目以"缩略图"表示形式呈现，以便它可以显示在浏览工具中。

- DVASPECT_ICON项由图标表示。

- DVASPECT_DOCPRINT项表示，就好像它是使用"文件"菜单中的"打印"命令一样。

*rSize*<br/>
引用将接收`CSize`OLE 项大小的对象。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果容器应用程序是使用 Microsoft 基础类库编写的，则当调用相应`COleClientItem`对象的[GetExtent](../../mfc/reference/coleclientitem-class.md#getextent)成员函数时，将调用此函数。 默认实现不执行任何操作。 您必须自己实现它。 如果要在处理 OLE 项大小的请求时执行特殊处理，请覆盖此函数。

## <a name="coleserveritemonhide"></a><a name="onhide"></a>COleServer项目：打开隐藏

由框架调用以隐藏 OLE 项。

```
virtual void OnHide();
```

### <a name="remarks"></a>备注

默认调用`COleServerDoc::OnShowDocument( FALSE )`。 该函数还会通知容器 OLE 项已隐藏。 如果要在隐藏 OLE 项时执行特殊处理，则重写此函数。

## <a name="coleserveritemoninitfromdata"></a><a name="oninitfromdata"></a>COleServer项目：从数据中打开

由框架调用，使用*pDataObject*的内容初始化 OLE 项。

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>参数

*pDataObject*<br/>
指向包含各种格式数据的 OLE 数据对象，用于初始化 OLE 项。

*b创造*<br/>
如果调用函数来初始化容器应用程序新创建的 OLE 项，则为 TRUE。 如果调用函数以替换现有 OLE 项的内容，则 FALSE。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果*b创作*为 TRUE，则如果容器基于当前选择实现"插入新对象"，则调用此函数。 创建新 OLE 项时，将使用所选数据。 例如，在电子表格程序中选择单元格区域，然后使用"插入新对象"根据所选范围内的值创建图表时。 默认实现不执行任何操作。 重写此函数，从*pDataObject*提供的格式中选择可接受的格式，并根据提供的数据初始化 OLE 项。 这是一个高级的可重写。

有关详细信息，请参阅[IOleObject：：Windows SDK 中的 InitfromData。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata)

## <a name="coleserveritemonopen"></a><a name="onopen"></a>COleServer项目：打开

由框架调用，以在服务器应用程序的单独实例中显示 OLE 项，而不是就位。

```
virtual void OnOpen();
```

### <a name="remarks"></a>备注

默认实现激活显示包含 OLE 项的文档的第一个帧窗口;如果应用程序是微型服务器，则默认实现将显示主窗口。 该函数还会通知容器 OLE 项已打开。

如果要在打开 OLE 项时执行特殊处理，则重写此函数。 这在链接项中尤其常见，您希望在链接打开时将所选内容设置为链接。

有关详细信息，请参阅[IOleClientSiteSite：Windows](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) SDK 中的"显示窗口"。

## <a name="coleserveritemonqueryupdateitems"></a><a name="onqueryupdateitems"></a>COleServer项目：打开查询更新项目

由框架调用以确定当前服务器文档中的任何链接项是否已过期。

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>返回值

如果文档具有需要更新的项目，则非零;如果所有项目都是最新的，则为 0。

### <a name="remarks"></a>备注

如果项目的源文档已更改，但链接的项尚未更新以反映文档中的更改，则项已过期。

## <a name="coleserveritemonrenderdata"></a><a name="onrenderdata"></a>COleServer项目：在渲染数据上

框架调用以检索指定格式的数据。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，指定请求信息的格式。

*lpStg 中*<br/>
指向要返回数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前使用`COleDataSource`[延迟渲染数据](../../mfc/reference/coledatasource-class.md#delayrenderdata)或[延迟渲染文件](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)成员函数放置在对象中的格式，用于延迟渲染。 如果提供的存储介质是文件或内存，则此函数的默认实现分别调用[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData。](#onrenderglobaldata) 如果未提供这两种格式，则默认实现返回 0，不执行任何操作。

如果*lpStg中*-> *tymedTYMED_NULL，STGMEDIUM*应分配和填充，如*lpFormatEtc->tymed*指定。 如果不TYMED_NULL，则 STGMEDIUM 应随数据一起填充。

这是一个高级的可重写。 重写此函数以请求的格式和介质提供数据。 根据数据的不同，您可能希望重写此函数的其他版本之一。 如果数据较小且大小固定，请重写`OnRenderGlobalData`。 如果数据位于文件中，或者大小可变，请重写`OnRenderFileData`。

有关详细信息，请参阅[IDataObject：获取数据](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)[、STGMEDIUM、FORMATETC](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[TYMED](/windows/win32/api/objidl/ne-objidl-tymed)在 Windows SDK 中。 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)

## <a name="coleserveritemonrenderfiledata"></a><a name="onrenderfiledata"></a>COleServer项目：在渲染文件数据上

当存储介质是文件时，框架调用以指定格式检索数据。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，指定请求信息的格式。

*pFile*<br/>
指向要呈现`CFile`数据的对象。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前使用`COleDataSource`[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)成员函数放置在对象中的格式，用于延迟渲染。 此函数的默认实现仅返回 FALSE。

这是一个高级的可重写。 重写此函数以请求的格式和介质提供数据。 根据数据的不同，您可能希望重写此函数的其他版本之一。 如果要处理多个存储介质，则重写[OnRenderData](#onrenderdata)。 如果数据位于文件中，或者大小可变，请覆盖[OnRenderFileData](#onrenderfiledata)。

有关详细信息，请参阅[IDataObject：获取 Windows](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) SDK 中的数据和[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

## <a name="coleserveritemonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleServer项目：在渲染全局数据上

当指定的存储介质是全局内存时，框架调用以指定格式检索数据。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，指定请求信息的格式。

*phGlobal*<br/>
指向要返回数据的全局内存的句柄。 如果未分配内存，则此参数可以是 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前使用`COleDataSource`[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)成员函数放置在对象中的格式，用于延迟渲染。 此函数的默认实现仅返回 FALSE。

如果*phGlobal*为 NULL，则应在 phGLOBAL 中分配并返回新的*HGLOBAL。* 否则 *，phGLOBAL*指定的 HGLOBAL 应填充数据。 放置在 HGLOBAL 中的数据量不得超过内存块的当前大小。 此外，块无法重新分配到更大的大小。

这是一个高级的可重写。 重写此函数以请求的格式和介质提供数据。 根据数据的不同，您可能希望重写此函数的其他版本之一。 如果要处理多个存储介质，则重写[OnRenderData](#onrenderdata)。 如果数据位于文件中，或者大小可变，请覆盖[OnRenderFileData](#onrenderfiledata)。

有关详细信息，请参阅[IDataObject：获取 Windows](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) SDK 中的数据和[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

## <a name="coleserveritemonsetcolorscheme"></a><a name="onsetcolorscheme"></a>COleServer项目：打开颜色方案

由框架调用以指定在编辑 OLE 项时使用的调色板。

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>参数

*lpLogPalette*<br/>
指向 Windows [LOGPALETTE 结构的指针](/windows/win32/api/wingdi/ns-wingdi-logpalette)。

### <a name="return-value"></a>返回值

如果使用调色板，则非零;否则 0。

### <a name="remarks"></a>备注

如果容器应用程序是使用 Microsoft 基础类库编写的，则当调用相应`COleClientItem`对象的[IOleObject：setColorscheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme)函数时，将调用此函数。 默认实现返回 FALSE。 如果要使用建议的调色板，请单击此函数。 服务器应用程序不需要使用建议的调色板。

有关详细信息，请参阅[IOleObject：：在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme)Windows SDK 中设置颜色方案。

## <a name="coleserveritemonsetdata"></a><a name="onsetdata"></a>COleServer项目：OnSetData

框架调用以将 OLE 项的数据替换为指定数据。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向指定数据格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构的指针。

*lpStg 中*<br/>
指向数据所在的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构的指针。

*b释放*<br/>
指示谁在完成函数调用后拥有存储介质的所有权。 调用方决定由谁负责释放代表存储介质分配的资源。 调用方通过设置*bRelease*来进行此用。 如果*bRelease*是非零，则服务器项将取得所有权，在介质使用完毕后释放介质。 当*bRelease*为 0 时，调用方将保留所有权，并且服务器项只能在调用期间使用存储介质。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

服务器项在成功获取数据之前不会取得数据的所有权。 也就是说，如果它返回 0，它不取得所有权。 如果数据源拥有所有权，则通过调用[ReleaseStgMedia](/windows/win32/api/ole2/nf-ole2-releasestgmedium)函数释放存储介质。

默认实现不执行任何操作。 重写此函数以将 OLE 项的数据替换为指定数据。 这是一个高级的可重写。

有关详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) [STGMEDIUM、FORMATETC](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[发布StgMedia。](/windows/win32/api/ole2/nf-ole2-releasestgmedium)

## <a name="coleserveritemonsetextent"></a><a name="onsetextent"></a>COleServer项目：在设置范围

由框架调用，告诉 OLE 项在容器文档中有多少可用空间。

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>参数

*nDrawAspect*<br/>
指定正在指定其边界的 OLE 项的方面。 此参数可能具有以下任何值：

- DVASPECT_CONTENT项的表示方式可以将其显示为容器内的嵌入对象。

- DVASPECT_THUMBNAIL项目以"缩略图"表示形式呈现，以便它可以显示在浏览工具中。

- DVASPECT_ICON项由图标表示。

- DVASPECT_DOCPRINT项表示，就好像它是使用"文件"菜单中的"打印"命令一样。

*大小*<br/>
指定 OLE 项新大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果容器应用程序是使用 Microsoft 基础类库编写的，则当调用相应`COleClientItem`对象的[SetExtent](../../mfc/reference/coleclientitem-class.md#setextent)成员函数时，将调用此函数。 如果*DVASPECT_CONTENT，* 则默认实现将[m_sizeExtent](#m_sizeextent)成员设置为指定大小;否则它返回 0。 重写此函数以在更改项目大小时执行特殊处理。

## <a name="coleserveritemonshow"></a><a name="onshow"></a>COleServer项目：在展会上

由框架调用，指示服务器应用程序将 OLE 项显示到位。

```
virtual void OnShow();
```

### <a name="remarks"></a>备注

当容器应用程序的用户创建项或执行需要显示项的谓词（如 Edit）时，通常会调用此函数。 默认实现尝试就地激活。 如果失败，该函数将调用`OnOpen`成员函数以在单独的窗口中显示 OLE 项。

如果要在显示 OLE 项时执行特殊处理，则重写此函数。

## <a name="coleserveritemonupdate"></a><a name="onupdate"></a>COleServer项目：更新

修改项时由框架调用。

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
DVASPECT 枚举中的值。 此参数可以具有以下任一值：

- DVASPECT_CONTENT项的表示方式可以将其显示为容器内的嵌入对象。

- DVASPECT_THUMBNAIL项目以"缩略图"表示形式呈现，以便它可以显示在浏览工具中。

- DVASPECT_ICON项由图标表示。

- DVASPECT_DOCPRINT项表示，就好像它是使用"文件"菜单中的"打印"命令一样。

### <a name="remarks"></a>备注

默认实现调用[Notify 更改](#notifychanged)，无论提示或发件人。

## <a name="coleserveritemonupdateitems"></a><a name="onupdateitems"></a>COleServer项目：更新项目

由框架调用以更新服务器文档中的所有项。

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>备注

默认实现调用文档中所有`COleClientItem`对象的[UpdateLink。](../../mfc/reference/coleclientitem-class.md#updatelink)

## <a name="coleserveritemsetitemname"></a><a name="setitemname"></a>COleServer项目：设置项目名称

创建链接项以设置其名称时调用此函数。

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>参数

*lpszItem名称*<br/>
指向项的新名称的指针。

### <a name="remarks"></a>备注

名称在文档中必须是唯一的。 当调用服务器应用程序编辑链接项时，应用程序使用此名称来查找该项目。 不需要为嵌入项调用此函数。

## <a name="see-also"></a>另请参阅

[MFC 样品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem 类](../../mfc/reference/cdocitem-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)
