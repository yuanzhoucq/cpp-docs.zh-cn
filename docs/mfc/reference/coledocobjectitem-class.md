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
ms.openlocfilehash: 454be491fe5875b1b1ac9b2b85fdebe2f1663ebc
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916968"
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
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|`COleDocObject`构造项。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|使用默认打印机设置打印容器应用程序的文档。|
|[COleDocObjectItem::ExecCommand](#execcommand)|执行用户指定的命令。|
|[COleDocObjectItem::GetActiveView](#getactiveview)|检索文档的活动视图。|
|[COleDocObjectItem::GetPageCount](#getpagecount)|检索容器应用程序的文档中的页数。|
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|准备要打印的容器应用程序文档。|
|[COleDocObjectItem::OnPrint](#onprint)|打印容器应用程序的文档。|
|[COleDocObjectItem::QueryCommand](#querycommand)|查询由用户界面事件生成的一个或多个命令的状态。|
|[COleDocObjectItem::Release](#release)|释放到 OLE 链接项的连接并在打开时将其关闭。 不会销毁客户端项。|

## <a name="remarks"></a>备注

在 MFC 中, 活动文档的处理方式类似于常规的就地可编辑嵌入, 具有以下差异:

- 派生的类仍保留当前嵌入项的列表; 但是, 这些项可能是`COleDocObjectItem`派生项。 `COleDocument`

- 活动文档处于活动状态时, 它会占用视图的整个工作区 (当它处于就地活动状态时)。

- 活动文档容器对 "**帮助**" 菜单具有完全控制。

- "**帮助**" 菜单包含活动文档容器和服务器的菜单项。

由于活动文档容器拥有 "**帮助**" 菜单, 因此容器负责将服务器**帮助**菜单消息转发到服务器。 此集成由`COleDocObjectItem`处理。

有关菜单合并和活动文档激活的详细信息, 请参阅[活动文档包含](../../mfc/active-document-containment.md)的概述。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>要求

**标头:** afxole

##  <a name="coledocobjectitem"></a>COleDocObjectItem:: COleDocObjectItem

调用此成员函数以初始化`COleDocObjectItem`对象。

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>参数

*pContainerDoc*<br/>
指向作为活动文档`COleDocument`容器的对象的指针。 若要启用 IMPLEMENT_SERIALIZE, 此参数必须为 NULL。 通常使用非 NULL 文档指针构造 OLE 项。

##  <a name="dodefaultprinting"></a>COleDocObjectItem::D oDefaultPrinting

由框架由使用默认设置的文档调用。

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>参数

*pCaller*<br/>
指向发送打印命令的[CView](../../mfc/reference/cview-class.md)对象的指针。

*pInfo*<br/>
指向描述要打印的作业的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)对象的指针。

##  <a name="execcommand"></a>COleDocObjectItem:: ExecCommand

调用此成员函数可执行用户指定的命令。

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>参数

*nCmdID*<br/>
要执行的命令的标识符。 必须位于由*pguidCmdGroup*标识的组中。

*nCmdExecOpt*<br/>
指定命令执行选项。 默认情况下, 将设置为在不提示用户的情况下执行命令。 有关值的列表, 请参阅[OLECMDEXECOPT](/windows/desktop/api/docobj/ne-docobj-olecmdexecopt) 。

*pguidCmdGroup*<br/>
命令组的唯一标识符。 默认情况下, 为 NULL, 它指定标准组。 传入*nCmdID*的命令必须属于组。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK;否则, 将返回以下错误代码之一。

|值|描述|
|-----------|-----------------|
|E_UNEXPECTED|出现意外错误。|
|E_FAIL|出现错误。|
|E_NOTIMPL|指示 MFC 本身应尝试转换和调度命令。|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup*为非 NULL, 但未指定可识别的命令组。|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID*未被识别为组 pGroup 中的有效命令。|
|OLECMDERR_DISABLED|*NCmdID*标识的命令已禁用, 无法执行。|
|OLECMDERR_NOHELP|调用方请求有关由*nCmdID*标识的命令的帮助, 但没有可用的帮助。|
|OLECMDERR_CANCELLED|用户取消了执行。|

### <a name="remarks"></a>备注

*PguidCmdGroup*和*nCmdID*参数一起唯一标识要调用的命令。 *NCmdExecOpt*参数指定要执行的确切操作。

##  <a name="getactiveview"></a>  COleDocObjectItem::GetActiveView

调用此成员函数以获取指向`IOleDocumentView`当前活动视图的接口的指针。

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>返回值

指向当前活动视图的[IOleDocumentView](/windows/desktop/api/docobj/nn-docobj-ioledocumentview)接口的指针。 如果没有当前视图, 它将返回 NULL。

### <a name="remarks"></a>备注

返回`IOleDocumentView`的指针上的引用计数在此函数返回之前不会递增。

##  <a name="getpagecount"></a>  COleDocObjectItem::GetPageCount

调用此成员函数以检索文档中的页数。

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>参数

*pnFirstPage*<br/>
指向文档的第一页的页码的指针。 可以为 NULL, 指示调用方不需要此数字。

*pcPages*<br/>
一个指针, 指向文档中的总页数。 可以为 NULL, 指示调用方不需要此数字。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="onprepareprinting"></a>COleDocObjectItem:: OnPreparePrinting

框架调用此成员函数来准备要打印的文档。

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>参数

*pCaller*<br/>
指向发送打印命令的[CView](../../mfc/reference/cview-class.md)对象的指针。

*pInfo*<br/>
指向描述要打印的作业的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)对象的指针。

*bPrintAll*<br/>
指定是否打印整个文档。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="onprint"></a>COleDocObjectItem:: OnPrint

框架调用此成员函数来打印文档。

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>参数

*pCaller*<br/>
指向发送打印命令的 CView 对象的指针。

*pInfo*<br/>
指向描述要打印的作业的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)对象的指针。

*bPrintAll*<br/>
指定是否打印整个文档。

##  <a name="querycommand"></a>COleDocObjectItem:: QueryCommand

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
正在查询的命令的标识符。

*pdwStatus*<br/>
一个指针, 指向作为查询结果返回的标志。 有关可能值的列表, 请参阅[OLECMDF](/windows/desktop/api/docobj/ne-docobj-olecmdf)。

*pCmdText*<br/>
指向[OLECMDTEXT](/windows/desktop/api/docobj/ns-docobj-olecmdtext)结构的指针, 将在该结构中返回单个命令的名称和状态信息。 可以为 NULL, 以指示调用方不需要此信息。

*pguidCmdGroup*<br/>
命令组的唯一标识符;可以为 NULL 以指定标准组。

### <a name="return-value"></a>返回值

有关返回值的完整列表, 请参阅 Windows SDK 中的[IOleCommandTarget:: QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus) 。

### <a name="remarks"></a>备注

此成员函数模拟[IOleCommandTarget:: QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus)方法的功能, 如 Windows SDK 中所述。

##  <a name="release"></a>  COleDocObjectItem::Release

释放到 OLE 链接项的连接并在打开时将其关闭。 不会销毁客户端项。

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>参数

*dwCloseOption*<br/>
指定在 OLE 项返回到已加载状态时, 该 OLE 项保存在什么情况下的标志。 有关可能值的列表, 请参阅[COleClientItem:: Close](../../mfc/reference/coleclientitem-class.md#close)。

### <a name="remarks"></a>备注

不会销毁客户端项。

## <a name="see-also"></a>请参阅

[MFC 示例 MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem 类](../../mfc/reference/cdocobjectserveritem-class.md)
