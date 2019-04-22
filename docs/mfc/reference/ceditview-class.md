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
ms.openlocfilehash: 3ab276e83e8642aa5de2fd96305cb6d7b648fc40
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781232"
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
|[CEditView::FindText](#findtext)|字符串文本中搜索。|
|[CEditView::GetBufferLength](#getbufferlength)|获取字符缓冲区的长度。|
|[CEditView::GetEditCtrl](#geteditctrl)|提供对访问`CEdit`一部分`CEditView`（Windows 编辑控件） 的对象。|
|[CEditView::GetPrinterFont](#getprinterfont)|检索当前打印机字体。|
|[CEditView::GetSelectedText](#getselectedtext)|检索当前选定文本。|
|[CEditView::LockBuffer](#lockbuffer)|锁定缓冲区。|
|[CEditView::PrintInsideRect](#printinsiderect)|呈现给定矩形内的文本。|
|[CEditView::SerializeRaw](#serializeraw)|序列化`CEditView`为磁盘上原始文本的对象。|
|[CEditView::SetPrinterFont](#setprinterfont)|将新的打印机字体设置。|
|[CEditView::SetTabStops](#settabstops)|设置制表用于屏幕显示和打印。|
|[CEditView::UnlockBuffer](#unlockbuffer)|解除锁定缓冲区。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|查找下一个匹配项的文本字符串。|
|[CEditView::OnReplaceAll](#onreplaceall)|给定字符串的所有匹配项替换为新的字符串。|
|[CEditView::OnReplaceSel](#onreplacesel)|将替换当前所选内容。|
|[CEditView::OnTextNotFound](#ontextnotfound)|当无法匹配任何进一步的文本查找操作时调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|默认类型的对象的样式`CEditView`。|

## <a name="remarks"></a>备注

`CEditView`类提供以下附加功能：

- 打印。

- 查找和替换。

因为类`CEditView`由派生类`CView`，类的对象`CEditView`可以用于文档和文档模板。

每个`CEditView`控件的文本保存在其自己的全局内存对象。 你的应用程序可以具有任意数量的`CEditView`对象。

创建类型的对象`CEditView`如果您想要编辑窗口，上面列出的新增功能或你希望在简单的文本编辑器功能。 一个`CEditView`对象可能会在窗口的整个工作区。 派生您自己的类从`CEditView`添加或修改的基本功能，或声明可以添加到文档模板的类。

类的默认实现`CEditView`处理以下命令：ID_EDIT_SELECT_ALL、 ID_EDIT_FIND、 ID_EDIT_REPLACE、 ID_EDIT_REPEAT 和 ID_FILE_PRINT。

默认字符限制`CEditView`是 (1024年\*1024年-1 = 1048575)。 这可以通过调用基础编辑控件的 EM_LIMITTEXT 函数更改。 但是，限制取决于操作系统各不相同，并且类型的编辑控件 （单个或多行）。 有关这些限制的详细信息，请参阅[EM_LIMITTEXT](/windows/desktop/Controls/em-limittext)。

若要更改此限制在控件中的，重写`OnCreate()`函数在`CEditView`类，并插入以下代码行：

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

类型的对象`CEditView`(或派生自的类型的`CEditView`) 具有以下限制：

- `CEditView` 未实现 true 所见即所得 (WYSIWYG) 编辑。 在屏幕上的可读性和匹配的打印的输出之间存在一个选择的`CEditView`opts 的屏幕可读性。

- `CEditView` 可以在单个字体显示文本。 支持任何特殊字符格式设置。 请参阅类[CRichEditView](../../mfc/reference/cricheditview-class.md)的更强大的功能。

- 文本量`CEditView`可以包含限制。 限制均适用于作为`CEdit`控件。

有关详细信息`CEditView`，请参阅[派生视图类 MFC 中可用](../../mfc/derived-view-classes-available-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>要求

**标头：** afxext.h

##  <a name="ceditview"></a>  CEditView::CEditView

构造 `CEditView` 类型的对象。

```
CEditView();
```

### <a name="remarks"></a>备注

构造对象之后, 必须调用[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)函数之前使用编辑控件。 如果派生的类从`CEditView`并将其添加到模板使用`CWinApp::AddDocTemplate`，框架将调用这两个此构造函数和`Create`函数。

##  <a name="dwstyledefault"></a>  CEditView::dwStyleDefault

包含的默认样式`CEditView`对象。

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>备注

将传递作为此静态成员*dwStyle*的参数`Create`函数可获得的默认样式为`CEditView`对象。

##  <a name="findtext"></a>  CEditView::FindText

调用`FindText`函数搜索`CEditView`对象的文本缓冲区。

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要找的文本。

*bNext*<br/>
指定搜索的方向。 如果为 TRUE，搜索方向为向缓冲区末尾的方向。 如果为 FALSE，则搜索方向是缓冲区的开头。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE，则搜索是区分大小写。 如果为 FALSE，则搜索不区分大小写。

### <a name="return-value"></a>返回值

如果找到搜索文本，则非零值否则为 0。

### <a name="remarks"></a>备注

此函数的文本搜索中指定的文本的缓冲区*lpszFind*，开始时指定的方向中的当前选定*bNext*，并使用由指定的大小写规则*bCase*。 如果找到了文本，它将所选内容设置为所找到文本，并返回一个非零值。 如果没有找到文本，该函数将返回 0。

通常情况下不需要调用`FindText`函数，除非您重写`OnFindNext`，它调用`FindText`。

##  <a name="getbufferlength"></a>  CEditView::GetBufferLength

调用此成员函数可获取当前在编辑控件的缓冲区中不包括 null 终止符的字符数。

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>返回值

缓冲区中的字符串的长度。

##  <a name="geteditctrl"></a>  CEditView::GetEditCtrl

调用`GetEditCtrl`以获取对使用编辑视图的编辑控件的引用。

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>返回值

对 `CEdit` 对象的引用。

### <a name="remarks"></a>备注

此控件是类型[CEdit](../../mfc/reference/cedit-class.md)，因此您可以操作 Windows 编辑控件直接使用`CEdit`成员函数。

> [!CAUTION]
>  使用`CEdit`对象可以更改状态的基础 Windows 编辑控件。 例如，不应更改使用的选项卡上设置[CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops)函数，因为`CEditView`缓存使用编辑控件中并在打印中的这些设置。 请改用[CEditView::SetTabStops](#settabstops)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

##  <a name="getprinterfont"></a>  CEditView::GetPrinterFont

调用`GetPrinterFont`若要获取指向的指针[CFont](../../mfc/reference/cfont-class.md)对象，描述当前打印机字体。

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>返回值

一个指向`CFont`对象，它指定当前的打印机字体;如果尚未设置打印机字体，则为 NULL。 该指针可能是暂时的，不应存储起来供将来使用。

### <a name="remarks"></a>备注

如果打印机字体尚未设置，默认打印行为的`CEditView`类是使用用于显示的相同字体进行打印。

使用此函数来确定当前的打印机字体。 如果不需的打印机字体，请使用[CEditView::SetPrinterFont](#setprinterfont)若要对其进行更改。

##  <a name="getselectedtext"></a>  CEditView::GetSelectedText

调用`GetSelectedText`复制到所选的文本`CString`对象，所选内容或选定内容中前面的第一个回车符的字符的字符结束。

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>参数

*strResult*<br/>
对引用`CString`要接收所选的文本的对象。

##  <a name="lockbuffer"></a>  CEditView::LockBuffer

调用此成员函数以获取指向缓冲区的指针。 不应修改缓冲区。

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>返回值

指向编辑控件的缓冲区的指针。

##  <a name="onfindnext"></a>  CEditView::OnFindNext

搜索指定的文本的缓冲区中的文本*lpszFind*，在指定的方向*bNext*，使用指定的大小写规则*bCase*。

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要找的文本。

*bNext*<br/>
指定搜索的方向。 如果为 TRUE，搜索方向为向缓冲区末尾的方向。 如果为 FALSE，则搜索方向是缓冲区的开头。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE，则搜索是区分大小写。 如果为 FALSE，则搜索不区分大小写。

### <a name="remarks"></a>备注

搜索当前所选内容的开头开始，并通过调用来实现[FindText](#findtext)。 在默认实现中，`OnFindNext`调用[OnTextNotFound](#ontextnotfound)如果找不到文本。

重写`OnFindNext`若要更改的方式`CEditView`-派生的对象中搜索文本。 `CEditView` 调用`OnFindNext`当用户选择在标准的查找对话框的查找下一步按钮。

##  <a name="onreplaceall"></a>  CEditView::OnReplaceAll

`CEditView` 调用`OnReplaceAll`当用户在标准的替换对话框中选择全部替换按钮。

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要找的文本。

*lpszReplace*<br/>
要替换搜索文本的文本。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE，则搜索是区分大小写。 如果为 FALSE，则搜索不区分大小写。

### <a name="remarks"></a>备注

`OnReplaceAll` 搜索指定的文本的缓冲区中的文本*lpszFind*，使用指定的大小写规则*bCase*。 当前所选内容的开头开始搜索。 每次找到搜索文本时，此函数使用指定的文本替换该匹配项的文本*lpszReplace*。 搜索通过调用[FindText](#findtext)。 在默认实现中， [OnTextNotFound](#ontextnotfound)如果没有找到文本，则调用。

如果当前所选内容不匹配*lpszFind*，所选内容将更新为指定的文本的第一个匹配项*lpszFind* ，并且不执行替换。 这允许用户确认这是他们想要选择与要替换的文本不匹配时执行的操作。

重写`OnReplaceAll`若要更改的方式`CEditView`-派生的对象替换的文本。

##  <a name="onreplacesel"></a>  CEditView::OnReplaceSel

`CEditView` 调用`OnReplaceSel`当用户在标准的替换对话框中选择替换按钮。

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要找的文本。

*bNext*<br/>
指定搜索的方向。 如果为 TRUE，搜索方向为向缓冲区末尾的方向。 如果为 FALSE，则搜索方向是缓冲区的开头。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE，则搜索是区分大小写。 如果为 FALSE，则搜索不区分大小写。

*lpszReplace*<br/>
要替换所找到的文本的文本。

### <a name="remarks"></a>备注

替换之后所选内容，此函数的文本搜索中指定的文本的下一个匹配项的缓冲区*lpszFind*，在指定的方向*bNext*，区分大小写通过指定*bCase*。 搜索通过调用[FindText](#findtext)。 如果未找到文本， [OnTextNotFound](#ontextnotfound)调用。

重写`OnReplaceSel`若要更改的方式`CEditView`-派生的对象替换所选的文本。

##  <a name="ontextnotfound"></a>  CEditView::OnTextNotFound

重写此函数可更改默认实现，它将调用 Windows 函数`MessageBeep`。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要找的文本。

##  <a name="printinsiderect"></a>  CEditView::PrintInsideRect

调用`PrintInsideRect`打印文本中指定的矩形*rectLayout*。

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向打印机设备上下文指针。

*rectLayout*<br/>
引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT 结构](/windows/desktop/api/windef/ns-windef-tagrect)指定是用来呈现文本的矩形。

*nIndexStart*<br/>
要呈现的第一个字符的缓冲区中的索引。

*nIndexStop*<br/>
后面要呈现的最后一个字符的字符缓冲区中的索引。

### <a name="return-value"></a>返回值

要打印的下一个字符的索引 （即后面呈现的最后一个字符的字符）。

### <a name="remarks"></a>备注

如果`CEditView`控件没有样式 ES_AUTOHSCROLL、 文本换行呈现矩形内。 如果控件将样式 ES_AUTOHSCROLL，文本被截断的矩形的右边缘。

`rect.bottom`的元素*rectLayout*对象发生变化，因此矩形的尺寸定义原始文本所占用的矩形的一部分。

##  <a name="serializeraw"></a>  CEditView::SerializeRaw

调用`SerializeRaw`能够`CArchive`对象读取或写入的文本`CEditView`到文本文件的对象。

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
引用`CArchive`对象，它存储序列化的文本。

### <a name="remarks"></a>备注

`SerializeRaw` 不同于`CEditView`的内部实现`Serialize`，它读取和写入纯文本，而无需上述对象说明数据。

##  <a name="setprinterfont"></a>  CEditView::SetPrinterFont

调用`SetPrinterFont`若要设置到由指定的字体的打印机字体*pFont*。

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
指向类型的对象的指针`CFont`。 如果为 NULL，用于打印的字体为基础的显示字体。

### <a name="remarks"></a>备注

如果希望始终使用特定字体打印视图，包括对`SetPrinterFont`在类的`OnPreparePrinting`函数。 此虚拟函数调用打印之前，因此字体更改发生之前打印视图的内容。

##  <a name="settabstops"></a>  CEditView::SetTabStops

调用此函数可设置用于显示和打印的制表位。

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>参数

*nTabStops*<br/>
每个制表位，以对话框单元的宽度。

### <a name="remarks"></a>备注

支持只是一个单一的制表位宽度。 (`CEdit`对象支持多个选项卡宽度。)宽度是字体的采用对话框单位等于 1 / 4 的打印或显示时使用的平均字符宽度 （基于大写和小写字母字符仅）。 不应使用`CEdit::SetTabStops`因为`CEditView`必须缓存制表位值。

此函数修改仅为其调用的对象的选项卡。 若要更改选项卡停止每个`CEditView`对象在应用程序中，请调用每个对象的`SetTabStops`函数。

### <a name="example"></a>示例

此代码片段通过仔细测量该控件使用的字体的每个第四个字符到控件中设置制表位。

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

##  <a name="unlockbuffer"></a>  CEditView::UnlockBuffer

调用此成员函数以解锁缓冲区。

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>备注

调用`UnlockBuffer`完成使用返回的指针后[LockBuffer](#lockbuffer)。

## <a name="see-also"></a>请参阅

[MFC 示例 SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CEdit 类](../../mfc/reference/cedit-class.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView 类](../../mfc/reference/cricheditview-class.md)
