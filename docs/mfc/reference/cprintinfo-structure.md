---
title: "CPrintInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrintInfo
dev_langs:
- C++
helpviewer_keywords:
- CPrintInfo structure
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ffa72acc58e0ac1a387e67e6542abcd466be9640
ms.lasthandoff: 02/24/2017

---
# <a name="cprintinfo-structure"></a>CPrintInfo 结构
存储有关打印或打印预览的作业的信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct CPrintInfo  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CPrintInfo::GetFromPage](#getfrompage)|返回正在打印的第一页的数目。|  
|[CPrintInfo::GetMaxPage](#getmaxpage)|返回文档的最后一页的数目。|  
|[CPrintInfo::GetMinPage](#getminpage)|返回文档的第一页的数目。|  
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|返回前面的第一页 DocObject 项组合的 DocObject 打印作业中打印的页数。|  
|[CPrintInfo::GetToPage](#gettopage)|返回正在打印的最后一页的数目。|  
|[CPrintInfo::SetMaxPage](#setmaxpage)|设置文档的最后一页的数目。|  
|[CPrintInfo::SetMinPage](#setminpage)|设置文档的第一页的数目。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|包含一个标志，指示框架是否应继续打印循环。|  
|[CPrintInfo::m_bDirect](#m_bdirect)|包含一个标志，指示是否在直接 （不显示打印对话框中） 打印文档。|  
|[CPrintInfo::m_bDocObject](#m_bdocobject)|包含一个标志，指示正在打印的文档是否 DocObject。|  
|[CPrintInfo::m_bPreview](#m_bpreview)|包含一个标志，指示是否正在预览文档。|  
|[CPrintInfo::m_dwFlags](#m_dwflags)|指定 DocObject 打印操作。|  
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|包含指向用户创建的结构的指针。|  
|[CPrintInfo::m_nCurPage](#m_ncurpage)|标识当前正在打印的页的页码。|  
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|指定由当前的打印作业操作系统分配的作业数|  
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|标识的预览窗口中; 中显示的页数1 或 2。|  
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|在组合的 DocObject 打印作业中指定特定文档的第一页的偏移的量。|  
|[CPrintInfo::m_pPD](#m_ppd)|包含一个指向`CPrintDialog`用于打印对话框中的对象。|  
|[CPrintInfo::m_rectDraw](#m_rectdraw)|指定定义当前可用页面区域的矩形。|  
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|包含页号显示的格式字符串。|  
  
## <a name="remarks"></a>备注  
 `CPrintInfo`是一种结构，并且没有基类的类。  
  
 框架将创建的对象`CPrintInfo`每次打印或打印预览命令将选择并在命令完成时才销毁它。  
  
 `CPrintInfo`包含有关打印作业作为一个整体，如要打印的页面范围和打印作业，如当前正在打印页上的当前状态的信息。 某些信息存储在相关联[CPrintDialog](../../mfc/reference/cprintdialog-class.md)对象; 此对象包含由用户在打印对话框中输入的值。  
  
 一个`CPrintInfo`对象在打印过程的框架和视图类之间传递，并且使用这两个之间交换信息。 例如，框架告知视图类要通过将分配到的值打印的文档的页`m_nCurPage`的成员`CPrintInfo`; 视图类检索的值并执行指定的页的实际打印。  
  
 另一个示例是在其文档的长度并不知晓直到打印这种情况。 在这种情况下，视图类测试文档末尾的每次打印一页。 当达到结束时，该视图类来设置`m_bContinuePrinting`的成员`CPrintInfo`到**FALSE**; 这将通知框架，以停止打印循环。  
  
 `CPrintInfo`成员函数使用`CView`列出在"另请参阅。" 有关由 Microsoft 基础类库提供的打印体系结构的详细信息，请参阅[框架窗口](../../mfc/frame-windows.md)和[文档/视图体系结构](../../mfc/document-view-architecture.md)和文章[打印](../../mfc/printing.md)和[打印︰ 多页文档](../../mfc/multipage-documents.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CPrintInfo`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxext.h  
  
##  <a name="a-namegetfrompagea--cprintinfogetfrompage"></a><a name="getfrompage"></a>CPrintInfo::GetFromPage  
 调用此函数可检索要打印的第一页的数目。  
  
```  
UINT GetFromPage() const;

 
```  
  
### <a name="return-value"></a>返回值  
 要打印的第一页的数量。  
  
### <a name="remarks"></a>备注  
 这是由用户在打印对话框中指定的值并存储在`CPrintDialog`所引用对象`m_pPD`成员。 如果用户未指定一个值，默认值为文档的第一页。  
  
##  <a name="a-namegetmaxpagea--cprintinfogetmaxpage"></a><a name="getmaxpage"></a>CPrintInfo::GetMaxPage  
 调用此函数可检索文档的最后一页的数目。  
  
```  
UINT GetMaxPage() const;

 
```  
  
### <a name="return-value"></a>返回值  
 该文档的最后一页的数量。  
  
### <a name="remarks"></a>备注  
 此值存储在`CPrintDialog`所引用对象`m_pPD`成员。  
  
##  <a name="a-namegetminpagea--cprintinfogetminpage"></a><a name="getminpage"></a>CPrintInfo::GetMinPage  
 调用此函数可检索文档的第一页的数目。  
  
```  
UINT GetMinPage() const;

 
```  
  
### <a name="return-value"></a>返回值  
 该文档的第一页的数量。  
  
### <a name="remarks"></a>备注  
 此值存储在`CPrintDialog`所引用对象`m_pPD`成员。  
  
##  <a name="a-namegetoffsetpagea--cprintinfogetoffsetpage"></a><a name="getoffsetpage"></a>CPrintInfo::GetOffsetPage  
 调用此函数可检索偏移量，从 DocObject 客户端打印多个 DocObject 项目时。  
  
```  
UINT GetOffsetPage() const;

 
```  
  
### <a name="return-value"></a>返回值  
 前面的第一页 DocObject 项组合的 DocObject 打印作业中打印的页数。  
  
### <a name="remarks"></a>备注  
 此值引用的**m_nOffsetPage**成员。 您的文档的第一页将为编号**m_nOffsetPage**值 + 1 作为 DocObject 与其他活动文档打印时。 **M_nOffsetPage**成员是有效才**m_bDocObject**值是**TRUE**。  
  
##  <a name="a-namegettopagea--cprintinfogettopage"></a><a name="gettopage"></a>CPrintInfo::GetToPage  
 调用此函数可检索要打印的最后一页的数目。  
  
```  
UINT GetToPage() const;

 
```  
  
### <a name="return-value"></a>返回值  
 要打印的最后一页的数量。  
  
### <a name="remarks"></a>备注  
 这是由用户在打印对话框中指定的值并存储在`CPrintDialog`所引用对象`m_pPD`成员。 如果用户未指定一个值，默认值为文档的最后一页。  
  
##  <a name="a-namembcontinueprintinga--cprintinfombcontinueprinting"></a><a name="m_bcontinueprinting"></a>CPrintInfo::m_bContinuePrinting  
 包含一个标志，指示框架是否应继续打印循环。  
  
### <a name="remarks"></a>备注  
 如果您正在执行打印时分页，您可以将此成员设置为**FALSE**的重写中`CView::OnPrepareDC`一旦到达文档结尾。 不需要修改此变量，如果已指定文档的打印作业使用开头的长度`SetMaxPage`成员函数。 `m_bContinuePrinting`成员是类型的公共变量**BOOL**。  
  
##  <a name="a-namembdirecta--cprintinfombdirect"></a><a name="m_bdirect"></a>CPrintInfo::m_bDirect  
 框架将此成员设置为**TRUE**如果打印对话框中将对于直接打印，则跳过**FALSE**否则为。  
  
### <a name="remarks"></a>备注  
 通常情况下跳过打印对话框，打印从 shell 或执行打印时使用的命令 ID **ID_FILE_PRINT_DIRECT**。  
  
 通常不会更改此成员，但如果您更改它，将其更改之前调用[CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting)的重写中[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)。  
  
##  <a name="a-namembdocobjecta--cprintinfombdocobject"></a><a name="m_bdocobject"></a>CPrintInfo::m_bDocObject  
 包含一个标志，指示正在打印的文档是否 DocObject。  
  
### <a name="remarks"></a>备注  
 数据成员`m_dwFlags`和**m_nOffsetPage**是无效的除非此标志，否则**TRUE**。  
  
##  <a name="a-namembpreviewa--cprintinfombpreview"></a><a name="m_bpreview"></a>CPrintInfo::m_bPreview  
 包含一个标志，指示是否正在预览文档。  
  
### <a name="remarks"></a>备注  
 这将由这取决于哪个命令用户执行的框架。 打印对话框中不显示打印预览作业。 **M_bPreview**成员是类型的公共变量**BOOL**。  
  
##  <a name="a-namemdwflagsa--cprintinfomdwflags"></a><a name="m_dwflags"></a>CPrintInfo::m_dwFlags  
 包含指定 DocObject 打印操作的标志的组合。  
  
### <a name="remarks"></a>备注  
 有效仅当数据成员**m_bDocObject**是**TRUE**。  
  
 这些标志可以是一个或多个下列值︰  
  
- **PRINTFLAG_MAYBOTHERUSER**  
  
- **PRINTFLAG_PROMPTUSER**  
  
- **PRINTFLAG_USERMAYCHANGEPRINTER**  
  
- **PRINTFLAG_RECOMPOSETODEVICE**  
  
- **PRINTFLAG_DONTACTUALLYPRINT**  
  
- **PRINTFLAG_FORCEPROPERTIES**  
  
- **PRINTFLAG_PRINTTOFILE**  
  
##  <a name="a-namemlpuserdataa--cprintinfomlpuserdata"></a><a name="m_lpuserdata"></a>CPrintInfo::m_lpUserData  
 包含指向用户创建的结构的指针。  
  
### <a name="remarks"></a>备注  
 可以使用此存储不希望将存储在您的视图类的特定于打印的数据。 **M_lpUserData**成员是类型的公共变量**LPVOID**。  
  
##  <a name="a-namemncurpagea--cprintinfomncurpage"></a><a name="m_ncurpage"></a>CPrintInfo::m_nCurPage  
 包含当前页的数目。  
  
### <a name="remarks"></a>备注  
 框架将调用`CView::OnPrepareDC`和`CView::OnPrint`一次为每个页面的文档中，指定其他值，此成员的每次; 其值的范围从返回的值`GetFromPage`到返回的`GetToPage`。 使用此成员中的替代`CView::OnPrepareDC`和`CView::OnPrint`要打印的文档指定的页。  
  
 当第一次调用预览模式时，框架将读取此成员以确定应最初预览文档的页的值。 您可以将此成员的值设置的重写中`CView::OnPreparePrinting`进入预览模式时保持在文档中的用户的当前位置。 `m_nCurPage`成员是类型的公共变量**UINT**。  
  
##  <a name="a-namemnjobnumbera--cprintinfomnjobnumber"></a><a name="m_njobnumber"></a>CPrintInfo::m_nJobNumber  
 指示由当前的打印作业的操作系统分配的作业编号。  
  
### <a name="remarks"></a>备注  
 此值可能为**SP_ERROR**如果作业尚未尚未打印 (即，如果`CPrintInfo`对象新构造，并且尚未尚未使用打印)，或者如果在启动作业时出错。  
  
##  <a name="a-namemnnumpreviewpagesa--cprintinfomnnumpreviewpages"></a><a name="m_nnumpreviewpages"></a>CPrintInfo::m_nNumPreviewPages  
 包含以预览模式; 显示的页数它可以是 1 或 2。  
  
### <a name="remarks"></a>备注  
 **M_nNumPreviewPages**成员是类型的公共变量**UINT**。  
  
##  <a name="a-namemnoffsetpagea--cprintinfomnoffsetpage"></a><a name="m_noffsetpage"></a>CPrintInfo::m_nOffsetPage  
 包含的组合的 DocObject 打印作业中的前特定 DocObject 的第一页的页面数。  
  
##  <a name="a-namemppda--cprintinfomppd"></a><a name="m_ppd"></a>CPrintInfo::m_pPD  
 包含一个指向`CPrintDialog`用来显示打印作业打印对话框中的对象。  
  
### <a name="remarks"></a>备注  
 `m_pPD`成员是公共变量声明为指向`CPrintDialog`。  
  
##  <a name="a-namemrectdrawa--cprintinfomrectdraw"></a><a name="m_rectdraw"></a>CPrintInfo::m_rectDraw  
 指定以逻辑坐标表示页上的可用绘图区域。  
  
### <a name="remarks"></a>备注  
 要在重写中引用 this `CView::OnPrint`。 您可以使用此成员来跟踪后打印页眉、 页脚和等等，哪一区域仍保持可用。 **M_rectDraw**成员是类型的公共变量`CRect`。  
  
##  <a name="a-namemstrpagedesca--cprintinfomstrpagedesc"></a><a name="m_strpagedesc"></a>CPrintInfo::m_strPageDesc  
 包含用来在打印预览，则为过程中显示的页码在格式字符串此字符串由两个子字符串，另一个用于单页显示对于双页显示，每个由 '\n' 字符结尾组成。  
  
### <a name="remarks"></a>备注  
 框架将使用作为默认值"页 %u\npages%u-%u\n"。 如果您希望另一种格式的页码，指定一个格式字符串中的重写`CView::OnPreparePrinting`。 **M_strPageDesc**成员是类型的公共变量`CString`。  
  
##  <a name="a-namesetmaxpagea--cprintinfosetmaxpage"></a><a name="setmaxpage"></a>CPrintInfo::SetMaxPage  
 调用此函数可指定文档的最后一页的数目。  
  
```  
void SetMaxPage(UINT nMaxPage);
```  
  
### <a name="parameters"></a>参数  
 *nMaxPage*  
 该文档的最后一页的数目。  
  
### <a name="remarks"></a>备注  
 此值存储在`CPrintDialog`所引用对象`m_pPD`成员。 如果它在打印之前，大家都知道文档的长度，从重写中调用此函数`CView::OnPreparePrinting`。 如果文档的长度取决于用户在打印对话框中指定的设置，则调用此函数的重写从`CView::OnBeginPrinting`。 如果文档的长度不知道它打印前，使用`m_bContinuePrinting`成员来控制打印循环。  
  
### <a name="example"></a>示例  
  请参阅示例[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)。  
  
##  <a name="a-namesetminpagea--cprintinfosetminpage"></a><a name="setminpage"></a>CPrintInfo::SetMinPage  
 调用此函数可指定文档的第一页的数目。  
  
```  
void SetMinPage(UINT nMinPage);
```  
  
### <a name="parameters"></a>参数  
 *nMinPage*  
 该文档的第一页的数目。  
  
### <a name="remarks"></a>备注  
 页码通常从 1 开始。 此值存储在`CPrintDialog`所引用对象`m_pPD`成员。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 DIBLOOK](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)   
 [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)   
 [CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)   
 [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)   
 [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)   
 [CView::OnPrint](../../mfc/reference/cview-class.md#onprint)




