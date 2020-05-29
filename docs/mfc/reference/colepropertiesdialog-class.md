---
title: COle属性对话类
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
ms.openlocfilehash: f065894ff49af755ab4020f71b0213b19db49054
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374895"
---
# <a name="colepropertiesdialog-class"></a>COle属性对话类

封装 Windows 公共 OLE“对象属性”对话框。

## <a name="syntax"></a>语法

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle 属性对话框：：COle 属性对话框](#colepropertiesdialog)|构造 `COlePropertiesDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle属性对话：:Do模态](#domodal)|显示对话框，并允许用户进行选择。|
|[COle 属性对话框：：应用刻度](#onapplyscale)|当文档项的缩放已更改时，由框架调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COle 属性对话框：：m_gp](#m_gp)|用于初始化`COlePropertiesDialog`对象的"常规"页的结构。|
|[COle 属性对话框：：m_lp](#m_lp)|用于初始化`COlePropertiesDialog`对象的"链接"页的结构。|
|[COle 属性对话框：：m_op](#m_op)|用于初始化对象的结构`COlePropertiesDialog`。|
|[COle属性对话：：m_psh](#m_psh)|用于添加其他自定义属性页的结构。|
|[COle属性对话：：m_vp](#m_vp)|用于自定义`COlePropertiesDialog`对象的"视图"页的结构。|

## <a name="remarks"></a>备注

通用 OLE 对象属性对话框提供了一种以符合 Windows 标准的方式显示和修改 OLE 文档项属性的简单方法。 这些属性包括文档项表示的文件信息、用于显示图标和图像缩放的选项以及项链接上的信息（如果项是链接的）。

要使用`COlePropertiesDialog`对象，请首先使用`COlePropertiesDialog`构造函数创建对象。 构造对话框后，调用`DoModal`成员函数以显示对话框，并允许用户修改项的任何属性。 `DoModal`返回用户是否选择了"确定 （IDOK）"还是"取消"（IDCANCEL）按钮。 除了"确定"和"取消"按钮外，还有一个"应用"按钮。 当用户选择"应用"时，对文档项属性所做的任何更改将应用于该项目，其图像将自动更新，但保持活动状态。

[m_psh](#m_psh)数据成员是指向结构的`PROPSHEETHEADER`指针，在大多数情况下，您不需要显式访问它。 一个例外是，当您需要默认的"常规"、"视图"和"链接"页以外的其他属性页时。 在这种情况下，您可以在调用`m_psh``DoModal`成员函数之前修改数据成员以包括自定义页面。

有关 OLE 对话框的详细信息，请参阅 OLE[中的"对话框](../../mfc/dialog-boxes-in-ole.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>要求

**标题：** afxodlgs.h

## <a name="colepropertiesdialogcolepropertiesdialog"></a><a name="colepropertiesdialog"></a>COle 属性对话框：：COle 属性对话框

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
指向正在访问其属性的文档项的指针。

*nScaleMin*<br/>
文档项图像的最小缩放百分比。

*nScaleMax*<br/>
文档项图像的最大缩放百分比。

*pparentwnd*<br/>
指向对话框的父或所有者的指针。

### <a name="remarks"></a>备注

从`COlePropertiesDialog`派生常见的 OLE 对象属性对话框类，以便实现文档项的缩放。 此类实例实现的任何对话框都不支持文档项的缩放。

默认情况下，常见的 OLE 对象属性对话框有三个默认页面：

- 常规

   此页包含所选文档项表示的文件的系统信息。 从此页面中，用户可以将所选项目转换为其他类型。

- 查看

   此页包含用于显示项目、更改图标和更改图像缩放的选项。

- 链接

   此页包含用于更改链接项目的位置和更新链接项的选项。 从此页面中，用户可以断开所选项目的链接。

要将页面添加到默认提供的页面之外，请在离开[m_psh](#m_psh)`COlePropertiesDialog`派生类的构造函数之前修改m_psh成员变量。 这是构造函数的高级`COlePropertiesDialog`实现。

## <a name="colepropertiesdialogdomodal"></a><a name="domodal"></a>COle属性对话：:Do模态

调用此成员函数以显示 Windows 常见 OLE 对象属性对话框，并允许用户查看和/或更改文档项的各种属性。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL（如果成功）;否则 0。 IDOK 和 IDCANCEL 是指示用户选择"确定"还是"取消"按钮的常量。

如果返回 IDCANCEL，您可以调用 Windows [CommDlg 扩展错误](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能以确定是否发生了错误。

## <a name="colepropertiesdialogm_gp"></a><a name="m_gp"></a>COle 属性对话框：：m_gp

[OLEUIGNRLPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuignrlpropsw)类型的一种结构，用于初始化 OLE 对象属性对话框的"常规"页。

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>备注

此页显示嵌入的类型和大小，并允许用户访问"转换"对话框。 如果对象是链接，此页面还会显示链接目标。

有关结构的详细信息，`OLEUIGNRLPROPS`请参阅 Windows SDK。

## <a name="colepropertiesdialogm_lp"></a><a name="m_lp"></a>COle 属性对话框：：m_lp

用于初始化 OLE 对象属性对话框的链接页的类型[OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw)的结构。

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>备注

此页显示链接项目的位置，并允许用户更新或中断指向该项目的链接。

有关结构的详细信息，`OLEUILINKPROPS`请参阅 Windows SDK。

## <a name="colepropertiesdialogm_op"></a><a name="m_op"></a>COle 属性对话框：：m_op

[用于](/windows/win32/api/oledlg/ns-oledlg-oleuiobjectpropsw)初始化通用 OLE 对象属性对话框的结构。

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>备注

此结构包含用于初始化常规、链接和视图页的成员。

有关详细信息，请参阅 Windows SDK 中的 OLEUIOBJECTPROPS 和[OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw)结构。

## <a name="colepropertiesdialogm_psh"></a><a name="m_psh"></a>COle属性对话：：m_psh

[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)类型的一个结构，其成员存储对话框对象的特征。

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>备注

构造`COlePropertiesDialog`对象后，可以使用`m_psh`在调用`DoModal`成员函数之前设置对话框的各个方面。

如果直接修改`m_psh`数据成员，将覆盖任何默认行为。

有关结构的详细信息，`PROPSHEETHEADER`请参阅 Windows SDK。

## <a name="colepropertiesdialogm_vp"></a><a name="m_vp"></a>COle属性对话：：m_vp

[用于](/windows/win32/api/oledlg/ns-oledlg-oleuiviewpropsw)初始化 OLE 对象属性对话框的"视图"页的结构。

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>备注

此页面允许用户在对象的"内容"和"标志性"视图之间切换，并在容器中更改其缩放。 它还允许用户在对象显示为图标时访问"更改图标"对话框。

有关结构的详细信息，`OLEUIVIEWPROPS`请参阅 Windows SDK。

## <a name="colepropertiesdialogonapplyscale"></a><a name="onapplyscale"></a>COle 属性对话框：：应用刻度

当缩放值已更改并选择了"确定"或"应用"时，由框架调用。

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向正在访问其属性的文档项的指针。

*nCurrentScale*<br/>
对话框刻度的数值。

*b 相对托奥里格*<br/>
指示缩放是否应用于文档项的原始大小。

### <a name="return-value"></a>返回值

处理时非零;否则 0。

### <a name="remarks"></a>备注

默认实现不执行任何操作。 必须重写此函数才能启用缩放控件。

> [!NOTE]
> 在显示常见的 OLE 对象属性对话框之前，框架调用此函数，该函数为*pItem*的 NULL，nCurrentScale 调用 1。 *nCurrentScale* 这样做是为了确定是否应启用缩放控件。

## <a name="see-also"></a>另请参阅

[MFC 样品中国保监会](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage 类](../../mfc/reference/cpropertypage-class.md)
