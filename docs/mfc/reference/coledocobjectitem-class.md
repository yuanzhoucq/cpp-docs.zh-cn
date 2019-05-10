---
title: COleDocObjectItem 类
ms.date: 11/04/2016
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
helpviewer_keywords:
- COleDocObjectItem [MFC], COleDocObjectItem
- COleDocObjectItem [MFC], DoDefaultPrinting
- COleDocObjectItem [MFC], ExecCommand
- COleDocObjectItem [MFC], GetActiveView
- COleDocObjectItem [MFC], GetPageCount
- COleDocObjectItem [MFC], OnPreparePrinting
- COleDocObjectItem [MFC], OnPrint
- COleDocObjectItem [MFC], QueryCommand
- COleDocObjectItem [MFC], Release
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
ms.openlocfilehash: 382960b4dc4dcfa61c836a87044dd14585756174
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225508"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem 类

实现活动文档包容。

## <a name="syntax"></a>语法

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|构造`COleDocObject`项。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|将容器应用程序的文档使用的默认打印机设置打印。|
|[COleDocObjectItem::ExecCommand](#execcommand)|执行由用户指定的命令。|
|[COleDocObjectItem::GetActiveView](#getactiveview)|检索文档的活动视图。|
|[COleDocObjectItem::GetPageCount](#getpagecount)|检索容器应用程序的文档中的页面数。|
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|准备容器应用程序的文档进行打印。|
|[COleDocObjectItem::OnPrint](#onprint)|输出容器应用程序的文档。|
|[COleDocObjectItem::QueryCommand](#querycommand)|查询由用户界面事件生成的一个或多个命令的状态。|
|[COleDocObjectItem::Release](#release)|释放为 OLE 链接项连接并关闭它，如果它处于打开状态。 不会销毁的客户端项。|

## <a name="remarks"></a>备注

在 MFC 中，活动文档被处理方法类似于常规、 就地编辑嵌入，具有以下差异：

- `COleDocument`的派生的类仍然保留当前嵌入的项的列表; 不过，这些项可能`COleDocObjectItem`-派生的项。

- 活动文档处于活动状态，它会占据整个工作区的视图，处于就地活动状态时。

- 活动文档容器拥有完全控制权**帮助**菜单。

- **帮助**菜单包含的活动文档容器和服务器的菜单项。

由于活动文档容器拥有**帮助**菜单中，容器负责转发服务器**帮助**菜单消息到服务器。 这种集成处理通过`COleDocObjectItem`。

菜单合并功能和活动文档激活的详细信息，请参阅概述[活动文档包容](../../mfc/active-document-containment.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>要求

**标头：** afxole.h

##  <a name="coledocobjectitem"></a>  COleDocObjectItem::COleDocObjectItem

调用此成员函数以初始化`COleDocObjectItem`对象。

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>参数

*pContainerDoc*<br/>
一个指向`COleDocument`充当活动文档容器的对象。 此参数必须为 NULL 以启用 IMPLEMENT_SERIALIZE。 通常情况下使用非 NULL 文档指针构造 OLE 项。

##  <a name="dodefaultprinting"></a>  COleDocObjectItem::DoDefaultPrinting

由框架调用到使用默认设置的文档。

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>参数

*pCaller*<br/>
一个指向[CView](../../mfc/reference/cview-class.md)发送打印命令的对象。

*pInfo*<br/>
一个指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)对象，描述要打印的作业。

##  <a name="execcommand"></a>  COleDocObjectItem::ExecCommand

调用此成员函数以执行用户指定的命令。

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>参数

*nCmdID*<br/>
要执行的命令标识符。 必须在由标识的组*pguidCmdGroup*。

*nCmdExecOpt*<br/>
指定命令执行选项。 默认情况下，设置为不提示用户执行命令。 请参阅[OLECMDEXECOPT](/windows/desktop/api/docobj/ne-docobj-olecmdexecopt)有关值的列表。

*pguidCmdGroup*<br/>
命令组的唯一标识符。 默认情况下，NULL，指定标准的组。 该命令中传递*nCmdID*必须属于的组。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK 返回否则，返回以下错误代码之一。

|“值”|描述|
|-----------|-----------------|
|E_UNEXPECTED|出现意外的错误。|
|E_FAIL|出现错误。|
|E_NOTIMPL|指示 MFC 本身应尝试转换并将其分派命令。|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup*非 null 值，但未指定已识别的命令组。|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID*未被识别为组 pGroup 中的有效命令。|
|OLECMDERR_DISABLED|该命令由标识*nCmdID*被禁用，并且不能执行。|
|OLECMDERR_NOHELP|由标识命令的帮助请求调用方*nCmdID*但没有帮助可用。|
|OLECMDERR_CANCELLED|用户已取消执行。|

### <a name="remarks"></a>备注

*PguidCmdGroup*并*nCmdID*参数一起唯一地标识要调用的命令。 *NCmdExecOpt*参数指定要执行的具体操作。

##  <a name="getactiveview"></a>  COleDocObjectItem::GetActiveView

调用此成员函数可获取一个指向`IOleDocumentView`当前处于活动状态的视图的接口。

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>返回值

一个指向[IOleDocumentView](/windows/desktop/api/docobj/nn-docobj-ioledocumentview)当前处于活动状态的视图的接口。 如果没有当前视图，则返回 NULL。

### <a name="remarks"></a>备注

对返回的引用计数`IOleDocumentView`此函数返回之前，不会增加指针。

##  <a name="getpagecount"></a>  COleDocObjectItem::GetPageCount

调用此成员函数可检索的文档中的页数。

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>参数

*pnFirstPage*<br/>
一个指向文档的第一页的页码。 可以为 NULL，指示调用方不需要此数字。

*pcPages*<br/>
指向文档中的页总数的指针。 可以为 NULL，指示调用方不需要此数字。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="onprepareprinting"></a>  COleDocObjectItem::OnPreparePrinting

准备用于打印的文档框架调用此成员函数。

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>参数

*pCaller*<br/>
一个指向[CView](../../mfc/reference/cview-class.md)发送打印命令的对象。

*pInfo*<br/>
一个指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)对象，描述要打印的作业。

*bPrintAll*<br/>
指定是否要打印整个文档。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="onprint"></a>  COleDocObjectItem::OnPrint

此成员函数调用由框架对文档进行打印。

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>参数

*pCaller*<br/>
指向正在发送打印命令的 CView 对象的指针。

*pInfo*<br/>
一个指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)对象，描述要打印的作业。

*bPrintAll*<br/>
指定是否要打印整个文档。

##  <a name="querycommand"></a>  COleDocObjectItem::QueryCommand

查询由用户界面事件生成的一个或多个命令的状态。

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>参数

*nCmdID*<br/>
对其进行查询的命令标识符。

*pdwStatus*<br/>
指向作为查询结果返回的标志的指针。 有关可能的值的列表，请参阅[OLECMDF](/windows/desktop/api/docobj/ne-docobj-olecmdf)。

*pCmdText*<br/>
指向[OLECMDTEXT](/windows/desktop/api/docobj/ns-docobj-_tagolecmdtext)中要返回其单个命令的名称和状态信息的结构。 可以为 NULL 以指示调用方不需要此信息。

*pguidCmdGroup*<br/>
命令组; 的唯一标识符可以为 NULL，以指定标准的组。

### <a name="return-value"></a>返回值

返回值的完整列表，请参阅[IOleCommandTarget::QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus) Windows SDK 中。

### <a name="remarks"></a>备注

此成员函数模拟的功能[IOleCommandTarget::QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus)方法，如 Windows SDK 中所述。

##  <a name="release"></a>  COleDocObjectItem::Release

释放为 OLE 链接项连接并关闭它，如果它处于打开状态。 不会销毁的客户端项。

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>参数

*dwCloseOption*<br/>
标志，指定何种情况下向加载状态返回时保存 OLE 项。 有关可能的值的列表，请参阅[COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close)。

### <a name="remarks"></a>备注

不会销毁的客户端项。

## <a name="see-also"></a>请参阅

[MFC 示例 MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem 类](../../mfc/reference/cdocobjectserveritem-class.md)
