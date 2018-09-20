---
title: COleChangeSourceDialog 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc05da05ece61652a94c25ccae5b3164c067b8f0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400934"
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
|[COleChangeSourceDialog::DoModal](#domodal)|显示 OLE 更改源对话框。|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|获取完整的源代码显示名称。|
|[COleChangeSourceDialog::GetFileName](#getfilename)|源名称获取文件名。|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|获取以前的源的前缀。|
|[COleChangeSourceDialog::GetItemName](#getitemname)|获取与源名称的项名称。|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|获取新的源的前缀|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|指示源是否有效。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|结构，它控制对话框的行为。|

## <a name="remarks"></a>备注

创建类的对象`COleChangeSourceDialog`时您想要调用此对话框。 之后`COleChangeSourceDialog`构造对象，则可以使用[m_cs](#m_cs)结构初始化的值或在对话框中的控件的状态。 `m_cs`结构属于类型[OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea)。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

有关详细信息，请参阅[OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) Windows SDK 中的结构。

有关特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs.h

##  <a name="colechangesourcedialog"></a>  COleChangeSourceDialog::COleChangeSourceDialog

此函数将构造`COleChangeSourceDialog`对象。

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向链接[COleClientItem](../../mfc/reference/coleclientitem-class.md)其源是要更新。

*pParentWnd*<br/>
指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象属于的。 如果它为 NULL，父窗口的对话框的将设置为应用程序主窗口。

### <a name="remarks"></a>备注

若要显示的对话框，请调用[DoModal](#domodal)函数。

有关详细信息，请参阅[OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea)结构并[OleUIChangeSource](/windows/desktop/api/oledlg/nf-oledlg-oleuichangesourcea) Windows SDK 中的函数。

##  <a name="domodal"></a>  COleChangeSourceDialog::DoModal

调用此函数可显示 OLE 更改源对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框中的完成状态。 以下值之一：

- IDOK 如果成功显示的对话框。

- 如果用户已取消对话框的，IDCANCEL。

- IDABORT 是否发生错误。 如果返回 IDABORT，调用[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅[OleUIChangeSource](/windows/desktop/api/oledlg/nf-oledlg-oleuichangesourcea) Windows SDK 中的函数。

### <a name="remarks"></a>备注

如果你想要通过设置的成员初始化各种对话框控件[m_cs](#m_cs)结构，应执行此操作之前调用`DoModal`，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，您可以调用成员函数从对话框中检索用户输入设置或信息。 以下列表命名了典型查询函数：

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItemName](#getitemname)

##  <a name="getdisplayname"></a>  COleChangeSourceDialog::GetDisplayName

调用此函数可检索链接的客户端项的完整显示名称。

```
CString GetDisplayName();
```

### <a name="return-value"></a>返回值

完整源显示名称 （名字对象） [COleClientItem](../../mfc/reference/coleclientitem-class.md)构造函数中指定。

##  <a name="getfilename"></a>  COleChangeSourceDialog::GetFileName

调用此函数可检索链接的客户端项的显示名称的文件的名字对象部分。

```
CString GetFileName();
```

### <a name="return-value"></a>返回值

源的显示名称的文件的名字对象部分[COleClientItem](../../mfc/reference/coleclientitem-class.md)构造函数中指定。

### <a name="remarks"></a>备注

项名字对象以及文件名字对象提供了完整的显示名称。

##  <a name="getfromprefix"></a>  COleChangeSourceDialog::GetFromPrefix

调用此函数可获取上一个前缀字符串的源。

```
CString GetFromPrefix();
```

### <a name="return-value"></a>返回值

源的上一个前缀字符串。

### <a name="remarks"></a>备注

调用此函数后，才[DoModal](#domodal)返回 IDOK。

此值源于直接`lpszFrom`的成员[OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea)结构。

有关详细信息，请参阅[OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) Windows SDK 中的结构。

##  <a name="getitemname"></a>  COleChangeSourceDialog::GetItemName

调用此函数可检索链接的客户端项的显示名称的项名字对象部分。

```
CString GetItemName();
```

### <a name="return-value"></a>返回值

源的显示名称的项名字对象部分[COleClientItem](../../mfc/reference/coleclientitem-class.md)构造函数中指定。

### <a name="remarks"></a>备注

项名字对象以及文件名字对象提供了完整的显示名称。

##  <a name="gettoprefix"></a>  COleChangeSourceDialog::GetToPrefix

调用此函数可获取新的前缀字符串的源。

```
CString GetToPrefix();
```

### <a name="return-value"></a>返回值

源的新前缀字符串。

### <a name="remarks"></a>备注

调用此函数后，才[DoModal](#domodal)返回 IDOK。

此值源于直接`lpszTo`的成员[OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea)结构。

有关详细信息，请参阅[OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) Windows SDK 中的结构。

##  <a name="m_cs"></a>  COleChangeSourceDialog::m_cs

此数据成员是类型的结构[OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea)。

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>备注

`OLEUICHANGESOURCE` 用于控制 OLE 更改源对话框中的行为。 可以直接修改此结构的成员。

有关详细信息，请参阅[OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) Windows SDK 中的结构。

##  <a name="isvalidsource"></a>  COleChangeSourceDialog::IsValidSource

调用此函数可确定新的源是否有效。

```
BOOL IsValidSource();
```

### <a name="return-value"></a>返回值

非零，如果新的源有效，否则为 0。

### <a name="remarks"></a>备注

调用此函数后，才[DoModal](#domodal)返回 IDOK。

有关详细信息，请参阅[OLEUICHANGESOURCE](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangesourcea) Windows SDK 中的结构。

## <a name="see-also"></a>请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
