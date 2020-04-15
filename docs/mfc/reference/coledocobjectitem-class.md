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
ms.openlocfilehash: a696226185dd99b9e277e74d92cbe15c95cc900a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375050"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem 类

实现活动文档包容。

## <a name="syntax"></a>语法

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleDoc对象项目：COleDoc对象项目](#coledocobjectitem)|构造项`COleDocObject`。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleDocObject项目：:D默认打印](#dodefaultprinting)|使用默认打印机设置打印容器应用程序的文档。|
|[COleDocObject项目：：执行命令](#execcommand)|执行用户指定的命令。|
|[COleDoc对象项目：获取活动视图](#getactiveview)|检索文档的活动视图。|
|[COleDoc对象项目：获取页面计数](#getpagecount)|检索容器应用程序文档中的页数。|
|[COleDocObject项目：：准备打印](#onprepareprinting)|准备容器应用程序的文档以进行打印。|
|[COleDocObject项目：：在打印上](#onprint)|打印容器应用程序的文档。|
|[COleDoc对象项目：查询命令](#querycommand)|查询由用户界面事件生成的一个或多个命令的状态。|
|[COleDocObject项目：：发布](#release)|释放与 OLE 链接项的连接，并在打开时关闭它。 不销毁客户端项。|

## <a name="remarks"></a>备注

在 MFC 中，Active 文档的处理方式类似于常规的、就地可编辑的嵌入，并具有以下差异：

- 派生`COleDocument`类仍维护当前嵌入项的列表;但是，派生类仍保留当前嵌入的项的列表。但是，这些项目可能是`COleDocObjectItem`派生项。

- 当活动文档处于活动状态时，当它就地处于活动状态时，它将占据视图的整个工作区。

- 活动文档容器可完全控制 **"帮助"** 菜单。

- **"帮助**"菜单包含活动文档容器和服务器的菜单项。

由于 Active 文档容器拥有 **"帮助**"菜单，因此该容器负责将服务器**帮助**菜单消息转发到服务器。 此集成由 处理`COleDocObjectItem`。

有关菜单合并和活动文档激活的详细信息，请参阅[活动文档包含](../../mfc/active-document-containment.md)概述。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="coledocobjectitemcoledocobjectitem"></a><a name="coledocobjectitem"></a>COleDoc对象项目：COleDoc对象项目

调用此成员函数以初始化`COleDocObjectItem`对象。

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>参数

*p集装箱文件*<br/>
指向充当活动文档`COleDocument`容器的对象的指针。 此参数必须为 NULL 才能启用IMPLEMENT_SERIALIZE。 通常，OLE 项使用非 NULL 文档指针构造。

## <a name="coledocobjectitemdodefaultprinting"></a><a name="dodefaultprinting"></a>COleDocObject项目：:D默认打印

框架使用默认设置调用文档。

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

## <a name="coledocobjectitemexeccommand"></a><a name="execcommand"></a>COleDocObject项目：：执行命令

调用此成员函数以执行用户指定的命令。

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>参数

*nCmdID*<br/>
要执行的命令的标识符。 必须位于*pguidCmdGroup*标识的组中。

*nCmdExecOpt*<br/>
指定命令执行选项。 默认情况下，设置为在不提示用户的情况下执行命令。 有关值列表，请参阅[OLECMDEXECOPT。](/windows/win32/api/docobj/ne-docobj-olecmdexecopt)

*普吉德集团*<br/>
命令组的唯一标识符。 默认情况下，NULL，它指定标准组。 *在 nCmdID*中传递的命令必须属于该组。

### <a name="return-value"></a>返回值

如果成功，返回S_OK;否则，返回以下错误代码之一。

|“值”|描述|
|-----------|-----------------|
|E_UNEXPECTED|出现了意外错误。|
|E_FAIL|出错。|
|E_NOTIMPL|指示 MFC 本身应尝试转换和调度命令。|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup*是非 NULL，但不指定已识别的命令组。|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID*未在组 pGroup 中识别为有效命令。|
|OLECMDERR_DISABLED|*nCmdID*标识的命令已禁用，无法执行。|
|OLECMDERR_NOHELP|呼叫者请求对*nCmdID*标识的命令寻求帮助，但没有可用的帮助。|
|OLECMDERR_CANCELLED|用户取消了执行。|

### <a name="remarks"></a>备注

*pguidCmdGroup*和*nCmdID*参数一起唯一标识要调用的命令。 *nCmdExecOpt 参数*指定要执行的确切操作。

## <a name="coledocobjectitemgetactiveview"></a><a name="getactiveview"></a>COleDoc对象项目：获取活动视图

调用此成员函数以获取指向当前活动视图`IOleDocumentView`接口的指针。

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>返回值

指向当前活动视图的[IOleDocumentView](/windows/win32/api/docobj/nn-docobj-ioledocumentview)接口的指针。 如果没有当前视图，它将返回 NULL。

### <a name="remarks"></a>备注

返回的`IOleDocumentView`指针上的引用计数不会递增，然后再由此函数返回它。

## <a name="coledocobjectitemgetpagecount"></a><a name="getpagecount"></a>COleDoc对象项目：获取页面计数

调用此成员函数以检索文档中的页数。

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>参数

*pnFirstPage*<br/>
指向文档第一页编号的指针。 可以是 NULL，表示调用方不需要此号码。

*pcPages*<br/>
指向文档中页总数的指针。 可以是 NULL，表示调用方不需要此号码。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

## <a name="coledocobjectitemonprepareprinting"></a><a name="onprepareprinting"></a>COleDocObject项目：：准备打印

框架调用此成员函数以准备用于打印的文档。

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

## <a name="coledocobjectitemonprint"></a><a name="onprint"></a>COleDocObject项目：：在打印上

框架调用此成员函数以打印文档。

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

## <a name="coledocobjectitemquerycommand"></a><a name="querycommand"></a>COleDoc对象项目：查询命令

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
要查询的命令的标识符。

*pdw状态*<br/>
作为查询的结果返回指向标志的指针。 有关可能值的列表，请参阅[OLECMDF](/windows/win32/api/docobj/ne-docobj-olecmdf)。

*pCmdText*<br/>
指向[OLECMDTEXT](/windows/win32/api/docobj/ns-docobj-olecmdtext)结构的指针，在该结构中返回单个命令的名称和状态信息。 可以为 NULL 以指示调用方不需要此信息。

*普吉德集团*<br/>
命令组的唯一标识符;可以为 NULL 指定标准组。

### <a name="return-value"></a>返回值

有关返回值的完整列表，请参阅[IOleCommandTarget：：Windows](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) SDK 中的查询状态。

### <a name="remarks"></a>备注

此成员函数模拟[IOleCommandTarget：：查询状态](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus)方法的功能，如 Windows SDK 中所述。

## <a name="coledocobjectitemrelease"></a><a name="release"></a>COleDocObject项目：：发布

释放与 OLE 链接项的连接，并在打开时关闭它。 不销毁客户端项。

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>参数

*dwCloseOption*<br/>
标记指定在哪些情况下，当 OLE 项返回到加载状态时，它保存它。 有关可能值的列表，请参阅[COleClientItemItem：：关闭](../../mfc/reference/coleclientitem-class.md#close)。

### <a name="remarks"></a>备注

不销毁客户端项。

## <a name="see-also"></a>另请参阅

[MFC 样品 MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServer 项目类](../../mfc/reference/cdocobjectserveritem-class.md)
