---
title: CFontDialog 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
dev_langs:
- C++
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb03a63b922a2718c1b17fdb4970f80da3b8b5a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054834"
---
# <a name="cfontdialog-class"></a>CFontDialog 类

可以将字体选择对话框合并到应用程序。

## <a name="syntax"></a>语法

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|构造 `CFontDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CFontDialog::DoModal](#domodal)|显示对话框，并允许用户进行选择。|
|[CFontDialog::GetCharFormat](#getcharformat)|检索所选字体的字符格式设置。|
|[CFontDialog::GetColor](#getcolor)|返回所选字体的颜色。|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|将分配到的当前所选字体的特征`LOGFONT`结构。|
|[CFontDialog::GetFaceName](#getfacename)|返回所选字体的字体名称。|
|[CFontDialog::GetSize](#getsize)|返回所选字体的磅值。|
|[CFontDialog::GetStyleName](#getstylename)|返回所选字体的样式名称。|
|[CFontDialog::GetWeight](#getweight)|返回所选字体的粗细。|
|[CFontDialog::IsBold](#isbold)|确定字体为粗体。|
|[CFontDialog::IsItalic](#isitalic)|确定是否该字体为斜体。|
|[CFontDialog::IsStrikeOut](#isstrikeout)|确定是否使用带删除线显示字体。|
|[CFontDialog::IsUnderline](#isunderline)|确定字体是否带下划线。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|用于自定义的结构`CFontDialog`对象。|

## <a name="remarks"></a>备注

一个`CFontDialog`对象是一个列表的系统中当前安装的字体的对话框。 用户可以从列表中，选择特定的字体和此选择然后报告给应用程序。

若要构造`CFontDialog`对象，使用提供的构造函数或派生新的子类并使用你自己的自定义构造函数。

一次`CFontDialog`构造对象，则可以使用`m_cf`结构初始化的值或在对话框中的控件的状态。 [M_cf](#m_cf)结构的类型是[CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta)。 此结构的详细信息，请参阅 Windows SDK。

初始化对话框对象的控件之后, 调用`DoModal`成员函数以显示该对话框，并允许用户选择一种字体。 `DoModal` 返回用户是否选择了确定 (IDOK) 或取消 (IDCANCEL) 按钮。

如果`DoModal`返回 IDOK，您可以使用其中一个`CFontDialog`的成员函数来检索用户输入的信息。

可以使用 Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror)函数来确定在对话框中的初始化过程中是否发生了错误并了解有关错误的详细信息。 此函数的详细信息，请参阅 Windows SDK。

`CFontDialog` 依赖于 COMMDLG。随 Windows 3.1 及更高版本的 DLL 文件。

若要自定义对话框中，派生的类从`CFontDialog`，提供自定义对话框模板，并添加消息映射来处理从扩展控件的通知消息。 任何未处理的消息应传递给类的基类。

不需要自定义挂钩函数。

有关使用的详细信息`CFontDialog`，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>要求

**标头：** afxdlgs.h

##  <a name="cfontdialog"></a>  CFontDialog::CFontDialog

构造 `CFontDialog` 对象。

```
CFontDialog(
    LPLOGFONT lplfInitial = NULL,
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,
    DWORD dwFlags = CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*plfInitial*<br/>
一个指向[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)数据结构，您可以设置某些字体的特征。

*charFormat*<br/>
一个指向[CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat)数据结构，您可以设置某些字体的特征在 rich edit 控件。

*dwFlags*<br/>
指定一个或多个用于选择字体的标记。 可以使用按位“OR”运算符对一个或多个预设值进行组合。 如果修改 `m_cf.Flag` 结构成员，请确保在更改中使用按位“OR”运算符以保持默认行为不变。 在每个标记的详细信息，请参阅的说明[CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta) Windows SDK 中的结构。

*pdcPrinter*<br/>
一个指向打印机设备上下文的指针。 如果已提供此参数，它将指向要选择其字体的打印机的打印机设备上下文。

*pParentWnd*<br/>
一个指向字体对话框的父窗口或所有者窗口的指针。

### <a name="remarks"></a>备注

请注意，构造函数将自动填充 `CHOOSEFONT` 结构的成员。 仅在要让字体对话框不同于默认字体对话框时，才应该更改这些内容。

> [!NOTE]
>  仅在不支持 Rich Edit 控件时，才存在此函数的第一个版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

##  <a name="domodal"></a>  CFontDialog::DoModal

调用此函数可显示 Windows 常见字体对话框中，并允许用户选择一种字体。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL，则调用 Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror)函数来确定是否发生了错误。

IDOK 和 IDCANCEL 是常数，用于指示是否在用户选择了确定或取消按钮。

### <a name="remarks"></a>备注

如果你想要通过设置的成员初始化各种字体对话框控件[m_cf](#m_cf)结构，应执行此操作之前调用`DoModal`，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，您可以调用其他成员函数来检索设置或用户的信息输入到对话框。

### <a name="example"></a>示例

  请参阅有关[CFontDialog::CFontDialog](#cfontdialog)并[CFontDialog::GetColor](#getcolor)。

##  <a name="getcharformat"></a>  CFontDialog::GetCharFormat

检索所选字体的字符格式设置。

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>参数

*cf*<br/>
一个[CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat)结构，它包含有关所选字体的字符格式设置信息。

##  <a name="getcolor"></a>  CFontDialog::GetColor

调用此函数可检索所选的字体颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

选定字体的颜色。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

##  <a name="getcurrentfont"></a>  CFontDialog::GetCurrentFont

调用此函数可将当前所选字体的特征分配到的成员[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)结构。

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>参数

*lplf*<br/>
一个指向`LOGFONT`结构。

### <a name="remarks"></a>备注

其他`CFontDialog`成员函数可用于访问当前字体的各个特征。

如果在调用期间调用此函数[DoModal](#domodal)，它将返回当前选定内容时 (用户会看到或具有的对话框中更改)。 如果在调用后调用此函数`DoModal`(仅当`DoModal`返回 IDOK)，它将返回用户所实际选择。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

##  <a name="getfacename"></a>  CFontDialog::GetFaceName

调用此函数可检索所选字体的字体名称。

```
CString GetFaceName() const;
```

### <a name="return-value"></a>返回值

在选定的字体的字体名称`CFontDialog`对话框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

##  <a name="getsize"></a>  CFontDialog::GetSize

调用此函数可检索所选字体的大小。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

字体的大小，以点的十分之几秒。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

##  <a name="getstylename"></a>  CFontDialog::GetStyleName

调用此函数可检索所选字体的样式名称。

```
CString GetStyleName() const;
```

### <a name="return-value"></a>返回值

字体的样式名称。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

##  <a name="getweight"></a>  CFontDialog::GetWeight

调用此函数可检索所选字体的粗细。

```
int GetWeight() const;
```

### <a name="return-value"></a>返回值

所选字体的粗细。

### <a name="remarks"></a>备注

权重字体的详细信息，请参阅[CFont::CreateFont](../../mfc/reference/cfont-class.md#createfont)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

##  <a name="isbold"></a>  CFontDialog::IsBold

调用此函数可确定所选的字体为粗体。

```
BOOL IsBold() const;
```

### <a name="return-value"></a>返回值

如果所选的字体加粗特征启用，则非零值否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

##  <a name="isitalic"></a>  CFontDialog::IsItalic

调用此函数可确定所选的字体为斜体。

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>返回值

如果所选的字体已启用，则斜体特征，非零值否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

##  <a name="isstrikeout"></a>  CFontDialog::IsStrikeOut

调用此函数可确定是否使用带删除线显示所选的字体。

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>返回值

所选的字体是否带删除线特征启用，则非零值否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

##  <a name="isunderline"></a>  CFontDialog::IsUnderline

调用此函数可确定所选的字体是否带下划线。

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>返回值

如果所选的字体已启用，则下划线特征，非零值否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

##  <a name="m_cf"></a>  CFontDialog::m_cf

结构，其成员存储对话框对象的特征。

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>备注

构造后`CFontDialog`对象，可以使用`m_cf`修改之前，调用对话框中的各个方面`DoModal`成员函数。 此结构的详细信息，请参阅[CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../visual-cpp-samples.md)<br/>
[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)

