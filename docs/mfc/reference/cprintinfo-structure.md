---
title: CPrintInfo 结构
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: 3b081b0728514c0fca2eb31462e1bcd9e91a47aa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753016"
---
# <a name="cprintinfo-structure"></a>CPrintInfo 结构

存储有关打印或打印预览作业的信息。

## <a name="syntax"></a>语法

```
struct CPrintInfo
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPrintInfo：从页面获取](#getfrompage)|返回要打印的第一页的数量。|
|[CPrintInfo：获取最大页面](#getmaxpage)|返回文档最后一页的编号。|
|[CPrintInfo：获取明页](#getminpage)|返回文档的第一页编号。|
|[CPrintInfo：获取不一页](#getoffsetpage)|返回在组合文档对象打印作业中打印的 DocObject 项第一页前面的页数。|
|[CPrintInfo：获取页面](#gettopage)|返回要打印的最后一页的数量。|
|[CPrintInfo：：设置最大页面](#setmaxpage)|设置文档最后一页的编号。|
|[CPrintInfo：设置明页](#setminpage)|设置文档第一页的编号。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CPrint信息：m_bContinuePrinting](#m_bcontinueprinting)|包含指示框架是否应继续打印循环的标志。|
|[CPrint信息：：m_bDirect](#m_bdirect)|包含指示文档是否直接打印的标志（不显示"打印"对话框）。|
|[CPrint信息：m_bDocObject](#m_bdocobject)|包含指示要打印的文档是否为 DocObject 的标志。|
|[CPrint信息：m_bPreview](#m_bpreview)|包含指示文档是否正在预览的标志。|
|[CPrint信息：m_dwFlags](#m_dwflags)|指定文档对象打印操作。|
|[CPrint信息：m_lpUserData](#m_lpuserdata)|包含指向用户创建结构的指针。|
|[CPrint信息：m_nCurPage](#m_ncurpage)|标识当前打印的页面的编号。|
|[CPrint信息：m_nJobNumber](#m_njobnumber)|指定操作系统为当前打印作业分配的作业编号|
|[CPrint信息：m_nNumPreviewPages](#m_nnumpreviewpages)|标识预览窗口中显示的页数;1 或 2。|
|[CPrint信息：m_nOffsetPage](#m_noffsetpage)|在组合的 DocObject 打印作业中指定特定文档对象的第一页的偏移量。|
|[CPrint信息：m_pPD](#m_ppd)|包含指向用于"打印"`CPrintDialog`对话框的对象的指针。|
|[CPrint信息：m_rectDraw](#m_rectdraw)|指定定义当前可用页面区域的矩形。|
|[CPrint信息：m_strPageDesc](#m_strpagedesc)|包含用于页码显示的格式字符串。|

## <a name="remarks"></a>备注

`CPrintInfo`是一个结构，没有基类。

框架`CPrintInfo`在每次选择"打印预览"命令时都会创建一个对象，并在命令完成后将其销毁。

`CPrintInfo`包含有关整个打印作业的信息，例如要打印的页面范围和打印作业的当前状态，例如当前打印的页面。 某些信息存储在关联的[CPrintDialog](../../mfc/reference/cprintdialog-class.md)对象中;此对象包含用户在"打印"对话框中输入的值。

在`CPrintInfo`打印过程中，在框架和视图类之间传递对象，用于在两者之间交换信息。 例如，框架通过将值`m_nCurPage``CPrintInfo`分配给视图类检索值并执行指定页面的实际打印。

另一个示例是文档的长度在打印之前不为人所知的情况。 在此情况下，每次打印页面时，视图类都会测试文档末尾的视图类。 到达末尾时，视图类将`m_bContinuePrinting`的成员设置为 FALSE;视图类将 的成员`CPrintInfo`设置为 FALSE。这将通知框架停止打印循环。

`CPrintInfo`由"另请参阅"下`CView`列出的成员函数使用。 有关 Microsoft 基础类库提供的打印体系结构的详细信息，请参阅[框架 Windows](../../mfc/frame-windows.md)和[文档/视图体系结构](../../mfc/document-view-architecture.md)以及[文章"打印](../../mfc/printing.md)和[打印：多页文档](../../mfc/multipage-documents.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CPrintInfo`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="cprintinfogetfrompage"></a><a name="getfrompage"></a>CPrintInfo：从页面获取

调用此函数以检索要打印的第一页的编号。

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>返回值

要打印的第一页的数量。

### <a name="remarks"></a>备注

这是用户在"打印"对话框中指定的值，它存储在`CPrintDialog``m_pPD`成员引用的对象中。 如果用户未指定值，则默认值为文档的第一页。

## <a name="cprintinfogetmaxpage"></a><a name="getmaxpage"></a>CPrintInfo：获取最大页面

调用此函数以检索文档最后一页的编号。

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>返回值

文档最后一页的编号。

### <a name="remarks"></a>备注

此值存储在成员引用`CPrintDialog`的对象中。 `m_pPD`

## <a name="cprintinfogetminpage"></a><a name="getminpage"></a>CPrintInfo：获取明页

调用此函数以检索文档第一页的编号。

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>返回值

文档第一页的编号。

### <a name="remarks"></a>备注

此值存储在成员引用`CPrintDialog`的对象中。 `m_pPD`

## <a name="cprintinfogetoffsetpage"></a><a name="getoffsetpage"></a>CPrintInfo：获取不一页

调用此函数以从 DocObject 客户端打印多个 DocObject 项时检索偏移量。

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>返回值

在组合的 DocObject 打印作业中打印的 DocObject 项第一页前面的页数。

### <a name="remarks"></a>备注

此值由`m_nOffsetPage`成员引用。 当文档的第一页与其他活动文档一起`m_nOffsetPage`打印为 DocObject 时，将编号为值 = 1。 仅当`m_nOffsetPage`值为 TRUE 时`m_bDocObject`，该成员才有效。

## <a name="cprintinfogettopage"></a><a name="gettopage"></a>CPrintInfo：获取页面

调用此函数以检索要打印的最后一页的数量。

```
UINT GetToPage() const;
```

### <a name="return-value"></a>返回值

要打印的最后一页数。

### <a name="remarks"></a>备注

这是用户在"打印"对话框中指定的值，它存储在`CPrintDialog``m_pPD`成员引用的对象中。 如果用户未指定值，则默认值是文档的最后一页。

## <a name="cprintinfom_bcontinueprinting"></a><a name="m_bcontinueprinting"></a>CPrint信息：m_bContinuePrinting

包含指示框架是否应继续打印循环的标志。

### <a name="remarks"></a>备注

如果要执行打印时间分页，则可以在到达文档末尾`CView::OnPrepareDC`后重写此成员设置为 FALSE。 如果使用`SetMaxPage`成员函数在打印作业的开头指定文档的长度，则不必修改此变量。 该`m_bContinuePrinting`成员是 BOOL 类型的公共变量。

## <a name="cprintinfom_bdirect"></a><a name="m_bdirect"></a>CPrint信息：：m_bDirect

如果"打印"对话框将绕过以进行直接打印，则框架将此成员设置为 TRUE;否则。

### <a name="remarks"></a>备注

当您从 shell 打印或使用命令 ID ID_FILE_PRINT_DIRECT进行打印时，通常绕过"打印"对话框。

您通常不会更改此成员，但如果您更改了它，请先在您重写[CView :D：：：onPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)之前更改它。 [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting)

## <a name="cprintinfom_bdocobject"></a><a name="m_bdocobject"></a>CPrint信息：m_bDocObject

包含指示要打印的文档是否为 DocObject 的标志。

### <a name="remarks"></a>备注

数据成员`m_dwFlags`，`m_nOffsetPage`并且无效，除非此标志为 TRUE。

## <a name="cprintinfom_bpreview"></a><a name="m_bpreview"></a>CPrint信息：m_bPreview

包含指示文档是否正在预览的标志。

### <a name="remarks"></a>备注

这由框架设置，具体取决于用户执行的命令。 打印预览作业不显示"打印"对话框。 该`m_bPreview`成员是 BOOL 类型的公共变量。

## <a name="cprintinfom_dwflags"></a><a name="m_dwflags"></a>CPrint信息：m_dwFlags

包含指定 DocObject 打印操作的标志组合。

### <a name="remarks"></a>备注

仅当数据成员`m_bDocObject`为 TRUE 时才有效。

标志可以是以下一个或多个值：

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

## <a name="cprintinfom_lpuserdata"></a><a name="m_lpuserdata"></a>CPrint信息：m_lpUserData

包含指向用户创建结构的指针。

### <a name="remarks"></a>备注

可以使用它存储不希望存储在视图类中的特定于打印的数据。 该`m_lpUserData`成员是 LPVOID 类型的公共变量。

## <a name="cprintinfom_ncurpage"></a><a name="m_ncurpage"></a>CPrint信息：m_nCurPage

包含当前页面的编号。

### <a name="remarks"></a>备注

框架调用`CView::OnPrepareDC`文档的每`CView::OnPrint`一页，每次为该成员指定不同的值;其值范围从 返回`GetFromPage`的值到 返回的值。 `GetToPage` 在 重写 中使用此成员，`CView::OnPrepareDC`并`CView::OnPrint`打印文档的指定页面。

首次调用预览模式时，框架将读取此成员的值，以确定应首先预览文档的哪个页面。 您可以在重写中设置此成员的值`CView::OnPreparePrinting`，以在输入预览模式时维护用户在文档中的当前位置。 该`m_nCurPage`成员是 UINT 类型的公共变量。

## <a name="cprintinfom_njobnumber"></a><a name="m_njobnumber"></a>CPrint信息：m_nJobNumber

指示操作系统为当前打印作业分配的作业编号。

### <a name="remarks"></a>备注

如果作业尚未打印（即`CPrintInfo`对象是新构造且尚未用于打印），或者启动作业时出现错误，则可能会SP_ERROR此值。

## <a name="cprintinfom_nnumpreviewpages"></a><a name="m_nnumpreviewpages"></a>CPrint信息：m_nNumPreviewPages

包含预览模式下显示的页数;它可以是 1 或 2。

### <a name="remarks"></a>备注

该`m_nNumPreviewPages`成员是 UINT 类型的公共变量。

## <a name="cprintinfom_noffsetpage"></a><a name="m_noffsetpage"></a>CPrint信息：m_nOffsetPage

在组合的 DocObject 打印作业中，包含特定文档对象第一页前面的页数。

## <a name="cprintinfom_ppd"></a><a name="m_ppd"></a>CPrint信息：m_pPD

包含指向用于显示打印作业`CPrintDialog`的"打印"对话框的对象的指针。

### <a name="remarks"></a>备注

成员`m_pPD`是作为指向`CPrintDialog`的指针声明的公共变量。

## <a name="cprintinfom_rectdraw"></a><a name="m_rectdraw"></a>CPrint信息：m_rectDraw

在逻辑坐标中指定页面的可用绘图区域。

### <a name="remarks"></a>备注

您可能希望在 重写 中引用这一`CView::OnPrint`点。 您可以使用此成员跟踪打印标题、页脚等后仍可用的区域。 成员`m_rectDraw`是类型的`CRect`公共变量。

## <a name="cprintinfom_strpagedesc"></a><a name="m_strpagedesc"></a>CPrint信息：m_strPageDesc

包含用于在打印预览期间显示页码的格式字符串;此字符串由两个子字符串组成，一个用于单页显示，一个用于双页显示，每个子字符串由"\n"字符终止。

### <a name="remarks"></a>备注

框架使用"页面 %u\nPages %u-%u\n"作为默认值。 如果希望页码具有不同的格式，请在 重写 中`CView::OnPreparePrinting`指定格式字符串。 成员`m_strPageDesc`是类型的`CString`公共变量。

## <a name="cprintinfosetmaxpage"></a><a name="setmaxpage"></a>CPrintInfo：：设置最大页面

调用此函数以指定文档最后一页的编号。

```cpp
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>参数

*nMaxPage*<br/>
文档最后一页的编号。

### <a name="remarks"></a>备注

此值存储在成员引用`CPrintDialog`的对象中。 `m_pPD` 如果在打印文档之前知道文档的长度，请从 重写 调用 此`CView::OnPreparePrinting`函数。 如果文档的长度取决于用户在"打印"对话框中指定的设置，请从 重写 调用`CView::OnBeginPrinting`此函数。 如果在打印文档之前不知道文档的长度，请使用`m_bContinuePrinting`该成员控制打印循环。

### <a name="example"></a>示例

  请参阅[CView 的示例：：在准备打印](../../mfc/reference/cview-class.md#onprepareprinting)。

## <a name="cprintinfosetminpage"></a><a name="setminpage"></a>CPrintInfo：设置明页

调用此函数以指定文档第一页的编号。

```cpp
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>参数

*nMinPage*<br/>
文档第一页的编号。

### <a name="remarks"></a>备注

页码通常从 1 开始。 此值存储在成员引用`CPrintDialog`的对象中。 `m_pPD`

## <a name="see-also"></a>请参阅

[MFC 样品 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[C查看：：结束打印](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView：：结束打印预览](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[C查看：：在准备DC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[C查看：：准备打印](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[C查看：：在打印](../../mfc/reference/cview-class.md#onprint)
