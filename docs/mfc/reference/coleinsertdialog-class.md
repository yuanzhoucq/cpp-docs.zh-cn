---
title: COleInsert对话类
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
ms.openlocfilehash: b5de4ff5daa80e1d8727444a4cfd275597e18c08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374976"
---
# <a name="coleinsertdialog-class"></a>COleInsert对话类

用于 OLE“插入对象”对话框。

## <a name="syntax"></a>语法

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle 插入对话框：：COle 插入对话框](#coleinsertdialog)|构造 `COleInsertDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleInsert对话：：创建项目](#createitem)|创建对话框中选择的项目。|
|[COleInsertDialog：:Do模态](#domodal)|显示"OLE 插入对象"对话框。|
|[COleInsert对话：：获取类ID](#getclassid)|获取与所选项关联的 CLSID。|
|[COleInsert对话：：获取绘制方面](#getdrawaspect)|告诉是否将项目绘制为图标。|
|[COleInsert对话：：获取图标Meta文件](#geticonicmetafile)|获取与此项目的标志性形式关联的元文件的句柄。|
|[COleInsert对话：：获取路径名称](#getpathname)|获取对话框中选择的文件的完整路径。|
|[COleInsert对话：：获取选择类型](#getselectiontype)|获取所选对象的类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COleInsert对话：：m_io](#m_io)|控制对话框行为的 OLEUIINSERTOBJECT 类型的结构。|

## <a name="remarks"></a>备注

要调用此对话框时`COleInsertDialog`，请创建类的对象。 构造`COleInsertDialog`对象后，可以使用[m_io](#m_io)结构在对话框中初始化控件的值或状态。 结构`m_io`为"奥莱伊插入对象"类型。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

> [!NOTE]
> 应用程序向导生成的容器代码使用此类。

有关详细信息，请参阅 Windows SDK 中的[OLEUIINSERTOBJECT 结构](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw)。

有关特定于 OLE 的对话框的详细信息，请参阅 OLE[中的"对话框](../../mfc/dialog-boxes-in-ole.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>要求

**标题：** afxodlgs.h

## <a name="coleinsertdialogcoleinsertdialog"></a><a name="coleinsertdialog"></a>COle 插入对话框：：COle 插入对话框

此函数仅构造对象`COleInsertDialog`。

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

dwFlags**<br/>
创建标志，其中包含要使用位-OR 运算符组合的任意数量的以下值：

- IOF_SHOWHELP 指定在调用对话框时将显示"帮助"按钮。

- IOF_SELECTCREATENEW 指定在调用对话框时，最初将选择"创建新单选"按钮。 这是默认值，不能与IOF_SELECTCREATEFROMFILE一起使用。

- IOF_SELECTCREATEFROMFILE 指定在调用对话框时，最初将选择"从文件创建单选"按钮。 不能与IOF_SELECTCREATENEW一起使用。

- IOF_CHECKLINK 指定在调用对话框时，将首先选中"链接"复选框。

- IOF_DISABLELINK 指定在调用对话框时将禁用"链接"复选框。

- IOF_CHECKDISPLAYASICON 指定最初将选中"显示为图标"复选框，将显示当前图标，并在调用对话框时启用"更改图标"按钮。

- IOF_VERIFYSERVERSEXIST 指定对话框应通过确保在显示对话框之前在注册数据库中指定的服务器来验证它添加到列表框中的类。 设置此标志可能会显著削弱性能。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象`CWnd`（类型）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

要显示对话框，请调用[DoModal](#domodal)函数。

## <a name="coleinsertdialogcreateitem"></a><a name="createitem"></a>COleInsert对话：：创建项目

仅当[DoModal](#domodal)返回 IDOK 时，才调用此函数以创建[COleClientItem](../../mfc/reference/coleclientitem-class.md)类型的对象。

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要创建的项。

### <a name="return-value"></a>返回值

创建项时非零;否则 0。

### <a name="remarks"></a>备注

必须先分配对象，`COleClientItem`然后才能调用此函数。

## <a name="coleinsertdialogdomodal"></a><a name="domodal"></a>COleInsertDialog：:Do模态

调用此函数以显示"OLE 插入对象"对话框。

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>参数

dwFlags**<br/>
以下值之一：

`COleInsertDialog::DocObjectsOnly`仅插入文档对象。

`COleInsertDialog::ControlsOnly`仅插入 ActiveX 控件。

零既不插入文档对象，也不插入 ActiveX 控件。 此值导致与上面列出的第一个原型相同的实现。

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则 IDOK。

- 如果用户取消了对话框，则进行 IDCANCEL。

- 如果发生错误，则 IDABORT。 如果返回 IDABORT，请调用[COleDialog：getLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数，以获取有关所发生错误类型的详细信息。 有关可能错误的列表，请参阅 Windows SDK 中的[OleUIInsertObject](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw)函数。

### <a name="remarks"></a>备注

如果要通过设置[m_io](#m_io)结构的成员来初始化各种对话框控件，则应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用其他成员函数来检索用户输入到对话框中的设置或信息。

## <a name="coleinsertdialoggetclassid"></a><a name="getclassid"></a>COleInsert对话：：获取类ID

仅当[DoModal](#domodal)返回 IDOK 并且选择类型为`COleInsertDialog::createNewItem`时，才调用此函数以获取与选定项关联的 CLSID。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>返回值

返回与所选项关联的 CLSID。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[CLSID 密钥](/windows/win32/com/clsid-key-hklm)。

## <a name="coleinsertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleInsert对话：：获取绘制方面

调用此函数以确定用户是否选择将所选项目显示为图标。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>返回值

呈现对象所需的方法。

- 如果未选中"显示为图标"复选框，则DVASPECT_CONTENT返回。

- DVASPECT_ICON如果选中"显示为图标"复选框，则返回。

### <a name="remarks"></a>备注

仅当[DoModal](#domodal)返回 IDOK 时才调用此函数。

有关绘图方面的详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)数据结构。

## <a name="coleinsertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleInsert对话：：获取图标Meta文件

调用此函数以获取包含所选项标志性方面的元文件的句柄。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>返回值

包含选定项目标志性方面的元文件的句柄，如果通过选择 **"确定**"在对话框中取消对话框时选中"显示为图标"复选框。否则 NULL。

## <a name="coleinsertdialoggetpathname"></a><a name="getpathname"></a>COleInsert对话：：获取路径名称

仅当[DoModal](#domodal)返回 IDOK 并且选择类型不是`COleInsertDialog::createNewItem`时，才调用此函数获取所选文件的完整路径。

```
CString GetPathName() const;
```

### <a name="return-value"></a>返回值

对话框中选择的文件的完整路径。 如果选择类型为`createNewItem`，则此函数在发布`CString`模式下返回无意义，或在调试模式下导致断言。

## <a name="coleinsertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleInsert对话：：获取选择类型

调用此函数，在通过选择 **"确定**"来取消"插入对象"对话框时选择选择类型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>返回值

选择的类型。

### <a name="remarks"></a>备注

返回类型值由类中声明的`Selection``COleInsertDialog`枚举类型指定。

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

这些值的简要说明如下：

- `COleInsertDialog::createNewItem`选择了"创建新单选"按钮。

- `COleInsertDialog::insertFromFile`选择了"从文件创建"单选按钮，并且未选中"链接"复选框。

- `COleInsertDialog::linkToFile`选择了"从文件创建"单选按钮，并选中了"链接"复选框。

## <a name="coleinsertdialogm_io"></a><a name="m_io"></a>COleInsert对话：：m_io

用于控制"插入对象"对话框的行为的 OLEUIINSERTOBJECT 类型的结构。

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>备注

此结构的成员可以直接或通过成员函数进行修改。

有关详细信息，请参阅 Windows SDK 中的[OLEUIINSERTOBJECT 结构](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw)。

## <a name="see-also"></a>另请参阅

[MFC 样品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
