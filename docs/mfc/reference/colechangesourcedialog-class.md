---
title: COleChange来源对话类
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
ms.openlocfilehash: 78da0a495de6ea951deab984550756a2d6f3e2bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321873"
---
# <a name="colechangesourcedialog-class"></a>COleChange来源对话类

用于 OLE“更改源”对话框。

## <a name="syntax"></a>语法

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleChange来源对话：：COleChange来源对话](#colechangesourcedialog)|构造 `COleChangeSourceDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleChange来源对话：:Do模态](#domodal)|显示"OLE 更改源"对话框。|
|[COleChange来源对话：：获取显示名称](#getdisplayname)|获取完整的源显示名称。|
|[COleChange来源对话：：获取文件名](#getfilename)|从源名称获取文件名。|
|[COleChange来源对话：：从前缀获取](#getfromprefix)|获取前一源的前缀。|
|[COleChange 来源对话：：获取项目名称](#getitemname)|从源名称获取项名称。|
|[COleChange来源对话：：获取前缀](#gettoprefix)|获取新源的前缀|
|[COleChange来源：：有效来源](#isvalidsource)|指示源是否有效。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COleChange来源：：m_cs](#m_cs)|控制对话框行为的结构。|

## <a name="remarks"></a>备注

要调用此对话框时`COleChangeSourceDialog`，请创建类的对象。 构造`COleChangeSourceDialog`对象后，可以使用[m_cs](#m_cs)结构在对话框中初始化控件的值或状态。 结构`m_cs`为[奥莱图元。](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构。

有关特定于 OLE 的对话框的详细信息，请参阅 OLE[中的"对话框](../../mfc/dialog-boxes-in-ole.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>要求

**标题：** afxodlgs.h

## <a name="colechangesourcedialogcolechangesourcedialog"></a><a name="colechangesourcedialog"></a>COleChange来源对话：：COleChange来源对话

此函数构造对象`COleChangeSourceDialog`。

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要更新其源的链接[的 COleClientItem](../../mfc/reference/coleclientitem-class.md)的指针。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象`CWnd`（类型）。 如果为 NULL，则对话框的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

要显示对话框，请调用[DoModal](#domodal)函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构和[OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew)函数。

## <a name="colechangesourcedialogdomodal"></a><a name="domodal"></a>COleChange来源对话：:Do模态

调用此函数以显示 OLE 更改源对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则 IDOK。

- 如果用户取消了对话框，则进行 IDCANCEL。

- 如果发生错误，则 IDABORT。 如果返回 IDABORT，请调用[COleDialog：getLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数，以获取有关所发生错误类型的详细信息。 有关可能错误的列表，请参阅 Windows SDK 中的[OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew)函数。

### <a name="remarks"></a>备注

如果要通过设置[m_cs](#m_cs)结构的成员来初始化各种对话框控件，则应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用成员函数从对话框中检索用户输入的设置或信息。 以下列表名称典型的查询函数：

- [GetFileName](#getfilename)

- [获取显示名称](#getdisplayname)

- [获取项目名称](#getitemname)

## <a name="colechangesourcedialoggetdisplayname"></a><a name="getdisplayname"></a>COleChange来源对话：：获取显示名称

调用此函数以检索链接的客户端项的完整显示名称。

```
CString GetDisplayName();
```

### <a name="return-value"></a>返回值

构造函数中指定的[COleClientItem](../../mfc/reference/coleclientitem-class.md)的完整源显示名称（名字）。

## <a name="colechangesourcedialoggetfilename"></a><a name="getfilename"></a>COleChange来源对话：：获取文件名

调用此函数以检索链接客户端项的显示名称的文件名称部分。

```
CString GetFileName();
```

### <a name="return-value"></a>返回值

在构造函数中指定的[COleClientItem](../../mfc/reference/coleclientitem-class.md)的源显示名称的文件名称部分。

### <a name="remarks"></a>备注

文件名称与项目名称一起提供完整的显示名称。

## <a name="colechangesourcedialoggetfromprefix"></a><a name="getfromprefix"></a>COleChange来源对话：：从前缀获取

调用此函数以获取源的前缀字符串。

```
CString GetFromPrefix();
```

### <a name="return-value"></a>返回值

源的前缀字符串。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

此值直接来自`lpszFrom`[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构的成员。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构。

## <a name="colechangesourcedialoggetitemname"></a><a name="getitemname"></a>COleChange 来源对话：：获取项目名称

调用此函数以检索链接客户端项的显示名称的项名称部分。

```
CString GetItemName();
```

### <a name="return-value"></a>返回值

在构造函数中指定的[COleClientItem](../../mfc/reference/coleclientitem-class.md)的源显示名称的项名称部分。

### <a name="remarks"></a>备注

文件名称与项目名称一起提供完整的显示名称。

## <a name="colechangesourcedialoggettoprefix"></a><a name="gettoprefix"></a>COleChange来源对话：：获取前缀

调用此函数获取源的新前缀字符串。

```
CString GetToPrefix();
```

### <a name="return-value"></a>返回值

源的新前缀字符串。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

此值直接来自`lpszTo`[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构的成员。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构。

## <a name="colechangesourcedialogm_cs"></a><a name="m_cs"></a>COleChange来源：：m_cs

此数据成员是[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)类型的结构。

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>备注

`OLEUICHANGESOURCE`用于控制 OLE 更改源对话框的行为。 可以直接修改此结构的成员。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构。

## <a name="colechangesourcedialogisvalidsource"></a><a name="isvalidsource"></a>COleChange来源：：有效来源

调用此函数以确定新源是否有效。

```
BOOL IsValidSource();
```

### <a name="return-value"></a>返回值

如果新源有效，则非零，否则为 0。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)结构。

## <a name="see-also"></a>另请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
