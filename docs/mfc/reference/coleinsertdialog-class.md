---
title: COleInsertDialog 类
ms.date: 11/04/2016
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
ms.openlocfilehash: a884f946b60be0567f39477f434db8efe041e393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503929"
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog 类

用于 OLE“插入对象”对话框。

## <a name="syntax"></a>语法

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|构造 `COleInsertDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|创建在对话框中选定的项。|
|[COleInsertDialog::DoModal](#domodal)|显示 OLE "插入对象" 对话框。|
|[COleInsertDialog::GetClassID](#getclassid)|获取与所选项关联的 CLSID。|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|指示是否将项绘制为图标。|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项的图标形式关联的图元文件的句柄。|
|[COleInsertDialog::GetPathName](#getpathname)|获取对话框中所选文件的完整路径。|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|获取所选对象的类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|控制对话框行为的 OLEUIINSERTOBJECT 类型的结构。|

## <a name="remarks"></a>备注

如果要调用此对话框`COleInsertDialog` ，请创建类的对象。 构造`COleInsertDialog`对象后，可以使用 [m_io](#m_io) 结构在对话框中初始化控件的值或状态。 `m_io`结构的类型为 OLEUIINSERTOBJECT。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

> [!NOTE]
>  应用程序向导生成的容器代码使用此类。

有关详细信息，请参阅 Windows SDK 中的[OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw)结构。

有关特定于 OLE 的对话框的详细信息，请参阅[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs

##  <a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog

此函数仅`COleInsertDialog`构造对象。

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
包含要使用按位 "或" 运算符组合的以下任意数量值的创建标志：

- IOF_SHOWHELP 指定在调用对话框时将显示 "帮助" 按钮。

- IOF_SELECTCREATENEW 指定最初在调用对话框时，将选择 "新建" 单选按钮。 这是默认值，不能与 IOF_SELECTCREATEFROMFILE 一起使用。

- IOF_SELECTCREATEFROMFILE 指定最初在调用对话框时，将选择 "从文件创建" 单选按钮。 不能与 IOF_SELECTCREATENEW 一起使用。

- IOF_CHECKLINK 指定在最初调用对话框时，将检查 "链接" 复选框。

- IOF_DISABLELINK 指定在调用对话框时将禁用 "链接" 复选框。

- IOF_CHECKDISPLAYASICON 指定最初要检查的 "显示为图标" 复选框，当前图标将显示，并且在调用对话框时将启用 "更改图标" 按钮。

- IOF_VERIFYSERVERSEXIST 指定对话框应验证它添加到列表框中的类，方法是确保注册数据库中指定的服务器在显示该对话框之前。 设置此标志可能会显著影响性能。

*pParentWnd*<br/>
指向对话框对象所属的父对象或所有者窗口对象`CWnd`（类型为）。 如果为 NULL，则对话框对象的父窗口设置为主应用程序窗口。

### <a name="remarks"></a>备注

若要显示该对话框，请调用[DoModal](#domodal)函数。

##  <a name="createitem"></a>COleInsertDialog：： CreateItem

仅当[DoModal](#domodal)返回 IDOK 时，才调用此函数创建[COleClientItem](../../mfc/reference/coleclientitem-class.md)类型的对象。

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要创建的项。

### <a name="return-value"></a>返回值

如果创建了项，则为非零值;否则为0。

### <a name="remarks"></a>备注

必须先分配`COleClientItem`对象，然后才能调用此函数。

##  <a name="domodal"></a>COleInsertDialog：:D oModal

调用此函数以显示 OLE "插入对象" 对话框。

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
以下值之一：

`COleInsertDialog::DocObjectsOnly`仅插入 DocObjects。

`COleInsertDialog::ControlsOnly`仅插入 ActiveX 控件。

零不插入 DocObject 和 ActiveX 控件。 此值将导致与上面列出的第一个原型相同的实现。

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则为 IDOK。

- 如果用户取消了对话框，则为 IDCANCEL。

- 如果发生错误，则为 IDABORT。 如果返回 IDABORT，则调用[COleDialog：： GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅 Windows SDK 中的[OleUIInsertObject](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw)函数。

### <a name="remarks"></a>备注

如果希望通过设置[m_io](#m_io)结构的成员来初始化各种对话框控件，应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用其他成员函数以将设置或信息输入检索到用户的对话框中。

##  <a name="getclassid"></a>COleInsertDialog：： GetClassID

调用此函数可获取与所选项相关联的 CLSID （仅当[DoModal](#domodal)返回 IDOK，选择类型为`COleInsertDialog::createNewItem`时）。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>返回值

返回与选定项关联的 CLSID。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[CLSID 关键字](/windows/win32/com/clsid-key-hklm)。

##  <a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect

调用此函数可确定用户是否选择将选定项显示为图标。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>返回值

呈现对象所需的方法。

- 如果未选中 "显示为图标" 复选框，则返回 DVASPECT_CONTENT。

- 如果选中了 "显示为图标" 复选框，则返回 DVASPECT_ICON。

### <a name="remarks"></a>备注

仅当[DoModal](#domodal)返回 IDOK 时，才调用此函数。

有关绘制方面的详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)数据结构。

##  <a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile

调用此函数可获取包含选定项的图标方面的图元文件的句柄。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>返回值

如果在通过选择 **"确定"** 关闭对话框时选中了 "显示为图标" 复选框，则为包含选定项的图标方面的图元文件的句柄。否则为 NULL。

##  <a name="getpathname"></a>COleInsertDialog::GetPathName

调用此函数以仅在[DoModal](#domodal)返回 IDOK 时获取所选文件的完整路径，并且选择类型不`COleInsertDialog::createNewItem`为。

```
CString GetPathName() const;
```

### <a name="return-value"></a>返回值

对话框中所选文件的完整路径。 如果选择类型为`createNewItem`，则此函数将以发布模式返回无意义`CString`的，或在调试模式下引发断言。

##  <a name="getselectiontype"></a>COleInsertDialog::GetSelectionType

调用此函数可获取通过选择 **"确定"** 关闭 "插入对象" 对话框时选择的选择类型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>返回值

所选对象的类型。

### <a name="remarks"></a>备注

返回类型值由`Selection` `COleInsertDialog`类中声明的枚举类型指定。

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

这些值的简要说明如下所示：

- `COleInsertDialog::createNewItem`已选择 "新建" 单选按钮。

- `COleInsertDialog::insertFromFile`"从文件创建" 单选按钮已选中，并且未选中 "链接" 复选框。

- `COleInsertDialog::linkToFile`选中了 "从文件创建" 单选按钮，并选中了 "链接" 复选框。

##  <a name="m_io"></a>COleInsertDialog::m_io

用于控制 "插入对象" 对话框的行为的 OLEUIINSERTOBJECT 类型的结构。

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>备注

可以直接或通过成员函数修改此结构的成员。

有关详细信息，请参阅 Windows SDK 中的[OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw)结构。

## <a name="see-also"></a>请参阅

[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
