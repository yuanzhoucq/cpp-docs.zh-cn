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
ms.openlocfilehash: 33b5975eea534eeaf308f73b5ca7fca2cd76787f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753196"
---
# <a name="ceditview-class"></a>CEditView 类

视图类的类型，提供 Windows 编辑控件功能并可用于实现简单的文本编辑器功能。

## <a name="syntax"></a>语法

```
class CEditView : public CCtrlView
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[编辑视图：编辑视图](#ceditview)|构造 `CEditView` 类型的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[编辑视图：查找文本](#findtext)|搜索文本中的字符串。|
|[编辑视图：获取缓冲区长度](#getbufferlength)|获取字符缓冲区的长度。|
|[编辑视图：获取编辑](#geteditctrl)|提供对`CEdit``CEditView`对象部分（Windows 编辑控件）的访问。|
|[编辑视图：：获取打印机字体](#getprinterfont)|检索当前打印机字体。|
|[编辑视图：获取选定文本](#getselectedtext)|检索当前文本选择。|
|[CEditView：锁缓冲器](#lockbuffer)|锁定缓冲区。|
|[CEditView：:P林特内斯特](#printinsiderect)|在给定矩形内渲染文本。|
|[CEditView：序列化](#serializeraw)|将`CEditView`对象序列化为原始文本。|
|[编辑视图：：设置打印机字体](#setprinterfont)|设置新的打印机字体。|
|[编辑视图：：设置标签](#settabstops)|设置屏幕显示和打印的制表位。|
|[CEditView：解锁缓冲区](#unlockbuffer)|解锁缓冲区。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[编辑视图：：在查找下一个](#onfindnext)|查找文本字符串的下一个匹配项。|
|[编辑视图：：全部更换](#onreplaceall)|将给定字符串的所有匹配项替换为新字符串。|
|[编辑视图：打开替换塞尔](#onreplacesel)|替换当前选择。|
|[编辑视图：：未找到文本](#ontextnotfound)|当查找操作无法与任何进一步文本匹配时调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CEditView：:dwStyle默认](#dwstyledefault)|类型`CEditView`对象的默认样式。|

## <a name="remarks"></a>备注

该`CEditView`类提供以下附加功能：

- 打印。

- 查找和替换。

由于类`CEditView`是类`CView`的派生，类`CEditView`的对象可以与文档和文档模板一起使用。

每个`CEditView`控件的文本都保存在其自己的全局内存对象中。 应用程序可以具有任意数量的`CEditView`对象。

如果需要具有上面列出的`CEditView`添加功能的编辑窗口，或者想要简单的文本编辑器功能，请创建类型对象。 对象`CEditView`可以占用窗口的整个工作区。 派生`CEditView`您自己的类，用于添加或修改基本功能，或声明可添加到文档模板的类。

类`CEditView`的默认实现处理以下命令：ID_EDIT_SELECT_ALL、ID_EDIT_FIND、ID_EDIT_REPLACE、ID_EDIT_REPEAT 和ID_FILE_PRINT。

的`CEditView`默认字符限制为 （1024 \* 1024 - 1 = 1048575）。 这可以通过调用基础编辑控件的EM_LIMITTEXT函数来更改。 但是，根据操作系统和编辑控件的类型（单行或多行）的不同，限制是不同的。 有关这些限制的详细信息，请参阅[EM_LIMITTEXT](/windows/win32/Controls/em-limittext)。

若要在控件中更改此限制，请重写`OnCreate()``CEditView`类的函数并插入以下代码行：

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

类型`CEditView`（或派生自`CEditView`的类型）的对象具有以下限制：

- `CEditView`不能实现真实的，你所看到的是你得到的 （WYSIWYG） 编辑。 如果在屏幕上可以选择可读性与匹配的打印输出，`CEditView`则选择屏幕可读性。

- `CEditView`只能以一种字体显示文本。 不支持特殊字符格式。 有关更强大的功能，请参阅类[CRichEditView。](../../mfc/reference/cricheditview-class.md)

- `CEditView`可以包含的文本量是有限的。 限制与`CEdit`控件相同。

有关 的详细信息`CEditView`，请参阅[MFC 中可用的派生视图类](../../mfc/derived-view-classes-available-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="ceditviewceditview"></a><a name="ceditview"></a>编辑视图：编辑视图

构造 `CEditView` 类型的对象。

```
CEditView();
```

### <a name="remarks"></a>备注

构造对象后，必须先调用[CWnd：：创建](../../mfc/reference/cwnd-class.md#create)函数，然后才能使用编辑控件。 如果派生`CEditView`类并使用 将其添加到模板`CWinApp::AddDocTemplate`，则框架将调用此构造函数和`Create`函数。

## <a name="ceditviewdwstyledefault"></a><a name="dwstyledefault"></a>CEditView：:dwStyle默认

包含`CEditView`对象的默认样式。

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>备注

将此静态成员作为`Create`函数的*dwStyle*参数传递，`CEditView`以获取对象的默认样式。

## <a name="ceditviewfindtext"></a><a name="findtext"></a>编辑视图：查找文本

调用函数`FindText`以搜索`CEditView`对象的文本缓冲区。

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要找到的文本。

*b下一个*<br/>
指定搜索的方向。 如果为 TRUE，则搜索方向朝向缓冲区的末尾。 如果 FALSE，则搜索方向朝向缓冲区的开头。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE，则搜索区分大小写。 如果 FALSE，则搜索不区分大小写。

### <a name="return-value"></a>返回值

如果找到搜索文本，则非零;否则 0。

### <a name="remarks"></a>备注

此函数在缓冲区中搜索*lpszFind*指定的文本，从当前选择开始，按照*bNext*指定的方向，以及*bCase*指定的区分大小写。 如果找到文本，它将所选内容设置到找到的文本并返回非零值。 如果未找到文本，则函数返回 0。

通常不需要调用 函数，`FindText`除非您重写`OnFindNext`调用`FindText`。

## <a name="ceditviewgetbufferlength"></a><a name="getbufferlength"></a>编辑视图：获取缓冲区长度

调用此成员函数以获取编辑控件缓冲区中当前字符数，不包括空终止符。

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>返回值

缓冲区中字符串的长度。

## <a name="ceditviewgeteditctrl"></a><a name="geteditctrl"></a>编辑视图：获取编辑

调用`GetEditCtrl`以获取对编辑视图使用的编辑控件的引用。

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>返回值

对 `CEdit` 对象的引用。

### <a name="remarks"></a>备注

此控件的类型为[CEdit](../../mfc/reference/cedit-class.md)，因此您可以直接使用`CEdit`成员函数操作 Windows 编辑控件。

> [!CAUTION]
> 使用对象`CEdit`可以更改基础 Windows 编辑控件的状态。 例如，不应使用[CEdit：SetTabStops](../../mfc/reference/cedit-class.md#settabstops)函数更改选项卡设置，因为`CEditView`缓存这些设置以便在编辑控件和打印中使用。 而是使用[CEditView：：设置 TabStop](#settabstops)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

## <a name="ceditviewgetprinterfont"></a><a name="getprinterfont"></a>编辑视图：：获取打印机字体

调用`GetPrinterFont`以获取指向描述当前打印机字体的[CFont](../../mfc/reference/cfont-class.md)对象的指针。

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>返回值

指向指定当前打印机`CFont`字体的对象的指针;如果未设置打印机字体，则为 NULL。 该指针可能是暂时的，不应存储起来供将来使用。

### <a name="remarks"></a>备注

如果未设置打印机字体，`CEditView`则类的默认打印行为是使用用于显示的相同字体进行打印。

使用此函数确定当前打印机字体。 如果它不是所需的打印机字体，请使用[CEditView：setPrinterFont](#setprinterfont)来更改它。

## <a name="ceditviewgetselectedtext"></a><a name="getselectedtext"></a>编辑视图：获取选定文本

调用`GetSelectedText`以将所选文本复制到`CString`对象中，最多到所选内容的末尾或所选内容中第一个回车字符前面的字符。

```cpp
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>参数

*strResult*<br/>
对要接收所选`CString`文本的对象的引用。

## <a name="ceditviewlockbuffer"></a><a name="lockbuffer"></a>CEditView：锁缓冲器

调用此成员函数以获取指向缓冲区的指针。 不应修改缓冲区。

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>返回值

指向编辑控件缓冲区的指针。

## <a name="ceditviewonfindnext"></a><a name="onfindnext"></a>编辑视图：：在查找下一个

在缓冲区中搜索*lpszFind*指定的文本，按照*bNext*指定的方向搜索文本，由*bCase*指定区分大小写。

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要找到的文本。

*b下一个*<br/>
指定搜索的方向。 如果为 TRUE，则搜索方向朝向缓冲区的末尾。 如果 FALSE，则搜索方向朝向缓冲区的开头。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE，则搜索区分大小写。 如果 FALSE，则搜索不区分大小写。

### <a name="remarks"></a>备注

搜索从当前选择的开头开始，并通过调用[FindText](#findtext)来完成。 在默认实现中，`OnFindNext`如果未找到文本，则调用[OnTextNot。](#ontextnotfound)

重写`OnFindNext`以更改`CEditView`派生对象搜索文本的方式。 `CEditView`当用户`OnFindNext`在标准"查找"对话框中选择"查找下一步"按钮时调用。

## <a name="ceditviewonreplaceall"></a><a name="onreplaceall"></a>编辑视图：：全部更换

`CEditView`当用户`OnReplaceAll`在标准"替换"对话框中选择"全部替换"按钮时调用。

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要找到的文本。

*lpsz替换*<br/>
要替换搜索文本的文本。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE，则搜索区分大小写。 如果 FALSE，则搜索不区分大小写。

### <a name="remarks"></a>备注

`OnReplaceAll`在缓冲区中搜索*lpszFind*指定的文本的文本，由*bCase*指定区分大小写。 搜索从当前选择的开头开始。 每次找到搜索文本时，此函数都会将文本的匹配项替换为*lpszReplace*指定的文本。 搜索是通过调用[FindText](#findtext)来完成的。 在默认实现中，如果未找到文本，则调用[OnTextNotFound。](#ontextnotfound)

如果当前选择与*lpszFind*不匹配，则所选内容将更新为*lpszFind*指定的文本的第一次出现，并且不执行替换。 这允许用户确认这是他们想要做的，当选择与要替换的文本不匹配时。

重写`OnReplaceAll`以更改`CEditView`派生对象替换文本的方式。

## <a name="ceditviewonreplacesel"></a><a name="onreplacesel"></a>编辑视图：打开替换塞尔

`CEditView`当用户`OnReplaceSel`在标准"替换"对话框中选择"替换"按钮时调用。

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要找到的文本。

*b下一个*<br/>
指定搜索的方向。 如果为 TRUE，则搜索方向朝向缓冲区的末尾。 如果 FALSE，则搜索方向朝向缓冲区的开头。

*bCase*<br/>
指定搜索是否区分大小写。 如果为 TRUE，则搜索区分大小写。 如果 FALSE，则搜索不区分大小写。

*lpsz替换*<br/>
要替换找到的文本的文本。

### <a name="remarks"></a>备注

替换所选内容后，此函数在缓冲区中搜索文本，以*bNext*指定的方向，按照*bNext*指定的方式，以 bCase 指定的区分大小写为下一次出现*lpszFind*指定的文本。 搜索是通过调用[FindText](#findtext)来完成的。 如果未找到文本，则调用[OnTextNotFound。](#ontextnotfound)

重写`OnReplaceSel`以更改`CEditView`派生对象替换所选文本的方式。

## <a name="ceditviewontextnotfound"></a><a name="ontextnotfound"></a>编辑视图：：未找到文本

重写此函数以更改默认实现，该实现调用 Windows`MessageBeep`函数 。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要找到的文本。

## <a name="ceditviewprintinsiderect"></a><a name="printinsiderect"></a>CEditView：:P林特内斯特

调用`PrintInsideRect`以在*rectLayout*指定的矩形中打印文本。

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

*重新布局*<br/>
引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT 结构](/windows/win32/api/windef/ns-windef-rect)，指定要在其中呈现文本的矩形。

*nIndex 开始*<br/>
要呈现的第一个字符的缓冲区内的索引。

*nIndexStop*<br/>
在要呈现的最后一个字符之后的字符缓冲区中的索引。

### <a name="return-value"></a>返回值

要打印的下一个字符的索引（即最后一个字符呈现后的字符）。

### <a name="remarks"></a>备注

如果`CEditView`控件没有样式ES_AUTOHSCROLL，则文本将包在呈现矩形中。 如果控件的样式ES_AUTOHSCROLL，则文本将剪切在矩形的右边缘。

`rect.bottom` *rectLayout*对象的元素将发生更改，以便矩形的尺寸定义文本占用的原始矩形的一部分。

## <a name="ceditviewserializeraw"></a><a name="serializeraw"></a>CEditView：序列化

调用`SerializeRaw`以使`CArchive`对象读取或写入对象中`CEditView`的文本到文本文件。

```cpp
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
引用存储序列`CArchive`化文本的对象。

### <a name="remarks"></a>备注

`SerializeRaw`不同于`CEditView`'的内部实现，`Serialize`因为它只读取和写入文本，没有前面的对象描述数据。

## <a name="ceditviewsetprinterfont"></a><a name="setprinterfont"></a>编辑视图：：设置打印机字体

调用`SetPrinterFont`以将打印机字体设置为*pFont*指定的字体。

```cpp
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
指向类型`CFont`对象的指针。 如果为 NULL，则用于打印的字体基于显示字体。

### <a name="remarks"></a>备注

如果希望视图始终使用特定字体进行打印，请在类`SetPrinterFont``OnPreparePrinting`的函数中包含调用。 此虚拟函数在打印之前调用，因此在打印视图内容之前进行字体更改。

## <a name="ceditviewsettabstops"></a><a name="settabstops"></a>编辑视图：：设置标签

调用此函数以设置用于显示和打印的制表位。

```cpp
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>参数

*nTabStops*<br/>
每个制表符的宽度，以对话框单位表示。

### <a name="remarks"></a>备注

仅支持一个制表位宽度。 （`CEdit`对象支持多个选项卡宽度。宽度以对话框单位表示，等于打印或显示时所用字体的平均字符宽度的四分之一（仅基于大写字母字符和小写字母字符）。 不应使用`CEdit::SetTabStops`，因为`CEditView`必须缓存制表停止值。

此函数仅修改为其调用的对象的选项卡。 要更改应用程序中每个`CEditView`对象的制表位，请调用每个对象的`SetTabStops`函数。

### <a name="example"></a>示例

此代码片段通过仔细测量控件使用的字体，将控件中的制表符停止设置为每 4 个字符。

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

## <a name="ceditviewunlockbuffer"></a><a name="unlockbuffer"></a>CEditView：解锁缓冲区

调用此成员函数以解锁缓冲区。

```cpp
void UnlockBuffer() const;
```

### <a name="remarks"></a>备注

使用`UnlockBuffer` [LockBuffer](#lockbuffer)返回的指针完成后调用。

## <a name="see-also"></a>请参阅

[MFC 样品 SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[克里希编辑视图类](../../mfc/reference/cricheditview-class.md)
