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
ms.openlocfilehash: b819bc430868717a2df01a086b482dfe6d56cc0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504166"
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
|[COlePropertiesDialog::DoModal](#domodal)|显示对话框并允许用户进行选择。|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|当文档项缩放已更改时由框架调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|用于初始化`COlePropertiesDialog`对象的 "常规" 页的结构。|
|[COlePropertiesDialog::m_lp](#m_lp)|用于初始化`COlePropertiesDialog`对象的 "链接" 页的结构。|
|[COlePropertiesDialog::m_op](#m_op)|用于初始化`COlePropertiesDialog`对象的结构。|
|[COlePropertiesDialog::m_psh](#m_psh)|用于添加其他自定义属性页的结构。|
|[COlePropertiesDialog::m_vp](#m_vp)|用于自定义`COlePropertiesDialog`对象的 "视图" 页的结构。|

## <a name="remarks"></a>备注

常见的 OLE 对象属性对话框提供一种简单的方式, 以与 Windows 标准一致的方式显示和修改 OLE 文档项的属性。 这些属性包括文档项表示的文件的信息、用于显示图标和图像缩放的选项, 以及有关项链接的信息 (如果项已链接)。

若要使用`COlePropertiesDialog`对象, 请先`COlePropertiesDialog`使用构造函数创建对象。 构造对话框后, 调用`DoModal`成员函数以显示对话框, 并允许用户修改项的任何属性。 `DoModal`返回用户是否选择了 "确定" (IDOK) 或 "取消" (IDCANCEL) 按钮。 除了 "确定" 和 "取消" 按钮外, 还有一个 "应用" 按钮。 当用户选择 "应用" 时, 对文档项的属性所做的任何更改都将应用到该项, 并且它的图像将自动更新, 但仍保持活动状态。

[M_psh](#m_psh)数据成员是指向`PROPSHEETHEADER`结构的指针, 在大多数情况下, 不需要显式访问它。 一种例外情况是, 在需要默认的 "常规"、"视图" 和 "链接" 页之外的其他属性页时。 在这种情况下, 您可以`m_psh`在`DoModal`调用成员函数之前修改数据成员以包含您的自定义页。

有关 OLE 对话框的详细信息, 请参阅[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>要求

**标头:** afxodlgs

##  <a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog

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
指向要访问其属性的文档项的指针。

*nScaleMin*<br/>
文档项图像的最小缩放百分比。

*nScaleMax*<br/>
文档项图像的最大缩放百分比。

*pParentWnd*<br/>
指向对话框父对象或所有者的指针。

### <a name="remarks"></a>备注

派生您的公共 OLE 对象属性对话框类`COlePropertiesDialog` , 以便为您的文档项实现缩放。 此类的实例实现的任何对话框都不支持缩放文档项。

默认情况下, "通用 OLE 对象属性" 对话框包含三个默认页面:

- 常规

   此页包含所选文档项所表示的文件的系统信息。 在此页中, 用户可以将所选项转换为另一种类型。

- 视图

   此页面包含用于显示项目、更改图标和更改图像缩放的选项。

- 链接

   此页面包含用于更改链接项的位置和更新链接项的选项。 在此页上, 用户可以断开所选项的链接。

若要添加默认情况下所提供的页面, 请在退出派生类的构造函数`COlePropertiesDialog`之前修改 [m_psh](#m_psh) 成员变量。 这是`COlePropertiesDialog`构造函数的高级实现。

##  <a name="domodal"></a>COlePropertiesDialog::D oModal

调用此成员函数以显示 "Windows common OLE 对象属性" 对话框, 并允许用户查看和/或更改文档项的各种属性。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

如果成功, 则为 IDOK 或 IDCANCEL;否则为0。 IDOK 和 IDCANCEL 是常量, 用于指示用户是否选择了 "确定" 或 "取消" 按钮。

如果返回 IDCANCEL, 则可以调用 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函数来确定是否发生了错误。

##  <a name="m_gp"></a>COlePropertiesDialog::m_gp

类型为[OLEUIGNRLPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuignrlpropsw)的结构, 用于初始化 OLE 对象的 "属性" 对话框的 "常规" 页。

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>备注

此页面显示嵌入的类型和大小, 并允许用户访问 "转换" 对话框。 如果对象是链接, 则此页还会显示链接目标。

有关`OLEUIGNRLPROPS`结构的详细信息, 请参阅 Windows SDK。

##  <a name="m_lp"></a>COlePropertiesDialog::m_lp

类型为[OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw)的结构, 用于初始化 OLE 对象的 "属性" 对话框的 "链接" 页。

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>备注

此页面显示链接项的位置, 并允许用户更新或中断与该项的链接。

有关`OLEUILINKPROPS`结构的详细信息, 请参阅 Windows SDK。

##  <a name="m_op"></a>COlePropertiesDialog::m_op

[OLEUIOBJECTPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiobjectpropsw)类型的结构, 用于初始化公用 OLE 对象属性对话框。

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>备注

此结构包含用于初始化 "常规"、"链接" 和 "视图" 页的成员。

有关详细信息, 请参阅 Windows SDK 中的 OLEUIOBJECTPROPS 和[OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw)结构。

##  <a name="m_psh"></a>COlePropertiesDialog::m_psh

[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)类型的结构, 其成员存储对话框对象的特征。

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>备注

构造`COlePropertiesDialog`对象之后, 您可以使用`m_psh`在调用`DoModal`成员函数之前设置对话框的各个方面。

如果直接修改`m_psh`数据成员, 将重写任何默认行为。

有关`PROPSHEETHEADER`结构的详细信息, 请参阅 Windows SDK。

##  <a name="m_vp"></a>COlePropertiesDialog::m_vp

类型为[OLEUIVIEWPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiviewpropsw)的结构, 用于初始化 OLE 对象的 "属性" 对话框的 "视图" 页。

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>备注

此页允许用户在对象的 "content" 和 "图标" 视图之间切换, 并更改其在容器中的缩放比例。 它还允许用户在将对象显示为图标时访问 "更改图标" 对话框。

有关`OLEUIVIEWPROPS`结构的详细信息, 请参阅 Windows SDK。

##  <a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale

当缩放值已更改并且选择了 "确定" 或 "应用" 时由框架调用。

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要访问其属性的文档项的指针。

*nCurrentScale*<br/>
对话框比例的数值。

*bRelativeToOrig*<br/>
指示缩放是否适用于文档项的原始大小。

### <a name="return-value"></a>返回值

如果已处理, 则为非零;否则为0。

### <a name="remarks"></a>备注

默认实现不执行任何操作。 必须重写此函数以启用缩放控件。

> [!NOTE]
>  在显示 "公用 OLE 对象属性" 对话框之前, 框架将调用此函数, 并在*pItem*中使用 NULL 值, 对*nCurrentScale*调用。 这样做是为了确定是否应启用缩放控件。

## <a name="see-also"></a>请参阅

[MFC 示例 CIRC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage 类](../../mfc/reference/cpropertypage-class.md)
