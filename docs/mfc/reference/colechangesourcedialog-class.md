---
title: COleChangeSourceDialog 类
ms.date: 11/04/2016
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
ms.openlocfilehash: 239d7eed89796f414a7665b203ca50fafec51277
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504390"
---
# <a name="colechangesourcedialog-class"></a>COleChangeSourceDialog 类

用于 OLE“更改源”对话框。

## <a name="syntax"></a>语法

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|构造 `COleChangeSourceDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleChangeSourceDialog::DoModal](#domodal)|显示 "OLE 更改源" 对话框。|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|获取完整的源显示名称。|
|[COleChangeSourceDialog::GetFileName](#getfilename)|从源名称获取文件名。|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|获取上一个源的前缀。|
|[COleChangeSourceDialog::GetItemName](#getitemname)|从源名称获取项名称。|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|获取新源的前缀|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|指示源是否有效。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|控制对话框行为的结构。|

## <a name="remarks"></a>备注

如果要调用此对话框`COleChangeSourceDialog` ，请创建类的对象。 构造`COleChangeSourceDialog`对象后，可以使用 [m_cs](#m_cs) 结构在对话框中初始化控件的值或状态。 结构的类型为[OLEUICHANGESOURCE。](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) `m_cs` 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构。

有关特定于 OLE 的对话框的详细信息，请参阅[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs

##  <a name="colechangesourcedialog"></a>COleChangeSourceDialog::COleChangeSourceDialog

此函数构造`COleChangeSourceDialog`对象。

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要更新其源的链接的[COleClientItem](../../mfc/reference/coleclientitem-class.md)的指针。

*pParentWnd*<br/>
指向对话框对象所属的父对象或所有者窗口对象`CWnd`（类型为）。 如果为 NULL，则对话框的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

若要显示该对话框，请调用[DoModal](#domodal)函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构和[OLEUICHANGESOURCE](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew)函数。

##  <a name="domodal"></a>COleChangeSourceDialog：:D oModal

调用此函数可显示 OLE "更改源" 对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则为 IDOK。

- 如果用户取消了对话框，则为 IDCANCEL。

- 如果发生错误，则为 IDABORT。 如果返回 IDABORT，则调用[COleDialog：： GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅 Windows SDK 中的[OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew)函数。

### <a name="remarks"></a>备注

如果希望通过设置[m_cs](#m_cs)结构的成员来初始化各种对话框控件，应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用成员函数以从对话框中检索用户输入的设置或信息。 以下列表列出了典型的查询函数：

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItemName](#getitemname)

##  <a name="getdisplayname"></a>COleChangeSourceDialog：： GetDisplayName

调用此函数可检索链接客户端项的完整显示名称。

```
CString GetDisplayName();
```

### <a name="return-value"></a>返回值

构造函数中指定的[COleClientItem](../../mfc/reference/coleclientitem-class.md)的完整源显示名称（名字对象）。

##  <a name="getfilename"></a>COleChangeSourceDialog：： GetFileName

调用此函数可检索链接客户端项的显示名称的文件名字对象部分。

```
CString GetFileName();
```

### <a name="return-value"></a>返回值

构造函数中指定的[COleClientItem](../../mfc/reference/coleclientitem-class.md)的源显示名称的文件名字对象部分。

### <a name="remarks"></a>备注

文件名字对象与项名字对象一起提供完整的显示名称。

##  <a name="getfromprefix"></a>COleChangeSourceDialog::GetFromPrefix

调用此函数可获取源的上一个前缀字符串。

```
CString GetFromPrefix();
```

### <a name="return-value"></a>返回值

源的上一个前缀字符串。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

此值直接来自`lpszFrom` [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构的成员。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构。

##  <a name="getitemname"></a>COleChangeSourceDialog::GetItemName

调用此函数可检索链接客户端项的显示名称的项名字对象部分。

```
CString GetItemName();
```

### <a name="return-value"></a>返回值

构造函数中指定的[COleClientItem](../../mfc/reference/coleclientitem-class.md)的源显示名称的项名字对象部分。

### <a name="remarks"></a>备注

文件名字对象与项名字对象一起提供完整的显示名称。

##  <a name="gettoprefix"></a>COleChangeSourceDialog::GetToPrefix

调用此函数可为源获取新的前缀字符串。

```
CString GetToPrefix();
```

### <a name="return-value"></a>返回值

源的新的前缀字符串。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

此值直接来自`lpszTo` [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构的成员。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构。

##  <a name="m_cs"></a>  COleChangeSourceDialog::m_cs

此数据成员是[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)类型的结构。

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>备注

`OLEUICHANGESOURCE`用于控制 OLE "更改源" 对话框的行为。 可以直接修改此结构的成员。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构。

##  <a name="isvalidsource"></a>COleChangeSourceDialog::IsValidSource

调用此函数可确定新源是否有效。

```
BOOL IsValidSource();
```

### <a name="return-value"></a>返回值

如果新的源有效，则为非零; 否则为0。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构。

## <a name="see-also"></a>请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
