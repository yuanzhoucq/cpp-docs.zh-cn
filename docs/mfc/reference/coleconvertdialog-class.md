---
title: COleConvertDialog 类
ms.date: 11/04/2016
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
ms.openlocfilehash: ba57e756457fcffca806eeba7454ddf7bcf99d34
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504292"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog 类

有关详细信息, 请参阅 Windows SDK 中的[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)结构。

## <a name="syntax"></a>语法

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|构造 `COleConvertDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleConvertDialog::DoConvert](#doconvert)|执行在对话框中指定的转换。|
|[COleConvertDialog::DoModal](#domodal)|显示 "OLE 更改项" 对话框。|
|[COleConvertDialog::GetClassID](#getclassid)|获取与所选项关联的 CLSID。|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|指定是否将项绘制为图标。|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项的图标形式关联的图元文件的句柄。|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|获取所选选择的类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|控制对话框行为的结构。|

## <a name="remarks"></a>备注

> [!NOTE]
>  应用程序向导生成的容器代码使用此类。

有关特定于 OLE 的对话框的详细信息, 请参阅[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>要求

**标头:** afxodlgs

##  <a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog

仅`COleConvertDialog`构造对象。

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要转换或激活的项。

*dwFlags*<br/>
创建标志, 其中包含使用按位 "或" 运算符组合的下列任意数量的值:

- CF_SELECTCONVERTTO 指定最初在调用对话框时, 将选择 "转换为" 单选按钮。 这是默认设置。

- CF_SELECTACTIVATEAS 指定最初在调用对话框时选择 "激活为" 单选按钮。

- CF_SETCONVERTDEFAULT 指定当选择 "转换为" 单选按钮时`clsidConvertDefault` , 由`m_cv`结构的成员指定的 CLSID 将用作类列表框中的默认选择。

- CF_SETACTIVATEDEFAULT 指定当选择 "激活为" 单选按钮时`clsidActivateDefault` , `m_cv`结构成员指定的 CLSID 将用作类列表框中的默认选择。

- CF_SHOWHELPBUTTON 指定在调用对话框时将显示 "帮助" 按钮。

*pClassID*<br/>
指向要转换或激活的项的 CLSID。 如果为 NULL, 则将使用与*pItem*关联的 CLSID。

*pParentWnd*<br/>
指向对话框对象所属的父对象或所有者窗口对象`CWnd`(类型为)。 如果为 NULL, 则对话框的父窗口设置为主应用程序窗口。

### <a name="remarks"></a>备注

若要显示该对话框, 请调用[DoModal](#domodal)函数。

有关详细信息, 请参阅[CLSID 键](/windows/win32/com/clsid-key-hklm)和[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)结构。

##  <a name="doconvert"></a>COleConvertDialog::D oConvert

在从[DoModal](#domodal)成功返回后调用此函数, 以转换或激活[COleClientItem](../../mfc/reference/coleclientitem-class.md)类型的对象。

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要转换或激活的项。 不能为 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

根据用户在 "转换" 对话框中选择的信息来转换或激活该项。

##  <a name="domodal"></a>COleConvertDialog::D oModal

调用此函数可显示 OLE 转换对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示, 则为 IDOK。

- 如果用户取消了对话框, 则为 IDCANCEL。

- 如果发生错误, 则为 IDABORT。 如果返回 IDABORT, 则调用[COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表, 请参阅 Windows SDK 中的[OleUIConvert](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw)函数。

### <a name="remarks"></a>备注

如果希望通过设置[m_cv](#m_cv)结构的成员来初始化各种对话框控件, 应在调用`DoModal`之前执行此操作, 但在构造对话框对象之后。

如果`DoModal`返回 IDOK, 则可以调用其他成员函数来检索用户在对话框中输入的设置或信息。

##  <a name="getclassid"></a>COleConvertDialog:: GetClassID

调用此函数可获取与用户在 "转换" 对话框中选择的项关联的 CLSID。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>返回值

与在 "转换" 对话框中选择的项关联的 CLSID。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

有关详细信息, 请参阅 Windows SDK 中的[CLSID 关键字](/windows/win32/com/clsid-key-hklm)。

##  <a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect

调用此函数可确定用户是否选择将选定项显示为图标。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>返回值

呈现对象所需的方法。

- 如果未选中 "显示为图标" 复选框, 则返回 DVASPECT_CONTENT。

- 如果选中了 "显示为图标" 复选框, 则返回 DVASPECT_ICON。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

有关绘制方面的详细信息, 请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)数据结构。

##  <a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile

调用此函数可获取包含选定项的图标方面的图元文件的句柄。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>返回值

如果在通过选择 "确定" 关闭对话框时选中了 "显示为图标" 复选框, 则为包含选定项的图标方面的图元文件的句柄。否则为 NULL。

##  <a name="getselectiontype"></a>COleConvertDialog::GetSelectionType

调用此函数可确定在 "转换" 对话框中选择的转换类型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>返回值

所选对象的类型。

### <a name="remarks"></a>备注

返回类型值由`Selection` `COleConvertDialog`类中声明的枚举类型指定。

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

这些值的简要说明如下所示:

- `COleConvertDialog::noConversion`如果对话框已取消或用户未选择任何转换, 则返回。 如果`COleConvertDialog::DoModal`返回 IDOK, 则用户可能选择了不同于之前选择的图标。

- `COleConvertDialog::convertItem`如果 "转换为" 单选按钮已选中, 则用户选择了其他要转换为的项, `DoModal`并返回 IDOK。

- `COleConvertDialog::activateAs`如果选中了 "激活方式" 按钮, 则用户选择了一个不同的项来激活, `DoModal`并返回 IDOK。

##  <a name="m_cv"></a>  COleConvertDialog::m_cv

用于控制 "转换" 对话框的行为的 OLEUICONVERT 类型的结构。

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>备注

可以直接或通过成员函数修改此结构的成员。

有关详细信息, 请参阅 Windows SDK 中的[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)结构。

## <a name="see-also"></a>请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
