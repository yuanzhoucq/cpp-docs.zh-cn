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
ms.openlocfilehash: 27bf98ea4fe6951624873c1463d50f37558c9234
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781479"
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
|[COleInsertDialog::DoModal](#domodal)|显示 OLE 插入对象对话框。|
|[COleInsertDialog::GetClassID](#getclassid)|获取与所选的项相关联的 CLSID。|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|指示是否绘制为一个图标的项。|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项的图标窗体相关联的图元文件的句柄。|
|[COleInsertDialog::GetPathName](#getpathname)|获取在对话框中选择的文件的完整路径。|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|获取所选对象的类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|类型 OLEUIINSERTOBJECT 控制对话框的行为的结构。|

## <a name="remarks"></a>备注

创建类的对象`COleInsertDialog`时您想要调用此对话框。 之后`COleInsertDialog`构造对象，则可以使用[m_io](#m_io)结构初始化的值或在对话框中的控件的状态。 `m_io`结构属于类型 OLEUIINSERTOBJECT。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

> [!NOTE]
>  应用程序向导生成的容器的代码使用此类。

有关详细信息，请参阅[OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) Windows SDK 中的结构。

有关特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs.h

##  <a name="coleinsertdialog"></a>  COleInsertDialog::COleInsertDialog

此函数将构造仅`COleInsertDialog`对象。

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
创建包含任意数量的以下值，以使用按位 OR 运算符组合的标志：

- IOF_SHOWHELP 指定对话框的调用时，将显示帮助按钮。

- 创建新的单选按钮将处于 IOF_SELECTCREATENEW 指定最初选定对话框的调用时。 这是默认值，不能用于 IOF_SELECTCREATEFROMFILE。

- 从文件创建单选按钮将处于 IOF_SELECTCREATEFROMFILE 指定最初选定对话框的调用时。 不能用于 IOF_SELECTCREATENEW。

- IOF_CHECKLINK 指定链接复选框将选中最初调用的对话框时。

- 调用对话框的时，将禁用 IOF_DISABLELINK 指定链接复选框。

- IOF_CHECKDISPLAYASICON 指定显示为图标的复选框将最初检查，将显示当前图标，并且调用对话框时，将启用更改图标按钮。

- IOF_VERIFYSERVERSEXIST 指定对话框中应验证它将添加到列表框通过确保在注册数据库中指定的服务器，显示的对话框之前存在的类。 设置此标志会显著降低性能。

*pParentWnd*<br/>
指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象属于的。 如果它为 NULL，对话框对象的父窗口设置为应用程序主窗口。

### <a name="remarks"></a>备注

若要显示的对话框，请调用[DoModal](#domodal)函数。

##  <a name="createitem"></a>  COleInsertDialog::CreateItem

调用此函数可创建类型的对象[COleClientItem](../../mfc/reference/coleclientitem-class.md)仅当[DoModal](#domodal)返回 IDOK。

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要创建的项。

### <a name="return-value"></a>返回值

创建项; 如果非零值否则为 0。

### <a name="remarks"></a>备注

您必须分配`COleClientItem`对象才能调用此函数。

##  <a name="domodal"></a>  COleInsertDialog::DoModal

调用此函数可显示 OLE 插入对象对话框。

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
以下值之一：

`COleInsertDialog::DocObjectsOnly` 将插入仅 DocObjects。

`COleInsertDialog::ControlsOnly` 将插入仅 ActiveX 控件。

DocObject 和 ActiveX 控件都不会将插入零。 上面列出的此值会导致相同的实现的第一个原型。

### <a name="return-value"></a>返回值

对话框中的完成状态。 以下值之一：

- IDOK 如果成功显示的对话框。

- 如果用户已取消对话框的，IDCANCEL。

- IDABORT 是否发生错误。 如果返回 IDABORT，调用[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅[OleUIInsertObject](/windows/desktop/api/oledlg/nf-oledlg-oleuiinsertobjecta) Windows SDK 中的函数。

### <a name="remarks"></a>备注

如果你想要通过设置的成员初始化各种对话框控件[m_io](#m_io)结构，应执行此操作之前调用`DoModal`，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，您可以调用其他成员函数以检索的设置或信息输入到用户对话框。

##  <a name="getclassid"></a>  COleInsertDialog::GetClassID

调用此函数可获取与所选的项仅当相关联的 CLSID [DoModal](#domodal)返回 IDOK 和所选内容类型是`COleInsertDialog::createNewItem`。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>返回值

返回与所选的项相关联的 CLSID。

### <a name="remarks"></a>备注

有关详细信息，请参阅[CLSID 项](/windows/desktop/com/clsid-key-hklm)Windows SDK 中。

##  <a name="getdrawaspect"></a>  COleInsertDialog::GetDrawAspect

调用此函数可确定用户选择以图标形式显示选定的项。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>返回值

呈现对象所需的方法。

- 如果未选中显示为图标复选框，将返回 DVASPECT_CONTENT。

- 如果显示为图标的复选框已选中，将返回 DVASPECT_ICON。

### <a name="remarks"></a>备注

调用此函数仅当[DoModal](#domodal)返回 IDOK。

绘制方面的详细信息，请参阅[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的数据结构。

##  <a name="geticonicmetafile"></a>  COleInsertDialog::GetIconicMetafile

调用此函数可获取包含选定项的图标方面的图元文件的句柄。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>返回值

句柄图元文件包含选定项的图标的方面，如果显示为图标的复选框选中对话框时通过选择解除**确定**; 否则为 NULL。

##  <a name="getpathname"></a>  COleInsertDialog::GetPathName

调用此函数可获取选定的文件才的完整路径[DoModal](#domodal)返回 IDOK 和所选内容类型不是`COleInsertDialog::createNewItem`。

```
CString GetPathName() const;
```

### <a name="return-value"></a>返回值

在对话框中选择文件的完整路径。 如果所选内容类型为`createNewItem`，此函数将返回无意义`CString`在发布模式下或在调试模式下引发断言。

##  <a name="getselectiontype"></a>  COleInsertDialog::GetSelectionType

调用此函数可获取所选内容类型选择插入对象对话框时通过选择解除**确定**。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>返回值

所做选择的类型。

### <a name="remarks"></a>备注

通过指定返回类型值`Selection`枚举类型中声明`COleInsertDialog`类。

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

请按照这些值的简短说明：

- `COleInsertDialog::createNewItem` 已选择新创建的单选按钮。

- `COleInsertDialog::insertFromFile` 已选择从文件创建单选按钮和未选中链接复选框。

- `COleInsertDialog::linkToFile` 已选择从文件创建单选按钮和链接复选框已选中。

##  <a name="m_io"></a>  COleInsertDialog::m_io

类型 OLEUIINSERTOBJECT 的结构，用于控制行为的插入对象对话框。

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>备注

直接或通过成员函数，可以修改此结构的成员。

有关详细信息，请参阅[OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) Windows SDK 中的结构。

## <a name="see-also"></a>请参阅

[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
