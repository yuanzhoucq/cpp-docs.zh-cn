---
title: CEditView 类
ms.date: 11/04/2016
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
ms.openlocfilehash: e9b7dea980e607c776e2d50c679042c765080fdb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506727"
---
# <a name="ceditview-class"></a>CEditView 类

视图类的类型，提供 Windows 编辑控件功能并可用于实现简单的文本编辑器功能。

## <a name="syntax"></a>语法

```
class CEditView : public CCtrlView
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CEditView::CEditView](#ceditview)|构造 `CEditView` 类型的对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CEditView::FindText](#findtext)|搜索文本中的字符串。|
|[CEditView::GetBufferLength](#getbufferlength)|获取字符缓冲区的长度。|
|[CEditView::GetEditCtrl](#geteditctrl)|提供对`CEdit` `CEditView`对象 (Windows 编辑控件) 的部分的访问。|
|[CEditView::GetPrinterFont](#getprinterfont)|检索当前打印机字体。|
|[CEditView::GetSelectedText](#getselectedtext)|检索当前选定文本。|
|[CEditView::LockBuffer](#lockbuffer)|锁定缓冲区。|
|[CEditView::PrintInsideRect](#printinsiderect)|在给定矩形内呈现文本。|
|[CEditView::SerializeRaw](#serializeraw)|`CEditView`将对象作为原始文本序列化到磁盘。|
|[CEditView::SetPrinterFont](#setprinterfont)|设置新的打印机字体。|
|[CEditView::SetTabStops](#settabstops)|为屏幕显示和打印设置制表位。|
|[CEditView::UnlockBuffer](#unlockbuffer)|锁定缓冲区。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|查找文本字符串的下一个匹配项。|
|[CEditView::OnReplaceAll](#onreplaceall)|将出现的所有给定字符串替换为新字符串。|
|[CEditView::OnReplaceSel](#onreplacesel)|替换当前选定内容。|
|[CEditView::OnTextNotFound](#ontextnotfound)|当查找操作无法匹配任何其他文本时调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|类型`CEditView`的对象的默认样式。|

## <a name="remarks"></a>备注

`CEditView`类提供以下附加函数:

- 出来.

- 查找和替换。

由于类`CEditView`是类`CView`的派生类, 因此类`CEditView`的对象可与文档和文档模板一起使用。

每`CEditView`个控件的文本将保存在其自己的全局内存对象中。 应用程序可以具有任意数量的`CEditView`对象。

如果需要具有上面`CEditView`列出的已添加功能的编辑窗口, 或者需要简单的文本编辑器功能, 请创建类型的对象。 `CEditView`对象可以占据窗口的整个工作区。 从`CEditView`派生你自己的类, 以添加或修改基本功能, 或声明可添加到文档模板的类。

类`CEditView`的默认实现将处理以下命令:ID_EDIT_SELECT_ALL、ID_EDIT_FIND、ID_EDIT_REPLACE、ID_EDIT_REPEAT 和 ID_FILE_PRINT。

的默认字符限制`CEditView`为 (1024 \* 1024-1 = 1048575)。 这可以通过调用基础编辑控件的 EM_LIMITTEXT 函数进行更改。 但是, 限制会有所不同, 具体取决于操作系统和编辑控件的类型 (单个或多行)。 有关这些限制的详细信息, 请参阅[EM_LIMITTEXT](/windows/win32/Controls/em-limittext)。

若要更改控件中的此限制, 请`OnCreate()`重写`CEditView`类的函数并插入以下代码行:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

类型`CEditView`的对象 (或派生自`CEditView`的类型的对象) 具有以下限制:

- `CEditView`不实现 true 你所看到的内容是你所见即所得 (WYSIWYG) 编辑。 在屏幕上的可读性和打印输出之间进行选择时, 选择 " `CEditView`屏幕可读性"。

- `CEditView`只能显示单个字体中的文本。 不支持特殊字符格式设置。 有关更多功能, 请参阅类[CRichEditView](../../mfc/reference/cricheditview-class.md) 。

- `CEditView`可以包含的文本量受到限制。 此限制与`CEdit`控件的限制相同。

有关的详细信息`CEditView`, 请参阅[MFC 中可用的派生视图类](../../mfc/derived-view-classes-available-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>要求

**标头:** afxext。h

##  <a name="ceditview"></a>CEditView:: CEditView

构造 `CEditView` 类型的对象。

```
CEditView();
```

### <a name="remarks"></a>备注

构造对象之后, 必须先调用[CWnd:: Create](../../mfc/reference/cwnd-class.md#create)函数, 然后才能使用编辑控件。 如果从`CEditView`派生类并使用`CWinApp::AddDocTemplate`将其添加到模板中, 则框架将调用此构造函数和`Create`函数。

##  <a name="dwstyledefault"></a>CEditView::d wStyleDefault

包含`CEditView`对象的默认样式。

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>备注

将此静态成员作为`Create`函数的*dwStyle*参数传递, 以获取该`CEditView`对象的默认样式。

##  <a name="findtext"></a>CEditView:: FindText

调用函数, `CEditView`搜索对象的文本缓冲区。 `FindText`

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要查找的文本。

*bNext*<br/>
指定搜索的方向。 如果为 TRUE, 则搜索方向朝向缓冲区的末尾。 如果为 FALSE, 则搜索方向朝向缓冲区的开头。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE, 则搜索区分大小写。 如果为 FALSE, 则搜索不区分大小写。

### <a name="return-value"></a>返回值

如果找到搜索文本, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此函数在缓冲区中的文本中搜索*lpszFind*指定的文本, 从当前所选内容开始, 按*bNext*指定的方向, 并使用*bCase*指定的区分大小写。 如果找到文本, 它会将所选内容设置为找到的文本并返回一个非零值。 如果未找到文本, 则函数返回0。

通常不需要调用`FindText`函数, 除非重写`OnFindNext`, 这将调用`FindText`。

##  <a name="getbufferlength"></a>CEditView:: GetBufferLength

调用此成员函数以获取编辑控件缓冲区中当前包含的字符数, 不包括 null 终止符。

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>返回值

缓冲区中的字符串的长度。

##  <a name="geteditctrl"></a>CEditView:: GetEditCtrl

调用`GetEditCtrl`以获取对 "编辑" 视图使用的编辑控件的引用。

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>返回值

对 `CEdit` 对象的引用。

### <a name="remarks"></a>备注

此控件的类型为[CEdit](../../mfc/reference/cedit-class.md), 因此可以使用`CEdit`成员函数直接操作 Windows 编辑控件。

> [!CAUTION]
>  `CEdit`使用对象可以更改基本 Windows 编辑控件的状态。 例如, 不应使用[CEdit:: SetTabStops](../../mfc/reference/cedit-class.md#settabstops)函数更改选项卡设置, 因为`CEditView`缓存这些设置以在编辑控件和打印中使用两者。 改为使用[CEditView:: SetTabStops](#settabstops)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

##  <a name="getprinterfont"></a>CEditView:: GetPrinterFont

调用`GetPrinterFont`以获取指向描述当前打印机字体的[CFont](../../mfc/reference/cfont-class.md)对象的指针。

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>返回值

指向`CFont`对象的指针, 该对象指定当前打印机字体;如果尚未设置打印机字体, 则为 NULL。 该指针可能是暂时的，不应存储起来供将来使用。

### <a name="remarks"></a>备注

如果尚未设置打印机字体, 则`CEditView`类的默认打印行为是使用用于显示的相同字体打印。

使用此函数可确定当前打印机的字体。 如果不是所需的打印机字体, 请使用[CEditView:: SetPrinterFont](#setprinterfont)对其进行更改。

##  <a name="getselectedtext"></a>CEditView:: GetSelectedText

调用`GetSelectedText`可将所选文本`CString`复制到对象中, 直至所选内容的末尾或第一个回车符前面的字符。

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>参数

*strResult*<br/>
对接收所选`CString`文本的对象的引用。

##  <a name="lockbuffer"></a>CEditView:: LockBuffer

调用此成员函数以获取指向缓冲区的指针。 不应修改该缓冲区。

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>返回值

指向编辑控件缓冲区的指针。

##  <a name="onfindnext"></a>CEditView:: OnFindNext

在缓冲区中搜索*lpszFind*指定的文本的缓冲区中的文本, 并在*bNext*指定的方向上按照*bCase*指定的区分大小写。

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要查找的文本。

*bNext*<br/>
指定搜索的方向。 如果为 TRUE, 则搜索方向朝向缓冲区的末尾。 如果为 FALSE, 则搜索方向朝向缓冲区的开头。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE, 则搜索区分大小写。 如果为 FALSE, 则搜索不区分大小写。

### <a name="remarks"></a>备注

搜索从当前所选内容的开头开始, 并通过调用[FindText](#findtext)来完成。 在默认实现中, `OnFindNext`如果未找到文本, 则调用[OnTextNotFound](#ontextnotfound) 。

重`OnFindNext`写以更改派生对象`CEditView`搜索文本的方式。 `CEditView`当`OnFindNext`用户选择 "标准查找" 对话框中的 "查找下一个" 按钮时调用。

##  <a name="onreplaceall"></a>CEditView:: OnReplaceAll

`CEditView`当`OnReplaceAll`用户选择 "标准替换" 对话框中的 "全部替换" 按钮时调用。

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要查找的文本。

*lpszReplace*<br/>
要替换搜索文本的文本。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE, 则搜索区分大小写。 如果为 FALSE, 则搜索不区分大小写。

### <a name="remarks"></a>备注

`OnReplaceAll`在缓冲区中搜索*lpszFind*指定的文本, 并在*bCase*指定的情况下区分大小写。 搜索从当前所选内容的开头开始。 每次找到搜索文本时, 此函数就会将该文本的出现替换为*lpszReplace*指定的文本。 搜索是通过调用[FindText](#findtext)来完成的。 在默认实现中, 如果未找到文本, 则会调用[OnTextNotFound](#ontextnotfound) 。

如果当前所选内容与*lpszFind*不匹配, 则会将所选内容更新为*lpszFind*指定的文本的第一个匹配项, 并且不会执行 replace。 这允许用户确认在所选内容与要替换的文本不匹配时要执行的操作。

重`OnReplaceAll`写以更改派生对象`CEditView`替换文本的方式。

##  <a name="onreplacesel"></a>CEditView:: OnReplaceSel

`CEditView`当`OnReplaceSel`用户在 "标准替换" 对话框中选择 "替换" 按钮时调用。

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要查找的文本。

*bNext*<br/>
指定搜索的方向。 如果为 TRUE, 则搜索方向朝向缓冲区的末尾。 如果为 FALSE, 则搜索方向朝向缓冲区的开头。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE, 则搜索区分大小写。 如果为 FALSE, 则搜索不区分大小写。

*lpszReplace*<br/>
用于替换所找到文本的文本。

### <a name="remarks"></a>备注

替换所选内容后, 此函数将在缓冲区中的文本中搜索*lpszFind*指定的文本的下一个匹配项, 并以由 *bCase*指定的区分大小写。 搜索是通过调用[FindText](#findtext)来完成的。 如果未找到文本, 则调用[OnTextNotFound](#ontextnotfound) 。

重`OnReplaceSel`写以更改派生对象`CEditView`替换所选文本的方式。

##  <a name="ontextnotfound"></a>CEditView:: OnTextNotFound

重写此函数以更改调用 Windows 函数`MessageBeep`的默认实现。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要查找的文本。

##  <a name="printinsiderect"></a>CEditView::P rintInsideRect

调用`PrintInsideRect`以打印*rectLayout*指定的矩形中的文本。

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向打印机设备上下文的指针。

*rectLayout*<br/>
对[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT 结构](/windows/win32/api/windef/ns-windef-rect)的引用, 指定要在其中呈现文本的矩形。

*nIndexStart*<br/>
要呈现的第一个字符的缓冲区中的索引。

*nIndexStop*<br/>
在要呈现的最后一个字符之后的字符缓冲区中的索引。

### <a name="return-value"></a>返回值

要打印的下一个字符的索引 (即, 最后呈现的字符之后的字符)。

### <a name="remarks"></a>备注

`CEditView`如果控件不具有样式 ES_AUTOHSCROLL, 则在呈现矩形内环绕文本。 如果控件具有 ES_AUTOHSCROLL 样式, 则将在矩形的右边缘剪切文本。

更改*rectLayout*对象的元素,以使矩形的维度定义由文本占用的原始矩形部分。`rect.bottom`

##  <a name="serializeraw"></a>CEditView:: SerializeRaw

调用`SerializeRaw`以`CEditView`使对象在对象中读取或写入文本文件中的文本。 `CArchive`

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
对存储序列化文本的对象的引用。`CArchive`

### <a name="remarks"></a>备注

`SerializeRaw`不同于`CEditView`的的内部`Serialize`实现, 因为它仅读取并写入文本, 而不包含之前的对象说明数据。

##  <a name="setprinterfont"></a>CEditView:: SetPrinterFont

调用`SetPrinterFont`将打印机字体设置为*pFont*指定的字体。

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
指向类型`CFont`的对象的指针。 如果为 NULL, 则用于打印的字体基于显示字体。

### <a name="remarks"></a>备注

如果希望视图始终使用特定字体进行打印, 请在类的`SetPrinterFont` `OnPreparePrinting`函数中包含对的调用。 此虚函数在打印之前被调用, 因此, 字体更改发生在视图内容打印之前。

##  <a name="settabstops"></a>CEditView:: SetTabStops

调用此函数可设置用于显示和打印的制表位。

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>参数

*nTabStops*<br/>
每个制表位的宽度 (以对话框单位为单位)。

### <a name="remarks"></a>备注

仅支持单一的制表位宽度。 ( `CEdit`对象支持多个制表符宽度。)宽度采用对话单位, 这等于打印或显示时使用的字体的第四个字符 (仅基于大写字母和小写字母字符)。 不应使用`CEdit::SetTabStops` , 因为`CEditView`必须缓存制表位值。

此函数仅修改为其调用该函数的对象的选项卡。 若要更改应用程序中每`CEditView`个对象的制表位, 请调用每`SetTabStops`个对象的函数。

### <a name="example"></a>示例

此代码片段通过仔细度量控件使用的字体, 将控件中的制表位设置为每个第四个字符。

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

##  <a name="unlockbuffer"></a>CEditView:: UnlockBuffer

调用此成员函数以解锁缓冲区。

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>备注

使用`UnlockBuffer` [LockBuffer](#lockbuffer)返回的指针完成后调用。

## <a name="see-also"></a>请参阅

[MFC 示例 SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CEdit 类](../../mfc/reference/cedit-class.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView 类](../../mfc/reference/cricheditview-class.md)
