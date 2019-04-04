---
title: CPrintInfo 结构
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: 96b6204fe46cb624d22506b2d3e5c1d7621b1865
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772210"
---
# <a name="cprintinfo-structure"></a>CPrintInfo 结构

存储有关打印或打印预览作业的信息。

## <a name="syntax"></a>语法

```
struct CPrintInfo
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CPrintInfo::GetFromPage](#getfrompage)|返回正在打印的第一页的页码。|
|[CPrintInfo::GetMaxPage](#getmaxpage)|返回的最后一页文档的数目。|
|[CPrintInfo::GetMinPage](#getminpage)|返回第一页的文档数。|
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|返回前面的第一页 DocObject 项组合的 DocObject 打印作业中打印的页数。|
|[CPrintInfo::GetToPage](#gettopage)|返回正在打印的最后一页的数目。|
|[CPrintInfo::SetMaxPage](#setmaxpage)|设置文档的最后一页的数量。|
|[CPrintInfo::SetMinPage](#setminpage)|设置第一页的文档数。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|包含一个标志，指示框架是否应继续打印循环。|
|[CPrintInfo::m_bDirect](#m_bdirect)|包含一个标志，指示是否正在打印文档直接 （而不显示打印对话框中）。|
|[CPrintInfo::m_bDocObject](#m_bdocobject)|包含一个标志，指示是否正在打印的文档 DocObject。|
|[CPrintInfo::m_bPreview](#m_bpreview)|包含一个标志，指示是否正在预览文档。|
|[CPrintInfo::m_dwFlags](#m_dwflags)|指定 DocObject 打印操作。|
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|包含指向用户创建结构的指针。|
|[CPrintInfo::m_nCurPage](#m_ncurpage)|标识当前正在打印的页的页码。|
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|指定由当前打印作业的操作系统分配的作业编号|
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|标识在预览窗口中; 中显示的页面数1 或 2。|
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|在组合 DocObject 打印作业中指定特定 DocObject 的第一页的偏移的量。|
|[CPrintInfo::m_pPD](#m_ppd)|包含一个指向`CPrintDialog`使用打印对话框中的对象。|
|[CPrintInfo::m_rectDraw](#m_rectdraw)|指定定义当前可用页面区域的矩形。|
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|包含页号显示的格式字符串。|

## <a name="remarks"></a>备注

`CPrintInfo` 是一种结构，而未一个基类。

该框架将创建的对象`CPrintInfo`每次打印或打印预览命令选择和命令完成时销毁它。

`CPrintInfo` 包含有关打印作业作为一个整体，如要打印的页范围和打印作业，例如当前正在打印的页的当前状态的信息。 一些信息存储在相关联[CPrintDialog](../../mfc/reference/cprintdialog-class.md)对象; 此对象包含用户在打印对话框中输入的值。

一个`CPrintInfo`对象框架和视图类之间传递打印过程中，用于这两个之间交换信息。 例如，框架告知视图类的要通过将分配到的值打印的文档页`m_nCurPage`的成员`CPrintInfo`; 视图类检索值，并执行指定的页的实际打印。

另一个示例是在其中文档的长度之前未知的打印这种情况。 在这种情况下，视图类测试文档末尾的每次打印一页。 视图类达到结束后，设置`m_bContinuePrinting`的成员`CPrintInfo`为 FALSE; 这会通知框架，以停止打印循环。

`CPrintInfo` 成员函数的使用`CView`列出在"另请参阅。" 有关通过 Microsoft 基础类库提供的打印体系结构的详细信息，请参阅[帧 Windows](../../mfc/frame-windows.md)并[文档/视图体系结构](../../mfc/document-view-architecture.md)和文章[打印](../../mfc/printing.md)和[打印：多页文档](../../mfc/multipage-documents.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CPrintInfo`

## <a name="requirements"></a>要求

**标头：** afxext.h

##  <a name="getfrompage"></a>  CPrintInfo::GetFromPage

调用此函数可检索要打印的第一页的数目。

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>返回值

要打印的第一页的数目。

### <a name="remarks"></a>备注

这是用户在打印对话框中指定的值并存储在`CPrintDialog`所引用对象`m_pPD`成员。 如果用户未指定一个值，默认值为文档的第一页。

##  <a name="getmaxpage"></a>  CPrintInfo::GetMaxPage

调用此函数可检索的文档的最后一页。

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>返回值

文档的最后一页的数目。

### <a name="remarks"></a>备注

此值存储在`CPrintDialog`所引用对象`m_pPD`成员。

##  <a name="getminpage"></a>  CPrintInfo::GetMinPage

调用此函数可检索的文档的第一页。

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>返回值

第一页的文档数。

### <a name="remarks"></a>备注

此值存储在`CPrintDialog`所引用对象`m_pPD`成员。

##  <a name="getoffsetpage"></a>  CPrintInfo::GetOffsetPage

调用此函数可检索偏移量，从 DocObject 客户端打印多个 DocObject 项时。

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>返回值

前面的第一页 DocObject 项组合的 DocObject 打印作业中打印的页数。

### <a name="remarks"></a>备注

此值引用的`m_nOffsetPage`成员。 将带编号的文档的第一页`m_nOffsetPage`值 + 1 作为 DocObject 与其他活动文档一起打印时。 `m_nOffsetPage`成员无效，仅当`m_bDocObject`值为 TRUE。

##  <a name="gettopage"></a>  CPrintInfo::GetToPage

调用此函数可检索要打印的最后一页的数目。

```
UINT GetToPage() const;
```

### <a name="return-value"></a>返回值

要打印的最后一页的数目。

### <a name="remarks"></a>备注

这是用户在打印对话框中指定的值并存储在`CPrintDialog`所引用对象`m_pPD`成员。 如果用户未指定一个值，默认值为文档的最后一页。

##  <a name="m_bcontinueprinting"></a>  CPrintInfo::m_bContinuePrinting

包含一个标志，指示框架是否应继续打印循环。

### <a name="remarks"></a>备注

如果正在执行打印时分页，您可以将此成员设置为 FALSE 的重写中`CView::OnPrepareDC`一旦达到文档的结尾。 无需修改此变量，如果已指定打印作业使用的开始处的文档的长度`SetMaxPage`成员函数。 `m_bContinuePrinting`成员是类型 BOOL 的公共变量。

##  <a name="m_bdirect"></a>  CPrintInfo::m_bDirect

Framework： 将此成员设置为 TRUE，如果直接打印，则将不使用打印对话框FALSE 否则为。

### <a name="remarks"></a>备注

通常情况下绕过打印对话框，从命令行程序或完成打印时进行打印时使用的命令 ID ID_FILE_PRINT_DIRECT。

通常不会更改此成员，但如果您更改它，将其更改之前调用[CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting)在重写[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)。

##  <a name="m_bdocobject"></a>  CPrintInfo::m_bDocObject

包含一个标志，指示是否正在打印的文档 DocObject。

### <a name="remarks"></a>备注

数据成员`m_dwFlags`和`m_nOffsetPage`是无效的除非此标志为 TRUE。

##  <a name="m_bpreview"></a>  CPrintInfo::m_bPreview

包含一个标志，指示是否正在预览文档。

### <a name="remarks"></a>备注

这将由具体取决于命令的用户执行的框架。 打印对话框中不显示打印预览作业。 `m_bPreview`成员是类型 BOOL 的公共变量。

##  <a name="m_dwflags"></a>  CPrintInfo::m_dwFlags

包含指定 DocObject 打印操作的标志的组合。

### <a name="remarks"></a>备注

有效仅当数据成员`m_bDocObject`为 TRUE。

标志可以是一个或多个以下值：

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

##  <a name="m_lpuserdata"></a>  CPrintInfo::m_lpUserData

包含指向用户创建结构的指针。

### <a name="remarks"></a>备注

可以使用此存储不想存储在视图类中的特定于打印的数据。 `m_lpUserData`成员是类型 LPVOID 的公共变量。

##  <a name="m_ncurpage"></a>  CPrintInfo::m_nCurPage

包含当前页的页码。

### <a name="remarks"></a>备注

框架将调用`CView::OnPrepareDC`并`CView::OnPrint`一次对于每一页文档，每次; 为此成员指定一个不同的值及其值的范围从返回的值`GetFromPage`到返回的`GetToPage`。 使用此成员中的替代`CView::OnPrepareDC`和`CView::OnPrint`打印文档的指定的页。

第一次调用预览模式时，框架将读取此成员以确定应最初预览文档的哪一页的值。 您可以设置此成员的值中的重写`CView::OnPreparePrinting`输入预览模式时维护文档中的用户的当前位置。 `m_nCurPage`成员是类型为 UINT 的公共变量。

##  <a name="m_njobnumber"></a>  CPrintInfo::m_nJobNumber

指示分配适用于当前打印作业的作业编号。

### <a name="remarks"></a>备注

如果尚没有打印作业，此值可能为 SP_ERROR (即，如果`CPrintInfo`对象新构造，并具有尚未使用打印)，或如果在启动作业时出错。

##  <a name="m_nnumpreviewpages"></a>  CPrintInfo::m_nNumPreviewPages

包含显示在预览模式下; 的页面数它可以是 1 或 2。

### <a name="remarks"></a>备注

`m_nNumPreviewPages`成员是类型为 UINT 的公共变量。

##  <a name="m_noffsetpage"></a>  CPrintInfo::m_nOffsetPage

包含前面组合 DocObject 打印作业中的特定 DocObject 的第一页的页面数。

##  <a name="m_ppd"></a>  CPrintInfo::m_pPD

包含一个指向`CPrintDialog`对象用来显示打印作业的打印对话框。

### <a name="remarks"></a>备注

`m_pPD`成员是公共变量声明为指向`CPrintDialog`。

##  <a name="m_rectdraw"></a>  CPrintInfo::m_rectDraw

指定以逻辑坐标表示的页的可用绘图区域。

### <a name="remarks"></a>备注

您可能想要的重写中引用此`CView::OnPrint`。 可以使用此成员来跟踪哪些区域仍然可用后打印页眉、 页脚和等等。 `m_rectDraw`成员是类型的公共变量`CRect`。

##  <a name="m_strpagedesc"></a>  CPrintInfo::m_strPageDesc

包含用于在打印预览，则为过程中显示的页码的格式字符串此字符串包含两个子字符串，一个用于单页面显示，一个用于双页显示，每个 \n 字符终止。

### <a name="remarks"></a>备注

框架将使用默认值为"页 %u\npages%u-%u\n"。 如果你想以不同格式的页码，指定一个格式字符串中的重写`CView::OnPreparePrinting`。 `m_strPageDesc`成员是类型的公共变量`CString`。

##  <a name="setmaxpage"></a>  CPrintInfo::SetMaxPage

调用此函数可指定文档的最后一页的数目。

```
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>参数

*nMaxPage*<br/>
文档的最后一页的数目。

### <a name="remarks"></a>备注

此值存储在`CPrintDialog`所引用对象`m_pPD`成员。 如果在打印之前已知文档的长度，则调用此函数的重写从`CView::OnPreparePrinting`。 如果文档的长度依赖于用户在打印对话框中指定的设置，则调用此函数的重写从`CView::OnBeginPrinting`。 如果之前打印文档的长度未知，使用`m_bContinuePrinting`成员来控制打印循环。

### <a name="example"></a>示例

  有关示例，请参阅[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)。

##  <a name="setminpage"></a>  CPrintInfo::SetMinPage

调用此函数可指定文档的第一页的数目。

```
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>参数

*nMinPage*<br/>
第一页的文档数。

### <a name="remarks"></a>备注

通常情况下从 1 开始的页码。 此值存储在`CPrintDialog`所引用对象`m_pPD`成员。

## <a name="see-also"></a>请参阅

[MFC 示例 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[CView::OnPrint](../../mfc/reference/cview-class.md#onprint)
