---
title: COlePropertiesDialog 类
ms.date: 11/04/2016
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
ms.openlocfilehash: e574f535609ec9401bd76badf11fa7e05cc0c619
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781856"
---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog 类

封装 Windows 公共 OLE“对象属性”对话框。

## <a name="syntax"></a>语法

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|构造 `COlePropertiesDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COlePropertiesDialog::DoModal](#domodal)|显示对话框中，并允许用户进行选择。|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|缩放的文档项发生更改时由框架调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|用于初始化的"常规"页的结构`COlePropertiesDialog`对象。|
|[COlePropertiesDialog::m_lp](#m_lp)|用于初始化的"链接"页的结构`COlePropertiesDialog`对象。|
|[COlePropertiesDialog::m_op](#m_op)|用于初始化的结构`COlePropertiesDialog`对象。|
|[COlePropertiesDialog::m_psh](#m_psh)|用于添加其他自定义属性页的结构。|
|[COlePropertiesDialog::m_vp](#m_vp)|用于自定义的"视图"页的结构`COlePropertiesDialog`对象。|

## <a name="remarks"></a>备注

常见的 OLE 对象属性对话框提供了方便地显示和修改 OLE 文档项以与 Windows 标准一致的方式的属性。 等等，这些属性包括文档项，项的链接显示的图标和图像缩放和信息 （如果该项目链接） 选项表示的文件的信息。

若要使用`COlePropertiesDialog`对象，请先创建对象使用`COlePropertiesDialog`构造函数。 已构造对话框的后，调用`DoModal`成员函数以显示该对话框，并允许用户修改的项的任何属性。 `DoModal` 返回用户选择确定 (IDOK) 或取消 (IDCANCEL) 按钮。 除了确定和取消按钮，还有应用按钮。 当用户选择应用时，任何对文档项的属性所做的更改应用于项和其映像会自动更新，但将保持活动状态。

[M_psh](#m_psh)数据成员是指向`PROPSHEETHEADER`结构，并在大多数情况下不需要显式访问。 一个例外是当您需要默认常规、 视图和链接页之外的附加属性页。 在这种情况下，您可以修改`m_psh`数据成员，以包括自定义页面之前，调用`DoModal`成员函数。

OLE 对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs.h

##  <a name="colepropertiesdialog"></a>  COlePropertiesDialog::COlePropertiesDialog

创建一个 `COlePropertiesDialog` 对象。

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*pItem*<br/>
要访问其属性的文档项的指针。

*nScaleMin*<br/>
最小缩放比例的文档项图像的百分比。

*nScaleMax*<br/>
最多可缩放的文档项图像的百分比。

*pParentWnd*<br/>
到对话框的父成员或所有者的指针。

### <a name="remarks"></a>备注

派生从常见 OLE 对象属性对话框类`COlePropertiesDialog`才能实现缩放的文档项。 实现此类的实例的任何对话框将不支持缩放的文档项。

默认情况下，常见的 OLE 对象属性对话框中有三个默认页：

- 常规

   此页包含所选的文档项表示的文件的系统信息。 从此页中，用户可以将选定的项转换为另一种类型。

- 视图

   此页包含用于显示项、 更改该图标，以及更改图像的缩放选项。

- 链接

   此页包含用于更改链接的项的位置和更新链接的项的选项。 从此页中，用户可以断开选定项的链接。

若要添加超出所提供的默认页，修改[m_psh](#m_psh)成员变量的构造函数在退出之前你`COlePropertiesDialog`-派生的类。 这是一个高级的实现`COlePropertiesDialog`构造函数。

##  <a name="domodal"></a>  COlePropertiesDialog::DoModal

调用此成员函数以显示 Windows 公共 OLE 对象属性对话框中，并允许用户查看和/或更改文档项的各种属性。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL 如果成功，则否则为 0。 IDOK 和 IDCANCEL 是常数，用于指示是否在用户选择了确定或取消按钮。

如果返回 IDCANCEL，则可以调用 Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror)函数来确定是否发生了错误。

##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp

类型的结构[OLEUIGNRLPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuignrlpropsa)，可用来初始化 OLE 对象属性对话框的常规页。

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>备注

此页显示的类型和嵌入的大小，并允许对转换对话框中的用户访问。 此页还显示链接目标的对象是否链接。

有关详细信息`OLEUIGNRLPROPS`结构，请参阅 Windows SDK。

##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp

类型的结构[OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa)，可用来初始化 OLE 对象属性对话框的链接页。

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>备注

此页显示链接的项的位置，并允许用户更新或中断，请对项的链接。

有关详细信息`OLEUILINKPROPS`结构，请参阅 Windows SDK。

##  <a name="m_op"></a>  COlePropertiesDialog::m_op

类型的结构[OLEUIOBJECTPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiobjectpropsa)，可用来初始化常见的 OLE 对象属性对话框。

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>备注

此结构包含用来初始化的常规、 链接和视图页的成员。

有关详细信息，请参阅 OLEUIOBJECTPROPS 并[OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa) Windows SDK 中的结构。

##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh

类型的结构[PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2)，其成员存储对话框对象的特征。

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>备注

构造后`COlePropertiesDialog`对象，可以使用`m_psh`若要设置之前，调用对话框中的各个方面`DoModal`成员函数。

如果您修改`m_psh`数据成员直接，您将重写任何默认行为。

有关详细信息`PROPSHEETHEADER`结构，请参阅 Windows SDK。

##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp

类型的结构[OLEUIVIEWPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiviewpropsa)，可用来初始化 OLE 对象属性对话框的视图页。

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>备注

此页面允许用户切换"content"和"图标"视图的对象，并更改其缩放的容器中。 当以图标形式显示该对象时，它还允许对更改图标对话框中的用户访问。

有关详细信息`OLEUIVIEWPROPS`结构，请参阅 Windows SDK。

##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale

缩放值已更改，并选择确定或应用时由框架调用。

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>参数

*pItem*<br/>
要访问其属性的文档项的指针。

*nCurrentScale*<br/>
对话框刻度的数字值。

*bRelativeToOrig*<br/>
指示是否缩放应用于文档项的原始大小。

### <a name="return-value"></a>返回值

如果处理; 非零值否则为 0。

### <a name="remarks"></a>备注

默认实现不执行任何操作。 必须重写此函数可启用缩放控件。

> [!NOTE]
>  常见的 OLE 对象属性对话框显示之前，框架将调用此函数带 NULL *pItem* ，-1 表示*nCurrentScale*。 这样做是为了确定是否应启用缩放控件。

## <a name="see-also"></a>请参阅

[MFC 示例 CIRC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage 类](../../mfc/reference/cpropertypage-class.md)
